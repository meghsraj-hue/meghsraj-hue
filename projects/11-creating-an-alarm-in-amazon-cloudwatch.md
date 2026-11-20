# Creating an Alarm in Amazon CloudWatch

**Project type:** Cloud/DevOps implementation project documented in my portfolio.

## Implementation summary

I created a CloudWatch alarm to monitor a resource condition and make a threshold breach visible through an alarm state. I selected the resource metric and defined the threshold, evaluation period and missing data behavior. I configured the alarm action supported by the project. I observed the metric and tested the state transition using a suitable condition. I confirmed notification delivery separately if a notification target was configured. I documented why the threshold is meaningful for the monitored resource. The project output consisted of An alarm that evaluates the chosen metric and changes state when its criteria are met. Notification delivery is an additional result only when tested. This approach enables earlier awareness of abnormal resource behavior. The business opportunity is faster operational response and reduced reliance on manual checks, supported by a clear response process. An operations team can use the alarm as an entry point for a response procedure. Its value depends on selecting a useful threshold and connecting the alert to someone who can investigate the condition.

## Technologies and evidence

See the corresponding project in my original report for implementation details. Add source code, sanitized screenshots, configuration files, and validation logs here when available.

**Evidence status:** Documentation summary; repository artifacts and independent execution evidence should be added or verified before making additional claims.

## Relevance to technical program management

This project illustrates the infrastructure, deployment, dependency, and operational considerations I coordinate across engineering and delivery teams.
