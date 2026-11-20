# Using AWS Lambda to Copy Objects Between S3 Buckets

**Project type:** Cloud/DevOps implementation project documented in my portfolio.

## Implementation summary

I implemented an AWS Lambda function to copy content between S3 buckets, using function based automation for a file handling workflow. I created the source and destination buckets and defined the function logic to copy the intended object. I configured the trigger used in the project and the execution role permissions. I ran the function with a sample object and confirmed the destination object. I reviewed logs and checked for recursive triggering if the workflow writes to a bucket that can invoke the function. The project output consisted of a Lambda function copying S3 content to the intended destination, with invocation logs and a destination object as evidence. This approach enables event driven file distribution or downstream processing. The business opportunity is removing a manual copy step and providing a reusable automation pattern; duplication alone is not a complete backup strategy. The automation pattern can support distribution of uploaded files or movement of objects into a downstream processing location. A dependable business workflow would also define error handling, monitoring and retry behavior.

