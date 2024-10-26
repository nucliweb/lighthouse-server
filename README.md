# lighthouse-server

## Requirements

- A [Railway](https://railway.app/) account
- The [Railway CLI](https://docs.railway.app/develop/cli) installed

## Deploy to Railway

```bash
$ railway login
> Open the browser? Yes
Logged in as John Lion (john@lion.com)


$ railway init
> Team Personal
> Project Name lighthouse-server
Created project lighthouse-server on Personal
https://railway.app/project/xxxx-xxxx-xxxx-xxxx

$ railway up --detach
```

## Add a PostgreSQL Database

```bash
$ railway add
> [x] PostgreSQL
  [ ] MySQL
  [ ] Redis
  [ ] MongoDB
  🎉 Added PostgreSQL to project
```

Looking to connect a database? Add a Variable Reference and select the DATABASE_URL option in the dropdown

## Add a Domain on Railway

Go into the lighthouse-server Settings tab and click "Generate domain" and port `8080` and Generate Domain

## Use server in the lighthouserc.json

```javascript
// lighthouserc.json
{
  "ci": {
    "collect": {
      "url": ["http://localhost:9000"],
      "numberOfRuns": 5,
      "startServerCommand": "npm run serve"
    },
    "assert": {
      "preset": "lighthouse:no-pwa"
    },
    "upload": {
      "target": "lhci",
      "serverBaseUrl": "[LHCI_SERVER_URL]"
    },
    "headful": false
  }
}
```
