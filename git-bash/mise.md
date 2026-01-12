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

uv
```shell
mise use -g uv

# Add to the PATH

echo "export PATH='$PATH:$HOME/.local/bin'" >> ~/.bashrc
```

jq
```shell
mise use -g jq
```

Install `awscli`:
```shell
uv tool install awscli
```

Uninstall `awscli`:
```shell
uv tool uninstall awscli
```

> [NOTE]
> This method will install AWS CLI version 1.

To install AWS CLI v2, follow the following steps.

Install AWS CLI v2 from GitHub repository v2 branch:
```shell
uv tool install git+https://github.com/aws/aws-cli@v2
```

