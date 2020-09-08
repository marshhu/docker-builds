#docker 命令
   #docker pull 从 Docker 镜像仓库获取镜像
     docker pull [选项] [Docker Registry 地址[:端口号]/]仓库名[:标签]
   #列出镜像
     docker image ls [-aq]
     docker images [-aq]   
   #删除虚悬镜像
     docker image prune
   #删除本地镜像
     docker image rm [选项] <镜像1> [<镜像2> ...]
     docker rmi [选项] <镜像1> [<镜像2> ...]  
     #删除所有仓库名为 redis 的镜像  
       docker image rm $(docker image ls -q redis)
     #删除所有在 mongo:3.2 之前的镜像
       docker image rm $(docker image ls -q -f before=mongo:3.2)
   #构建镜像
     docker build [选项] <上下文路径/URL/->
     
#Dockerfile指令
   #FROM 指定基础镜像
     FROM scratch   #空白镜像
   #RUN 执行命令
     shell 格式：RUN <命令>  
       eg: RUN echo '<h1>Hello, Docker!</h1>' > /usr/share/nginx/html/index.html
     exec 格式：RUN ["可执行文件", "参数1", "参数2"]，这更像是函数调用中的格式 
   #COPY 复制文件
     COPY [--chown=<user>:<group>] <源路径>... <目标路径>
     COPY [--chown=<user>:<group>] ["<源路径1>",... "<目标路径>"] 
   #CMD 容器启动命令
     shell 格式：CMD <命令>
     exec 格式：CMD ["可执行文件", "参数1", "参数2"...]
   #ENTRYPOINT 入口点
   
   
#docker compose
https://docs.docker.com/compose/