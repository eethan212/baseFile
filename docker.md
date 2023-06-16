### docker command
 
```python
# 查看版本
docker version
# 从docker文件构建docker映像
docker build -t image-name docker-file-location
# 运行docker映像(-d 守护态)
docker run -d image-name
# 查看可用的docker映像
docker images
# 查看最近的运行容器
docker ps -l
# 查看所有正在运行的容器
docker ps -a
# 停止运行容器
docker stop container_id
# 删除一个镜像
docker rmi image_name
# 删除所有镜像
docker rmi $(docker images -q)
# 强制删除所有镜像
docker rmi -r $(docker images -q)
# 删除所有虚悬镜像
docker image prune
docker rmi $(docker images -q -f dangling=true)
# 进入docker容器
docker exec -it container_id /bin/bash
# 查看所有的数据卷
docker volume ls
# 删除指定的数据卷
docker volume rm [volumn_name]
# 删除所有未关联的数据卷
docker volumn rm $(docker volumns ls -qf dangling=true)
```
 
 
 
### Dockerfile
 
```python
# 指令
COPY 
ADD  # COPY并解压
RUN
CMD  # 脚本执行(只允许用一次)
ENTRYPOINT # 脚本执行(只允许用一次，可与CMD一起使用) 
# ps: 如果要启动多个，可以将多个程序的启动命令写在同一个startup.sh中，然后用ENTRYPOINT启动startup.sh
ENV  # 环境变量 
VOLUMN  # 数据卷
EXPOSE  # 暴露端口 
WORKDIR  # 像cd 
```
