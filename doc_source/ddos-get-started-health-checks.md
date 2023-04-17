# Configure health\-based detection for your protections<a name="ddos-get-started-health-checks"></a>

You can optionally configure Shield Advanced to use health\-based detection, which can improve responsiveness and accuracy in attack detection and mitigation\. You can use this option with any resource type except for Route 53 hosted zones\. 

To use health\-based detection, you first need to define a health check for your resource in Route 53 and then associate the health check with your Shield Advanced protection\. It's important that the health check that you configure accurately reflect the health of the resource\. For information and examples for configuring health checks to use with Shield Advanced, see [Configuring health\-based detection using health checks](ddos-advanced-health-checks.md)\. 

Health checks are required for Shield Response Team \(SRT\) proactive engagement support\. For information about proactive engagement, see [Configuring proactive engagement](ddos-srt-proactive-engagement.md)\.

**Note**  
Health checks must be reporting healthy when you associate them with your Shield Advanced protections\.

**To configure health\-based detection**

1. Under **Associated Health Check**, choose the ID of the health check that you want to associate with the protection\. 
**Note**  
If you do not see the health check you need, go to the Route 53 console and verify the health check and its ID\. For information, see [Creating and Updating Health Checks](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/health-checks-creating.html)\.

1. Choose **Next**\. The console wizard advances to the alarms and notifications page\. 