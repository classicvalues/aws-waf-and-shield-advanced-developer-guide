# Configuration required for Application Load Balancers that are CloudFront origins<a name="waf-tokens-with-alb-and-cf"></a>

Read this section if you associate your web ACL to an Application Load Balancer and you deploy the Application Load Balancer as the origin for a CloudFront distribution\.

With this architecture, you need to provide the following additional configuration in order for the token information to be handled correctly\.
+ Configure CloudFront to forward the `aws-waf-token` cookie to the Application Load Balancer\. By default, CloudFront removes cookies from the web request before forwarding it to the origin\. To keep the token cookie with the web request, configure CloudFront cache behavior to include either just the token cookie or all cookies\. For information about how to do this, see [Caching content based on cookies](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/Cookies.html) in the *Amazon CloudFront Developer Guide*\.
+ Configure AWS WAF so that it recognizes the domain of the CloudFront distribution as a valid token domain\. By default, CloudFront sets the `Host` header to the Application Load Balancer origin, and AWS WAF uses that as the domain of the protected resource\. The client browser, however, sees the CloudFront distribution as the host domain, and tokens that are generated for the client use the CloudFront domain as the token domain\. Without any additional configuration, when AWS WAF checks the protected resource domain against the token domain, it will get a mismatch\. To fix this, add the CloudFront distribution domain name to the token domain list in your web ACL configuration\. For information about how to do this, see [Configuring the web ACL token domain list](waf-tokens-domains.md#waf-tokens-domain-lists)\.