# Docker
### Containers Management

- docker create Image: Create a New container
- docker start Container: Start a container
- docker stop Container: Gracefu stop a container
- docker kill Container: Kill (SIGKILL) a container
- docker restart Container: Graceful stop and restart a container
- docker pause Container: Suspend a container
- docker unpause Container: Resume a container
- docker rm Container: Destroy a container


### Container Bulk Management And Parameters

- docker stop $(docker ps -q): To stop all the running containers
- docker stop $(docker ps -a -q): To stop all the stopped and running containers
- docker kill $(docker ps -q): to kill all the running containers
- docker kill $(docker ps -a -q): To kill all the stopped and running containers
- docker restart $(docker ps -q): To restart all running containers
- docker restart $(docker ps -a -q): To restart all the stopped and running containers
- docker rm $(docker ps -q): To Destroy all running containers
- docker rm $(docker ps -a -q): To Destroy all the stopped and running containers
- docker pause $(docker ps -q): To pause all running containers
- docker pause $(docker -a -q): To pause all the stopped and running containers
- docker start $(docker ps -q): To start all running containers
- docker start $(docker-a -q): To start all the stopped and running containers
- docker rm -vf $(docker ps -a -q): To delete all container including its volumes use
- docker rmi -f $(docker images -a -q): To delete all the images
- docker system prune: to delete all dangling and unused images, containers, cache and volumes
- docker system prune -a: to delete all used and unused images
- docker system prune --volumes: to delete all docker volumes

### Commands

- docker attach Container: attach to a container
- docker cp Container:PATH HOSTPATH: copy files from the container
- docker cp HOSTPATH Container:PATH: copy files into the container
- docker export Container: Export the content of the container(tar archive)
- docker exec Container: Run a command inside a container
- docker exec -it CONTAINER /bin/bash: Open an interactive shell inside a container
- docker wait CONTAINER: Wait until the container terminates and return the exit code

### Images

- docker images: list all local images
- docker history IMAGE: SHOW the image history
- docker inspect IMAGE: Show information(Json formatted)
- docker tag IMAGE TAG: Tag an image
- docker commit CONTAINER IMAGE: create an image(from a container)
- docker import URL: create an image(from a tarball)
- docker rmi IMAGE: Delete Images
- docker pull REPO:(tag) : pull an image/repo from a registry
- docker push REPO:(tag) : push and image/repo to a registry
- docker search TEXT: search an image on the official registry
- docker login: login to a registry
- docker logout:  Logout from a registry
- docker save REPO:(tag) : Export an image/repo as a tarball
- docker load: Load images from a tarball

### Volumes

- docker volumes: list all volumes
- docker volumes create VOLUME: create a volume
- docker volumes inspect VOLUME: show information(json formatted)
- docker volumes rm VOLUME: Destroy a volumes


#### Backup a container

- docker run --rm --volumes-from CONTAINER -v $(pwd):/backup busybox tar cvfz /backup/backup.tar CONTAINERPATH

#### Restore container from backup

- docker run --rm --volumes-from CONTAINER -v $(pwd):/backup busybox bash -c "cd CONTAINERPATH && tar xvf /backup/backup.tar --strip 1"

#### Networking

- docker run --name netshoot --rm -it nicolaka/netshoot /bin/bash

``

# Xây Dựng Web Server Proxy bằng mã nguồn mở dùng Docker
- NPM (Nginx Proxy Manager) là hệ thống quản lý reversed proxy chạy trên Docker.
- NPM sử dụng Nginx và cung cấp cho người dùng trình quản lý thông qua giao diện web, giúp quản lí dễ dàng và hiệu quả hơn.

## Nginx Proxy Manager?

Nginx Proxy Manager (NPM) là hệ thống quán lí reversed proxy chạy trên Docker.
NPM sử dụng Nginx làm proxy Server.
Ngoài việc cấu hình Proxy Server, nó còn cho phép bạn cấu hình redirect domain, kích hoạt và tự động gia hạn SSL let's Encypt.

## Setup Nginx Proxy Manager

Setup Docker and Docker Compose

Setup Nginx Proxy Manager:
git clone https://github.com/jc21/nginx-proxy-manager.git
cd nginx-proxy-manager/doc/example/
docker-compose up -d

Kiểm tra:

Port 80: Nginx Proxy Server
Port 81: Nginx Proxy Manager

Email: admin@example.com
Password: changeme

https://viblo.asia/p/devops-docker-phan-1-docker-la-gi-3P0lPJa8Kox
