# Урок 1. Механизмы пространства имен
Задание: необходимо продемонстрировать изоляцию одного и того же приложения (как решено на семинаре - командного интерпретатора) в различных пространствах имен.

Для запуска Bash в новом пространстве имен воспользуемся командой (так как команда требует привилегии суперпользователя, то выполняем через sudo):

sudo unshare -pf -n --mount-proc bash

Посмотрим получилось ли у нас изолировать и какие процессы запущенны:

ps -afx

https://github.com/SokolikAA/container1/blob/4a39255d74558fae39c8d6cd5ec7d48083a53e5e/Screen1.JPG



