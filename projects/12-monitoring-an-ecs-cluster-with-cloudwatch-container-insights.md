# Monitoring an ECS Cluster with CloudWatch Container Insights

**Project type:** Cloud/DevOps implementation project documented in my portfolio.

## Implementation summary

I implemented CloudWatch monitoring for an ECS cluster, using Container Insights to inspect the container environment and its resource behavior. I enabled the supported Container Insights configuration for the ECS environment. I generated workload activity and inspected the available cluster, service and task views. I reviewed CPU, memory and other collected telemetry. I related the observations to the running workload and documented where to find metrics and logs during troubleshooting. The project output consisted of Container telemetry visible in CloudWatch for the ECS environment, allowing resource usage and operational behavior to be inspected. This approach enables informed troubleshooting and capacity discussions. For Flexytie, the business opportunity is identifying resource pressure earlier and basing sizing changes on observed demand; cost reductions require actual before and after measurements. The telemetry can help a team investigate resource pressure and compare usage across workloads. This information supports capacity decisions and troubleshooting discussions using observed behavior.

