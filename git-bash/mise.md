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

Copy the mise executable to `~/bin` directory:
```shell
cp mise/bin/mise.exe ~/bin
```

Finally, add mise activate to PATH:
```shell
echo "export PATH='$PATH:/c/Users/$USERNAME/AppData/Local/mise/shims'" >> ~/.bashrc
```

```shell
source ~/.bashrc
```

Check if everything is correct:
```shell
mise doctor
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

### aws-cli

If you have `uv` installed, you can easily set up AWS CLI `v2` by running the following command. This will install the package directly from the v2 branch of the [aws-cli](https://github.com/aws/aws-cli/tree/v2) repository:
```shell
uv tool install git+https://github.com/aws/aws-cli@v2 -p 3.13
```

> [!NOTE]
> If you run `uv tool install awscli`, you'll be installing AWS CLI v1. It works correctly, but it's not recommended.
