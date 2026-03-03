University: ITMO University
Faculty: FICT Course: Введение в веб технологии
Year: 2025/2026
Group: U4125
Author: Vinogradskaia Anastasia Leonidovna
Lab: Lab1
Date of create: 03.03.2026
Date of finished: 03.03.2026

Что сделано:
Часть 1 
1. Установлен docker(почитала https://docs.docker.com/)
2. Проверена установка командой docker --version
3. Запущен тестовый контейнер docker run hello-world, проверено что docker корректно создает и запускает контейнеры
4. Изучены базовые команды:
- docker images 
- docker ps 
- docker ps -a

<img width="1002" height="541" alt="image" src="https://github.com/user-attachments/assets/371af13c-af78-420f-b657-304590d6c5c9" />

+ Разобралась в теории (пообщалась с нейросетями):
- Docker — это платформа контейнеризации
Контейнер изолирует приложение со всеми зависимостями и позволяет запускать его одинаково на любой машине
- Образ — это шаблон (набор слоев файловой системы), из которого создается контейнер
-Контейнер — запущенный экземпляр образа
Контейнер использует ядро хостовой ОС и легче по ресурсам, виртуальная машина эмулирует полноценную отдельную систему

Часть 2
1. Скачан образ ubuntu:latest командой docker pull ubuntu:latest
Что такое тег?
Образ может иметь несколько версий
ubuntu:latest — это последняя доступная версия
Можно было бы указать конкретную, например ubuntu:22.04
2. Запущен интерактивный контейнер docker run -it ubuntu bash
- docker run — создать и запустить контейнер
- -i — интерактивный режим
- -t — псевдотерминал (чтобы можно было вводить команды)
- ubuntu — образ
- bash — что запускать внутри контейнера
3. Внутри контейнера выполнено обновление пакетов и установка curl через apt update && apt install -y curl
4. Проверена установка командой curl --version
5. Выполнен выход из контейнера

<img width="1317" height="791" alt="image" src="https://github.com/user-attachments/assets/83e6a835-ba0e-46cc-8d1a-a10076a16a8e" />
<img width="1317" height="524" alt="image" src="https://github.com/user-attachments/assets/fdef0107-7b1e-4477-bb63-3a72179e904e" />
  

Часть 3
1. Запущен контейнер nginx:alpine в фоновом режиме командой docker run -d -p 8080:80 --name web-server nginx:alpine
2. Проверена работа сервера в браузере по адресу http://localhost:8080
3. Просмотрены логи контейнера через docker logs web-server
4. Выполнено подключение внутрь контейнера через docker exec -it web-server sh

<img width="1317" height="791" alt="image" src="https://github.com/user-attachments/assets/68ef2721-59ca-4b6a-a246-6f1b1f3456ea" />
<img width="654" height="240" alt="image" src="https://github.com/user-attachments/assets/ad9d32b5-10f2-48d5-88b5-662181931c06" />


Часть 4
1. Просмотрены запущенные и все контейнеры (docker ps, docker ps -a)
2. Остановлен контейнер docker stop web-server
3. Повторно запущен через docker start web-server
4. Удален контейнер docker rm web-server
5. Удален образ docker rmi nginx:alpine
<img width="1196" height="261" alt="image" src="https://github.com/user-attachments/assets/895bca18-360e-47d2-91bc-512b61bc95cf" />

Часть 5
1. Создан том docker volume create my-volume
2. Запущен контейнер с подключением тома
3. docker run -it -d --name volume-test -v my-volume:/data ubuntu bash
4. Внутри контейнера создан файл /data/test.txt
5. Контейнер остановлен и удален
6. Создан новый контейнер с тем же томом
7. Проверила, что файл сохранился, значит, постоянное хранилище сохранилось
<img width="1118" height="273" alt="image" src="https://github.com/user-attachments/assets/eb67b562-1ab1-4860-8052-95b76038e10a" />

