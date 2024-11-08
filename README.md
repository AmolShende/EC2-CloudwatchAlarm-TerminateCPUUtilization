To automatically terminate an EC2 instance when its CPU utilization reaches 90%, you can use a CloudWatch alarm configured to trigger an instance termination action. 

###Step 1: Log in to AWS Console
- Go to the [AWS Management Console](https://aws.amazon.com/console/).
- Open **CloudWatch** from the list of services.

#### Step 2: Create a CloudWatch Alarm for EC2 CPU Utilization
•	In the **CloudWatch** console, go to **Alarms** on the left panel, and click **Create alarm**.
•	Select **Select metric** to choose a metric to monitor.
•	In the metric list, navigate to **EC2** > **Per-Instance Metrics**.
•	Select **CPUUtilization** for the EC2 instance you want to monitor, and click **Select metric**.
•	Configure the **Conditions**:
-	**Threshold type**: Set to “Static.”
-	**Threshold value**: Choose **Greater than or equal to 90** to trigger the alarm if CPU utilization reaches or exceeds 90%.
•	Set **Period** to 5 minute (or any preferred interval), and **Statistic** to **Average** to accurately capture average CPU utilization.

#### Step 3: Configure the Termination Action
•	Under **Configure actions**, click on **In alarm** to configure an action for when the threshold is breached.
•	In the **Take the action** dropdown, choose **Terminate this instance**.
-	**Important**: Ensure you select **Terminate** and not **Stop** if you want to delete the instance.
•	**Review warnings**: You may see a warning that termination is irreversible. Confirm you understand this action.

#### Step 4: Add a Name and Description
- Give your alarm a unique **name** and optional **description** so you can easily identify it later.

#### Step 5: Review and Create Alarm
•	Review all your settings to ensure accuracy.
•	Click **Create alarm** to finalize it.

#### Step 6: Test (Optional)
To test the alarm setup, you can simulate high CPU utilization by running a CPU-intensive process on the instance. If the alarm is configured correctly, it should trigger and automatically terminate the instance when the utilization crosses 90%.

### Important Considerations
- **Irreversible Action**: Terminating the instance deletes it permanently, along with any non-persistent data stored on the instance.
- **Data Backup**: Ensure that any important data is backed up before enabling this action.
- **Alarm Timing**: Be mindful of the period you set; a shorter period could result in more sensitive alarm triggers, while a longer period may delay termination.

This configuration will help automate the termination process, optimizing your costs and resources by removing instances with high, sustained CPU loads.

### To trigger alarm through AWS CLI or Cloudshell
aws cloudwatch set-alarm-state --alarm-name test-ec2-testing --state-value ALARM --state-reason "Testing EC2 Alaram" --output json 
###Note :- Alaram name to be replaced
