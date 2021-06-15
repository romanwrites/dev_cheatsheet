# Windows cmd

Find out where is java
```
where java
```

Set `path` env variable value
```
setx path "%path%;<your-new-path>"
```
Be very careful with this one, it will silently truncate path string if it's over 1024 bytes length
