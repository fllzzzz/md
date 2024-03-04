### RUN
- 在构建过程中执行命令
- 在容器内部执行
- 在新的镜像层中运行，并且在后续构建中，只有在该层之前的内容发生变化时才会重新运行
- 可以出现多次，并且每个RUN指令都会创建一个新的镜像层。为了减少镜像的层数，可以将多个命令合并为一行

### CMD
- 定义容器启动时默认要执行的命令
- 只能包含一个CMD指令，如果有多个，则只有最后一个CMD指令会生效
- docker run命令中指定了其他命令，则会覆盖CMD指令中的默认命令


### ENTRYPOINT
- 配置容器启动时的默认执行命令
- ENTRYPOINT指令的命令会在容器启动时始终执行，无论在docker run命令中是否指定了其他命令。它不会被覆盖，而是作为容器的主要执行命令
- 如果在docker run命令中指定了其他命令，这些命令将作为ENTRYPOINT指令的参数进行传递。也就是说，ENTRYPOINT指令中的命令将成为执行时的前缀

### ENV
- 设置环境变量。它允许在镜像构建过程中设置环境变量，这些环境变量将在容器运行时可用

```yaml
ENV MY_NAME John Doe
ENV APP_HOME /app

RUN mkdir $APP_HOME
WORKDIR $APP_HOME
```

### WORKDIR

### ARG
- 定义构建参数
- 构建过程中可以通过--build-arg选项进行覆盖

### COPY,ADD
- `--chown=<user>:<group>`
- `--chown=<user>:<group>`