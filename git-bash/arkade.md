# Arkade

## Install Arkade on Git Bash

First of all, check if the following path `/c/Users/<user>/bin` is defined in the PATH environment variable:
```shell
printenv PATH | tr ':' '\n'
```

If it is defined, check if the `$HOME/bin` directory exists:
```shell
ls -la $HOME | grep bin
```

If the `$HOME/bin` directory doesn't exist, create it in your home directory:
```shell
mkdir $HOME/bin
```

After create `$HOME/bin` directory, create a new directory called `apps` in your home directory:
```shell
mkdir $HOME/apps && cd $HOME/apps
```

> [!NOTE]
> The `~/apps` directory is optional, as it is only used to store application that have been downloaded. You can also use the `/tmp` directory to
> store downloads.

Download the `arkade` executable from GitHub release page:
```shell
curl -fsSLo "arkade.exe" "https://github.com/alexellis/arkade/releases/download/0.11.60/arkade.exe"
```

Copy the executable to `bin` in your home directory: 
```shell
cp arkade.exe $HOME/bin/
```

Check `arkade` version:
```shell
arkade version
```

Add arkade `bin` directory to your PATH: 
```shell
echo "export PATH=$PATH:$HOME/.arkade/bin/" >> ~/.bashrc
```
