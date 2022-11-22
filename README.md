# Python_GoogleSheets_Unity
# АНАЛИЗ ДАННЫХ И ИСКУССТВЕННЫЙ ИНТЕЛЛЕКТ [in GameDev]
Отчет по лабораторной работе #2 выполнил(а):
- Кокшаров Арсений Максимович
- РИ000024
Отметка о выполнении заданий (заполняется студентом):

| Задание | Выполнение | Баллы |
| ------ | ------ | ------ |
| Задание 1 | * | 60 |
| Задание 2 | # | 20 |
| Задание 3 | # | 20 |

знак "*" - задание выполнено; знак "#" - задание не выполнено;

Работу проверили:
- к.т.н., доцент Денисов Д.В.
- к.э.н., доцент Панов М.А.
- ст. преп., Фадеев В.О.

[![N|Solid](https://cldup.com/dTxpPi9lDf.thumb.png)](https://nodesource.com/products/nsolid)

[![Build Status](https://travis-ci.org/joemccann/dillinger.svg?branch=master)](https://travis-ci.org/joemccann/dillinger)

Структура отчета

- Данные о работе: название работы, фио, группа, выполненные задания.
- Цель работы.
- Задание 1.
- Код реализации выполнения задания. Визуализация результатов выполнения (если применимо).


## Цель работы
познакомиться с программными средствами для организции передачи данных между инструментами google, Python и Unity.


##Задание 1
Реализовать совместную работу и передачу данных в связке Python
- Google-Sheets – Unity. 
1.1 В облачном сервисе google console подключить API для работы с google
sheets и google drive.
![GoogleCloudAPI](https://github.com/Kokarse/Python_GoogleSheets_Unity/raw/main/Screenshots/GoogleCloudAPI.png)
- Реализовать запись данных из скрипта на python в google-таблицу. Данные
описывают изменение темпа инфляции на протяжении 11 отсчётных периодов, с
учётом стоимости игрового объекта в каждый период.

```py
import gspread
import numpy as np
gc = gspread.service_account(filename='unitydatasciense-369010-9b3bc7dcdac1.json')
sh = gc.open("UnitySheets")
price = np.random.randint(2000, 10000, 11)
mon = list(range(1,11))
i = 0
while i <= len(mon):
    i += 1
    if i == 0:
        continue
    else:
        tempInf = ((price[i-1]-price[i-2])/price[i-2])*100
        tempInf = str(tempInf)
        tempInf = tempInf.replace('.',',')
        sh.sheet1.update(('A' + str(i)), str(i))
        sh.sheet1.update(('B' + str(i)), str(price[i-1]))
        sh.sheet1.update(('C' + str(i)), str(tempInf))
        print(tempInf)
```
![PyCharm](https://github.com/Kokarse/Python_GoogleSheets_Unity/raw/main/Screenshots/PyCharm.png)
![GoogleSheets](https://github.com/Kokarse/Python_GoogleSheets_Unity/raw/main/Screenshots/GoogleSheets.png)
- Создать новый проект на Unity, который будет получать данные из google-
таблицы, в которую были записаны данные в предыдущем пункте.
- Написать функционал на Unity, в котором будет воспризводиться аудио-
файл в зависимости от значения данных из таблицы.
![Unity](https://github.com/Kokarse/Python_GoogleSheets_Unity/raw/main/Screenshots/Unity.png)



**BigDigital Team: Denisov | Fadeev | Panov**
