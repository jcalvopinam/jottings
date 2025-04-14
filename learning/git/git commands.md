- Shows the list of commits that have new files created within a specified date range.
```shell
git log --pretty=format:"%h - %an, %ad : %s" --date=short --since="2024-02-16" --until="today" --diff-filter=A
```

- Shows the list of commits within a specified date range and with changes to files containing the word 'activity' in their content.
```shell
git log --pretty=format:"%h - %an, %ad : %s" --date=short --grep="activity" --since="2024-16-02" --until="today" --reverse
```
