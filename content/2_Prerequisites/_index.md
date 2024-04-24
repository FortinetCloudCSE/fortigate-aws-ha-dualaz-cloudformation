---
title: "Prerequisites"
menuTitle: "Prerequisites"
weight: 20
---

Before attempting to create a stack with the templates, a few prerequisites should be checked to ensure a successful deployment:
1.	An AMI subscription must be active for the FortiGate license type being used in the template.
    * [Intel BYOL Marketplace Listing](https://aws.amazon.com/marketplace/pp/prodview-lvfwuztjwe5b2)
    * [Intel PAYG Marketplace Listing](https://aws.amazon.com/marketplace/pp/prodview-wory773oau6wq)
    * [ARM BYOL Marketplace Listing](https://aws.amazon.com/marketplace/pp/prodview-ccnrlwz74uwgk)
    * [ARM PAYG Marketplace Listing](https://aws.amazon.com/marketplace/pp/prodview-ohcnwr7nr2icy)

2.	The solution requires 3 EIPs to be created so ensure the AWS region being used has available capacity.  Reference [AWS Documentation](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-resource-limits.html) for more information on EC2 resource limits and how to request increases.

3.	If BYOL licensing is to be used, ensure these licenses have been registered on the support site.

4.   **Create a new S3 bucket in the same region where the template will be deployed.  If the bucket is in a different region than the template deployment, bootstrapping will fail and the FGTs will be inaccessible**.

5.  If BYOL licensing is to be used, upload these licenses to the root directory of the same S3 bucket from the step above.

6.  **Ensure that an S3 gateway endpoint is deployed and assigned to both of the PublicSubnet's AWS route table.**  If you are using the 'NewSecurityVPC_FGCP_DualAZ.template.json' template, then this will be deployed for you.  Reference [AWS Documentation](https://docs.aws.amazon.com/vpc/latest/userguide/vpce-gateway.html#create-gateway-endpoint) for further information.

7.  **Ensure that all of the PublicSubnet's and HAmgmtSubnet's AWS route tables have a default route to an AWS Internet Gateway.**  Reference [AWS Documentation](https://docs.aws.amazon.com/vpc/latest/userguide/VPC_Route_Tables.html#route-tables-internet-gateway) for further information.  Otherwise you must set the variable **only_private_ec2_api** to **'yes'**.
