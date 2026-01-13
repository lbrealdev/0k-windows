# mise

## Install mise on Git Bash

Download the mise executable form GitHub release page:
```shell
curl -fsSLo "mise_windows.zip" "https://github.com/jdx/mise/releases/download/v2026.1.1/mise-v2026.1.1-windows-x64.zip"
```

Extract the zip file:
```shell
unzip -q mise_windows.zip
```

Copy the executable from mise directory to `~/bin`:
```shell
cp mise/bin/mise.exe ~/bin
```

Lasty, add mise activate to the `.bashrc` file:
```shell
echo "export PATH='$PATH:/c/Users/$USERNAME/AppData/Local/mise/shims'" >> ~/.bashrc
```

```shell
source ~/.bashrc
```

```shell
mise doctor
```

Check if everything was well:
```shell
mise version
```

## Setup Tools

### uv

Run the following command to install `uv`:
```shell
mise use -g uv
```

Once installed, add the following entry to the PATH:
```shell
echo "export PATH='$PATH:$HOME/.local/bin'" >> ~/.bashrc
```

### jq

Install jq:
```shell
mise use -g jq
```

### AWS CLI

If you have `uv` installed, you can easily setup the AWS CLI `v2`, running the following command. This will install the package directly from the v2 branch of the aws-cli repository:
```shell
uv tool install git+https://github.com/aws/aws-cli@v2 -p 3.13
```

> [!NOTE]
> If you execute `uv tool install awscli` you're installing the AWS CLI v1, it works, but is not recommended.
> This installation method takes a few minutes because of dependency resolution.
