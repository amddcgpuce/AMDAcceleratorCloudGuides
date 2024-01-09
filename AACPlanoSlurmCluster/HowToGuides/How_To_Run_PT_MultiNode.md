## 1. We will be using elastic_ddp.py file to run Pytorch DDP test.
https://raw.githubusercontent.com/ozziemoreno/files/main/elastic_ddp.py

## 2. Request 2 nodes, 8 GPUs per node though Slurm.
```
salloc --exclusive --mem=0 --gres=gpu:8 -p 1CN128C8G2H_2IB_MI210_SLES15 -N 2
```
_Example: Change -N to 3 to request 3 nodes_

### Sample output
```
salloc: Granted job allocation 61583
salloc: Waiting for resource configuration
salloc: Nodes smc-r07-[07-08] are ready for job
<user>@smc-r07-07:~$
```
Slurm logs into the first node or "master" node, in this case smc-r07-07. Exiting this session terminates sessions on all nodes.
Login to the 2nd node. (either from first node, or from Slurm control node in a new terminal)
```
ssh smc-r07-08
```

## 3. On the master node
### Print the list of nodes which are able to communicate
```
scontrol show hostname $SLURM_NODELIST
```
#### Sample output
```
smc-r07-07
smc-r07-08
```

### 3 a. Launch the podman / PT docker container (rocm/pytorch:latest)
```
podman run -it --privileged --network=host --ipc=host -v $HOME:/workdir -v /shareddata:/shareddata -v /shared:/shared --workdir /workdir docker://rocm/pytorch:latest bash
```

Inside the container copy the file from step 1 elastic_ddp.py to /var/lib/jenkins.
```
torchrun --nnodes=2 --nproc_per_node=8 --rdzv_id=100 --rdzv_backend=c10d --rdzv_endpoint=smc-r07-07:29400 elastic_ddp.py
```
Change --rdzv_endpoint to allocated master node in your instance, keep the port same 29400. <br>
Change --nnodes to 3 for 3 node testing. --nproc_per_node to change GPU per node. <br>
The training will start but will wait for the torchrun command on other nodes. <br>

#### output on master node
```
[2023-12-19 21:46:44,746] torch.distributed.run: [WARNING] master_addr is only used for static rdzv_backend and when rdzv_endpoint is not specified.
[2023-12-19 21:46:44,746] torch.distributed.run: [WARNING]
*****************************************
Setting OMP_NUM_THREADS environment variable for each process to be 1 in default, to avoid your system being overloaded, please further tune the variable for optimal performance in your application as needed.
*****************************************
```

## 4. On the second node
Run the podman, copy elastic_ddp.py torchrun commands from 3 a. (Same steps as above) <br>
Note that the --rdzv_endpoint will still point to the master node. No changes required in the torchrun command. <br>
The training will proceed on both of the nodes.

#### output on second node
```
root@smc-r07-08:/var/lib/jenkins# torchrun --nnodes=2 --nproc_per_node=8 --rdzv_id=100 --rdzv_backend=c10d --rdzv_endpoint=smc-r07-07:29400 elastic_ddp.py

[2023-12-19 21:48:15,473] torch.distributed.run: [WARNING] master_addr is only used for static rdzv_backend and when rdzv_endpoint is not specified.
[2023-12-19 21:48:15,473] torch.distributed.run: [WARNING]
*****************************************
Setting OMP_NUM_THREADS environment variable for each process to be 1 in default, to avoid your system being overloaded, please further tune the variable for optimal performance in your application as needed.
*****************************************
Start running basic DDP example on rank 9.
Start running basic DDP example on rank 8.
Start running basic DDP example on rank 12.Start running basic DDP example on rank 10.
Start running basic DDP example on rank 15.

Start running basic DDP example on rank 13.
Start running basic DDP example on rank 11.
Start running basic DDP example on rank 14.
root@smc-r07-08:/var/lib/jenkins#
```

#### output on first node, training will resume
```
Start running basic DDP example on rank 0.
Start running basic DDP example on rank 7.Start running basic DDP example on rank 5.

Start running basic DDP example on rank 4.
Start running basic DDP example on rank 2.
Start running basic DDP example on rank 6.
Start running basic DDP example on rank 3.
Start running basic DDP example on rank 1.
root@smc-r07-07:/var/lib/jenkins#
```
Above logs indicate that distributed training is success in a multi node environment.

## 4 Notes
You can also run single node training to test individual node. <br>
Just change --nnodes=1 from above commands. <br>
```
 torchrun --nnodes=1 --nproc_per_node=8 --rdzv_id=100 --rdzv_backend=c10d --rdzv_endpoint=smc-r07-07:29400 elastic_ddp.py

```
