Введение в Линукс
=================

Разогрев
--------

Зайдите в терминал. Введите команды, попытайтесь проинтерпретировать их вывод.
```
echo hello world
date
hostname
arch
uname -a
dmesg | less  # выйти можно будет, нажав клавишу q
uptime
whoami
who
id
last

top  # выйти можно будет, нажав клавишу q
htop
apt-get install htop
sudo apt-get install htop
htop

echo $SHELL
env
echo $PS1
OLDPS1=$PS1
PS1="$PS1^_^ "

ls
ls -l
ls -a
ls -l -a
ls -la
ls -lah
ls -lahF

PS1=$OLDPS1
echo {con,pre}{sent,fer}{s,ed}
echo *
echo .*
ls .*
ls -d .*
ls .bash*

man universe
man ls  # выйти можно будет, нажав клавишу q
man who  # выйти можно будет, нажав клавишу q
sudo apt-get install manpages-ru  # может не получиться
man ls

clear
cal 2014
cal 9 1752  # что за чертовщина?

time ls
time sleep 2
history

cd
pwd
ls -al
cd .
pwd
cd ..
pwd
ls -al
cd ..
pwd
ls -al
cd ..
pwd
cd /etc
ls -al | less  # выйти можно будет, нажав клавишу q
ls -al | less  # наберите /pass<Enter>
cat passwd
cat group
cd -
pwd
cd && pwd

cd /usr/share/dict
ls
cat american-english | grep key
cat american-english | head
cat american-english | head -n 20
cat american-english | grep key | cat -n
cat american-english | grep key | wc
cat american-english | grep \'s  # приложение можно завершить по Ctrl+C
cat american-english | grep -v \'s  # приложение можно завершить по Ctrl+C
cat american-english | grep key | head
cat american-english | grep -i key | head

cd
mkdir found_in_dict
cd /usr/share/dict
cat american-english | grep key | head > ~/found_in_dict/case_sensitive.txt
cat american-english | grep -i key | head > ~/found_in_dict/case_insensitive.txt
cd ~/found_in_dict/
pwd
ls
diff case_sensitive.txt case_insensitive.txt

cd
wget --no-check-certificate http://github.com/vpavlenko/linux-task/blob/master/Cache.tar.gz?raw=true
mv Cache.tar.gz\?raw\=true Cache.tar.gz
tar xvf Cache.tar.gz
cd Cache
ls
grep -nr sourceforge .
cd 0 && ls && cd 2F && ls
file *
firefox *
firefox * &
ps aux | grep firefox
pkill firefox
ps aux | grep firefox

which python
ls -lah `which python`
ls -laHh `which python`
man ls  # /follow

ls /bin
hexdump -C /bin/less
hexdump -C /bin/less | less
strings /bin/less
history | tail
md5sum /bin/less

ifconfig
ping google.ru  # завершить: Ctrl+C
traceroute google.ru

cd /proc
ls /proc  # что здесь? побродите, поизучайте

which less
ls /bin | grep less
ps aux | grep less
chmod a-x /bin/less
sudo chmod a-x /bin/less
ps aux | grep less
ls /bin | grep less
chmod a+x /bin/less
ps aux | grep less
```

Задание 1: разминка
-------------------

1. Используя команды `cd`, `ls` и `pwd`, загляните в директории `/bin`, `/sbin`, `/usr/bin`, `/boot`.
Что в них хранится?

2. Что делает команда `cat /dev/urandom | cut -c 1-16 | head -1 | hexdump -C`?

3. Зайдите в директорию `/proc`. Просмотрите командой `cat` файлы `cpuinfo`, `meminfo`, `uptime`.
Понимаете ли вы, что значит "`/proc` является виртуальной файловой системой, которая предоставляет доступ
к данным ядра"?

4. Создайте в своей домашней директории папки `work` и `play`.

5. Удалите папку `play`.

7. Что хранится в файлах /etc/passwd, /etc/group, /etc/shadow? Можете ли вы просмотреть
содержимое всех трёх файлов? Залогиниться под рута можно командой sudo su.

6. Скопируйте файл `/etc/passwd` в вашу домашнюю директорию (`/home/USERNAME` или же `~`).
Затем переменуйте копию этого файла в no_passwords.txt

Задание 2: wget
---------------

1. Выкачайте все страницы туториала http://rypress.com/tutorials/objective-c/
Пожалуйста, не выкачайте заодно весь интернет.
Прочитайте `man wget` или узнайте у Гугла, как это сделать.

