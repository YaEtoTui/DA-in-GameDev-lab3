# АНАЛИЗ ДАННЫХ И ИСКУССТВЕННЫЙ ИНТЕЛЛЕКТ [in GameDev]
Отчет по лабораторной работе #3 выполнил:
- Сажин Егор Алексеевич
- РИ210946
Отметка о выполнении заданий (заполняется студентом):

| Задание | Выполнение | Баллы |
| ------ | ------ | ------ |
| Задание 1 | * | 60 |
| Задание 2 | * | 20 |
| Задание 3 | * | 20 |

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
- Задание 2.
- Код реализации выполнения задания. Визуализация результатов выполнения (если применимо).
- Задание 3.
- Код реализации выполнения задания. Визуализация результатов выполнения (если применимо).
- Выводы.
- ✨Magic ✨

## Цель работы
Познакомиться с программными средствами для создания системы машинного обучения и ее интеграции в Unity.

## Задание 1
### Реализовать систему машинного обучения в связке Python - Google-Sheets – Unity. При выполнении задания можно использовать видео-материалы и исходные данные, предоставленные преподавателями курса.

Для 1 задания были сделаны все приготовления, указанные в видеоматериале. Запускаем сцену, проверив работу ML-Agent’a. 
Затем создаём 3, 9, 27 копии модели «Плоскость-Сфера-Куб» и запускаем симуляцию сцены. На следующих скринах можно увидеть реализацию машинного обучения:

Здесь обучаем 1 объект
![Снимок экрана (677)](https://user-images.githubusercontent.com/102538132/197032998-ce8d361c-3581-413f-b3e3-394c30039b9f.png)

3 объекта

![Снимок экрана (678)](https://user-images.githubusercontent.com/102538132/197033017-cf3d4548-579a-464f-812b-d020d9e250ad.png)
![Снимок экрана (679)](https://user-images.githubusercontent.com/102538132/197033029-ec285a26-51fe-4fb3-9d96-314c0d30eafd.png)

9 объектов

![Снимок экрана (680)](https://user-images.githubusercontent.com/102538132/197033039-eddd6635-53bd-4771-a60f-b3d3dfc29d0f.png)
![Снимок экрана (681)](https://user-images.githubusercontent.com/102538132/197033064-0dc29175-4a17-453a-bb08-93ed213ba89f.png)

27 объектов. На последнем скрине переменная Std of Reward не видно, ее значение = 0.252

![Снимок экрана (682)](https://user-images.githubusercontent.com/102538132/197033112-e6adfeaf-5df8-46a5-b780-73de16c7d5c3.png)
![Снимок экрана (683)](https://user-images.githubusercontent.com/102538132/197033132-af89474e-974d-4911-b7dc-400a3ca214e0.png)

После завершения обучения проверим работу модели: 


![Снимок экрана (684)](https://user-images.githubusercontent.com/102538132/197033324-2febd4de-26be-4189-8be8-f1b24b69eddd.png)
![Снимок экрана (685)](https://user-images.githubusercontent.com/102538132/197033338-e51aad29-af01-4894-843b-f40091a3c2ae.png)

Все результаты можно увидеть на скринах выше.

Вывод: С увеличением количества объектов количество шагов(step) увеличивается. Потраченное время(time elapsed) тоже увеличивается, но сравнивая 9 и 27 объектов, наоборот, уменьшается. Переменная Std of Reward уменьшается и Mean Reward увеличивается.


## Задание 2
### Подробно опишите каждую строку файла конфигурации нейронной сети, доступного в папке с файлами проекта по ссылке. Самостоятельно найдите информацию о компонентах Decision Requester, Behavior Parameters, добавленных на сфере.
 

```py

behaviors: # Первая строка behaviors отвечает за поведение объекта.
  RollerBall: # Дальше мы описываем объект RollerBall
    trainer_type: ppo # Выбираем тип тренера
    hyperparameters: # Перечисляем его гиперпараметры
      batch_size: 10 # Его размер партии
      buffer_size: 100 # Размер буффера
      learning_rate: 3.0e-4 # Скорость обучения объекта
      beta: 5.0e-4 # Его бета
      epsilon: 0.2 # Эпсилон
      lambd: 0.99 # Лямбда
      num_epoch: 3 # Номер эпохи
      learning_rate_schedule: linear # График скорости обучения: линейный
    network_settings:
      normalize: false
      hidden_units: 128
      num_layers: 2
    reward_signals:
      extrinsic:
        gamma: 0.99
        strength: 1.0
    max_steps: 500000
    time_horizon: 64
    summary_freq: 10000

```


## Задание 3
### Самостоятельно разработать сценарий воспроизведения звукового сопровождения в Unity в зависимости от изменения считанных данных в задании 2



## Выводы
Выполняя эту лабораторную работу, я впервые поработал с аудифайлами, научился работать с аудиоресурсом в Unity, связывать PyCharm с Google Sheets через Google Console и связывать Google Sheets с Unity: передавать набор данных из PyCharm в Google Sheets и брать набор данных из Google Sheets и использовать их в Unity .


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
