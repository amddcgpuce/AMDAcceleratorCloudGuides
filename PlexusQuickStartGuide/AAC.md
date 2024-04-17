# AAC - AMD Accelerator Cloud
AAC provides containerized cloud platform that empowers users to effortlessly launch and manage high-performance computing (HPC) and AI workloads. A web interface is available to researchers, data scientists and developers so that they can tap into the immense potential of HPC and AI without the complexity. This infrastructure features multiple MI210 and MI250 accelerator enabled nodes. AAC provides insights into resource utilization and system management. It has support for queued and interavtive workloads, simplified large-scale multi-node workloads (Horovod), shared access to commonly used training datasets and support for roaming data folders across clusters.


## 1. Getting started
User can use AAC in 2 ways:
1. Web Interface (https://aac.amd.com)
2. Direct SSH access through [CLI](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/tree/main?tab=readme-ov-file#how-to-ssh-to-the-plano-slurm-cluster).

This document is on using AAC through Web interface after login using email address and password.

## 2. Queues
The compute nodes are the backbone of the cluster and provide the computing power needed to run jobs. The compute nodes are organized in different queues based on different Operating System (RHEL8, RHEL9, Ubunutu22, SLES15) and Accelerator type (MI210 and MI250). Queues are assigned to the User's Team as per their requirements so that they can launch workloads. User can see their assinged queues in this section.
[Assigned queues](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/blob/main/PlexusQuickStartGuide/HowTo_Check_Queues_Assigned.md)


## 3. Applications
Applications required for benchmarking, AI, Deep Learning, HPC, Interactive Shell etc are provided here. User can select the required application and start the workload. Some docker and singularity applications are listed below:
1. [Gromacs Docker](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/blob/main/PlexusQuickStartGuide/HowTo_Launch_Gromacs_Docker_Application.md)
2. [Gromacs Singularity](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/blob/main/PlexusQuickStartGuide/HowTo_Launch_Gromacs_Singularity_Application.md)
3. [HPCG Docker](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/blob/main/PlexusQuickStartGuide/HowTo_Launch_HPCG_Docker_Application.md)
4. [HPCG Singularity](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/blob/main/PlexusQuickStartGuide/HowTo_Launch_HPCG_Singularity_Application.md)
5. [Pytorch Docker](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/blob/main/PlexusQuickStartGuide/HowTo_Launch_Pytorch_Application.md)
6. [Pytorch Multinode Singularity](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/blob/main/PlexusQuickStartGuide/HowTo_Launch_PyTorch_Application_Multinode.md)
7. [RocHPL Docker](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/blob/main/PlexusQuickStartGuide/HowTo_Launch_RocHPL_Docker_Application.md)
8. [RocHPL Sigularity](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/blob/main/PlexusQuickStartGuide/HowTo_Launch_RocHPL_Singularity_Application.md)
9. [TensorFlow Docker](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/blob/main/PlexusQuickStartGuide/HowTo_Launch_TensorFlowDocker_Application.md)
10. [TensorFlow Multinode Singularity](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/blob/main/PlexusQuickStartGuide/HowTo_Launch_TensorFlow_Multinode_Singularity_Application.md)
11. [Jammy (SSH)](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/blob/main/PlexusQuickStartGuide/How_To_Launch_Jammy(SSH)_Application.md)


## 4. Workloads
1. [Run a Workload](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/blob/main/PlexusQuickStartGuide/HowTo_Run_Workload.md)
2. [Monitor a Workload](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/blob/main/PlexusQuickStartGuide/HowTo_Monitor_Workload.md)
3. [Cancel a Workload](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/blob/main/PlexusQuickStartGuide/HowTo_Cancel_Workload.md)
4. [Rerun a Workload](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/blob/main/PlexusQuickStartGuide/How_To_Rerun_A_Workload.md)
5. [List all Worklaods](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/blob/main/PlexusQuickStartGuide/HowTo_Check_ListOf_Workloads_Launched.md)
6. [Check Logs of Workload](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/blob/main/PlexusQuickStartGuide/HowTo_Check_Logs_After_Launching_Workloads.md)
7. [Check Metrics of Workload](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/blob/main/PlexusQuickStartGuide/HowTo_Check_Metrics.md)

   
## 5. Files
User can upload large size files for workload's usage. These files can be managed in this section.

[Manage files](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/blob/main/PlexusQuickStartGuide/HowTo_manage_Files.md)

## 6. Account Settings
User can change Profile picture using Gravatar, change password, setup 2 factor authorization, view assigned teams & edit profile details.
1. [Teams Information](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/blob/main/PlexusQuickStartGuide/HowTo_Check_Team_Assigned.md)
2. [Change Password](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/blob/main/PlexusQuickStartGuide/HowTo_Reset_Password.md)

For Frequently asked questions, [click here](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/blob/main/PlexusQuickStartGuide/FrequentlyAskedQuestions.md)
