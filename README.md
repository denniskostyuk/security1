# Домашнее задание к занятию «Уязвимости и атаки на информационные системы» - `Костюк Денис`

# Задание 1
Скачайте и установите виртуальную машину Metasploitable: https://sourceforge.net/projects/metasploitable/.  
Это типовая ОС для экспериментов в области информационной безопасности, с которой следует начать при анализе уязвимостей.  
Просканируйте эту виртуальную машину, используя nmap.  
Попробуйте найти уязвимости, которым подвержена эта виртуальная машина.  
Сами уязвимости можно поискать на сайте https://www.exploit-db.com/.  
Для этого нужно в поиске ввести название сетевой службы, обнаруженной на атакуемой машине, и выбрать подходящие по версии уязвимости.  
Ответьте на следующие вопросы:  
- Какие сетевые службы в ней разрешены?  
- Какие уязвимости были вами обнаружены? (список со ссылками: достаточно трёх уязвимостей)  
Приведите ответ в свободной форме.  

## Ответ 1

- Запущены службы: ftp, ssh, telnet, smtp, domain, http, rpcbind, netbios-ssn, microsoft-ds, exec, login, shell, rmiregistry, ingreslock, nfs, ccproxy-ftp, mysql, postgresql, vnc, X11, irc, ajp13:
![image](https://github.com/denniskostyuk/security1/blob/main/task-11.png)

- по результатам сканирования на определение версий ПО были найдены уязвимости:
https://www.exploit-db.com/exploits/30604
https://www.exploit-db.com/exploits/17491
https://www.exploit-db.com/exploits/30020
![image](https://github.com/denniskostyuk/security1/blob/main/task-12.png)


#### Требования к результату 

Прикрепите в файл README.md скриншот страницы шаблона с названием «Задание 1»

Шаблон Zadanie 1:
   ![Скрин1](https://github.com/denniskostyuk/zabbix-2/blob/main/task-1_template.png)

А также итемы для шаблона Zadanie 1:
   ![Скрин2](https://github.com/denniskostyuk/zabbix-2/blob/main/task-1_item1.png)
   ![Скрин3](https://github.com/denniskostyuk/zabbix-2/blob/main/task-1_item2.png)
