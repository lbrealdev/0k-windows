# Git Bash (Git For Windows)

- [mise](tools/mise.md)
- [tree.com](tools/tree-com.md)

## Alias

```shell
echo "alias python3='uv run'" > ~/.bash_aliases
source ~/.bash_aliases
alias
```

## Wrapper Script

```shell
printf '#!/bin/bash\nuv run python "$@"\n' > ~/bin/python3 && chmod +x ~/bin/python3
```
