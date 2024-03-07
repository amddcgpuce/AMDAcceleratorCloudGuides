# How To Setup a TensorFlow Conda Environment on Plano Slurm Cluster
Allocate an Ubuntu 8GPU MI210 job from the partition `1CN128C8G2H_2IB_MI210_Ubuntu22`
```
salloc --exclusive --mem=0 --gres=gpu:8 -p 1CN128C8G2H_2IB_MI210_Ubuntu22
```
In the allocated session, load ROCm 5.5.1 Environment
```
module load rocm-5.5.1
```
Load anaconda3
```
module load anaconda3
```
Source the `conda.sh` file
```
. $CONDA_ROOT/etc/profile.d/conda.sh
```
Create conda environment named `tf-rocm` with python 3.9
```
conda create -n tf-rocm python=3.9 -y 
```
Activate the conda environment that was just created 
```
conda activate tf-rocm
```
Install Rocm Release of TensorFlow
```
pip3 install tensorflow-rocm
```

Test GPU devices using TensorFlow
```
python3
```
```
import tensorflow as tf
tf.config.list_physical_devices('GPU')
```
