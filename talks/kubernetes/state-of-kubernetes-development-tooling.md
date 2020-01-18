# GOTO 2019 - Kubernetes Day 3: The State of Kubernetes Development Tooling by Ellen Körbes

[Link to talk](https://www.youtube.com/watch?v=b1RsNXGLuUk)

# Tools

`Squash`: Attach a debugger to containers.

`Stern`:

- Stream logs from multiple pods in your cluster.
- You can stream your logs everywhere in your namespace

- Just one terminal window

`Forge`: Fancy shell script

`Inlets`: Reverse proxy and tunnel

`Ksync`: Watches your file system

`Garden`:

- You don't need kubernetes manifests
- Allow in cluster builds, good when you want
  to share image caches inside your team so everybody
  uses the same cache
- Tests are a first class citicen
