***

# Building Docker applications - with container definitions

***
This article describes how to create docker applications in AAC. To accomplish this procedure, you will need AAC Developer or Admin permissions.

**1.** Click on the top bar menu option **Applications**, and then click on **Applications** again.
![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475255/31842912-bb5f-43a5-b90a-26d4aa62fb8a)

**2.** Click on **New Application** button  
If you do not see the **+ New Application** button, you do not have Developer or Admin permissions.

**3.** Select **Docker** on the **Container type** screen. Click on the **NEXT** button.
![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475255/c63ff198-6f0e-4403-b5c2-3c5d5ed5053a)

**4.** Configure the general application attributes
In the general information panel, configure the general application attributes, see next image below.

- **Name (required)**: Name of the application.  
- **Description**: Description of the application.  
- **Family**: The Application Family of this application.  
- **Version number**: Version of the application.  
- **Allow replicas**: Toggles replicas on / off. Kubernetes container feature.  
- **Categories**: Assign a category to the application.  
- **Architectures (required)**: Either x86_64 or arm64.  
- **Accelerator**: either AMD GPU, NVIDIA GPU or Google TPU.  
- **Is service**: Indicates that the application will be executed as a docker interactive.  
- **Is stateful set**: Toggles statefulset on / off. Kubernetes container feature.  
- **Ports**: Services can configure the application port to be exposed to users. Several ports can be configured by clicking in Add Port button.  
  - Example for Jupyterlab with SSH connection: ui: 8888, ssh: 22  
- **Intel MPI**: Toggles Intel MPI on / off  
- **Featured**: Toggles Featured on / off. When on, includes this application at the top of the Applications list in the Featured section.  
- **Price per use**: Price charged to the user for using the app.  
- **Price per hour usage**: Price charged to the user per hour of usage.  
- **Price per core usage**: Price charged to the user per core usage.  
- **Price per GPU usage**: Price charged to the user per GPU usage.  
**Stateful Sets**
Stateful sets are useful when you need to keep a predictable hostname list for multi-POD jobs, as in the following example:  
  - some_hostname_prefix_0 is the hostname of the 1st replica.  
  - some_hostname_prefix_1 is the hostname of the 2nd replica.  
  - some_hostname_prefix_2 is the hostname of the 3rd replica.
With stateful sets, the same hostname is kept between a POD failure / restart. This is useful for MPI jobs, or jobs where you need PODs to register to a centralized server e.g. Spark and NiFi. Since the hostnames follow a predictable pattern, you always keep the same fixed host list for your job, even after a POD failure / restart.  

**Repository authentication**  
In the case your application uses containers that are stored in a private image repository, you will need to setup the following authentication fields:
- **User**: user of the docker image repository account.  
- **Password**: the password of the docker image repository account. It can be also the security token provided by some repositories such as NVidia.  
- **Server**: the docker repository server URL. This is the URL for Docker hub: https://index.docker.io/v1/
![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475255/43b19695-668e-4cc9-929f-5e957fa2ef23)

**5.** After filling in the application attributes, click on the NEXT button  
**6.** Configure the application settings  
In the settings panels, we can configure the application settings.

The most common settings to configure are:

- **Help URI**: this contains a URL within help articles about the how to run the application.  
- **Workload default prerun script**: this defines the default script to execute before the container scripts are executed. It can also be defined during the job submission process.  
- **Workload default postrun script**: this defines the default script to execute after the container scripts are executed. It can also be defined during the job submission process.


After the application settings are configured, click **NEXT**.
![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475255/96d03916-7c53-4cb7-a004-1eed0812c70f)

**7.** Add container
Click the ellipses(...) button and then click **Add new container** on the dropdown menu.
![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475255/257c0def-79d8-4cd4-af8a-7674d28ecb9e)

Fill in the **CONTAINER INFORMATION** parameters:

- **Name (required)**: Container name.  
- **URL**: container URL  
- **Architectures required)**: Select either x86_64, or aarch64.  
- **Version**: container version
- **GPU**: check this box if the container requires GPU resources.  
- **Description**: Your description of the application container.  

Click **SAVE** to save the container.
![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475255/66eda6f2-8935-4c5f-9dad-8023cff88211)

**8.** Configure container  
Click on select container and then click on the container you just created, then click on the **Add application container** button.
![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475255/52eec0f7-48f3-48ef-ba4b-7f13b25134c1)

Set the following parameters to configure the application:
- **Name**: Name to be used for this container when used inside this application. Within a given application each container name must be unique. You may use the same container multiple times within a given application -- but each use must have a different name (example: redis-server-1; redis-server-2 might be the names used within the application for multiple instances of the original redis-server container).  
- **Order**: Order of execution of the container inside the application. Format integer (e.g. 1, 2, 3 etc.).  
- **Number of CPUS**: Number of CPUS required by the container execution. Format integer. If you set number of cpus = 0, it will run without limits or under cluster default limits.  
- **Memory**: Number of megabytes required by the container execution. Format integer. If you set memory = 0, it will run without limits or under cluster default limits.  
- **Number of gpus**: Number of gpus required by the container execution. If the container requires the use of a gpu, and you do not setup any value, the AAC will use 1 gpu by default. Format integer.
- **Mount list**: List of mount points in the container. Add new mounts by clicking in Add mount. Volumes can have the following formats:
  - ./host/dir:/container/dir:rw. Write permissions can be read/write (rw) or read/only (ro).
  - tmpfs mount points can also be defined by using this format: /container_dir.tmpfs:tmpfs.
    - **Example**: ./redis:/redis:ro, ./redis/data:/data_redis:rw or container/dir_tmpfs:tmpfs
    - **In case of shm memory**, it can be configured by tmpfs by configuring a volume with the following text: /dev/shm:tmpfs
      - In **kubernetes** the size of this memory is limited to 1G.
      - In **Slurm with docker** the size is unlimited, so it is controlled by the application memory  
