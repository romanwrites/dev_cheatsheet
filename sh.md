# Unix-like shell stuff

## Store dotfiles nice way
I use it and recommend
[The best way to store your dotfiles: A bare Git repository](https://www.atlassian.com/git/tutorials/dotfiles)

## Docker
Get container id with name `postgres`. Stackoverflow [explanation](https://stackoverflow.com/a/34497614)
```bash
docker ps -aqf "name=postgres"
```

Remove container with name `postgres`
```bash
docker ps -aqf "name=postgres" | xargs -I{} docker rm -f {}
```

## Scripts
Find out which ports are busy  
1
```
sudo lsof | grep LISTEN
```
2
```
netstat -a -n | grep LISTEN
```

Count lines in files

1
```
cat **/*.cpp **/*.hpp | wc -l
```
2
```
find . -type f \( -name '*.cpp' -o -name '*.hpp' \) | xargs cat | wc -l
```

Copy file via ssh
```
scp -P <port> <source> <destination>

example:  
scp -P 2222 user@localhost:/home/user/some.tar.gz ~/dev/some_content
```

Find all files containing "string" inside of it
```
grep -iRlH "what to find" where_to_find
```

Find all files containg "sting" in the name of a file
```
find . -name "file mask" | grep -H "string"

//example:
find . -name "*.yaml" | grep -H "telegraf"
```

Kubernetes dashboard to run in a command line
```bash
#!/bin/bash

while :
do
	kubectl get pods > z
	echo -e "\n" >> z
	kubectl get svc >> z
	echo -e "\n" >> z
	kubectl get deployments >> z
	sleep 1
	clear
	cat z
done
```

Clear cache. You can add your directories. But use it wisely.
```bash
#!/bin/bash
echo y | exec $(rm -rf ~/Library/Caches/*)
echo y | exec $(rm -rf ~/Library/Application\ Support/Slack/Cache/*)
echo y | exec $(rm -rf ~/Library/Application\ Support/Slack/Service\ Worker/CacheStorage/*)
echo y | exec $(rm -rf ~/Library/Application\ Support/discord/Cache/*)
echo y | exec $(rm -rf ~/Library/Application\ Support/Code/Cache/*)
```

See how much disk space is used by every dir or file at current dir. And sort output from lowest to highest
```bash
du -hs *[^*] | sort -h
```
