###AWS_CLI-Run-Command###

***Description***

This code snippet uses the aws ssm send-command command from the AWS CLI to execute a specific action on an EC2 instance

***Breakdown***

aws ssm send-command: This is the core command that interacts with AWS Systems Manager (SSM) service.
--document-name "c109410a2578464l6372981t1w975050327185-InstallDashboardApp-pjdPVZfa1iHG": This specifies the name of the SSM document that contains the instructions for the action. The long alphanumeric string likely refers to a custom SSM document named "InstallDashboardApp".
--document-version "1": This tells SSM to use version 1 of the specified document.
--targets '[{"Key":"InstanceIds","Values":["i-02ca16dedd4bd87a8"]}]': This defines the target for the command. It uses JSON format to specify that the target should be an EC2 instance identified by its Instance ID, which is "i-02ca16dedd4bd87a8" in this case.
--parameters '{}': This specifies any parameters that might be required by the SSM document. The empty curly braces {} indicate there are no additional parameters needed.
--timeout-seconds 600: This sets a maximum execution time of 10 minutes (600 seconds) for the command on the target instance. If the command takes longer, it will be terminated.
--max-concurrency "50": This parameter is likely a typo and not relevant for send-command. It's typically used with other SSM commands and specifies the maximum number of concurrent executions allowed.
--max-errors "0": This sets the maximum number of allowed errors during the execution. A value of "0" means any error will cause the command to stop running.
--region us-west-2: This specifies the AWS region where the EC2 instance resides. In this case, it's the US West (Oregon) region

***More Details**

AWS SSM Send Command - Install Dashboard App
This script utilizes the aws ssm send-command functionality to execute an SSM document named "InstallDashboardApp" on a designated EC2 instance.

Functionality
Sends the specified SSM document to a target EC2 instance.
Uses version 1 of the SSM document.
Targets a single EC2 instance identified by its Instance ID.
Parameters
--document-name (Required): Name of the SSM document containing the installation instructions (e.g., "c109410a2578464l6372981t1w975050327185-InstallDashboardApp-pjdPVZfa1iHG").
--targets (Required): JSON formatted string specifying the target EC2 instance.
"Key": "InstanceIds", "Values": ["<instance-id>"] - Replace <instance-id> with the actual ID of the target instance (e.g., "i-02ca16dedd4bd87a8").
--parameters (Optional): Parameters required by the SSM document (empty curly braces {} indicate none are needed in this case).
--timeout-seconds (Optional): Maximum execution time (in seconds) for the command on the target instance (defaults to 600 seconds or 10 minutes).
--max-concurrency (Optional): Not applicable for send-command. Likely a typo and can be removed.
--max-errors (Optional): Maximum allowed errors during execution (0 signifies any error halts the command).
--region (Optional): AWS region where the target EC2 instance resides (defaults to "us-west-2" in this example).
Usage
aws ssm send-command \
  --document-name "<document-name>" \
  --document-version "1" \
  --targets '[{"Key":"InstanceIds","Values":["<instance-id>"]}]' \
  --parameters '{}' \
  --timeout-seconds <timeout-duration> \
  --max-errors "0" \
  --region <region>
