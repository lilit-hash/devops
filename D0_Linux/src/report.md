## Part 1. Установка ОС

Скачиваем дистрибутив ISO с официального сайта http://ubuntu.com

Подключаем ISO к новой созданной VM

Устанавливаем дистрибутив с настройками по-умолчанию (серверная сборка идет уже без графического интерфейса)

Проверка установленной версии сервера

![alt text](img01.jpeg)

## Part 2. Создание пользователя

Создадим пользователя newuser и добавляем в группу adm. 

Вводим команду sudo adduser -p newuser -s /bin/bash newuser -G adm

![alt text](img03.jpeg)

Вывод команды cat /etc/passwd В последней строчке наш пользователь.

![alt text](img02.jpeg)

## Part 3. Настройка сети ОС

1. Изменение имени машины

![alt text](img05-1.jpeg)

2. Изменение временной зоны

![alt text](img06.jpeg)

Интерфейс lo - виртуальный интерфейс с именем localhost по адресу 127.0.0.1 для обращения по сети к самой машине, на которой мы работаем.

3. Применяем netplan -tan, проверяем настройки сети

![alt text](img23.jpeg)

4. Перезагрузка машины, проверка настроек
	reboot now

5. Пинг хостов 

![alt text](IMG_1332.jpg)

## Part 4. Обновление ОС

sudo apt update

sudo apt upgrade

![alt text](img04.jpeg)

## Part 5. Использование команды sudo

Проверка текущего наименлования хоста

Попытка изменить хостнейм от имени newuser

При получении сообщения об ограниченных правах для пользователя добавляем его в группу sudo

![alt text](img05-3.jpeg)

## Part 6. Установка и настройка службы времени

![alt text](img06-1.jpeg)

## Part 7. Установка и использование текстовых редакторов

Редактирование

vim test_VIM.txt

Клавиша INSERT -> hunnimod -> Esc -> :wq

![alt text](img07.jpeg)

nano test_Nano.txt -> hunnimod -> Ctrl+O -> Ctrl+X

![alt text](img08.jpeg)

joe test_joe.txt -> hunnimod -> Ctrl + K, X

![alt text](img11.jpeg)

Выход без изменений

vim test_VIM.txt -> 21 School 21 -> :q!

![alt text](img10.jpeg)

nano test_Nano.txt -> 21 School 21 -> Ctrl+X -> N (No)

![alt text](img09.jpeg)

joe test_joe.txt -> 21 School 21 -> Ctrl + C

![alt text](img.jpeg)

Замена слов

vim test_VIM.txt -> :s/test/part -> :wq

![alt text](img14.jpeg) 

![alt text](img15.jpeg) 

![alt text](img16.jpeg)

nano test_Nano.txt -> Ctrl+\ -> test -> part -> Yes -> Ctrl+O -> Ctrl+X

![alt text](img19.jpeg) 

![alt text](img18.jpeg) 

![alt text](img17.jpeg)

joe test_joe.txt -> Ctrl + K, F -> test -> part

![alt text](img12.jpeg) 

![alt text](img13.jpeg)

## Part 8. Установка и базовая настройка сервиса SSHD

1. Установить службу SSHd.

  sudo apt update

  sudo apt install ssh

  sudo apt install openssh-server

  ![alt text](img20.jpeg)

Автостарт при запуске системы

sudo systemctl enable ssh

Перенастройка порта

nano /etc/ssh/sshd_config

Добавляем Port 2022

![alt text](img21.jpeg)

Проверка запуска службы sshd, перезапуск, просмотр процесса

![alt text](img22.jpeg)

ps - команда, которая выводит статистику и информацию о состоянии процессов в системе, в том числе ИД процесса или нити, объем выполняемого ввода-вывода и используемый объем ресурсов процессора и памяти. 

Список ключей: 

-A, -e, (a) - выбрать все процессы; 

-a - выбрать все процессы, кроме фоновых; 

-d, (g) - выбрать все процессы, даже фоновые, кроме процессов сессий; 

-N - выбрать все процессы кроме указанных; 

-С - выбирать процессы по имени команды; 

-G - выбрать процессы по ID группы; 

-p, (p) - выбрать процессы PID; 

--ppid - выбрать процессы по PID родительского процесса; 

-s - выбрать процессы по ID сессии; 

-t, (t) - выбрать процессы по tty; 

-u, (U) - выбрать процессы пользователя.


Перезагружаем sudo reboot

netstat -tan

![alt text](img23-1.jpeg)

netstat - команда для вывода списка открытых портов и соответствующих им адресов, таблиц маршрутизации и скрытых соединений.

Список ключей:

-t - Отображение текущего подключения в состоянии переноса нагрузки с процессора на сетевой адаптер при передаче данных ( "offload" );

-a - Отображение всех подключений и ожидающих портов;

-n - Отображение адресов и номеров портов в числовом формате.

Proto - Протокол, используемый сокетом.

Recv-Q - Счётчик байт не скопированных программой пользователя из этого сокета.

Send-Q - Счётчик байтов, не подтверждённых удалённым узлом.

