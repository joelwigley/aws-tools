# aws-tools
Repository to contain some tools for use within AWS environments.

Scripts will generally require the *jq* package to be installed.

## ebs_backup

This tool can be used to schedule EC2 snapshots via cron.

On execution it will log to /var/log/ebs_backups.log. Output back from the snapshot API command will be logged to /var/log/ec2snapshot.log
