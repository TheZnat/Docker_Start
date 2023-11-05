Установка докера
sudo apt update
sudo apt install apt-transport-https
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
sudo apt update
sudo apt install docker-ce
sudo systemctl status docker
sudo usermod -aG docker $USER

--------------------

работка с докером 

docker ps /  docker ps -a - Список контейнеров /  'a' — сокращение от 'all' выводит список всех контейнеров, независимо от их состояния.

docker search name - поиск images в Docker Hub

docker pull name - выгрузка образа, если его нету локально, то подет скачивание образа с docker hub

docker run -it -p 1234:8080 name / docker run -d -p 8888:80 nginx - Создайте и запустите новый контейнер из образа (-it в интерактивном режиме / -d с доступом к коноцоли (режим демон) / -p смена порта наКакомПортеЗапускать:ЗначПоУмолчанию )

docker images - образы докера доступные локально

docker rmi 'REPOSITORY/IMAGE ID' - удаление образа

docker rm 'CONTAINER ID' - удаление докера

--------------------
работа с докер файлом

mkdir mydocker    # создаем папку,
cd mydocker	  # в нем файл DockerFile
nano Dockerfile   # пишем наш докер файл (пример самого файла тут )

docker build -t myimage:v1 . - создаем из нашего Dockerfile Images c именем myimage с тегом v1 (точка в конце это означет локально создать )
docker images - проверяем появился ли образ 
docker run -d -p 7000:80 myimage:v1 - запускаем 


изменение 

docker exes -it 'Container ID' /bin/bash  - логин в контейнер
cd /var/www/html
exit - выход 



копирование 
docker commit "image id" "Repository":"New Tag"


--------------------------
 docker stop имя/id контейнера - остановть выпослнения контйнера 
 docker restart имя/id контейнера - перезагрузить докер контейнер
