# ETHZ HPC cluster

<!-- old google doc link: https://docs.google.com/document/d/1wxGzJOOx807epac_vLYOhUOTiQBCtj29WkwK-Sy50rA/edit -->

## Getting Access
Contact Clara about being added to the Euler shares; specify your nethz id. If you do not have a nethz id (i.e., ETHZ username), mention this and provide your full name, preferred email address, and birthday.

Once Clara has confirmed you have been added, [request an HPC account from IT](https://scicomp.ethz.ch/wiki/New_account_request_process_for_HPC_clusters)  


## VPN
To login to the Euler cluster while you are not on ETHZ campus, you will need to use a VPN. If you have a student account, your login ID will be <nethzid>@student-net.ethz.ch. Everyone else (including PhD students) should login as  <nethzid>@staff-net.ethz.ch. There are multiple options for setting up a VPN:

Option 1:
- Go to https://sslvpn.ethz.ch
- Login as <nethzid>@staff-net.ethz.ch using your Radius password (this is not your ‘main’ password and is sometimes also referred to as your ‘network’ password)

Option 2:
- Download Cisco AnyConnect using [these instructions](https://unlimited.ethz.ch/display/itkb/VPN)

Option 3:
- Use the D-INFK jumphost (`jumphost.inf.ethz.ch`), which can be accessed without VPN.
Add the following to your `~/.ssh/config` file:
```
Host euler.ethz.ch
  HostName euler.ethz.ch
  User <your_nethzid>
  ProxyJump <your_nethzid>@jumphost.inf.ethz.ch
```


You can then ssh into the cluster. If you can’t get the VPN running, you may need to update your Radius password at https://www.password.ethz.ch (go to Self-service -> Change Password).

## Getting started
Consult the [Getting Started with Clusters](https://scicomp.ethz.ch/wiki/Getting_started_with_clusters) wiki page for more information

### Connecting and running
To connect, run ```ssh [username]@euler.ethz.ch``` - this will take you to your home drive which has 21.5GB of storage. You can check that you have access to GPUs by running the following command, which opens up an interactive shell with a GPU.
```bash
    srun -n 1 --cpus-per-task=1 --gpus=1 --gres=gpumem:4g --time=1:00:00 --mem-per-cpu=4092 --pty bash -i
```

More often, you will want to run a script (e.g., python, bash) on the cluster. To do this, you will need to submit a job. The following template will submit an example job to the cluster:
```bash
    # activate your virtual environment
    # cd to the directory where you want to run the job
    # ...
    # and then:
    sbatch job.sh
```

All resource requirements are written in `job.sh`, which looks like this:
```bash
#!/bin/sh

#SBATCH --ntasks=3
#SBATCH --time=4:00:00
#SBATCH --mem-per-cpu=6000
#SBATCH --gpus="rtx_3090:1"

python run.py
```
It will be run on 3 CPUs, for at most 4 hours, with 6000 MB of memory per CPU, and 1 RTX 3090 GPU.
You can check all the GPU specifiers [here](https://scicomp.ethz.ch/wiki/GPU_job_submission_with_SLURM).


### Storage space
To run experiments on large datasets (e.g. multi-lingual, multi-modal) you won’t be able to use the home directory given its strict cap on memory (21.5 GB). If you would like to be added to the group directory, which should have a good deal more space, contact Clara (note: storage space in the group directory is not guaranteed at the moment).

The scratch space (`/cluster/scratch/$USER`, 2.5 TB) is useful when you need a lot of storage space for a short period of time. It is purged every 15 days, so you should plan accordingly.

After you have been added to the group directory, make a directory of your own in `/cluster/work/cotterell/`. 
You can check how much space we have left by running `lquota /cluster/work/cotterell/`.

Note that there is a limit on both the number of files (5000000) and the amount of storage space (20 TB) for the whole Rycolab! Please make sure to *clean up* after yourself and delete/move any files you no longer need.

For some useful tips (e.g., where to put large files, small files), click [here](https://scicomp.ethz.ch/wiki/Storage_systems). 


### Python environments
Setting up an environment in Euler can be difficult. Since the use of Conda [is discouraged](https://scicomp.ethz.ch/wiki/Conda#Reasons_to_not_use_conda_on_an_HPC_file_system) by the cluster admins, we recommended that you use virtual environments through [venv](https://docs.python.org/3/library/venv.html). See the [Python virtual environment](https://scicomp.ethz.ch/wiki/Python_virtual_environment) wiki for more details

### Useful commands

| Command              |                          Description                           |
| -------------------- | :------------------------------------------------------------: |
| ``squeue``           |                   Shows your submitted jobs                    |
| ``scancel [job_id]`` |                           Kill a job                           |
| ``sinfo``            | view partition and node information for a system running Slurm |

### Running jobs

Consult the [Slurm Submission Line Advisor](https://scicomp.ethz.ch/public/lsla/index2.html) to explore different options on how to launch jobs.


## Loading modules

A list of the software modules available on the cluster can be found [here](https://scicomp.ethz.ch/wiki/Euler_applications_and_libraries).

If you are in need of a newer version of python and you can find it on the cluster, execute the `env2lmod` command. This will switch to the new architecture and you'll be able to load the gcc/8.2.0 and python_gpu/3.9.9 modules. You can set the new software to be loaded by default as described [here](https://scicomp.ethz.ch/wiki/New_SPACK_software_stack_on_Euler#Setting_a_permanent_default_for_the_software_stack).

If you are running a python script that needs access to the internet, load the eth_proxy module with: `module load eth_proxy`. The compute nodes of the cluster (when running “bsub …”) have no access to the internet by default. 

If you want to automate module loading (for each login) create an alias or just write the commands into `~/.bashrc`

## Using Jupyter Notebooks

The cluster admins are currently (July 2023) launching a new system to easily work with JupyterLab via your browser through an job running on the cluster. Find extensive documentation on how to use this new system on [the wiki](https://scicomp.ethz.ch/wiki/JupyterHub).

Alternatively, consult [this older repo](https://gitlab.ethz.ch/sfux/Jupyter-on-Euler-or-Leonhard-Open) for instructions on how to work with Jupyter Notebooks on the cluster.

## Using git-lfs
If you want to use git-lfs, you need to load git-lfs and git along with other modules. Check modules documentation to ensure version compatibility with gcc etc (for python compatibility with gcc check [here](https://scicomp.ethz.ch/wiki/Python_on_Euler)):
```bash
    module load gcc/6.3.0 python_gpu/3.8.5 git/2.31.1 zsh/5.8 git-lfs/2.3.0
    git-lfs install
```
<!-- ## Checking which resources are available

    scontrol show nodes < node_name>

Then, check AllocTRES, CfgTRES -->



