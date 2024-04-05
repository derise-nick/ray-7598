Here are the steps to set this up locally. Lines that start with `$` are run in the WSL terminal, `>` means Windows terminal

# Clone the github fork
### Set up an SSH key: https://www.thatamazingprogrammer.com/setting-up-ssh-keys-for-github-using-wsl-and-keychain
### Make a directory to put the repo in:
```
$ cd ~
$ mkdir final
```
### Clone the github repo
```
$ git clone git@github.com:derise-nick/ray-7598.git
$ git checkout master
$ git pull
```

### Set up python in wsl

### Download/install conda in your WSL
```
$ sudo wget https://repo.anaconda.com/archive/Anaconda3-2024.02-1-Linux-x86_64.sh
$ bash Anaconda3-2024.02-1-Linux-x86_64.sh
```

### Refresh the wsl context
```
$ exit
> wsl.exe
$ which python
# Should get your path here
```

### Create a python virtual environment using venv and make sure all pkgs are up-to-date
```
$ python -m venv 7598
$ source 7598/bin/activate
$ python -m pip install --upgrade pip wheel
```


# Set up Ray with the custom code

### Install the latest Ray Wheels (wheels are basically install distributions)
`$ pip install -U "ray[default] @ https://s3-us-west-2.amazonaws.com/ray-wheels/latest/ray-3.0.0.dev0-cp311-cp311-manylinux2014_x86_64.whl"`

### SymLink the ray install to your custom code (after this it uses the ray distro installed above, with our packages)
```
# From the top level of your repo directory
$ python python/ray/setup-dev.py
# Say no for everything but autoscaler
```
