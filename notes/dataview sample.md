# Dataview samples

## Tags
```dataview
table tags
from #cluster 
```

## Contains Tags
```dataview
table tags
where contains(tags,"task_definition")
```

## Dates
```dataview
table tags
where date >= date(2020-01-01) and date < date(2025-04-12)
sort file asc
```

## Tasks
```dataview
TASK
WHERE !complete
```
