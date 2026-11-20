# Highly Available Load Balanced Architecture Configured Through CLI

**Project type:** Cloud/DevOps implementation project documented in my portfolio.

## Implementation summary

I configured a load balanced architecture through the command line to distribute incoming traffic among healthy service instances. I used the CLI to configure the load balancer, listeners and target membership supported by the environment. I deployed the service on multiple targets and configured health checks. I recorded the actual zone and instance arrangement. The project output consisted of a shared endpoint routing requests to healthy targets. A resilience result requires evidence of continued service during a controlled target failure; multiple targets alone do not prove full high availability. This approach enables traffic distribution and reduces dependence on one service instance. For Flexytie, the business opportunity is improved continuity under target failure, subject to the complete architecture and test results. Traffic distribution can support services that need multiple active instances. Health based routing allows healthy targets to receive traffic when another target becomes unavailable, within the limits of the configured architecture.



## Original implementation walkthrough and screenshots

[View the source-derived technical walkthrough, commands and 46 embedded figures](../evidence/18-azure-load-balancer-high-availability/source-walkthrough.md).
