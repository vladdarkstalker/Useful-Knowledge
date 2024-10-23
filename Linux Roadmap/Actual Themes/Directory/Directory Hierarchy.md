**Sources:** 
1. https://roadmap.sh/linux, 
2. https://ru.wikipedia.org/wiki/FHS, 
3. https://refspecs.linuxfoundation.org/FHS_3.0/fhs-3.0.pdf, 
4. https://www.geeksforgeeks.org/linux-file-hierarchy-structure/
5. https://losst.pro/ctruktura-fajlovoj-sistemy-linux
6. https://wiki.merionet.ru/articles/obyasnenie-struktury-katalogov-linux
7. https://docs.redhat.com/en/documentation/red_hat_enterprise_linux/4/html/reference_guide/s1-filesystem-fhs#s3-filesystem-srv
8. https://dev.to/softwaresennin/linux-directory-structure-simplified-a-comprehensive-guide-3012

---

A Linux system’s directory structure, also known as the Filesystem Hierarchy Standard (FHS), is a defined tree structure that helps to prevent files from being scattered all over the system and instead organise them in a logical and easy-to-navigate manner. However, the descriptions here are those used specifically for the FHS and are not considered authoritative for platforms other than Linux.

### Directory structure

- `/` Root directory, the top level of the file system.
- `/home` User home directories.
- `/bin` Essential command binaries 
- `/boot` Static files of the boot loader 
- `/dev` Device files 
- `/etc` Host-specific system configuration 
- `/lib` Essential shared libraries and kernel modules 
- `/media` Mount point for removable media 
- `/mnt` Mount point for mounting a filesystem temporarily 
- `/opt` Add-on application software packages 
- `/run` Data relevant to running processes 
- `/sbin` Essential system binaries 
- `/srv` Data for services provided by this system 
- `/tmp` Temporary files 
- `/usr` Secondary hierarchy 
- `/var` Variable data

#### 1. / (Root)

Primary hierarchy root and root directory of the entire file system hierarchy.

- Every single file and directory start from the root directory.
- The only root user has the right to write under this directory.
- `/root` is the root user’s home directory, which is not the same as `/`

#### 2. /bin

Essential command binaries that need to be available in single-user mode; for all users, e.g., cat, ls, cp. Утилиты могут использоваться пока еще не подключен каталог /usr/.

- Contains binary executables.
- Common linux commands you need to use in single-user modes are located under this directory.
- Commands used by all the users of the system are located here e.g. ps, ls, ping, grep, cp

#### 3. /boot

 Boot loader files, e.g., kernels, initrd.  
 
- Kernel initrd, vmlinux, grub files are located under /boot
- Example: initrd.img-2.6.32-24-generic, vmlinuz-2.6.32-24-generic

#### 4. /dev

 Essential device files, e.g., /dev/null. Таким образом, все подключенные флешки, клавиатуры, микрофоны, камеры - это просто файлы в каталоге /dev/. Этот каталог содержит не совсем обычную файловую систему. Структура файловой системы Linux и содержащиеся в папке /dev файлы инициализируются при загрузке системы, сервисом udev. Выполняется сканирование всех подключенных устройств и создание для них специальных файлов. Это такие устройства, как: /dev/sda, /dev/sr0, /dev/tty1, /dev/usbmon0 и т д.

- These include terminal devices, usb, or any device attached to the system.
- Example: /dev/tty1, /dev/usbmon0

#### 5. /etc

 Host-specific system-wide configuration files.  Кроме конфигурационных файлов, в системе инициализации Init Scripts, здесь находятся скрипты запуска и завершения системных демонов, монтирования файловых систем и автозагрузки программ. Структура каталогов linux в этой папке может быть немного запутанной, но предназначение всех их - настройка и конфигурация.

- Contains configuration files required by all programs.
- This also contains startup and shutdown shell scripts used to start/stop individual programs.
- Example: /etc/resolv.conf, /etc/logrotate.conf.

#### 6. /home

 Users’ home directories, containing saved files, personal settings, etc.

