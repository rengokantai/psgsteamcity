# psgsteamcity
## 2. Setting up TeamCity
### 3 Windows Installation
```
Get-Service TeamCity
Get-Service TCBuildAgent
```

### 4 Linux and Mac Installation
mac
```
Downloads/TeamCity
bin/runAll.sh start
```
linux see [here](https://github.com/rengokantai/set/blob/master/README.md)

### 5 A docker-compose.yml for TeamCity
```
version: '2'
services:
  teamcity:
    image: jetbrains/teamcity-server:10.0.1
    volumes:
      - ./data/server/datadir:/data/teamcity_server/datadir:/data/teamcity_server/datadir
      - ./data/server/logs:/opt/teamcity/logs
    ports:
      - 8111:8111
  teamcity-agent:
    image: jetbrains/teamcity-agent:10.0.1
    volumes:
      - ./data/agent:/data/teamcity_agent/conf
    environment:
      SERVER_URL: http://teamcity:8111
```

### 6 Starting TeamCity Docker Containers
```
docker-compose up -d teamcity
```
#### 04:40
```
docker-compose logs -f teamcity-agent
```
