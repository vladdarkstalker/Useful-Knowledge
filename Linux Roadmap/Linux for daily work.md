**Sources:** [100 команд Linux для ежедневной работы / Tproger](https://tproger.ru/articles/100–komand–linux–dlya–ezhednevnoj–raboty), [regular expression. (zephyrventum.github.io)](https://zephyrventum.github.io/download/linux1/man/brexpr.html)

---

## Общие команды Linux

1. `apropos <command>` – команда для поиска в файлах справочной страницы в Unix и Unix–подобных операционных системах.
2. `less` – отображает содержимое файла или вывод команды по одной странице за раз.
3. `command1 && command2 && ...` – предназначен для выполнения нескольких команд последовательно).
4. `| (pipe)` – вводит результат первой команды в последующую (`ps axu | grep proc_name`).
5. `Ctrl+Shift+C` – копировать текст из bash.
6. `Ctrl+Shift+V` – вставить текст из bash.
7. `alias` – is used to create shortcuts or aliases for other commands or sets of commands. Команда не сохраняет алиасы после перезагрузки, если понадобится постоянный алиас, поместите его в: `~/.bashrc`.
	`alias myfold='cd ~/Files/Scripts/Main'` – the ease of switching into smth directory.
	`unalias` – удалить алиас.
8. `echo` – it is used to output text to the terminal.
9. `getconf` – this use case is helpful when you want to explore all the available configuration values on your Linux system.
10. `grep –r "search_string" /dir/...` – рекурсивно ищет вхождения строки в файлах.
11. `su – имя_пользователя` – переключение на другого пользователя в Linux.
12. `./myscript` or `sh script` – позволяет запускать скрипты, не забывая дать права на исполнение.


## Регулярные выражения (метасимволы)