Local Address - Адрес и номер порта локального конца сокета. Если не указана опция --numeric (-n), адрес сокета преобразуется в каноническое имя узла (FQDN), и номер порта преобразуется в соответствующее имя службы.

Foreign Address - Адрес и номер порта удалённого конца сокета. Аналогично "Local Address"

State - Состояние сокета.

0.0.0.0 -  это немаршрутизируемый адрес IPv4, который используется в качестве адреса по умолчанию или адреса-заполнителя.




## Part 9. Установка и использование утилит top, htop


Вызов команды top

uptime - 6:00 

количество авторизованных пользователей - 1

общая загрузка системы - 0.08, 0.24, 0.17

общее количество процессов - 200

загрузка cpu - 0.2 us, 0.3 sy, 0.0 ni, 99.5 id, 0.0 wa, 0.0 hi, 0.0 si, 0.0 st 

загрузка памяти - 3888.3 total, 3223.1 free, 257.7 used, 407.5 buff/cache 

pid процесса занимающего больше всего памяти - 734

pid процесса, занимающего больше всего процессорного времени - 783


![alt text](img24.jpeg)

Вызов команды htop. 

htop / Сортировка по PERCENT_CPU по умолчанию

![alt text](img32.jpeg)

Сортировка по PID

![alt text](img25.jpeg)

Сортировка по TIME

![alt text](img31.jpeg)

Сортировка по PERCENT_MEM

![alt text](img30.jpeg)

Поиск по syslog

![alt text](img34.jpeg)

Добавлен вывод hostname, clock и uptime

![alt text](img37.jpeg)



## Part 10. Использование утилиты fdisk

Запускаем команду fdisk -l для просмотра данных о жестком диске

![alt text](img38.jpeg)

Disk /dev/sda: 20 GiB, 10737418240 bytes, 21474836480 sectors - название диска, размер, кол-во секторов

Disk model: VmWare Virtual S - модель диска

Логические диски:

Device       Start      End    Sectors      Size      Type

/dev/sda1     2048     4095     2048         1M     BIOS Boot

/dev/sda2  4096      3719167    3715072     1.8G    Linux filesystem

/dev/sda3  3719168   38221824   38221824    18.2G   Linux filesystem


Получение информации о размере swap-файла на жёстком диске

![alt text](image.jpeg)


## Part 11. Использование утилиты df

df / получение информации о дисковом пространстве

![alt text](img40.jpeg)

Размер раздела - 10218772; 

Размер занятого пространства - 2995412; 

Размер свободного пространства - 66822688; 

Процент использования - 31;

Единица измерения - 1K-blocks (килобайт).

Запустить команду df -Th / получение информации о дисковом пространстве с типом файловой системы и размерами в читаемом виде

![alt text](img41.jpeg)

Размер раздела - 9.8G; 

Размер занятого пространства - 1.6M; 

Размер свободного пространства - 6.4G; 

Процент использования - 31;

Тип файловой системы - ext4

## Part 12. Использование утилиты du

du / получение информации о размере всех файлов в определённой папке

![alt text](immg.jpeg)

Получение информации о размере папок /home, /var, /var/log в байтах

![alt text](img44.jpeg) 

![alt text](img46.jpeg)

![alt text](img42.jpeg)

Получение информации о размере папок /home, /var, /var/log в человекочитаемом виде.

![alt text](img42-1.jpeg)

![alt text](img43.jpeg)

![alt text](img45.jpeg)

Получение информации о размере всего содержимого в /var/log в человекочитаемом виде (не общее, а каждого вложенного элемента, используя *)

![alt text](imgvar.jpeg)

## Part 13. Установка и использование утилиты ncdu

apt install ncdu

ncdu /home

![alt text](img47.jpeg)

ncdu /var

![alt text](img49.jpeg)

ncdu /var/log

![alt text](img50.jpeg)

## Part 14. Работа с системными журналами

cat /var/log/dmesg

![alt text](img51.jpeg)

cat /var/log/syslog

![alt text](img52.jpeg)

cat /var/log/auth.log

![alt text](img53.jpeg)

Aug 7 13:14:12 lienich pam_unix(sudo:session): session closed for user root

Время: 7 августа 13:14:12

Имя: root

Метод: pam_unix



Перезапуск службы sshd / systemctl restart sshd ->  sudo grep -i "restart" /var/log/syslog

![alt text](<img55 2.jpeg>)


## Part 15. Использование планировщика заданий CRON

Формат cron: минута час день месяц день_недели /путь/к/исполняемому/файлу

Посмотреть задачи cron для суперпользователя, для этого можно воспользоваться опцией -l:

`crontab -l`

![alt text](img60.jpeg)

crontab -e

Добавляем исполнение uptime каждые 2 минуты (для этого используется косая черта, иначе задача будет выполняться каждую 2-ю минуту часа)

![alt text](img57.jpeg)

Проверка crontab -l

![alt text](img59.jpeg)

Данные логов о выполнении cron

![alt text](img58.jpeg)

Очистка заданий планировщика / crontab -r -> crontab -l

![alt text](img60-1.jpeg)

