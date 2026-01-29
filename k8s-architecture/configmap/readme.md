# Kubernetes ConfigMap

## What is a ConfigMap?

A **ConfigMap** in Kubernetes is an object used to **store non-confidential configuration data** in key-value format.

It allows you to **separate configuration from application code**, so you don’t need to rebuild container images every time a configuration changes.

Examples of configuration data:
- Environment variables
- Application settings
- Configuration files
- Command-line arguments

---

## Why Use ConfigMap?

Without ConfigMaps:
- Configuration is hardcoded inside the application
- Any change requires rebuilding and redeploying the image

With ConfigMaps:
- Configuration is managed separately
- Easier updates and better maintainability
- Same container image can be used across environments (dev, staging, prod)

---

## How ConfigMap Works

1. Configuration values are stored in a ConfigMap.
2. Pods reference the ConfigMap.
3. Kubernetes injects the values into the container as:
   - Environment variables
   - Files inside the container
   - Command-line arguments

---

## Common Use Cases

- Application environment variables
- Database hostnames and ports
- Feature flags
- Application configuration files (YAML, JSON, properties)

---

## Creating a ConfigMap (YAML Example)

```yaml
apiVersion: v1
kind: ConfigMap
metadata:
  name: app-config
data:
  APP_NAME: my-application
  APP_ENV: production
```
---
### Best Practices

- Use ConfigMaps only for non-sensitive data
- Keep ConfigMaps small and readable
- Use one ConfigMap per application or feature
- Version your ConfigMaps when making major changes
- Combine with Secrets for sensitive values
---
### Advantages of ConfigMap

- Decouples configuration from code
- Easy configuration management
- Environment-specific customization
- Improves portability and reusability
---
### Limitations

- Not suitable for sensitive data
- Large ConfigMaps can be hard to manage
- Requires pod restart to apply changes
