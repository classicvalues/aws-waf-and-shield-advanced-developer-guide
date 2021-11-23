# Log Fields<a name="logging-fields"></a>

The following list describes the possible log fields\. 

**action**  
The action\. `ALLOW` and `BLOCK` are terminating rule actions\. `COUNT` is a non\-terminating rule action\. `CAPTCHA` is non\-terminating if the request includes a valid CAPTCHA token and terminating if it doesn't\. 

**args**  
The query string\.

**captchaResponse**  
The CAPTCHA response to the request, populated when the CAPTCHA action results in the termination of web request inspection\. The CAPTCHA action terminates web request inspection when the request either doesn't include a CAPTCHA token or the token is invalid or expired\. This field includes a response code and a failure reason\. When a CAPTCHA action results in the web request being allowed, the information is captured in the field `nonTerminatingMatchingRules`\.

**clientIp**  
The IP address of the client sending the request\.

**country**  
The source country of the request\. If AWS WAF is unable to determine the country of origin, it sets this field to `-`\. 

**excludedRules**  
The list of rules in the rule group that you have excluded\. The action for these rules is set to COUNT\.    
exclusionType  
A type that indicates that the excluded rule has the action COUNT\.  
ruleId  
The ID of the rule within the rule group that is excluded\.

**formatVersion**  
The format version for the log\.

**headers**  
The list of headers\.

**httpMethod**  
The HTTP method in the request\.

**httpRequest**  
The metadata about the request\.

**httpSourceId**  
The source ID\. This field shows the ID of the associated resource\. 

**httpSourceName**  
The source of the request\. Possible values: `CF` for Amazon CloudFront, `APIGW` for Amazon API Gateway, `ALB` for Application Load Balancer, and `APPSYNC` for AWS AppSync\.

**httpVersion**  
The HTTP version\.

**labels**  
The labels on the web request\. These labels were applied by rules that were used to evaluate the request\. 

**limitKey**  
Indicates the IP address source that AWS WAF should use to aggregate requests for rate limiting by a rate\-based rule\. Possible values are `IP`, for web request origin, and `FORWARDED_IP`, for an IP forwarded in a header in the request\.

**limitValue**  
The IP address used by a rate\-based rule to aggregate requests for rate limiting\. If a request contains an IP address that isn't valid, the `limitvalue` is `INVALID`\.

**maxRateAllowed**  
The maximum number of requests, which have an identical value in the field that is specified by `limitKey`, allowed in a five\-minute period\. If the number of requests exceeds the `maxRateAllowed` and the other predicates specified in the rule are also met, AWS WAF triggers the action that is specified for this rule\.

**nonTerminatingMatchingRules**  
The list of non\-terminating rules in the rule group that match the request\.     
action  
This is either `COUNT` or `CAPTCHA`\. The CAPTCHA action is non\-terminating when the web request contains a valid CAPTCHA token\.  
ruleId  
The ID of the rule within the rule group that matches the request and was non\-terminating\.   
ruleMatchDetails  
Detailed information about the rule that matched the request\. This field is only populated for SQL injection and cross\-site scripting \(XSS\) match rule statements\. 

**rateBasedRuleId**  
The ID of the rate\-based rule that acted on the request\. If this has terminated the request, the ID for `rateBasedRuleId` is the same as the ID for `terminatingRuleId`\.

**rateBasedRuleList**  
The list of rate\-based rules that acted on the request\.

**requestHeadersInserted**  
The list of headers inserted for custom request handling\.

**requestId**  
The ID of the request, which is generated by the underlying host service\. For Application Load Balancer, this is the trace ID\. For all others, this is the request ID\. 

**responseCodeSent**  
The response code sent with a custom response\.

**ruleGroupId**  
The ID of the rule group\. If the rule blocked the request, the ID for `ruleGroupID` is the same as the ID for `terminatingRuleId`\. 

**ruleGroupList**  
The list of rule groups that acted on this request\. 

**terminatingRule**  
The rule within the rule group that terminated the request\. If this is a non\-null value, it also contains a **ruleId** and **action**\. 

**terminatingRuleId**  
The ID of the rule that terminated the request\. If nothing terminates the request, the value is `Default_Action`\.

**terminatingRuleMatchDetails**  
Detailed information about the terminating rule that matched the request\. A terminating rule has an action that ends the inspection process against a web request\. Possible actions for a terminating rule are `ALLOW`, `BLOCK`, and `CAPTCHA`\. The matching rule might have more than one inspection criteria that must be met, so the details for the terminating rule are provided as an array of match criteria\. This is only populated for SQL injection and cross\-site scripting \(XSS\) match rule statements\. As with all rule statements that inspect for more than one thing, AWS WAF applies the action on the first match and stops inspecting the web request\. A web request with a terminating action could contain other threats, in addition to the one reported in the log\.

**terminatingRuleType**  
The type of rule that terminated the request\. Possible values: RATE\_BASED, REGULAR, GROUP, and MANAGED\_RULE\_GROUP\.

**timestamp**  
The timestamp in milliseconds\.

**uri**  
The URI of the request\. The preceding code example demonstrates what the value would be if this field had been redacted\.

**webaclId**  
The GUID of the web ACL\.