## basic
- docker version
- docker 
- docker --help
- docer images
- docker ps -a : show all containers (沒有-a default show just running)
- docker rm [containerID] : 刪除container
- docker inspect [containerName] : container 完整訊息
- docker start / stop [containerName] :  開啟 / 停止 container

## docker RUN (會直接push本地沒有的image下來)
- docker run -it -p 8000:80 --name aspnetcore_sample mcr.microsoft.com/dotnet/samples:aspnetapp
```
-i：attach時鍵盤輸入會被Container接手
-t：attach時Container的螢幕會接到原來的螢幕上。
* docker run -t -i可以直接寫成docker run -it 
* 從原來的Linux主機，進入了這個Container的內部操作介面

- p port number(對外:自己container使用的)
```

## docker 檔案或資料夾 複製 cp
- docker cp [copyFile] [containerName]:[ContainerPath] :將檔案複製到container指定路徑下
> docker cp index.html aspnetcore_sample:index.html :將目前路徑index複製到aspnetcore_sample container 目前路徑底下
> docker cp aspnetcore_sample:app D:\code\docker-note\webSample : 將aspnetcore_sample container app 資料夾複製到
本地端 D:\code\docker-note\webSample   
* 可搭配 cd 與 ls 指令確認檔案與資料夾 

## 進入 container
- docker exec -it <container-name> /bin/bash
## 跳出 container : Ctrl+D

## 產生 image (container 調整後,產生自己的image)
docker commit -m "mcr.microsoft.com/dotnet/samples:aspnetapp test" [containerName] [NewImageName]
docker commit -m "mcr.microsoft.com/dotnet/samples:aspnetapp test" aspnetcore_sample testimage
```
-m : 說明
*NewImageName 最好指定跟docker hub Repository 相同,前面要帶 ID (EX:maggylin/test),不然push時候要另外指定一個tag
```

## PUSH Docker Hub
1. docker login : 確認docker hub login 
2. docker push [hubName/repositoryName] => docker push maggylin/test
3. 如果 image 名稱不等於[hubName/repositoryName] , 使用docker tag [imageName] [humName] =>docker tag test username/test
4. 確認Doker Hub 有這個repository
