This tutorial is about performing profiling of Deep Learning models using PyTorch Profiler.

The code application is adapted from [https://pytorch.org/tutorials/intermediate/tensorboard_profiler_tutorial.html] 

the application is stored in the foldeer /examples. Here are two python files:
"resnet18_profiler_api_4batch.py", in which is specified for 4 batches
and "resnet18_profiler_api_32batch.py" for 32 batches.


# Setup Pytorch profiler in HPC system viasingularity container

###Step 0: Pull the PyTorch container image
e.g. from NVIDIA NGC container: https://catalog.ngc.nvidia.com/orgs/nvidia/containers/pytorch
[the host system must have the CUDA driver installed and the 
container must have CUDA]

$singularity pull docker://nvcr.io/nvidia/pytorch:22.12-py3

### Step 1: Launch singularity container
$singularity exec --nv pytorch_22.12-py3.sif  python main.py

We have already pulled a PyTorch container image. This is stored in the folder "/Container"

# To run this example, we have made a bash job "job.slurm" stored in the folder "/Jobs"

# To submit the job "job.slurm", run the command:
$sbatch job.slurm

## For visualisation: Install TensorBord in a virtual environment

###Step0: load a python model, create & activate Virt. Env. 
Find a python module: $module avail python
Load a python module .e.g.: 
$module load python/3.9.6-GCCcore-11.2.0
$mkdir Myenv
$python –m venv Myenv
$source Myenv/bin/activate

###Step1: Install via pip wheel packages
###Install PyTorch Profiler TensorBoard Plugin:
$python –m pip install torch_tb_profiler 

## The procedure based on virtual environment can be used to install "torch" and "torchvision"

#Activate the virt. env.
$source Myen/bin/activate
python -m pip install torch torchvision

#N.B. Remember to source the virt. env. in a bash job if you want to use the installed torch and torchvision.

