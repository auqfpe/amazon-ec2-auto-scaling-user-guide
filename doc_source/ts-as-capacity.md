# Troubleshooting Auto Scaling: Capacity Limits<a name="ts-as-capacity"></a>

This page provides information about issues with the capacity limits of your Auto Scaling group, potential causes, and the steps you can take to resolve the issues\.

To retrieve an error message, see [Retrieving an Error Message](CHAP_Troubleshooting.md#RetrievingErrors)\.

If your EC2 instances fail to launch due to issues with the capacity limits of your Auto Scaling group, you might get one or more of the following error messages\.

**Topics**
+ [We currently do not have sufficient <instance type> capacity in the Availability Zone you requested \(<requested Availability Zone>\)\.\.\.\.](#ts-as-capacity-1)
+ [<number of instances> instance\(s\) are already running\. Launching EC2 instance failed\.](#ts-as-capacity-2)

## We currently do not have sufficient <instance type> capacity in the Availability Zone you requested \(<requested Availability Zone>\)\.\.\.\.<a name="ts-as-capacity-1"></a>
+ **Error Message**: We currently do not have sufficient <instance type> capacity in the Availability Zone you requested \(<requested Availability Zone>\)\. Our system will be working on provisioning additional capacity\. You can currently get <instance type> capacity by not specifying an Availability Zone in your request or choosing <list of Availability Zones that currently supports the instance type>\. Launching EC2 instance failed\.
+ **Cause**: At this time, Auto Scaling cannot support your instance type in your requested Availability Zone\. 
+ **Solution**: 

  1. Create a new launch configuration by following the recommendations in the error message\.

  1. Update your Auto Scaling group with the new launch configuration using the [update\-auto\-scaling\-group](http://docs.aws.amazon.com/cli/latest/reference/autoscaling/update-auto-scaling-group.html) command\.

## <number of instances> instance\(s\) are already running\. Launching EC2 instance failed\.<a name="ts-as-capacity-2"></a>
+ **Cause**: The Auto Scaling group has reached the limit set by the `DesiredCapacity` parameter\.
+ **Solution**:
  + Update your Auto Scaling group by providing a new value for the `--desired-capacity` parameter using the [update\-auto\-scaling\-group](http://docs.aws.amazon.com/cli/latest/reference/autoscaling/update-auto-scaling-group.html) command\.
  + If you've reached your limit for number of EC2 instances, you can request an increase\. For more information, see [AWS Service Limits](http://docs.aws.amazon.com/general/latest/gr/aws_service_limits.html)\.