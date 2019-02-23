
# 构建镜像步骤
## 检出代码
```
git clone https://github.com/Quakertlist/fastdfs-docker.git
```

## 进入代码目录并编译
```
cd fastdfs-docker
docker build -t quakertlist/fastdfs .
```

# 环境变量介绍
## TRACKER_ENABLE
是否开启tracker标记，1为开启，默认为0

## NGINX_PORT
nginx开启监听端口，默认为80

## FASTDFS_TRACKE_PORT
开启tracker时的服务端口，默认22122

## FASTDFS_STORAGE_PORT
开启storage的监听端口，默认23000


# 使用示例
## 以下假设需要在192.168.1.100机器上开启
## 1.仅开启storage
```sh
# 开启分组名为group1的storage
docker run --add-host fastdfs.net:192.168.1.100 --name fastdfs --net=host-e NGINX_PORT=8801 -e FASTDFS_STORAGE_PORT=23000 -v $PWD/fastdfs:/storage/fastdfs -it quakertlist/fastdfs
```

## 2.开启storage 和tracker
```sh
# 开启tracker和分组名为group1的storage
docker run --add-host fastdfs.net:192.168.1.100 --name fastdfs --net=host -e NGINX_PORT=8801 -e TRACKER_ENABLE=1 -e FASTDFS_TRACKE_PORT=22122 -e FASTDFS_STORAGE_PORT=23000 -v $PWD/fastdfs:/storage/fastdfs -it quakertlist/fastdfs
```