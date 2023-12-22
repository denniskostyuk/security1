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

# Задание 2
Проведите сканирование Metasploitable в режимах SYN, FIN, Xmas, UDP.  
Запишите сеансы сканирования в Wireshark.  
Ответьте на следующие вопросы:  
- Чем отличаются эти режимы сканирования с точки зрения сетевого трафика?  
- Как отвечает сервер?  
Приведите ответ в свободной форме.  

## Ответ 2

На входе:
ip-адрес Metasploitable = 192.168.0.137  
ip-адрес хоста с NMAP = 192.168.0.182  

#### Режим SYN (-sS).
Nmap отправляет пакет с установленным флагом SYN.  

Если порт закрыт (например, порт 1322), то Metasploitable "сбрасывает" попытку соединения (отправляет RST-пакет):  
![image](https://github.com/denniskostyuk/security1/blob/main/task-21.png)  

Если порт открыт (например, порт 22), то Metasploitable отвечает готовностью установить соединение (SYN-ASK), после чего NMAP "сбрасывает" попытку соединения:  
![image](https://github.com/denniskostyuk/security1/blob/main/task-22.png)

#### Режим FIN (-sF)  
NMAP отправляет пакет с установленным флагом FIN, который используется для корректного закрытия соединения. Следовательно, цель должна ответить RST для закрытых портов, в соответствии с RFC.

Закрытые порты (например, порт 1322):  
![image](https://github.com/denniskostyuk/security1/blob/main/task-23.png)

Открытые порты (например, порт 22):  
![image](https://github.com/denniskostyuk/security1/blob/main/task-24.png)

#### Режим Xmas (-sX)
Сканирование TCP Xmas похоже на предыдущий метод, отличается тем, что использует TCP-пакеты с установленными флагами PSH, URG и FIN.  
Как и в режиме сканирования FIN, этот тип также ожидает пакеты RST для закрытых портов в соответствии с RFC.

Закрытые порты (например, порт 1322):  
![image](https://github.com/denniskostyuk/security1/blob/main/task-25.png)

Открытые порты (например, порт 22):  
![image](https://github.com/denniskostyuk/security1/blob/main/task-26.png)
