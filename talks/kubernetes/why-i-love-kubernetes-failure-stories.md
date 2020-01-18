# GOTO 2019 - Why I love Kubernetes failure Stories and You Should Too - Henning Jacobs (Senior Principal at Zalando)

[Link to talk](https://www.youtube.com/watch?v=E0GBU8Q-VFY)

#

The fact that https://github.com/hjacobs/kubernetes-failure-stories exists is a symptom of how difficult Kubernetes is.

# Incident 1

- Http retries
- No DNS caching
- Kubernetes ndots: 5 problems
- Short maximum lifetime of HTTP connections
- Fixed memory limit for CoreDNS
- Monitoring affected by DNS outage

DNS down in the cluster suddenly outage for the whole cluster.

# Common pitfalls

- Disable CPU throttling as it's more aggresive than what you would expect
- Insufficient e2e tests
- Most people do the same mistake: No Readiness and liveness probes or wrong readines/liveness. See [blogpost](https://srcco.de/posts/kubernetes-liveness-probes-are-dangerous.html)
- Resource requests limits you should always set.
- DNS. It's always DNS. Also, one pod for ClusterDns is not enough

# Actions

- Define SLOS (Service Level Objective). Ex: time to release.
- Created a way to get temporary write access for Developers. Devs don't have write access to Prod.

# Why kubernetes?

- Provides `enough abstractions` (StatefulSet, CronJob...)
- Provides `consistency` (API spec/status)
- It's extensible trough annotations, crds, api aggregations...
- Certain compatibility guaranteed with versioning
- Widely adopted by all cloud providers
- Works across environments and implementations, even with serverless you can benefit from Kubernetes.
