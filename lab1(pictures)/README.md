---
title: "lab1"
format: html
editor: visual
---

## Цель работы

Получить сведения о системе

## Исходные данные

1\. Программное обеспечение astralinux

2\. Rstudio

## План

1.  Получить сведения версию ядра
2.  Получить полные сведения о ядре
3.  Используемый дистрибутив
4.  Получить модель процессора
5.  Скрытые файлы

## Шаги:

1.  Получаем версию ядра при помощи команды uname -r

```{bash}
uname -r
```

![alt text](https://github.com/AndrewKom/auth_5sem/blob/main/lab1(pictures)/Work1.png)

2.  Получаем полные сведения о ядре при помощи команды uname -a

```{bash}
uname -a
```

![alt text](https://github.com/AndrewKom/auth_5sem/blob/main/lab1(pictures)/work2.png)

3.  Используей дистрибутив получаем при помощи команды lsb_release -a

```{bash}
lsb_release -a
```

![alt text](https://github.com/AndrewKom/auth_5sem/blob/main/lab1(pictures)/work3.png)

4.  Полную информацию получаем при помощи команды cat /proc/cpuinfo

```{bash}
cat /proc/cpuinfo 
```

![alt text](https://github.com/AndrewKom/auth_5sem/blob/main/lab1(pictures)/work4.png)

![alt text](https://github.com/AndrewKom/auth_5sem/blob/main/lab1(pictures)/work4.1.png)

5.  Модель процессора получаем при помощи команды cat /proc/cpuinfo \| grep "model name"

```{bash}
cat /proc/cpuinfo | grep "model name"
```

![alt text](https://github.com/AndrewKom/auth_5sem/blob/main/lab1(pictures)/work5.png)

6.  Все скрытые файлы смотрим при помощи команды ls -a

```{bash}
ls -a
```

![alt text](https://github.com/AndrewKom/auth_5sem/blob/main/lab1(pictures)/work6.png)

## Оценка результата
В результате лабораторной работы мы получили основную информацию об системе

## Вывод
Таким образом, я научился работать с базовыми командами Linux для получения сведений об операционной системе
