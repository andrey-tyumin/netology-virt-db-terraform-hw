Задача 1

В данном задании вы научитесь изменять существующие Dockerfile, адаптируя их под нужный инфраструктурный стек.

Измените базовый образ предложенного Dockerfile на Arch Linux c сохранением его функциональности.

```
FROM ubuntu:latest

RUN apt-get update && \
    apt-get install -y software-properties-common && \
    add-apt-repository ppa:vincent-c/ponysay && \
    apt-get update
 
RUN apt-get install -y ponysay

ENTRYPOINT ["/usr/bin/ponysay"]
CMD ["Hey, netology”]
```

Для получения зачета, вам необходимо предоставить:

    Написанный вами Dockerfile
    Скриншот вывода командной строки после запуска контейнера из вашего базового образа
    Ссылку на образ в вашем хранилище docker-hub
Ответ:  
Ссылка на образ: https://hub.docker.com/repository/docker/imustgetout/ponysayinarch  
Вывод консоли:
```
root@vps13419:~/41# cat ./Dockerfile 
FROM archlinux:latest

RUN pacman -Syy && \
    pacman -S --noconfirm ponysay
 
ENTRYPOINT ["/usr/bin/ponysay"]
CMD ["Hey, netology"]
root@vps13419:~/41docker build -t imustgetout/ponysayinarch:1st .
Sending build context to Docker daemon  2.048kB
Step 1/4 : FROM archlinux:latest
 ---> 21f583c74284
Step 2/4 : RUN pacman -Syy &&     pacman -S --noconfirm ponysay
 ---> Running in f77f8bdaced3
:: Synchronizing package databases...
 core downloading...
 extra downloading...
 community downloading...
resolving dependencies...
looking for conflicting packages...

Packages (4) gdbm-1.20-1  libnsl-1.3.0-2  python-3.9.6-1  ponysay-3.0.3-4

Total Download Size:   12.51 MiB
Total Installed Size:  64.19 MiB

:: Proceed with installation? [Y/n] 
:: Retrieving packages...
 gdbm-1.20-1-x86_64 downloading...
 libnsl-1.3.0-2-x86_64 downloading...
 python-3.9.6-1-x86_64 downloading...
 ponysay-3.0.3-4-any downloading...
checking keyring...
checking package integrity...
loading package files...
checking for file conflicts...
:: Processing package changes...
installing gdbm...
installing libnsl...
installing python...
Optional dependencies for python
    python-setuptools
    python-pip
    sqlite [installed]
    mpdecimal: for decimal
    xz: for lzma [installed]
    tk: for tkinter
installing ponysay...
:: Running post-transaction hooks...
(1/1) Arming ConditionNeedsUpdate...
Removing intermediate container f77f8bdaced3
 ---> 1a21ae154ae7
Step 3/4 : ENTRYPOINT ["/usr/bin/ponysay"]
 ---> Running in 50620ddec1b7
Removing intermediate container 50620ddec1b7
 ---> 8b0a1b609652
Step 4/4 : CMD ["Hey, netology"]
 ---> Running in e3b8e25e0bbb
Removing intermediate container e3b8e25e0bbb
 ---> c340559ba4b7
Successfully built c340559ba4b7
Successfully tagged imustgetout/ponysayinarch:1st
root@vps13419:~/41docker images
REPOSITORY                   TAG       IMAGE ID       CREATED          SIZE
imustgetout/ponysayinarch    1st       c340559ba4b7   33 seconds ago   470MB
imustgetout/netology-httpd   1st       172d0f7c4ccc   47 hours ago     138MB
ubuntu                       latest    c29284518f49   2 days ago       72.8MB
archlinux                    latest    21f583c74284   3 days ago       382MB
httpd                        2.4       bd29370f84ea   7 days ago       138MB
httpd                        latest    bd29370f84ea   7 days ago       138MB
debian                       latest    7a4951775d15   3 weeks ago      114MB
centos                       latest    300e315adb2f   7 months ago     209MB
root@vps13419:~/41# docker run c340559ba4b7
 __________________ 
< Hey, netology    >
 ------------------ 
                  \                                
                   \                               
                    \                              
                     \                             
                      \      ▄▄                    
        ▄▄▄▄▄▄▄▄█▄██▄▄▄▄▄ ▄▄███                    
       ▄█████████████████▄████▄▄▄                  
      ▄████▄█▄███████▄▄█▄███▄▄▄▄▄▄▄                
      ██████▄██▄██▄█▄█████▄▄██▄▄███                
       █▄▄██ ▀▀▀██▄▄█████▄███▄▄▄▄▄▄█  ▄            
       ▄████     ███████▄▄▄▄▄▄█████▄▄▄█  ▄▄▄       
        ▀▄▄▄▄▄    ████▄▄████████▄▀▀███▄▄▄▄██▄▄     
            ▀    ▄▄▄▄▄███████████▀ ▀▀▀ ▄████▄█     
                ██████▄█▄█████▀▀      ██████▀      
                █▄▄▄▄█████▄▄▄▄█▄█▄▄ ██████▄▀       
                    ▀▄█████▄▄█▄▄▄▄█▄████▄▀         
                ��▄█▄█▄▄▄█▄████▄▄▄█████▄            
          ▄▄▄▄▄▄█▄▄████████▄██▄█████▄▄██████▄▄▄    
      ▄▄▄█████████████████▄▄▄▄█████▄█████████████▄▄
    ▄█████████▄▄▄████████▄███████████████████████▀▀
  ▄█████████▄▄▄█▄▄▄▄▄█▄▄▄█████████▄██████████▀▀    
     ▀▀██████▄█████▄▄█▄█▄█████████▄█████████       
         ▀▀▀█████▄▄▄▄█▄▄█▄█████▄█▄████████▀        
            ████▄██  █▄▄██████▄                    
            █████▄▄▄ █▄████▄██▄▄                   
            █████████▀▄████▀▄████                  
            █████████ ████▄▄▀▄██▄█                 
          █▄▄▄███████ ▀▄████ ████▄▄                
          ██▄██▄██▄▄▀  ████▄▄▀█████                
           ▀▀▀▀▀▀▀     ▀▄▄▄▄█ ▀▀▀▀▀                
                                                   

root@vps13419:~/41# docker push imustgetout/ponysayinarch:1st
The push refers to repository [docker.io/imustgetout/ponysayinarch]
827abdc61f0a: Pushed 
9caffbe10909: Mounted from library/archlinux 
3db625bec04e: Mounted from library/archlinux 
1st: digest: sha256:2ec89fb618f66fe33f9f743fc9cb23a1243238152b24a3211855f518440f57ad size: 950
root@vps13419:~/41# 
```

 Скриншот: 
 
