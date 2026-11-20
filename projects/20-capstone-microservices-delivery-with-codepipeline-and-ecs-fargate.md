# Capstone Microservices Delivery with CodePipeline and ECS Fargate

**Project type:** Cloud/DevOps implementation project documented in my portfolio.

## Implementation summary

I completed a capstone implementation of microservices delivery using AWS CodePipeline and Amazon ECS Fargate, connecting pipeline execution with managed container deployment. I prepared the service repositories and container definitions. I configured image builds and the registry used in the project. I defined Fargate task and service settings, networking and runtime permissions. I connected source, build and deployment stages in CodePipeline. I ran the pipeline, inspected task startup and validated the service endpoints or frontend to backend interaction. The project output consisted of Containerized microservices running as ECS Fargate tasks and delivered through CodePipeline. The project connected pipeline execution with the container runtime and application access. This approach enables container delivery without administering the underlying task servers. For Flexytie, the business opportunity is reduced server maintenance and a consistent deployment process; independent scaling and zero downtime require their own configuration and tests. The capstone provides a managed container delivery pattern for applications with multiple services. Teams can build on it with service specific scaling, deployment policies and operational controls as requirements grow.



## Original implementation walkthrough and screenshots

[View the source-derived technical walkthrough, commands and 47 embedded figures](../evidence/20-ecs-fargate-microservices/source-walkthrough.md).
