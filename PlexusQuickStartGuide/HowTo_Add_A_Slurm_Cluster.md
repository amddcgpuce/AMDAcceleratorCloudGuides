***
## How to Add a Slurm Cluster to a Plexus Instance
***
**1. Login to https://aacstaging.amd.com/.**

**2. Select Clusters menu. Select New Cluster on Right Top Corner**
![image](https://github.com/sanjtrip/AMDAcceleratorCloudGuides/assets/78184710/7e61cab5-2d9b-4f4e-a2b7-73c97e11f55b)

**3. Select Slurm Cluster and click on NEXT on Right Top Corner**
![image](https://github.com/sanjtrip/AMDAcceleratorCloudGuides/assets/78184710/f619a971-1f34-4dfd-88fd-7ea0c5a77794)

**4.Fill the following details **
```
Hostname URL
Username
Select SSH - it will generate a SSH-Key
Add the SSH-key in the $HOME/.ssh/authorized_keys file for the "Username" on the Slurm Cluster.
Test connection - once successful, Click on Next on Right Top Corner
```
![image](https://github.com/sanjtrip/AMDAcceleratorCloudGuides/assets/78184710/2d8e812c-152b-4dfc-9a55-3089c35c36ab)

