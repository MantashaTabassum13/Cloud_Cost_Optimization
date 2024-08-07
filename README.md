AWS Cloud Cost Optimization - Identifying Stale Resources
Identifying Stale EBS Snapshots
In this guide, we’ll set up an AWS Lambda function designed to identify and delete stale Amazon Elastic Block Store (EBS) snapshots. Stale snapshots are those that are no longer associated with any active EC2 instance and contribute to unnecessary storage costs.

Description
This Lambda function is crafted to optimize cloud storage costs by automating the cleanup of unused EBS snapshots. The function performs the following steps:

Fetch All EBS Snapshots: It retrieves all EBS snapshots owned by the same AWS account ('self').

Retrieve Active EC2 Instances: It gathers a list of EC2 instances that are currently running. Instances that are stopped are also considered to ensure that snapshots related to volumes attached to inactive instances are not mistakenly deleted.

Check Snapshot Associations: For each snapshot, the function determines whether it is associated with a volume. If the volume exists, the function then checks whether the volume is currently attached to any active EC2 instance.

Delete Stale Snapshots: If a snapshot is found to be stale—i.e., the associated volume is not attached to any active instance, or the volume itself is not found—the function deletes the snapshot. This helps in reducing unnecessary storage costs.

By implementing this Lambda function, users can efficiently manage and reduce their cloud storage expenses by automatically removing obsolete EBS snapshots.


