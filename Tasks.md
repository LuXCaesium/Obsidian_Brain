# Tasks

##### Due Today
```tasks
not done
due today
```

##### Due This Week
```tasks
not done
due after monday and before friday
```

##### Past Due
```tasks
not done
due before date(today)
```

##### Due Today
```tasks
not done
no due date
```


#### Other Tasks
```dataviewjs
dv.taskList(dv.pages('-"Templates"').file.tasks
.where(t => !t.completed && !t.text.includes("@frank") &&
!t.text.includes("#task")
))
```



- [ ] 📅 2024-04-05  #task This is a task