podman build -t almalinux-java17-image .  
podman pull mysql  
podman pod create -p 8080:8080 -p 3306:3306 -p 33060:33060 --name my-pod  
podman run --detach --pod my-pod --name almalinux-java17-container -it almalinux-java17-image  
podman run --detach --pod my-pod --name mysql-container -e MYSQL_DATABASE=testdb -e MYSQL_USER=testuser -e MYSQL_PASSWORD=12345678 -e MYSQL_RANDOM_ROOT_PASSWORD=yes -it mysql  
