# Scaling an EBS Volume for a Linux Virtual Machine

**Project type:** Cloud/DevOps implementation project documented in my portfolio.

## Implementation summary

I expanded the storage available to a Linux virtual machine using Amazon EBS. The project addressed both the AWS volume capacity and the usable capacity inside the operating system. I inspected the existing volume, partition and filesystem sizes. I modified the EBS volume capacity and waited for the appropriate modification state. I extended the partition where required, then grew the filesystem using the command appropriate to its type. I checked the resulting usable capacity and confirmed that existing files and application access remained available. The project output consisted of a larger EBS volume and expanded Linux filesystem. The meaningful output is increased capacity visible inside the operating system, rather than only a larger value in the AWS console. This approach enables storage growth as application data increases. The business opportunity is avoiding capacity related service interruptions and extending the useful life of an existing environment. Storage expansion supports growing application files, logs or datasets. It provides a practical capacity change for an existing virtual machine while the team assesses longer term storage requirements.

## Technologies and evidence

See the corresponding project in my original report for implementation details. Add source code, sanitized screenshots, configuration files, and validation logs here when available.


