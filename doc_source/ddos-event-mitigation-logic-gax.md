# AWS Shield mitigation logic for AWS Global Accelerator standard accelerators<a name="ddos-event-mitigation-logic-gax"></a>

Shield mitigations only allow valid traffic to reach the listener endpoints of a Global Accelerator standard accelerator\. Standard accelerators are deployed globally, and they provide you with IP addresses that you can use to route traffic to AWS resources in any AWS Region\. The rate limits that Shield enforces for a Global Accelerator mitigation are based on the capacities of the resources to which the standard accelerator routes traffic\. Shield places mitigations when the total traffic exceeds the determined rate, and also when a fraction of that rate is exceeded for known DDoS vectors\. 

When you configure a standard accelerator, you define endpoint groups for each AWS Region where you'll route traffic for your application\. When Shield places a mitigation, it calculates the capacity of each endpoint group and updates rate limits at each Shield DDoS mitigation system accordingly\. The rate varies for each location, based on assumptions made by Shield about how traffic will route from the internet to your AWS resources\. The capacity for an endpoint group is calculated as the number of resources in the group multiplied by the lowest capacity for any resource in the group\. At regular intervals, Shield recalculates the capacity for your application and updates the rate limits as needed\. 

**Note**  
Using traffic dials to change the percentage of traffic that's directed to an endpoint group doesn't change how Shield calculates or distributes rate limits to its DDoS mitigation systems\. If you use traffic dials, configure your endpoint groups to mirror one another in terms of resource type and quantity\. This helps ensure that the capacity calculated by Shield is representative of the resources that are serving traffic for your application\.

For more information about endpoint groups and traffic dials in Global Accelerator, see [Endpoint groups in AWS Global Accelerator standard accelerators](https://docs.aws.amazon.com/global-accelerator/latest/dg/about-endpoint-groups.html)\.