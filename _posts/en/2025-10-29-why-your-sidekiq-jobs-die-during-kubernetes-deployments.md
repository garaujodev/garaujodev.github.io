---
layout: post
title: "TIL: Why Your Sidekiq Jobs Die During Kubernetes Deployments (and How to Fix It)"
date: 2025-10-29 09:00:00 -0300
categories: sidekiq rails kubernetes
description: "Fix Sidekiq pods getting killed during Kubernetes rollouts. Handle SIGTERM correctly and stop losing jobs mid-deployment."
---

Recently I was debugging an issue with my **Sidekiq + Kubernetes** setup. During rollouts, some pods were getting killed abruptly, jobs were interrupted, and deploys took way longer than expected.

After reading Sidekiq’s Kubernetes guide￼, I realized what was happening: I was starting Sidekiq through a `.sh` script that I called at the end of my **Dockerfile**.

### Problematic approach
```dockerfile
CMD ["/bin/sh", "-c", "./start_sidekiq.sh"]
```

When Kubernetes sends the **SIGTERM** signal during a rollout, it only reaches the shell process, not Sidekiq itself.
That means Sidekiq never receives the signal to enter the quiet state and finish its in-progress jobs, it just gets **SIGKILLed** once `terminationGracePeriodSeconds` expires.

In my case, that explained why some jobs were vanishing mid-deploy.


### The fix
Run Sidekiq directly, without a shell wrapper, so the Kubernetes signal reaches the actual process:

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: sidekiq-deployment
spec:
  template:
    spec:
      terminationGracePeriodSeconds: 120 # wait long enough for jobs to finish
      containers:
        - name: sidekiq
          image: myapp:latest
          command: ["bundle", "exec", "sidekiq"]
          args: ["-t", "100", "-e", "production", "-C", "config/sidekiq.yml"]
```

With this setup, Sidekiq gets the TERM signal directly, goes into quiet mode, and shuts down gracefully - no more lost jobs or stuck rollouts.

A small detail that’s easy to miss, but it makes deployments faster, safer, and more predictable. Kubernetes can’t protect you from a misplaced `/bin/sh -c`.