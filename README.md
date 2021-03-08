# xminer_docker
f2pool矿机容器化部署

## bminer
### 以太坊
构建镜像
```
docker build -f bminer/DockerfileETH -t opennmt-py:latest .
```
启动容器
```
# 其中 WORKER_NAME可以任意指定，为f2pool中显示的work名称，每台矿机指定不同的WORKER_NAME
docker run --runtime=nvidia -e WORKER_NAME="docker-y" --name opennmt opennmt-py:latest
```
