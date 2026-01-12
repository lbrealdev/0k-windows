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

awscli
```shell
uv tool install awscli
```