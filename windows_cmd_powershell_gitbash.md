# Windows cmd & powershell

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

## Git Bash
Copy ssh-key to clipboard
```
clip < ~/.ssh/id_rsa.pub
```

## Lockscreen
```
windows + L
```

## Screenshot to clipboard
```
shift + win + S
```

## Intellij IDEA

### Setup bash in IDEA terminal on windows
Go to `File -> Settings -> Tools -> Terminal`  
Set Shell path `"C:\Program Files\Git\bin\bash.exe"`

### Export Idea settings
`File > Manage IDE Settings > Export Settings`

## Outlook
To view as conversations
`View` > `Show as Conversations`
