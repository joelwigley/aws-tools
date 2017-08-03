# aws-tools
Repository to contain some tools for use within AWS environments.

Scripts will generally require the *jq* package to be installed.

## ebs_backup

This tool can be used to schedule EC2 snapshots via cron.

On execution it will log to /var/log/ebs_backups.log. Output back from the snapshot API command will be logged to /var/log/ec2snapshot.log

## updateasg

This script is designed to assist in pushing updates to instances within an auto-scaling group. Simply run the script on the "master" instance
and it will create an AMI, then a new launch configuration to use that AMI. It will then provide the option to cycle the scaling group. If you
choose to do this, it will increase the required instances in the ASG, wait till new instances launch from the new AMI, and then reduice the
required instances to normal, thus terminating the instances using the old/previous AMI.

The "master" instance this script is run on should ideally have an IAM role with enough permissions to create snapshots, images, edit scaling
groups and the like. The script will take the IAM role assigned to the "master" instance and apply it to new instances created by the ASG.
