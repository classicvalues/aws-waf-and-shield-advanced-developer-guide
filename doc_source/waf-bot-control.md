# AWS WAF Bot Control<a name="waf-bot-control"></a>

The Bot Control managed rule group provides a basic, common protection level that adds labels to self\-identifying bots, verifies generally desirable bots, and detects high confidence bot signatures\. This gives you the ability to monitor and control common categories of bot traffic\. Bot Control also provides a targeted protection level that adds detection for advanced bots that don't self identify\. Targeted protections use advanced detection techniques such as browser interrogation, fingerprinting, and behavior heuristics to identify bad bot traffic and then applies mitigation controls such as rate limiting and CAPTCHA and Challenge rule actions\. For additional details, see [AWS WAF Bot Control rule group](aws-managed-rule-groups-bot.md)\. 

**Note**  
You are charged additional fees when you use this managed rule group\. For more information, see [AWS WAF Pricing](http://aws.amazon.com/waf/pricing/)\.

With Bot Control, you can easily monitor, block, or rate limit bots such as scrapers, scanners, crawlers, status monitors, and search engines\. If you use the targeted inspection level of the rule group, you can also challenge bots that don't self identify, making it harder and more expensive for malicious bots to operate against your website\. You can protect your applications using the Bot Control managed rule group alone, or in combination with other AWS Managed Rules rule groups and your own custom AWS WAF rules\. 

Bot Control includes a console dashboard that shows how much of your current traffic is coming from bots, based on request sampling\. With the Bot Control managed rule group added to your web ACL, you can take action against bot traffic and receive detailed, real\-time information about common bot traffic coming to your applications\. 

When AWS WAF evaluates a web request against the Bot Control managed rule group, the rule group adds labels to requests that it detects as bot related, for example the category of bot and the bot name\. You can match against these labels in your own AWS WAF rules to customize handling\. The labels that are generated by the Bot Control managed rule group are included in Amazon CloudWatch metrics and your web ACL logs\. 

You can also use AWS Firewall Manager AWS WAF policies to deploy the Bot Control managed rule group across your applications in multiple accounts that are part of your organization in AWS Organizations\.