2. Используя команду `tar`, соберите все выкачанные файлы в один архив.

3. Найдите на всех страницах встречающиеся ссылки на внешние ресурсы.
Найдите повторы. Найдите сайты, ссылки на которые нам чаще всего случаются.
К вашим услугам `sed`, `find`, `grep -nr SOMETHING .`, `uniq`, `sort`.


Задание 3: пользователи и права
-------------------------------

Создайте группу пользователей class-11, в ней два пользователя: masha и petya.
Отдельно создайте группу class-10, в нём создайте пользователя vasya.
К вашим услугам `man adduser`, `man useradd`, `mkdir`, `chmod`, `chgrp`, `login`.

Почитайте справочную информацию про `who`, `passwd`, `login`, `logout`, `cat /etc/passwd`

В директории /home/petya создайте две папки public и private. 
Содержимое папки private не должно быть
доступно пользвателям masha и vasya. Содержимое папки public должно быть им доступно.

Создайте в папке public принадлежащий Пете файл all-writable.txt, содержимое которого каждый может редактировать.
Также создайте файл other-readonly.txt, содержимое которого может править только Петя.

Создайте папку /var/class-11, доступ к которой есть только у учеников, состоящих в группе
class-11. Стоит ли выставить sticky bit в атрибуты доступа к этой папке? Выставьте его.

Проверьте, что ваши настройки прав работают, логинясь под всех трёх пользователей.


Задание 4: скрипты 
------------------

1. Напишите скрипт, который принимает два параметра X и Y и выводит на стандартный вывод
разложение простых чисел на отрезке от X до Y. К вашим услугам гугл (найдите, как делаются циклы в баше)
и `factor`.

2. Возьмите сто английских слов, для каждого посчитайте, сколько раз оно встречается в гугле.
Используйте `curl`, `grep`, `sed`. Сделайте баш-скрипт. Придумайте, какие должны быть параметры у этого скрипта.
Если количество переданных параметров неправильное, то печатайте инструкцию по использованию скрипта.

1. Найдите в архиве Cache.tar.gz все картинки и переложите их в отдельную папку. Для
этого используйте рекурсивный обход (как это сделать в баше?) и команду `file`.

2. Переименуйте эти картинки номерами 1, 2, 3...

3. Переделайте скрипт так, чтобы он складывал файлы разных типов в разные папки.


Задание 5: администрирование
----------------------------

1. Поставьте веб-сервер ngingx. Переставьте в конфигах в /etc/nginx/ директорию, которую он обслуживает,
на /home/student/www/. Положите в эту папку простой html-css-js-сайт и проверьте, что он открывается 
из браузера на localhost.

2. Найдите пример CGI-скрипты для Питона, положите его в директорию сервера и завставьте сервер выполнять его.
Проставьте CGI-скрипту нужные права файла, чтобы веб-сервер смог его запустить.

3. От имени какого пользователя запускается веб-сервер? CGI-скрипт?

4. Напишите скрипт index.php, который считает содержимое файла messages.txt на сервере и выводит его,
предваряя h1-заголовком. Добейтесь того, чтобы index.php не отдавался сервером как файл, а исполнялся.
Для этого гуглите, как поставить php на ubuntu и как сконфигурировать php под nginx.

5. Напишите гостевую книгу: скрипт на php, который принимает имя автора и сообщение и сохраняет его на
сервере в таблице в базе данных. Поставьте и настройте СУБД mysql. Создайте в админке mysql необходимую таблицу.

6. Соберите из исходных текстов и установите [ejudge](https://ejudge.ru/wiki/index.php/%D0%98%D0%BD%D1%81%D1%82%D0%B0%D0%BB%D0%BB%D1%8F%D1%86%D0%B8%D1%8F_%D0%B8%D0%B7_%D0%B8%D1%81%D1%85%D0%BE%D0%B4%D0%BD%D1%8B%D1%85_%D1%82%D0%B5%D0%BA%D1%81%D1%82%D0%BE%D0%B2).

Материалы
---------

[Г. Курячий, К. Маслинский. Операционная система Linux](http://docs.altlinux.org/books/altlibrary-linuxintro2.pdf)
- достаточно прочитать лекции 1-8

http://www.doc.ic.ac.uk/~wjk/UnixIntro/ - отсюда я взял упражнения

http://linuxcommand.org/lc3_learning_the_shell.php
http://linuxcommand.org/lc3_writing_shell_scripts.php