- Home directories for all users to store their personal files.
- example: /home/kishlay, /home/kv

#### 7. /lib

 Libraries essential for the binaries in /bin/ and /sbin/.

- Library filenames are either ld* or lib*.so.*
- Example: ld-2.11.1.so, libncurses.so.5.7

#### 8. /media:

 Mount points for removable media such as CD-ROMs (appeared in FHS-2.3).

- Temporary mount directory for removable devices.
- Examples, /media/cdrom for CD-ROM; /media/floppy for floppy drives; /media/cdrecorder for CD writer

#### 9. /mnt 

 Temporarily mounted filesystems.

- Temporary mount directory where sysadmins can mount filesystems.

### 10. /opt 

Optional application software packages.

- Contains add-on applications from individual vendors.
- Add-on applications should be installed under either /opt/ or /opt/ sub-directory.

### 11. /sbin

Essential system binaries, e.g., fsck, init, route.

- Just like /bin, /sbin also contains binary executables.
- The linux commands located under this directory are used typically by system administrators, for system maintenance purposes.
- Example: iptables, reboot, fdisk, ifconfig, swapon

### 12. /srv

Site-specific data served by this system, such as data and scripts for web servers, data offered by FTP servers, and repositories for version control systems.

- srv stands for service.
- Contains server specific services related data.
- Example, /srv/cvs contains CVS related data.

### 13. /tmp

Temporary files. Often not preserved between system reboots and may be severely size restricted.

- Directory that contains temporary files created by system and users.
- Files under this directory are deleted when the system is rebooted.

### 14. /usr

Secondary hierarchy for read-only user data; contains the majority of (multi-)user utilities and applications.  
 

- Contains binaries, libraries, documentation, and source-code for second level programs.
- /usr/bin contains binary files for user programs. If you can’t find a user binary under /bin, look under /usr/bin. For example: at, awk, cc, less, scp
- /usr/sbin contains binary files for system administrators. If you can’t find a system binary under /sbin, look under /usr/sbin. For example: atd, cron, sshd, useradd, userdel
- /usr/lib contains libraries for /usr/bin and /usr/sbin
- /usr/local contains user’s programs that you install from source. For example, when you install apache from source, it goes under /usr/local/apache2
- /usr/src holds the Linux kernel sources, header-files and documentation.

### 15. /proc

 Virtual filesystem providing process and kernel information as files в реальном времени. In Linux, it corresponds to a procs mount. Generally, automatically generated and populated by the system, on the fly. По сути, это псевдофайловая система, содержащая подробную информацию о каждом процессе, его Pid, имя исполняемого файла, параметры запуска, доступ к оперативной памяти и так далее. Также здесь можно найти информацию об использовании системных ресурсов, например, /proc/cpuinfo, /proc/meminfo или /proc/uptime. Кроме файлов в этом каталоге есть большая структура папок linux, из которых можно узнать достаточно много информации о системе.

- Contains information about system process.
- This is a pseudo filesystem that contains information about running processes. For example: /proc/{pid} directory contains information about the process with that particular pid.
- This is a virtual filesystem with text information about system resources. For example: /proc/uptime

### 16. /var (variable)

Название каталога /var говорит само за себя, он должен содержать файлы, которые часто изменяются. Размер этих файлов постоянно увеличивается. Здесь содержатся файлы системных журналов, различные кеши, базы данных и так далее. Дальше рассмотрим назначение каталогов Linux в папке /var/.

### 17. /var/log

Здесь содержатся большинство файлов логов всех программ, установленных в операционной системе. У многих программ есть свои подкаталоги в этой папке, например, /var/log/apache - логи веб-сервера, /var/log/squid - файлы журналов кеширующего сервера squid. Если в системе что-либо сломалось, скорее всего, ответы вы найдете здесь.

### 18. /var/lib

Еще один тип изменяемых файлов - это файлы баз данных, пакеты, сохраненные пакетным менеджером и т д.

### 19. /var/mail

В эту папку почтовый сервер складывает все полученные или отправленные электронные письма, здесь же могут находиться его логи и файлы конфигурации.

