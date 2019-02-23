# fastdfs-docker
this is a fastdfs docker project

# tracker defalut port
12050  FASTDFS_TRACKE_PORT
# storage default port
12041  FASTDFS_STORAGE_PORT
# start storage:
docker run --add-host fastdfs.net:10.10.5.170 --name fastdfs --net=host -v $(pwd):/storage/fastdfs -it mypjb/fastdfs
docker run --add-host fastdfs.net:10.10.5.170 --name fastdfs --net=host -e FASTDFS_STORAGE_PORT=23000 -v $(pwd):/storage/fastdfs -it mypjb/fastdfs

# simultaneously started:
docker run --add-host fastdfs.net:10.10.5.170 --name fastdfs --net=host -e TRACKER_ENABLE=1 -v $(pwd):/storage/fastdfs -it mypjb/fastdfs
docker run --add-host fastdfs.net:10.10.5.170 --name fastdfs --net=host -e TRACKER_ENABLE=1 -e FASTDFS_STORAGE_PORT=23000 -e FASTDFS_TRACKE_PORT=22122  -v $(pwd):/storage/fastdfs -it mypjb/fastdfs


# if you want to define listen nginx port Atendofstream NGINX_PORT replace:
docker run --add-host fastdfs.net:10.10.5.170 --name fastdfs --net=host -e TRACKER_ENABLE=1 -e NGINX_PORT=81 -v $(pwd):/storage/fastdfs -it mypjb/fastdfs
