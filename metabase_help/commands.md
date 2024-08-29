# Ⓜ️ METABASE (Docker) COMMANDS

Installing metabase: `sudo docker pull metabase/metabase:latest`
Docker list of containers: `sudo docker ps`
Docker list of containers (including stopped ones): `sudo docker ps -a`

### Docker Containers
Start container: `sudo docker run -d -p 3000:3000 --name metabase metabase/metabase`
Stop container: `sudo docker stop metabase`
Restart container: `sudo docker restar metabase`
Remove container: `sudo docker rm metabase`