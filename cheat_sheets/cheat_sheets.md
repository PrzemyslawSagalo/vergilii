# Cheat Sheets

## Python

### Naming convention for functions and variables
| C++ Access Specifier | Python Convention          | Description                                                                                  |
|----------------------|---------------------------|-----------------------------------------------------------------------------------------------|
| Public               | (No specific convention)  | Members are accessible from outside the class.                                                |
| Private              | Double underscore `__foo` | Members are not directly accessible from outside the class. Name mangling changes the name to include the class name, preventing accidental access. |
| Protected            | Single underscore `_foo`  | By convention, these are for internal use. They can still be accessed, reflecting Python's flexible approach. |

**Name Mangling:**
When a child class and its parent class both have attributes named with double underscores (`__private_var`), Python treats them as separate attributes. This is because Python changes the name of these attributes to include the class name (`_Parent__private_var` for the parent and `_Child__private_var` for the child). This ensures they don't interfere with each other, keeping the parents' attributes separate from the child's.

## CI/CD/CD

### Deplyments

| Deployment Method | How It Works | When to Use |
|-------------------|--------------|-------------|
| **Blue/Green** | Two identical environments (blue = current, green = new). The new version is deployed to the inactive environment while current version remains live. Traffic is switched instantly between environments. Both environments remain fully provisioned. | Best for critical applications requiring zero-downtime deployments. Useful when you can afford duplicate infrastructure (e.g., production e-commerce, financial services). |
| **Canary** | New version is initially deployed to a subset of the infrastructure. Traffic is gradually shifted using metrics-based evaluation. Can be based on user segments, geographic regions, or random sampling. Requires sophisticated monitoring and traffic control systems. | Ideal for risk mitigation when deploying major changes. Best when you have strong monitoring and want to validate changes with real user traffic before full rollout. Common in SaaS and consumer-facing applications. |
| **Rolling** | Updates are deployed incrementally across server groups or pods. Each group is taken out of service, updated, verified, and returned to service before moving to next group. | Suitable for stateless applications that can handle temporary capacity reduction and mixed versions. Good for organizations with limited infrastructure resources. Common in containerized environments. |
| **Recreate** | Complete replacement where all instances of old version are terminated before new version is deployed. Results in application downtime during deployment. | Appropriate for development/testing environments or non-critical internal applications where downtime is acceptable. Also used when major breaking changes prevent running mixed versions. |
