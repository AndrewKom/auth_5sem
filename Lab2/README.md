## Цель работы

1.  Развить практические навыки использования современного стека инструментов сбора и аналитической обработки информации о сетевом трафике
2.  Освоить базовые подходы блокировки нежелательного сетевого трафика
3.  Закрепить знания о современных сетевых протоколах прикладного уровня

## Исходные данные

1.  WLS(Ubuntu 22.04.2)
2.  Zeek
3.  Wireshark
4.  Windows 10
5.  RStudio
6.  PyCharm

## План

1.  Собрать сетевой трафик
2.  Выделить метаинформацию сетевого трафика с помощью утилиты Zeek
3.  Собрать данные об источниках нежелательного трафика
4.  Написать программу, которая подсчитает процент нежелательного трафика
5.  Оформить отчет

## Описание шагов:

1.  Воспользуемся программой Wireshark для сбора трафика (заходим на различные ресурсы, чтобы получить большую выборку), также не забываем отключить блокираторы рекламы. Получаем файл: traf.pcap (152 МБ)\
![alt text](https://github.com/AndrewKom/auth_5sem/blob/main/lab2/traficPic-01.png)
2.  Устанавливаем WLS(Ubuntu) для работы с Zeek через Windows. Передаем файл и получаем метаинформацию сетевого трафика:

/opt/zeek/bin/zeek -r /mnt/c/traf.pcap

![alt text](https://github.com/AndrewKom/auth_5sem/blob/main/lab2/dsnzeek.png)

3.  Соединяем в единый файл списки нежелательного трафика с репрозитория: [StevenBlack (Steven Black) · GitHub](https://github.com/StevenBlack) \
    Полученный файл: Vrednie.txt\
![alt text](https://github.com/AndrewKom/auth_5sem/blob/main/lab2/vred.png)

4.  На языке python пишем программу, которая подсчитывает процент нежелательного трафика.\
    Преобразовываем файл dns из Zeek в датафрейм\
    Аналогично поступаем с файлом полученным с онлайн репрозитория\
    Анализируем полученные датафреймы и получаем процент нежелательного трафика: 5,149

``` python
import warnings
warnings.filterwarnings("ignore", category=RuntimeWarning)
import numpy as np
import pandas as pd
import zat.log_to_dataframe
df = zat.log_to_dataframe.LogToDataFrame()
zdf = df.create_dataframe('dns.log')
domain = zdf['query']
domain.name='CNAME'
df = pd.read_csv('Vrednie.txt',sep="\s+",names=['redirect_to','CNAME'])
vred = df['CNAME']

mer = pd.merge(domain,vred, how='left',indicator='exists', on=['CNAME'],)
mer['exists'] = np.where(mer.exists == 'both',True,False)

final = mer['exists'].value_counts(normalize=True)[1]*100

print("Процент вредного трафика: ", round(final,3))
```

![alt text](https://github.com/AndrewKom/auth_5sem/blob/main/lab2/py1.png)

5.  Оформляем отчет в программе RStudio

## Оценка результатов

Задача решена с помощью языка Python и утилиты Zeek на WLS. Я получил практические навыки использования современного стека инструментов сбора и аналитической обработки информации о сетевом трафике.

## Вывод

В данной работе я собрал трафик, поработал с утилитой Zeek и написал программу, которая вычислила процент нежелательного трафика. Таким образом, я освол базовые подходы блокировки нежелательного сетевого трафика и закрепил знания о современных сетевых протоколах прикладного уровня.
