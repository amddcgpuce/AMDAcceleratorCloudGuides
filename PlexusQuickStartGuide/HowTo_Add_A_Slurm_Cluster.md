***
## How to Add a Slurm Cluster to a Plexus Instance
***
**1. Login to https://aacstaging.amd.com/.**

**2. Select Clusters menu. Select New Cluster on Right Top Corner**
![image](https://github.com/sanjtrip/AMDAcceleratorCloudGuides/assets/78184710/7e61cab5-2d9b-4f4e-a2b7-73c97e11f55b)

**3. Select Slurm Cluster and click on NEXT on Right Top Corner**
![image](https://github.com/sanjtrip/AMDAcceleratorCloudGuides/assets/78184710/f619a971-1f34-4dfd-88fd-7ea0c5a77794)

**4. Fill the following details**
```
  Hostname URL
  Username
  Select SSH - it will generate a SSH-Key
  Add the SSH-key in the $HOME/.ssh/authorized_keys file for the "Username" on the Slurm Cluster.
```
**5. Click on Test Connection**
![image](https://github.com/sanjtrip/AMDAcceleratorCloudGuides/assets/78184710/580de569-e7fa-404b-9b12-3735eefff4b9)

**6. Once successful, Click on Next on Right Top Corner**
![image](https://github.com/sanjtrip/AMDAcceleratorCloudGuides/assets/78184710/2d8e812c-152b-4dfc-9a55-3089c35c36ab)

**7. Update the following fields**
```
  Name of the Cluster:  Any desired name for the Cluster
  Home Directory: Home directory of the 'user' on the Slurm Cluster
  Enironment script: Any Plexus related environment settings
```
![image](https://github.com/sanjtrip/AMDAcceleratorCloudGuides/assets/78184710/39cd4b49-783d-4c5f-b9a2-724b1da80292)

**8. Update the Script section and Click on NEXT on Top Right Corner**
```
    Enironment script: Any Plexus related environment settings
```
![image](https://github.com/sanjtrip/AMDAcceleratorCloudGuides/assets/78184710/68d57fa1-a95a-4f42-8284-3f4234c5bf24)

**9. Review Cluster Configuration, If appropriate, Click on CREATE on Top Right Corner**
![image](https://github.com/sanjtrip/AMDAcceleratorCloudGuides/assets/78184710/c0087b65-9014-4a9e-9f57-0f8bc173f22b)

**10. Newly create Cluster will be displayed in the available Clusters list**
![image](https://github.com/sanjtrip/AMDAcceleratorCloudGuides/assets/78184710/2865d1a7-b0fa-47ea-821e-dc2dbacffb13)

**11. Update $HOME/.bashrc file for the user (aacplexusd) on the Slurm Cluster - comment out the 4 lines for Plexus**
```
  # If not running interactively, don't do anything
  #case $- in
  #    *i*) ;;
  #      *) return;;
  #esac
```
**12. Select Newly Created Cluster (DEVTEST Cluster) and Click on Update Details on Right Side**
![image](https://github.com/sanjtrip/AMDAcceleratorCloudGuides/assets/78184710/6d1a3a00-7c76-4219-8b33-06b2339cf711)

**13. Check the Queues, Libraries and Metadata under Cluster. If any library is missing, debug it.**

**14. Update the Queue parameters by selecting a Queue**
```
  1. Set Interactive to ON for Queues which can run Docker
  2. Update GPU Memory to 64 (for MI210), 128 (for MI250) and 32 (for MI100)
  3. Set InfiniBand to ON, if appropriate
  4. Set Network IO (>0, as appropriate based on Netwrok speed)
  5. Set Runtime Required to On in Workload Limits section
```
![image](https://github.com/sanjtrip/AMDAcceleratorCloudGuides/assets/78184710/82fb04a2-daee-46ef-b4e0-e9d17c008bd6)

**15. Do any maintenance acivity on the Cluster, Queues**
```
Example:
  1. Remove Queues which cannot run Docker (like RHEL8, RHEL9 queues).
  2. Repeat all the above steps to configure a new Cluster for RHEL queues, if needed.
  3. Clone any Queue to make it Pre-emptible, if needed.
```

