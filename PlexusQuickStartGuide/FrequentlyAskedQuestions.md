# Frequently Asked Questions

### How To Launch/run a workload?

Please refer [HowTo_Run_Workload](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/blob/main/PlexusQuickStartGuide/HowTo_Run_Workload.md)

### How to change/increase Workload run time?

Once the workload is launched, we cannot change/increase the total workload time. It has to be configured before running. 

While launching the workload, in Select Resources step, **Maximum allowed runtime** option is available which can be used to change the total time allowed for the workload to run.

![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475062/ad6cd4f8-d197-4e91-8332-60a1bea05323)

By default 1 hour will be selected.

If maximum allowed run time is 1 hour, it implies, workload will run for 1 hour and then it will be automatically stopped after 1 hour as it will not be allowed to exceed **Maximum allowed runtime**.

Based on the time required for workload, user should change the **Maximum allowed runtime**.

Example: Maximum allowed time is changed to 2 hours and 30 min. That means, workload is allowed to run for a maximum duration of 2 hr and 30 min. 

&emsp; ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475062/37e42e06-6f42-48af-b3e2-062cd3f97a1d)

Please refer [HowTo_Run_Workload](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/blob/main/PlexusQuickStartGuide/HowTo_Run_Workload.md) for detailed steps in launching a workload


### How to Schedule a job?

While launching the workload, in Select Resources step, **Scheduled** option is available which can be used to schedule a job for desired date and time which can be made reccuring daily or weekly.

Scheduling a job is optional. This step can be skipped if you are trying to run the job immediately.

To schedule a job, Click the below toggle button to show Yes

![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475062/5ce78a5a-dc51-4b31-ab8f-ccccaf3a997d)

The time at which the workload has to be triggered, how frequently the workload has to be triggered i.e, how many days per week or on which week days can be defined under **Scheduled** field.

**Example1:** 

&emsp; Here, workload will be run for every two days at time 15:30. Last day is 9/20/2023 after which workload will not trigger.

&emsp; &emsp; ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475062/e3d4152f-2007-4fac-86b8-8ed77f7d10fa)

**Example2:**

&emsp; Here, workload will trigger every tuesday and wednesday at time 19:15. Workload will not trigger after 9/21/2023.

&emsp; &emsp; ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475062/4edb9383-20f8-44b1-bca7-8466b9a8c3e2)

Please refer [HowTo_Run_Workload](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/blob/main/PlexusQuickStartGuide/HowTo_Run_Workload.md) for detailed steps in launching a workload


### Why can't I see any queue while launching workload?

The following details should be checked to understand why queues are not visible while launching workload

1. Make sure you are assigned to a team. In user profile page, check if you are assigned to your organization team in **Teams** section.
   If you are not assigned to a team, contact your sponsor to get a team assigned.
   Please refer [HowTo_Check_Team_Assigned](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/blob/main/PlexusQuickStartGuide/HowTo_Check_Team_Assigned.md) for detailed steps to check the team assigned to user.

2. Once the above step is verified, navigate to queues page and check if queues are visibile. If queues are not visible, contact your sponsor to get queues assigned to your team.
   Please refer [HowTo_Check_Queues_Assigned](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/blob/main/PlexusQuickStartGuide/HowTo_Check_Queues_Assigned.md) for detailed steps to check queues assigned.

3. The queues availability while launching workload depends on the num of GPUs selected in **Select Resources** step. The number of GPUs should not be more than 8.
   Even after selecting GPUS <=8, queues are not visible, please contact your sponsor for assistance.


### Why is my workload/job in pending state?

A workload will be in pending state until the resources are available.

To elaborate, while launching a workload, user selects a queue. Each queue is a combination of certain number of nodes.
Node is where the workload will be executed. If the number of nodes required by you are already occupied, then the workload will be in pending state.
Once the required number of nodes are freed, the workload will start running.

**Note**: Maximum time a workload can run is for a week. So, if all the nodes are occupied with workloads which are running for 7 days, it might take 7 days for your workload to start running in some rare cases. 

### Why can't I see the performance tab after workload is completed.

Performance tab will be visible only if **Telemetry enabled** option is enabled in **Select Resources** step while launching workload.
![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475062/3eb62866-640c-4f6c-8a9c-ca0a8757ae3d)

Please refer **Select Resources** step in [HowTo_Run_Workload](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/blob/main/PlexusQuickStartGuide/HowTo_Run_Workload.md) guide.

### Why can't I see App Config/ Application Configuration step while launching workload

Interactive applications like pyTorch, Tensorflow, Jammy, etc will not have Application Configuration step. Hence, you will not see the step.

### How to submit interactive jobs?

AAC supports submitting interactive jobs by using applications like Jammy, Pytorch etc. Following guides can be referred.<br/>

Jammy: [How_To_Launch_Jammy(SSH)_Application](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/blob/main/PlexusQuickStartGuide/How_To_Launch_Jammy(SSH)_Application.md) <br/>
Pytorch: [HowTo_Launch_Pytorch_Application](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/blob/main/PlexusQuickStartGuide/HowTo_Launch_Pytorch_Application.md)<br/>
Tensorflow: [How_To_Launch_Tensorflow_Application](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/blob/main/PlexusQuickStartGuide/HowTo_Launch_TensorFlowDocker_Application.md)

### How to SSH into container for Jammy/Ubuntu applications?

Launch a Jammy application. Once interactive endpoints are available in workload overview page, Navigate to **STDOUT** and copy username and password.
![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475062/a018e9b4-aa69-4520-8f7e-b047f00abcf6)

Click **Connect**. Use the ssh url provided. Replace \<USER> with the username copied from STDOUT tab and enter password when prompted in any terminal/SSH client(like putty, mobaxterm etc).

![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475062/7d520e5e-123e-4d9f-a941-0cc6afd339eb)

Please refer [How_To_Launch_Jammy(SSH)_Application](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/blob/main/PlexusQuickStartGuide/How_To_Launch_Jammy(SSH)_Application.md) for detailed steps.


### How to connect JupyterLab for AI/ML applications like pytorch, tensorflow etc?

Launch a pytorch application. Once interactive endpoints are available, Click **Connect**
![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475062/cac47a19-d778-47c2-953c-df444beef3d5)

Copy the token from **STDOUT** tab and use it to connect.
![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475062/b76d78c4-5089-404c-b189-675bae7a76c4)

Please refer [HowTo_Launch_Pytorch_Application](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/blob/main/PlexusQuickStartGuide/HowTo_Launch_Pytorch_Application.md) for detailed steps.
