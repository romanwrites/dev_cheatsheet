# Windows cmd and powershell

## CMD
Find out where is java
```
where java
```

Set `path` env variable value
```
setx path "%path%;<your-new-path>"
```
Be very careful with this one, it will silently truncate path string if it's over 1024 bytes length

Open current folder
```
start .
```

## PowerShell
Count lines in files
```
dir -Recurse *.txt | Get-Content | Measure-Object -Line
```
