# Docker compose file to deploy GoCD server with x2 auto-registered GoCD agents

## Requirements
* Docker
* Docker compose

## Tested using the following environments
### Operating systems and Docker versions
* Ubuntu 16.04LTS (Server) using Docker version 17.05.0-ce, build 89658be
* macOS version 10.12.6 using Docker version 17.09.0-ce-rc1, build ae21824
* macOS version 10.13.6 using Docker version 18.06.1-ce-mac74, build 26766
### GoCD Docker image versions
* gocd/gocd-server:v17.9.0 + gocd/gocd-agent-ubuntu-16.04:v17.9.0
* gocd/gocd-server:v18.8.0 + gocd/gocd-agent-ubuntu-16.04:v18.8.0

## Usage Instructions

1. Clone the repo
2. From inside the repo run `docker-compose up -d` to run in daemon mode
3. Wait a few minutes for the server to start and the agents to register
4. Access the GoCD server at `http://<hostname>:8153`
5. To remove the stack use `docker-compose down`
6. To stop/start the stack use `docker-compose stop` and `docker-compose start`

**Notes**

- To change the auto-reg key, edit `/godata/config/cruise-config.xml` and update corresponding entries for the `AGENT_AUTO_REGISTER_KEY` environment variable(s) in `/docker-compose.yml`.
- The file `/godata/config/cruise-config.xml` will be populated/overwritten with agent details when the stack is relaunched/recreated.

For a clean install/re-install, edit `cruise-config.xml` and remove the `<agents>` section.

Example (from a previously launched stack remove the newly created section that looks like this):

```
  <agents>
    <agent hostname="c3ab4498e240" ipaddress="172.18.0.3" uuid="416f73c2-d33e-4cfd-a783-2ef350946b54" />
    <agent hostname="248cfcf561d6" ipaddress="172.18.0.4" uuid="822c3766-b306-42c6-bb0d-a6b8fb7f3ef7" />
  </agents>
```

Otherwise for stack (server & agents) stop/start, as advised use `docker-compose stop` and `docker-compose start`.
## Links
[Docker main site](https://www.docker.com/)

[GoCD Docker repo](https://hub.docker.com/u/gocd/)
