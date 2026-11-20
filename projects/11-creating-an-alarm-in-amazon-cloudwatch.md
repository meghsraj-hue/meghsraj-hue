# Creating an Alarm in Amazon CloudWatch

**Project type:** Cloud/DevOps implementation project documented in my portfolio.

## Implementation summary

I created a CloudWatch alarm to monitor a resource condition and make a threshold breach visible through an alarm state. I selected the resource metric and defined the threshold, evaluation period and missing data behavior. I configured the alarm action supported by the project. I observed the metric and tested the state transition using a suitable condition. I confirmed notification delivery separately if a notification target was configured. I documented why the threshold is meaningful for the monitored resource. The project output consisted of An alarm that evaluates the chosen metric and changes state when its criteria are met. Notification delivery is an additional result only when tested. This approach enables earlier awareness of abnormal resource behavior. The business opportunity is faster operational response and reduced reliance on manual checks, supported by a clear response process. An operations team can use the alarm as an entry point for a response procedure. Its value depends on selecting a useful threshold and connecting the alert to someone who can investigate the condition.