---

Задача 2

В данной задаче вы составите несколько разных Dockerfile для проекта Jenkins, опубликуем образ в dockerhub.io и посмотрим логи этих контейнеров.

    Составьте 2 Dockerfile:

        Общие моменты:
            Образ должен запускать Jenkins server

        Спецификация первого образа:
            Базовый образ - amazoncorreto
            Присвоить образу тэг ver1

        Спецификация второго образа:
            Базовый образ - ubuntu:latest
            Присвоить образу тэг ver2

    Соберите 2 образа по полученным Dockerfile

    Запустите и проверьте их работоспособность

    Опубликуйте образы в своём dockerhub.io хранилище

Для получения зачета, вам необходимо предоставить:

    Наполнения 2х Dockerfile из задания
    Скриншоты логов запущенных вами контейнеров (из командной строки)
    Скриншоты веб-интерфейса Jenkins запущенных вами контейнеров (достаточно 1 скриншота на контейнер)
    Ссылки на образы в вашем хранилище docker-hub

Задача 3

В данном задании вы научитесь:

    объединять контейнеры в единую сеть
    исполнять команды "изнутри" контейнера

Для выполнения задания вам нужно:

    Написать Dockerfile:
        Использовать образ https://hub.docker.com/_/node как базовый
        Установить необходимые зависимые библиотеки для запуска npm приложения https://github.com/simplicitesoftware/nodejs-demo
        Выставить у приложения (и контейнера) порт 3000 для прослушки входящих запросов
        Соберите образ и запустите контейнер в фоновом режиме с публикацией порта

    Запустить второй контейнер из образа ubuntu:latest

    Создайть docker network и добавьте в нее оба запущенных контейнера

    Используя docker exec запустить командную строку контейнера ubuntu в интерактивном режиме

    Используя утилиту curl вызвать путь / контейнера с npm приложением

Для получения зачета, вам необходимо предоставить:

    Наполнение Dockerfile с npm приложением
    Скриншот вывода вызова команды списка docker сетей (docker network cli)
    Скриншот вызова утилиты curl с успешным ответом

