# Bash commands

## Delete duplicated lines
```shell
awk '!seen[$0]++' history.txt > history_filtered.txt
```

