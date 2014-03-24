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
wget Cache.tar.gz
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

Разное
------

1. (`wget`) Выкачайте все страницы книжки http://www.tldp.org/LDP/Bash-Beginners-Guide/html/
Пожалуйста, не выкачайте при этом весь интернет.

2. Найдите в архиве Cache.tar.gz все картинки и переложите их в отдельную папку.


Материалы
---------


http://linuxcommand.org/lc3_learning_the_shell.php
http://linuxcommand.org/lc3_writing_shell_scripts.php

http://www.doc.ic.ac.uk/~wjk/UnixIntro/

http://docs.altlinux.org/books/altlibrary-linuxintro2.pdf
Лекции 1-8


Пользователи и группы (не готово)
---------------------------------

Создайте группу пользователей class-11, в ней два пользователя: masha и petya.
Отдельно создайте группу class-10, в нём создайте пользователя vasya.

who
passwd
login
logout
cat /etc/passwd

В директории /home/petya создайте две папки public и private. 
Содержимое папки private не должно быть
доступно пользователю masha.

Что хранится в файлах /etc/passwd, /etc/group, /etc/shadow? Можете ли вы просмотреть
содержимое всех трёх файлов? Залогиниться под рута можно командой sudo su.


