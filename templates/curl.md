# Curl

## POST with certificates
```
curl -k --cert <some.pem> --key <some.key> -X POST <url> -H "Content-Type: application/json" -d @/path/file.json
```
