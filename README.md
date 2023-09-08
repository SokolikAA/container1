# Урок 1. Механизмы пространства имен
Задание: необходимо продемонстрировать изоляцию одного и того же приложения (как решено на семинаре - командного интерпретатора) в различных пространствах имен.

Для запуска Bash в новом пространстве имен воспользуемся командой (так как команда требует привилегии суперпользователя, то выполняем через sudo):

sudo unshare -pf -n --mount-proc bash

Посмотрим получилось ли у нас изолировать и какие процессы запущенны:

ps -afx

Screen1.jpg

Изолированная оболчка видит всего два процесса (второй процесс сразу же исчезнет после выполнения команды). При этом PID процессов начинается с 1.
При этом основная система видит несколько родительских процессов и PID у нашего нового процесса 4357.
Далее, из изолированного терминала, пробуем запустить пинг любого сайта, например ya.ru.

ping ya.ru

Пинг до указанного сайта не проходит, так как сеть в этом пронстранстве имен имеется только локальная.
Вводим команду $ hostname, что бы увидеть наш хост:

hostname

В изолированном терминале выполняем команду:

sudo unshare -u bash

Команда $ unshare запускает программу в новом namespace. Флаг -u говорит ей запустить bash в новом UTS namespace.
Теперь можно изменить системный hostname из нашего нового процесса bash и это не повлияет ни на какой другой процесс в системе. 
Изменяем хост в изолированном терминале:

hostname homework1

Эта команда никак не затронула хост основной системы. 
Проверяем из основной системы:

