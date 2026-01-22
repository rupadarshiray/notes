---
created: 2026-01-12T15:16:25
modified: 2026-01-12T15:16:25
tags: []
aliases: []
---

# Exports

```dataviewjs

const currf = dv.current()

const Files = app.vault.getFiles().filter(file =>  file.path.includes("Exports/") && file.path.includes("pdf"));

function whattime(p){ 
if (dv.page(p)) {return dv.page(p).file.mtime}
else {return ""}
}

dv.table(["Files", "mtime", "note", "note mtime", 
//"path"
"link"
], Files
    .map(file => [
    dv.fileLink(file.path),
    String(moment(file.stat.mtime).format("DD-MM-YYYY")),
    ""+dv.fileLink(file.basename),
    whattime(file.basename),
    //file.path
    "[🔗](https://rupadarshiray.github.io/notes/"+file.basename.replaceAll(" ","%20")+".pdf)"
    ])
    )
```

