---
created: <% tp.file.creation_date() %>
---
tags:: #DailyNotes

# <% moment(tp.file.creation_date(),'YYYY-MM-DD').format("dddd, MMMM DD, YYYY") %>

<< [[<% fileDate = moment(tp.file.title, 'YYYY-MM-DD-dddd').subtract(1, 'd').format("[Notes]/[Daily]/YYYY/MM-MMMM/YYYY-MM-DD-dddd") %>|Yesterday]] | [[<% fileDate = moment(tp.file.title, 'YYYY-MM-DD-dddd').format("[Notes]/[Daily]/YYYY/MM-MMMM/gggg-[W]ww") %> | Week ]] |[[<% fileDate = moment(tp.file.title, 'YYYY-MM-DD-dddd').add(1, 'd').format("[Notes]/[Daily]/YYYY/MM-MMMM/YYYY-MM-DD-dddd") %>|Tomorrow]] >>

---
# 📝 Notes
- <% tp.file.cursor() %>

---