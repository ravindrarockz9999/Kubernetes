# Kubernetes Probes

Probes are health checks used by Kubernetes to determine the state of a container and decide when to start traffic, restart a container, or delay other checks.

## Kubernetes supports three types of probes:

- Startup Probe

- Readiness Probe

- Liveness Probe

### Types of Probes and Their Purpose
## 1. Startup Probe

### Purpose:
Checks whether the application has started successfully.

### Why it’s needed:
Some applications take a long time to start. Startup probe prevents Kubernetes from killing the container too early.

### Behavior if it fails:

- ❌ Container is restarted

- Other probes are disabled until startup probe succeeds

### Use when:

Apps have slow initialization (Java, legacy apps, large configs)

## 2. Liveness Probe

### Purpose:
Checks whether the application is still alive.

### Behavior if it fails:

❌ Container is restarted

### Use when:

App may hang, deadlock, or stop responding but not crash

## 3. Readiness Probe

### Purpose:
Checks whether the application is ready to receive traffic.

### Behavior if it fails:

- ✅ Pod stays Running

- ❌ Pod is marked NotReady

- ❌ Traffic is removed from Service

- ❌ Container is NOT restarted

### Use when:

- App depends on DB, cache, or external services

- Temporary overloads should stop traffic but not restart the app

## Probe Check Methods

All three probes (startup, liveness, readiness) support the same check types:

## 1. exec (command)

Runs a command inside the container.
```yaml
exec:
  command: ["cat", "/tmp/healthy"]
```
## 2. httpGet

Sends an HTTP request to a container endpoint.
```yaml
httpGet:
  path: /health
  port: 8080
```
## 3. tcpSocket

Checks if a TCP connection can be established.
```yaml
tcpSocket:
  port: 3306
```
### Summary
- Startup & Liveness → restart the container if they fail ✅

- Readiness → does NOT restart, only marks pod as NotReady ✅

## How Probes Work Together

### Typical setup:

Startup probe runs first (if defined)

After success:

Liveness probe checks health

Readiness probe controls traffic

## Best Practices

- Use startup probe for slow-starting apps
- Use readiness probe to protect users from broken dependencies
- Use liveness probe carefully (bad configs can cause restart loops)
- Avoid making liveness too strict

## Probe timing and behaviour

## 1️⃣ initialDelaySeconds

Time (in seconds) Kubernetes waits after the container starts before running the first probe.
**Example**
```yaml
initialDelaySeconds: 15       # Default: 0 second
```
### Why it exists:

- Gives your app time to boot

- Prevents early false failures

### Applies to:

- readinessProbe
- livenessProbe
- (Usually not needed when using startupProbe)

## 2️⃣ periodSeconds

How often (in seconds) Kubernetes runs the probe.
**Example**
```yaml
periodSeconds: 15            # Default: 10 second
```
- “Check health every 15 seconds”

### Applies to:
All probes
#### Impact:

- Smaller value → faster detection
- Larger value → less load on app

## 3️⃣ timeoutSeconds

How long Kubernetes waits for the probe to respond before marking it as failed.
```yaml
timeoutSeconds: 2           # Default: 1 second
```

- If no response in 2 seconds → probe fails

### Applies to:
All probes

- ⚠️ Too small = false failures under load
- ⚠️ Too large = slow failure detection

## 4️⃣ failureThreshold

Number of consecutive probe failures required before Kubernetes decides the probe has failed.
```yaml
failureThreshold: 3       # Default: 3 failures
```
- 3 failures in a row are needed then status pod will failed and status will CrashloopBackoff

## 5️⃣ successThreshold

Number of consecutive successful probe results required for Kubernetes to consider a probe successful again after it has failed.
```yaml
successThreshold: 2        # Default: 1 Success
```
- 2 successes in a row are required.
