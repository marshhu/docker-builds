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
     
   #查看日志
   
     docker logs
     
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
   
   #ENV 设置环境变量
   
     ENV <key> <value>
     
     ENV <key1>=<value1> <key2>=<value2>...
     
   #ARG 构建参数
   
     docker build 中用 --build-arg <参数名>=<值> 
     
   #VOLUME 定义匿名卷
   
     VOLUME ["<路径1>", "<路径2>"...]
     
     VOLUME <路径>
   
   #EXPOSE 声明端口
   
     EXPOSE <端口1> [<端口2>...]
     
   #WORKDIR 指定工作目录
     
     WORKDIR <工作目录路径>
     
   #USER 指定当前用户
     
     USER <用户名>[:<用户组>]
   #HEALTHCHECK 健康检查
   
     HEALTHCHECK [选项] CMD <命令>：设置检查容器健康状况的命令
     
     HEALTHCHECK NONE：如果基础镜像有健康检查指令，使用这行可以屏蔽掉其健康检查指令
     
   #ONBUILD 为他人做嫁衣裳
     
     ONBUILD <其它指令>
     
#docker容器

   #新建并启动
   
     docker run [-it] [--rm] [--name] [-p] [-d]
     
     [-d]参数  后台运行
     
   #启动已终止容器
     docker container start
   
   #获取容器的输出信息
     docker container logs [container ID or NAMES]  
     
   #终止容器
   
     docker container stop  
     
   #进入容器
     
     docker exec  -it [container ID or NAMES]  bash
     
   #导出和导入容器
    
     docker export
     
     docker import
     
   #删除容器
   
     docker container rm [-f] [container ID or NAMES]   //-f参数 可以删除运行中的容器
     
     docker container prune  //清理所有处于终止状态的容器
     
#docker compose

https://docs.docker.com/compose/