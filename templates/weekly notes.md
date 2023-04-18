---
created: <% tp.file.creation_date() %>
---
tags:: #WeeklyNotes

# <% tp.date.now("YYYY-[W]W", 0, tp.file.title, "YYYY-[W]W") %>

<< [[<% fileDate = moment(tp.file.title, 'YYYY-MM-DD-dddd').subtract(1, 'w').format("[Notes]/YYYY/MM-MMMM/gggg-[W]ww") %>|Last Week]] | [[<% fileDate = moment(tp.file.title, 'YYYY-MM-DD-dddd').format("[Notes]/YYYY/MM-MMMM/gggg-[W]ww") %> | This Week ]] |[[<% fileDate = moment(tp.file.title, 'YYYY-MM-DD-dddd').add(1, 'w').format("[Notes]/YYYY/MM-MMMM/gggg-[W]ww") %>| Next Week]] >>

---
### 📅 Daily Questions
##### 🌜 Last night, after work, I...
- 

##### 🙌 One thing I've excited about right now is...
- 

##### 🚀 One+ thing I plan to accomplish today is...
- [ ] 

##### 👎 One thing I'm struggling with today is...
- 

---
# 📝 Notes
- <% tp.file.cursor() %>

---
### Notes created today
```dataview
List FROM "" WHERE file.cday = date("<%tp.date.now("YYYY-MM-DD")%>") SORT file.ctime asc
```

### Notes last touched today
```dataview
List FROM "" WHERE file.mday = date("<%tp.date.now("YYYY-MM-DD")%>") SORT file.mtime asc
```