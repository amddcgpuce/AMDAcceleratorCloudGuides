***

# How To Launch PyTorch Singularity Multinode Application

***

 **1. Login to https://aac.amd.com/.**
 
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475062/d62dc96e-e37a-42b3-9b0e-72445014a621)
  
<br/>    

 **2. Click on Applications. Select 'PyTorch'.**
 
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475062/841e8a7d-5dec-40fe-8b79-7ba8eb1213ac)

<br/>   

 **3. In the 'Select An Application' pop-up, select the PyTorch multinode version. The container type is singularity**
    
   **Note**: In this case, we have selected **PyTorch 1-12-1 ROCm5-4 Python 3-8 Multinode** version and container is singularity.
   
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475062/ecad6bcf-41b7-496e-9fb4-0838b213beeb) 

 **4. Click on 'New Workload' button available on the top right corner.**

   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475062/b55e0f25-3820-4d59-8aa4-4822df8d7d0b)


 **5. Click 'Next' button to continue.**

   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475062/288c5513-1c13-482d-9e72-69c9cfd9e4fc)


 **6. Click 'Next' button to continue.**

   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475062/48d2a365-8c3b-4bd7-b504-ebb200d356bb)

   
 **7. In 'Select Resources' tab, select the number of nodes, GPUs per node and maximum allowed runtime.**
 <br/>  
     Here we have selected 2 Nodes, 1 GPU per node and max allowed runtime as 1hr<br/>  
     ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475062/97d87e9a-e5e2-4c74-aec0-62461eab6a08)
     ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475062/715c02e7-1156-41a1-abdb-fdff97da5a4f)

**8. Select the cluster and desired queue to run the job. In this case '1CN128C8G2H_2IB_MI210_SLES15' is selected. Click on 'Next'.**

   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475062/433cd874-e38d-418f-9e9f-7d08cb14308c)

**9. Review the configurations. Cick 'Run Workload'.**

   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475062/f0e0aa6c-ffd5-461c-bfad-970b1443bb5e)
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475062/ec20c00c-076d-4467-a4e7-11b9c598705d)
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475062/a1b7cee1-c546-4ceb-b97a-1d7ffb9d284b)
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475062/5a9be346-edfb-4214-89a7-9d704e5658c1)
   ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475062/2b4a963b-247a-4453-8e4a-ac0ffc943997)

**10. User will be navigated to Workloads page. The status of workload changes to 'Running' once queue is available.**

 ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475062/f2983d24-be37-4539-9e01-a5ec75e6ad7d)

**11. User can see the system logs in SYSLOG, output in STDOUT and errors in STDERR tabs.**

  ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475062/ff2fdc8d-6655-446b-82b6-05c6840b871d)


**12. Once workload completes, User can download the output logs from STDOUT tab by clicking 'Download Logs'. The Performance tab shows the telemetry**

  ![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475062/32eb34d4-2986-4280-9e00-2f1ff70913c9)









