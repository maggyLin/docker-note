### docker run

docker run --detach --hostname gitlab.example.com --publish 443:443 --publish 80:80 --publish 22:22 --name gitlab  --cap-add=NET_ADMIN --restart always --volume D:/code/docker/gitlab/config:/etc/gitlab --volume D:/code/docker/gitlab/logs:/var/log/gitlab --volume D:/code/docker/gitlab/data:/var/opt/gitlab --shm-size 256m gitlab/gitlab-ce:latest


docker run --detach --hostname gitlab.example.com --publish 443:443 --publish 80:80 --publish 22:22 --name gitlab  --cap-add=NET_ADMIN --volume D:/code/docker/gitlab/config:/etc/gitlab --volume D:/code/docker/gitlab/logs:/var/log/gitlab --volume D:/code/docker/gitlab/data:/var/opt/gitlab gitlab/gitlab-ce:latest

### cmd
gitlab-ctl restart
gitlab-ctl status
gitlab-ctl stop

### root password : 在 config資料夾(--volume D:/code/docker/gitlab/config:/etc/gitlab)
> docker exec -it gitlab grep 'Password:' /etc/gitlab/initial_root_password




### note...
> docker 第一次run gitlab下來, 要先 apt-get update , open browser 要使用 127.0.0.1 , 才能打開?


----
23端口 : https://www.cxyzjd.com/article/qq_32784303/90674127
iptables -A INPUT -p tcp --dport 23 -j ACCEPT
iptables -A OUTPUT -p tcp --sport 23 -j ACCEPT