### 20. /var/spool

Изначально, эта папка отвечала за очереди печати на принтере и работу набора программ cups.

### 21. /var/lock

Здесь находятся файлы блокировок. Эти файлы означают, что определенный ресурс, файл или устройство занят и не может быть использован другим процессом. Apt-get, например, блокирует свою базу данных, чтобы другие программы не могли ее использовать, пока программа с ней работает.

### 22. /var/run

Содержит файлы с PID процессов, которые могут быть использованы, для взаимодействия между программами. В отличие от каталога /run данные сохраняются после перезагрузки.

### 23. /sbin

Так же как и /bin, содержит двоичные исполняемые файлы, которые доступны на ранних этапах загрузки, когда не примонтирован каталог /usr. Но здесь находятся программы, которые можно выполнять только с правами суперпользователя. Это разные утилиты для обслуживания системы. Например, iptables, reboot, fdisk, ifconfig,swapon и т д.

### 24. /usr/bin/

Содержит исполняемые файлы различных программ, которые не нужны на первых этапах загрузки системы, например, музыкальные плееры, графические редакторы, браузеры и так далее.

### 25. /usr/sbin/

Содержит двоичные файлы программ для системного администрирования, которые нужно выполнять с правами суперпользователя. Например, таких как Gparted, sshd, useradd, userdel и т д.

### 26. /usr/lib/

Содержит библиотеки для программ из /usr/bin или /usr/sbin.

### 27. /usr/local

Содержит файлы программ, библиотек, и настроек созданные пользователем. Например, здесь могут храниться программы собранные и установленные из исходников и скрипты, написанные вручную.

### 28. /run

Еще один каталог, содержащий PID файлы процессов, похожий на /var/run, но в отличие от него, он размещен в TMPFS, а поэтому после перезагрузки все файлы теряются.

### 29. /sys

Назначение каталогов Linux из этой папки - получение информации о системе непосредственно от ядра. Это еще одна файловая система организуемая ядром и позволяющая просматривать и изменить многие параметры работы системы, например, работу swap, контролировать вентиляторы и многое другое.

**Tmpfs** — временное файловое хранилище во многих [Unix-подобных](https://ru.wikipedia.org/wiki/Unix-like "Unix-like") ОС. Предназначена для монтирования [файловой системы](https://ru.wikipedia.org/wiki/%D0%A4%D0%B0%D0%B9%D0%BB%D0%BE%D0%B2%D0%B0%D1%8F_%D1%81%D0%B8%D1%81%D1%82%D0%B5%D0%BC%D0%B0 "Файловая система"), но размещается в [ОЗУ](https://ru.wikipedia.org/wiki/%D0%9E%D0%97%D0%A3 "ОЗУ") вместо физического диска.

## Типы содержимого

Это основные типы контента, хранящегося в файловой системе Linux.

- **Постоянный (Persistent)** - это содержимое, которое должно быть постоянным после перезагрузки, например, параметры конфигурации системы и приложений.
- **Время выполнения (Runtime)** - контент, созданный запущенным процессом, обычно удаляется перезагрузкой
- **Переменный/динамический (Variable/Dynamic)** - это содержимое может быть добавлено или изменено процессами, запущенными в системе Linux.
- **Статический контент (Static)** - остается неизменным до тех пор, пока не будет явно отредактирован или перенастроен.


## Абсолютные и относительные пути

- Абсолютный путь: Это путь, который начинается с корневой директории. Корень - главный. Корневая директория обычно обозначается слэшем. Каждый раз, когда ваш путь начинается с `/`, Это оначает, что путь начинается с корневой директории. Например, `/home/pete/Desktop`.

- Относительный путь: Это путь, который начинается с того места, в котором вы сейчас находитесь. Если бы я был в `/home/pete/Documents` и хотел бы переместиться в директорию, которая находится в `Documents` и называется `taxes`, мне бы не пришлось указывать путь, начиная с корня `/home/pete/Documents/taxes`, можно просто ввести `taxes/`.
