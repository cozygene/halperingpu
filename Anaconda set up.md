# Setting up your conda environment

**Anaconda is already installed** on _halperingpu_ at _/scratch/anaconda3/bin/conda_ (please do not download and install a new one)

**Add conda to your _~/.bashrc_** (so that _conda_ command will be available on every shell startup)
```
/scratch/anaconda3/bin/conda init
source ~/.bashrc
```

By default, conda is set to create new envs on _/home_, however, this folder has pretty low storage volume and we thus install conda envs only on _/scratch_. 

**Create an empty conda configuration file**
```
touch ~/.condarc
```

**Add your _/scratch_ path to your _.condarc_** (to set it as the default path for env installations)
```
conda config --prepend envs_dirs /scratch/<your_username>/envs
```

Make sure your _.condarc_ includes the _/scratch_ path you've just added
```
cat ~/.condarc
```

Finally, you can **create a new environment** on _/scratch_ 
```
conda create -n <env_name> python=3.9
```

