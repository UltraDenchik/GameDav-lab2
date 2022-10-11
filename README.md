# GameDav-lab2
# АНАЛИЗ ДАННЫХ И ИСКУССТВЕННЫЙ ИНТЕЛЛЕКТ [in GameDev]
Отчет по лабораторной работе #2 выполнил(а):
- Китушкин Данил Яковлевич
- РИ210910
Отметка о выполнении заданий (заполняется студентом):

| Задание | Выполнение | Баллы |
| ------ | ------ | ------ |
| Задание 1 | * | 60 |
| Задание 2 | * | 20 |
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
- Задание 1.
- Реализовать совместную работу и передачу данных в связке Python
- Google-Sheets – Unity. При выполнении задания используйте видео-материалы и исходные данные, предоставленные преподавателя курса.
- Задание 2.
- Реализовать запись в Google-таблицу набора данных, полученных с помощью линейной регрессии из лабораторной работы № 1
- Задание 3.
- Самостоятельно разработать сценарий воспроизведения звукового сопровождения в Unity в зависимости от изменения считанных данных в задании 2
- Выводы.
- ✨Magic ✨

## Цель работы
Познакомиться с программными средствами для организции передачи данных между инструментами google, Python и Unity

## Задание 1
### Реализовать совместную работу и передачу данных в связке Python
Из приложенного видео, мне удалось настроить среду Unity и Python для работы с GoogleSheets
Ниже перечислены скриншоты выполненной работы:

UnitySheets:

![UnitySheets](https://user-images.githubusercontent.com/95544542/195111448-8f6a531b-4d7b-4fc5-9ae0-25f80e4eafd8.PNG)

UnityDebug:

![UnityDebug](https://user-images.githubusercontent.com/95544542/195111467-6d9e5c4f-a919-47f8-9f12-c88fd73c2968.PNG)

GoogleCloud:

![GoogleCloud](https://user-images.githubusercontent.com/95544542/195111510-eb3781c0-eb97-488a-a3c8-2d8b2bb9d73a.PNG)
Python:

![Python](https://user-images.githubusercontent.com/95544542/195111756-41ce23fb-cf65-422a-a2f1-6f8d3cd00539.PNG)

## Задание 2
### Реализовать запись в Google-таблицу набора данных, полученных с помощью линейной регрессии из лабораторной работы № 1

Ниже приведены скриншоты выполнения и код:

```py

import gspread
import numpy as np


def loss_function(a, b, x, y):
    num = len(x)
    prediction = model(a, b, x)
    return (0.5 / num) * (np.square(prediction - y)).sum()

def model(a, b, x):
    return a * x + b

def optimize(a, b, x, y):
    num = len(x)
    prediction = model(a, b, x)
    # Update the values of A and B by finding the partial derivatives of the loss function on a and b
    da = (1.0 / num) * ((prediction - y) * x).sum()
    db = (1.0 / num) * ((prediction - y).sum())
    a = a - Lr * da
    b = b - Lr * db
    return a, b

def iterate(a,b,x,y,times):
    for i in range(times):
        a,b = optimize(a,b,x,y)
    return a,b

gc = gspread.service_account(filename="unitydatasciense-365210-db4c3d9412ba.json")
sh = gc.open('UnitySheets')
x = [3, 21, 22, 34, 54, 34, 55, 67, 89, 99]
x = np.array(x)
y = [2, 22, 24, 65, 79, 82, 55, 130, 150, 199]
y = np.array(y)
a = np.random.rand(1)
b = np.random.rand(1)
Lr = 0.0001
i = 0
while i <= len(x+1):
    i += 1
    if i == 0:
        continue
    else:
        iter = np.random.randint(1, 15)
        print(iter)
        a,b = iterate(a,b,x,y,iter)
        loss = loss_function(a, b, x, y)
        tempInf = loss
        tempInf = str(tempInf)
        tempInf = tempInf.replace('.', ',')
        sh.sheet1.update(('A' + str(i)), str(x[i-1]))
        sh.sheet1.update(('B' + str(i)), str(y[i-1]))
        sh.sheet1.update(('C' + str(i)), str(tempInf))
        print(tempInf)

```

Скришот:

![2](https://user-images.githubusercontent.com/95544542/195117604-75be2843-ed6d-46e1-a140-fcbe913f40c5.PNG)


## Выводы

С помощью данной лабораторной работы, я научился работать в Google таблице, а так же подключать ее к Python и Unity

| Plugin | README |
| ------ | ------ |
| Dropbox | [plugins/dropbox/README.md][PlDb] |
| GitHub | [plugins/github/README.md][PlGh] |
| Google Drive | [plugins/googledrive/README.md][PlGd] |
| OneDrive | [plugins/onedrive/README.md][PlOd] |
| Medium | [plugins/medium/README.md][PlMe] |
| Google Analytics | [plugins/googleanalytics/README.md][PlGa] |

## Powered by

**BigDigital Team: Denisov | Fadeev | Panov**
