# Setting up your conda environment

**Anaconda is already installed** on _halperingpu_ at _/scratch/anaconda3/bin/conda_ (please do not download and install a new one).

**Add conda to your _~/.bashrc_** (so that _conda_ command will be available on every shell startup):
```
/scratch/anaconda3/bin/conda init
source ~/.bashrc
```

By default, conda is set to create new envs on _/home_, however, this folder has pretty low storage volume and we thus install conda envs only on _/scratch_. 

**Create an empty conda configuration file**:
```
touch ~/.condarc
```

**Set your username into a variable** (so we can use it later as $username):
```
username=<your_username>
```

**Add your _/scratch_ path to your _.condarc_** (to set it as the default path for env installations)
```
conda config --add envs_dirs /scratch/$username/envs
```

Then your _.condarc_ should look like (e.g., using _cat ~/.condarc_):
```
envs_dirs:
 - /scratch/dummy/envs
```

Finally, you can **create a new environment** on _/scratch_ using:
```
conda create -n <env_name>
```