1. `^` – начало строки 
2. `$` – конец строки 
3. `[]` – любой символ, заключенный в квадратные скобки; чтобы задать диапазон символов, в квадратных скобках указываются через дефис первый и последний символы диапазона 
4. `[^]` – любой символ, кроме символов, заданных в квадратных скобках 
5. `.` – любой отдельный символ 
6. `\` – отменяет специальное значение следующего за ним метасимвола 
7. `*` – указывает, что предыдущий шаблон встречается 0 или более раз 
8. `\{n\}` – указывает, что предыдущий шаблон встречается ровно n раз 
9. `\{n,\}` – указывает, что предыдущий шаблон встречается не менее n раз
10. `\{,n\}` – указывает, что предыдущий шаблон встречается не более n раз 
11. `\{n,m\}` – указывает, что предыдущий шаблон встречается не менее n и не более m раз

Примеры:
1. `^the` – ищутся строки, начинающиеся с буквосочетания "the" 
2. `be$` – ищутся строки, заканчивающиеся буквосочетанием "be" 
3. `[Ss]igna[lL]` – ищутся строки, содержащие буквосочетания: "signal", "Signal", "signaL" или "SignaL" 
4. `\.` – ищутся строки, содержащие точку 
5. `^...th` – ищутся строки, содержащие символы "th" в 4-й и 5-й позициях 
6. `^.*\{53\}th` – ищутся строки, содержащие символы "th" в 54-й и 55-й позициях 
7. `^.*\{10,30\}th` – ищутся строки, содержащие символы "th" в любых позициях между 11-й и 31-й 
8. `^.....$` – ищутся строки, состоящие из 5 любых символов 
9. `^t.*e$` – ищутся строки, начинающиеся с буквы "t" и заканчивающиеся буквой "e" 
10. `[0-9][a-z]` – ищутся строки, содержащие комбинацию: цифра-прописная буква 
11. `[^123]` – ищутся строки, не содержащие цифр "1" или "2" или "3"


## Команды Nano

1. Delete the word before the current position of the cursor
	Switch on marking – `Ctrl+6`
	Move forward one word – `Ctrl+Space`
	Cut (delete) the selection – `Ctrl+K`

2. Delete the word after the current position of the cursor
	Switch on marking – `Ctrl+6`
	Move backward one word – `Alt+Space`
	Cut (delete) the selection – `Ctrl+K`

3. Delete from the current cursor position to the beginning of the line
	Switch on marking – `Ctrl+6`
	Move to beginning of current line – `Ctrl+A`
	Cut (delete) the selection – `Ctrl+K`

4. Delete the word after the current position of the cursor
	`ctrl + Delete`

5. Delete the word before the current position of the cursor
	`Alt + Backspace`


## Set user–wide environment variables:

These are the variables that have been defined for a specific user and are executed whenever that user logs in via a local or remote login session. They are set in and loaded from the following configuration files in the user's home directory: bashrc, .bash profile, .bash login, and .profile.

Using the .bashrc file:
1. `sudo vi .bashrc`
2. `export NEW_VAR ="Linux"`
3. `source ~/.bashrc` – save your file and reload the .bashrc file.
4. `echo $NEW_VAR` – print out the new variable.

Using .bash_p﻿rofile:
1. `sudo vi .bash_profile`
2. `export $VAR1 ="Linux"` – modify the .bash_profile file.
3. `source ~/.bash_profile` – reload the .bashrc file with the following source command for changes to take effect.
4. `echo $VAR1` – print out the new variable.


## Set system–wide environment variables:

These are system–wide environment variables, meaning they are available to all users on the system. These variables can be found in the following directories and files that include system–wide configuration files: /etc/environment, /etc/profile, /etc/profile.d/, /etc/bash.bashrc, /etc/profile.d/, /etc/profile.d/, /etc/profile.d/, /etc/profile.d/, /etc/profile.

Using /etc/bash.bashrc file:
1. `export VAR1='Linux'` – add a system–wide environment variable to the file. It will be available to the users when any of them starts a new terminal but cannot be accessed remotely.
2. `source /etc/bash.bashrc` – reload the file for changes to take effect. The variable can be accessed by both the normal user and root.

Using /etc/profile file:
1. `sudo vi /etc/profile`  
2. `export VAR='Linux'` – environment variable will be available when any of the users on your system is accessing it remotely.
3. `source /etc/profile`  
4. `echo $VAR`

Using /etc/environment file:
1. `sudo vi /etc/environment`
2. `export MY_VAR='Linux'` – environment variable will be available to all users on both local and remote login sessions.
3. `source /etc/environment`
4. `echo $MY_VAR`


## Unset Environment Variables

`unset <variable>` – to unset an environment variable.
`unset NEW_VAR` –  unset any of the above variables.
Environment variables defined in the system–wide or user–wide configuration files can be erased solely by removing them from these files. After that, reload the file with the source command for changes to take effect: `source <file–name>`.


## How to decide where to set environment variables?

– `export` **command in the terminal**: Choose when you need to set environment variables temporarily for the current shell session, mainly for testing or debugging.
– `~/.bashrc`, `~/.bash_profile`, or `~/.profile`: Choose when you need to set user–specific environment variables that should persist across sessions and apply to login and non–login shell sessions.
– `/etc/bash.bashrc`: Choose when you need to set system–wide environment variables for all users of the Bash shell in interactive non–login shell sessions.
– `/etc/profile` or `/etc/profile.d/`: Choose when you need to set system–wide environment variables for all users during login shell sessions, keeping configurations organized using custom scripts.
– `env` **command in the terminal**: Choose when you need to set environment variables temporarily for a specific command execution without affecting the current shell session or other processes.
– `/etc/environment`: Choose when you need to set system–wide environment variables that persist across sessions and reboots, affecting all users and processes on the system.


## Directory Hierarchy

1. `/` – root directory, the top level of the file system.
2. `/home` – user home directories.
3. `/bin` – essential binary executables.
4. `/sbin` – system administration binaries.
5. `/etc` – configuration files.
6. `/var` – variable data (logs, spool files).
7. `/usr` – user programs and data.
8. `/lib` – shared libraries.
9. `/tmp` – temporary files.


## Команды Linux для управления файлами

1. `ls` – отображает список файлов и каталогов в текущей директории.
2. `cd` – изменяет текущую директорию.
	`.` – current directory
	`..` – parent directory
	`~` – home directory
	`–` – previous directory
3. `pwd` – выводит полный путь текущей директории.
4. `mkdir` – создает новый каталог.
	`mkdir /{dr, sm}` or `mkdir dir{00..42}` – create several specific directories at once.
	`mkdir –p path/to/directory` – create a directory and all necessary parent directories.
5. `rmdir` or `rm –r [directory]` – удаляет каталог.
6. `rm` – удаляет файлы или каталоги.
	`rm -f file1` – force (насильно) прикажет rm удалить все файлы не зависимо от того, защищены они от записи или нет, без уведомления пользователя (до тех пор, пока у вас есть соответствующие права).
	`rm -i file` – будет выдавать запросы на удаление файлов или директорий.
7. `cp` – копирует файлы и каталоги.
	`Wildcard` - символ, который может быть заменен на выбранный шаблон.
		`*` wildcard всех wildcard'ов, используется для обозначения любых символов или строк.
		`?` используется для обозначения одного символа.
		`[]` используется для обозначения любого символа в скобках.
	`cp –r from/* to/end` – copies the contents of the directory.
	`cp *.jpg /home/pete/Pictures`  – скопирует все файлы с расширением .jpg в текущей директории в каталог Pictures.
	`cp -i mycoolfile /home/pete/Pictures` – (interactive/интерактивно), чтобы получить запрос на перезапись файла.
8. `mv` – перемещает или переименовывает файлы и каталоги.
	`mv –v from/* to/` – move the entire contents `from` `to` leaving the `from` folder empty
	`mv -i directory1 directory2` – для получения запроса на перезапись.
	`mv -b directory1 directory2` – сделать резервную копию (backup) этого файла и переименовать его старую версию с помощю -b.
1. `touch` – создает новый файл или обновляет время доступа и модификации существующего файла.
	`touch dir{00..42}/text{00..42}.txt` – create several specific files at N directories
10. `cat` – выводит содержимое файла.
11. `pr` – команда для разбивки файлов на страницы или столбцы для печати, использующая в unix-системах.
12. `paste` – used for merging lines from multiple files.
13. `less` – позволяет просматривать содержимое файла постранично.
14. `head` – выводит первые строки файла.
15. `sort` – used to sort the contents of a text file, line by line.
16. `tr` – a command-line utility that translates or substitutes characters.
17. `tail` – выводит последние строки файла.
18. `join` –  combine lines of two files on a common field, which works similar to the ‘Join’ operation in SQL.
19. `split` – divides a file into multiple equal parts, based on the lines or bytes specified by the user.
20. `grep` – ищет заданный текст в файлах или выводе команд.
21. `find` or `fd` – находит файлы и каталоги на основе различных критериев.
	`find /home -name puppies.jpg` – найти файл.
	`find /home -type d -name MyFolder` – указав тип файла, который ищется как директорию (d) и имя MyFolder.
22. `chmod` – изменяет права доступа к файлам и каталогам.
	Числовая нотация `chmod 644 myfile`: `4` чтение для владельца;	`2` запись для владельца;	`1` выполнение для владельца;  `7` чтение, запись, выполнение.
	Символьная нотация `chmod [ugoa][+–=][rwx] file`: `u` владелец файла; `g` группа файла; `o` остальные пользователи (не владелец и не входящие в группу); `a` все (при использовании заменяет собой ugo); `+` добавить разрешение; `–` удалить разрешение; `=` установить разрешение точно (заменить текущие разрешения); `r` разрешение на чтение; `w` разрешение на запись; `x` разрешение на выполнение.
17. `chown` – изменяет владельца файлов и каталогов.
18. `chgrp` – изменяет группу файлов и каталогов.
19. `tar` – создает или распаковывает архивы.
20. `gzip` — create gzip archive.
21. `gunzip` — unzip gzip archive
22. `zip` – создает ZIP–архивы.
23. `unzip` – извлекает файлы из ZIP–архивов.
24. `file` – покажет описание содержимого файла.


## Команды Linux для управления пользователями

1. `adduser` – создает нового пользователя.
2. `usermod` – изменяет параметры существующего пользователя.
3. `deluser` – удаляет пользователя.
4. `passwd` – изменяет пароль пользователя.
5. `su` – переключается на другого пользователя или становится суперпользователем.
6. `sudo` – выполняет команду с привилегиями суперпользователя.
7. `finger` – отображает информацию о пользователе.
8. `who` – отображает информацию о вошедших пользователях.
9. `id` – отображает информацию о текущем пользователе или указанном пользователе.
10. `groups` – отображает группы, к которым принадлежит пользователь.
11. `useradd` – создает нового пользователя (альтернатива для `adduser`).
12. `userdel` – удаляет пользователя (альтернатива для `deluser`).
13. `usermod` – изменяет параметры существующего пользователя (альтернатива для usermod).
14. `passwd` – изменяет пароль пользователя (альтернатива для passwd).
15. `last` – отображает историю входа пользователей.
16. `w` – отображает текущих пользователей и их активность.
17. `logout` – выходит из текущей сессии пользователя.
18. `lslogins` – выводит полный список пользователей ОС (а также информацию о них).
19. `whoami` – какой пользователь сейчас используется.
20. `visudo` – для добавления суперпользователей.


## Команды Linux для управления приложениями

1. `apt–get install` – устанавливает новое приложение или пакет.
2. `apt–get remove` – удаляет установленное приложение или пакет.
3. `apt–get update` – обновляет список доступных обновлений пакетов.
4. `apt–get upgrade` – обновляет установленные пакеты до последних версий.
5. `apt–cache search` – ищет пакеты по ключевому слову.
6. `dpkg –i` – устанавливает .deb пакет.
7. `dpkg –r` – удаляет .deb пакет.
8. `dpkg –l` – отображает список установленных пакетов.
9. `snap install` – устанавливает приложение из snap–пакета.
10. `snap remove` – удаляет установленное snap–приложение.
11. `snap list` – отображает список установленных snap–приложений.
12. `systemctl start` – запускает системную службу.
13. `systemctl stop` – останавливает системную службу.
14. `systemctl restart` – перезапускает системную службу.
15. `systemctl enable` – включает автозапуск системной службы при загрузке системы.
16. `systemctl disable` – отключает автозапуск системной службы при загрузке системы.
17. `systemctl suspend` – contents of memory are moved to the swap location; the boot loader is configured to boot directly to the current kernel; the system shuts down (no–power mode); upon power up, the system reloads itself from swap.
18. `systemctl hibernate` – applications are stopped; system state is moved to RAM. the system remains powered on in a low–power state.
19. `service <service> start` – запускает службу.
20. `service <service> stop` – останавливает службу.
21. `service <service> restart` – перезапускает службу.
22. `service <service> status` – отображает статус службы.
23. `whatis` – дает краткое описание любой установленной программы.
24. `whereis` – полный путь к программе.


## Команды Linux для управления системой

1. `shutdown –command time "message"` – позволяет выключить или перезагрузить систему. Например, `shutdown –h now` выключает систему немедленно.
2. `reboot` – перезагружает систему. Просто запустите `reboot` в терминале.
3. `halt` – выключает систему. Просто запустите `halt` в терминале.
4. `poweroff` – выключает систему. Просто запустите `poweroff` в терминале.
5. `systemctl` – команда для управления системными сервисами. Например, `systemctl start apache2` запускает службу Apache.
6. `service` – альтернативный способ управления системными службами. Например, `service nginx restart` перезапускает службу Nginx.
7. `ifconfig` – отображает и настраивает сетевые интерфейсы системы, включая IP–адреса, маски и шлюзы.
8. `ip` – альтернативный способ управления сетевыми интерфейсами и конфигурацией сети.
9. `netstat` – отображает сетевые соединения, открытые порты и другую связанную информацию.
10. `ping` – отправляет ICMP–пакеты на указанный IP–адрес для проверки доступности хоста в сети.
11. `traceroute` – отображает путь, по которому проходят пакеты до указанного IP–адреса в сети.
12. `ssh` – устанавливает безопасное соединение с удаленным сервером по протоколу SSH.
13. `scp` – копирует файлы между удаленным и локальным серверами по протоколу SSH.
14. `rsync` – выполняет синхронизацию и копирование файлов между удаленными и локальными серверами.
15. `crontab` – позволяет управлять cron–задачами, которые выполняются автоматически по заданному расписанию.
16. `at` – позволяет запускать команды или скрипты в определенное время в будущем.
17. `shutdown` – планирует выключение или перезагрузку системы по расписанию.
18. `nohup` – запускает команду с игнорированием сигналов завершения процесса. Это полезно для выполнения задач в фоновом режиме.
19. `history` – отображает историю команд, введенных пользователем в терминале (`ctrl + R` команда обратного поиска).
20. `cat /etc/*–release` – какой дистрибутив установлен на моей машине.
21. `env` – list all environment variables.
22. `echo $PATH` – print a particular variable like `PATH`.
23. `source` – execute commands from a file in the current shell.
24. `export` – allows you to update and propagate the values of environment variables to the current session and any spawned child processes, ensuring that changes are immediately effective.	
	`export –p` – to view all exported variables on current shell
	`export AB=/usr/dog/contagious/ringbearer/grind` or `export PATH=$PATH:/opt/local/bin` – temporary environment


## Команды Linux для управления процессами

1. `top` – отображает список процессов и их характеристики, такие как использование CPU и памяти.
2. `ps` – выводит список текущих запущенных процессов с их идентификаторами (PID).
3. `kill` – отправляет сигнал процессу для его завершения. Например, `kill PID` завершит процесс с указанным идентификатором.
4. `pkill` – отправляет сигнал процессам по их имени или другим атрибутам. Например, `pkill firefox` завершит все процессы Firefox.
5. `htop` – интерактивное утилита мониторинга процессов, которая позволяет видеть дополнительную информацию и управлять процессами.
6. `free` – отображает общую, использованную и свободную память системы, включая физическую и подкачку.
7. `vmstat` – предоставляет информацию о использовании памяти, процессоре, вводе–выводе, планировании и других системных ресурсах.
8. `killall` – завершает все процессы с указанным именем. Например, `killall firefox` завершит все процессы Firefox.
9. `renice` – изменяет приоритет процесса в реальном времени. Например, `renice –n –5 –p PID` увеличит приоритет процесса с указанным идентификатором.
10. `nice` – запускает процесс с более низким приоритетом. Например, `nice –n 10 command` запустит команду с очень низким приоритетом.
11. `pgrep` – выводит идентификаторы процессов, соответствующие указанной строке. Например, `pgrep firefox` выведет идентификаторы процессов Firefox.
12. `strace` – отслеживает системные вызовы и сигналы, связываемые с процессом. Можно использовать для отладки или анализа процессов.
13. `lsof` – выводит открытые файлы и сетевые соединения для всех процессов на системе.
14. `sar` – собирает информацию о использовании ресурсов системы, таких как процессор, память, сеть и диски, и сохраняет ее для последующего анализа.
15. `uptime` – выводит информацию о времени работы системы, средней загрузке и количестве активных пользователей.
16. `time` – запускает команду и отображает время, затраченное на ее выполнение, включая CPU–время и время ввода–вывода.


## Команды Linux для управления памятью

1. `smem` – отображает детальную информацию об использовании памяти процессами, группами процессов и системой в целом.
2. `sync` – записывает все буферы операционной системы на диск, чтобы обеспечить сохранность данных перед завершением работы.
3. `swapoff` – отключает файл подкачки, что позволяет освободить диск, но может увеличить использование оперативной памяти.
4. `swapon` – включает файл подкачки, добавляя дополнительную виртуальную память для использования системой.
5. `sysctl` – позволяет просматривать и изменять настройки ядра, включая параметры, связанные с памятью.
6. `ulimit` – устанавливает ограничения на использование ресурсов, включая память, для отдельного пользователя или процесса.
7. `pmap` – выводит карту памяти процесса, позволяя увидеть как процесс использует физическую и виртуальную память.
8. `slabtop` – отображает информацию о кэшах ядра, которые используют физическую память системы.
9. `ulimit` – устанавливает ограничения на использование ресурсов, включая память, для отдельного пользователя или процесса.
10. `numactl` – управляет доступом процессов к памяти и процессорам, особенно в многоядерных системах.
11. `sysrq` – позволяет отправлять системным вызовом определенные команды ядру Linux, в том числе сброс памяти (Memory Management).
12. `mdb` – интерактивный отладчик для системы Solaris, который может использоваться для анализа памяти.
