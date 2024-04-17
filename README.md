# Welcome to AMD Accelerator Cloud (AAC) Reference Documentation

## Getting Started
Contact your AMD Sponsor to sign up for access to AMD Accelerator Cloud resources.

AAC can be accessed in two ways.
1. One is through web interface(aac.amd.com) using your email address and password
2. And the other one is through CLI using username and SSH key(Direct SSH access to cluster)

To submit interactive jobs, AAC web interface should be sufficient.
In case SSH access is required, public key should be provided. Based on the approval, SSH account will be activated. Please check with your sponsor

### 1. How to Login to the Web Interface Login
Go to https://aac.amd.com and login using the email address and password.</br>

Refer [PlexusQuickStartGuide](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/tree/main/PlexusQuickStartGuide) for Web interface guides
### 2. How to SSH to the Plano Slurm Cluster(For Users having Direct SSH access to cluster)
1. From the laptop or system used to generate SSH keys for AAC User Account Registration, enter the following at the Terminal or PowerShell prompt to SSH to the AAC Plano Slurm cluster:
   ```
   ssh <your_userid>@aac1.amd.com
   ```
   The SSH keys should be accessible under `$HOME/.ssh` directory or via `PuTTy` or `Mobaterm` tools used to generate the SSH keys.

<br/>Refer [AACPlanoSlurmCluster](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/tree/main/AACPlanoSlurmCluster) for more details.
## Contacting AAC Support Team
For questions or support requests, please email them to dl.dcgpu.aac.service-requests@amd.com


### The AAC Web Interface has moved to https://aac.amd.com 

### 1. How to Fix `ssh <USERID>@aac1.amd.com` failed with `Host key verification failed` message
The Slurm login node was changed during maintenance, so the host key fingerprint is different. SSH users may see a failure to login with a *WARNING* message such as one shown below. Please update `$HOME/.ssh/known_hosts` by *removing* the existing entries for `dell-r08-01` and retry `ssh <USERID>@aac1.amd.com`  and accept the new fingerprints:
```
ECDSA key fingerprint is SHA256:u1u0/uh0GLcs19KNHrmZIA6EDLMvJACK5y2fMkVg1fg.
ECDSA key fingerprint is MD5:76:6a:a4:34:56:c0:04:fa:7f:84:e6:85:0b:f1:65:e5.
```
#### Solution: 
1. First remove existing fingerprint of old Slurm login host: `ssh-keygen -R aac1.amd.com`
2. Login to the AAC Plano Slurm cluster: `ssh <USERID>@aac1.amd.com`
3. Enter "yes" to accept new host key fingerprint at the prompt to continue to login. 

### 2. How to Fix `The selected queue is no longer available` error
![lhkcojnlehhnkkck](https://github.com/amddcgpuce/AMDAcceleratedCloudGuides/assets/79542249/78c41680-49eb-4d59-bead-00d2b0a5f30e)

#### Solution:
The Slurm partition/queue names were changed during the maintenance to remove duplicate queue names and standardize on one set. The new partitition names can be used to allocate single node or a multi-node cluster using the Slurm commands.
```
1CN128C8G2H_2IB_MI210_RHEL9
1CN128C8G2H_2IB_MI210_RHEL8
1CN128C8G2H_2IB_MI210_SLES15
1CN128C8G2H_2IB_MI210_Ubuntu22
1CN96C8G1H_4IB_MI250_Ubuntu22
```