- **Environment var list**: List of environment variables to setup inside the container. Add new variables by clicking in Add Environment Var
  - **Format**: VAR1=value1
  - **Examples**: HOSTNAME=localhost, PORT=6379, etc
- **Health check**: Command to test the container health, if the health check fails the container will be restarted. 
  - In K8s services, if the container has more than 10 attempted restarts, without success, the application execution will be marked as *Failed*.
- **Ready check**: Command to verify the container is ready to be exposed to the client.
  - Ports are not open until the container is ready
- **Prerun script**: Command to be executed before the run script.
- **Run script**: Command to run the container.
  - In case of bash, this is a permanent command which is not possible to modify in every run (see next item, Example run script).
  - **Example Run script**: Parameter available just for bash (non-service) applications.
    - Here we can include the command we make 
- **Postrun script**: Command to run in the container after the application completes execution.

**8.1** Image related to a service application
![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475255/6c20f1a2-c115-45aa-980c-c6d9d6d33f67)

**8.2** Image related to a batch application
![image](https://github.com/amddcgpuce/AMDAcceleratorCloudGuides/assets/137475255/f1048c88-9ec9-421a-beda-0865fbcbcafb)
After filling in the container parameters, click **Save** to save the container configuration, and then click **NEXT**.

**9.** Multiple containers on an application
Only Service type applications (where the Is service option has been selected) can support multiple containers, therefore the interface will only allow you to add a single container to those applications where the **Is service** option has not been selected. In the case of services, several instances of the same container can be configured in the same application, but each container must have a different name, to be used inside the application.

**10.** Review the application and create it
Review the application details and making any edits or corrections needed.Click **CREATE** to execute the creation procedure.

**Important notes**  
**a.** The cluster user directory will be mounted in the /home/aac folder. It will be selected as working directory in the container.  
**b.** Prerun script application
- The prerun script is used to execute common scripts for all the containers in the application. It is mainly used to move data to the right folders inside the home user workspace.
- The prerun script can be configured in the default prerun script application setting or it can be written in the job prerun step.

**c.** Container must have different names when used in the same application.
- Containers configured in the application require different names.
- Several instances of the same container can be configured in the same application, but each container must have a different name, to be used inside the application.

**d.** Multiple container applications are just available in Kubernetes

**e.** The container run script must be set
- The run script can be either a custom script or the default entry point of the container.

**f.** Get the default container entrypoint
- You can get default container entry point by using the following command:
  - docker inspect --format="{{.Config.Entrypoint}}{{.Config.Cmd}}{{.Config.WorkingDir}}" redis
  - It returns entry point, command and workdir:
  - docker-entrypoint.sh][redis-server]/data
  - Where:
    - It returns docker-entrypoint.sh as entry point
    - It returns redis-server as command
    - It returns /data as workdir
- Your runscript will need to include the entrypoint + command. If it has just one of them (either entrypoint or command) you use that one.
- In some cases, the container executes a command which is inside the working directory or to the root directory /, and depends on other fields inside that folder. In that case, if you get problems with that, you can write cd /script_folder inside the prerun script container field.

**Kubernetes**
- You must know how to run the container you will deploy.
  - You need to know how to deploy and execute the container. If there is no documentation available describing how to execute the container in Kubernetes, you should first execute it in your local environment and test it there. Once you have the container working correctly in your local environment you will the scripts and variables to use in AAC.
- Application will finish when the container run script finishes.
  - It executes and finishes once the task is completed.

**Best practices**
- Do not use latest version containers.
  - Parameters and settings could change and break your application container configuration.
- Create a subdirectory for each application in the /home/acc.
  - Creating separate subdirectories will make for clean executions. Also, do not mix different app execution files. It makes the app files persist in the home user directory.

**Troubleshooting**
- SSH connection does not appear
  - In order to expose the SSH connection to a container. The application must:
    - Execute SSHdaemon on the container.
    - Configure a port called SSHwith value 22.
- Not found files
  - If you get messages from not found files, it is probably because the application or the container is configured to use a file from your home user directory.
  - To avoid this problem, you will need to attach such files to the workload execution as input files. They will remain in the /home/aac directory, of a specific cluster, until you delete them.
  - ERROR -\>
[prerun]: tar (child): demo-fastdata.tar.gz: Cannot open: No such file or directory

**Containers depending on other containers**
In the case where your application has container dependencies, you can use the order attribute shown in Figure 7.

**Memory requirements**  
In case you run into memory troubles, you can configure memory container requirements in Figure 7.Memory is configured in Megabytes.

**Container needs the public IP of another container**    
In this case, you will need to deploy two different applications:  
-  Configure the backend application with its containers and expose the required endpoint.
-  Configure the frontend application with the IP and endpoint provided by the backend application.

**Interactive workloads or services finish immediately**   
If you want to keep alive any execution, the container run script must be a live process. In case the run script executes a detached process, you can keep the container alive by adding && tail -f, otherwise the execution manager will finish the application.

**Kubernetes Manager pods fail**  
The manager pods are those called stream-copy, create-scripts, read-analytics, retrieve-files, read-stdout or read-stderr. In case they fail, these are the most likely reasons:
-  Fail without displaying a reason or displaying any http error:
-  This error is because there is an issue with the target cluster.
-  Show timeout error of 60 seconds.
-  This can be because the cluster cannot create the pod:
    - Cluster resources are insufficient.
    - Cluster issues (network, permissions).
