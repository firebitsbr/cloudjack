# CloudJack » AWS Subdomain Hijacking

### Route53/CloudFront Vulnerability Assessment Utility

CloudJack scans AWS accounts for subdomain hijacking vulnerabilities as a result of decoupled Route53 and CloudFront configurations. This vulnerability exists if a Route53 alias references 1) a deleted CloudFront web distribution or 2) an active CloudFront web distribution with deleted CNAME(s).

If this decoupling is discovered by an attacker, they can simply create their own CloudFront web distribution and/or CNAME(s) that match the victim's Route53 A record host name. Exploitation of this vulnerability results in the ability to spoof the victim's web site content, which otherwise would have been accessed through the victim's CloudFront web distribution and content origin.

More information about CloudJacking can be found at https://www.slideshare.net/BryanMcAninch/cloud-jacking

Requirements:

1. AWS IAM access key ID and corresponding secret key
2. AWS CLI installation configured with access key ID and secret key
3. AWS IAM policy allowing Route53 ListHostedZones and ListResourceRecordSets actions
4. AWS IAM policy allowing CloudFront ListDistributions actions
5. Python and python boto3 package

Usage:

user@host: python cloudjack.py

References:

http://docs.aws.amazon.com/Route53/latest/APIReference/API_ListHostedZones.html
http://docs.aws.amazon.com/Route53/latest/APIReference/API_ListResourceRecordSets.html
http://docs.aws.amazon.com/cloudfront/latest/APIReference/API_ListDistributions.html
http://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_access-keys.html

Wishlist:

1. Offensive reconnaisance and exploitation features
2. Parsable output formatting options (json, xml, csv)
