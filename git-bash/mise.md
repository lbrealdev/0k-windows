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
echo 'eval "$(mise activate bash)"' >> ~/.bashrc
```
