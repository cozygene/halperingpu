# Migrating your conda environment(s)

Installed your environment on _/home_? No worries! Let's move it to _/scratch_!

Do you have a _.condarc_ file?
```
cat ~/.condarc
```

**Skip the next step if the answer is yes**. O.w., create it
```
touch ~/.condarc
```

**Set your user name into a variable** (so we can use it later as $user_name)
```
user_name=<your_username>
```

**Add your _/scratch_ path to your _.condarc_** (to set it as the default path for env installations)
```
conda config --prepend envs_dirs /scratch/$user_name/envs
```

**Remove your _/home_ path from your _.condarc_** (This command will work only if this path appears in it, i.e., in case you previously actively added it; O.w., it will return an error. That's fine.)
```
conda config --remove envs_dirs /home/$user_name/envs 
```

**Make sure your _.condarc_ changes were properly applied** (should see _/scratch_ path but not _/home_)
```
cat ~/.condarc
```

**Repeat the following five steps for each of your (_/home_) environments**

1. **Set your env_name into a variable** (so we can use it later as $env_name)
```
env_name=<your_env_name>
```

2. **Activate your environment**
```
conda activate $env_name
```

3. **Export the environment** without prefix
```
conda env export --no-builds | grep -v "^prefix: " > $env_name.yml
```

4. **Deactivate and remove the old environment** (to free up _/home_ and your environment name)
```
conda deactivate
conda env remove -n $env_name
```

5. Re-**create your environment on _/scratch_** from the yml in the new location
```
conda env create -n $env_name -f $env_name.yml
```

Verify the new environment's path
```
conda env list
```

Now you shold be able to **activate your _migrated_ environment(s)** (hip hip hooray!)
```
conda activate $env_name
```
