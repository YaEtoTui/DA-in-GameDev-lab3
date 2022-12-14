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
    trainer_type: ppo # Выбираем тип обучения с поощрением
    hyperparameters: # Перечисляем его гиперпараметры
      batch_size: 10 # Количество опытов на каждой итерации градиентного спуска
      buffer_size: 100 # Количество опыта
      learning_rate: 3.0e-4 # Начальная скорость обучения объекта
      beta: 5.0e-4 # Его бета
      epsilon: 0.2 # Эпсилон
      lambd: 0.99 # Лямбда
      num_epoch: 3 # Количество проходов, которые необходимо выполнить через буфер опыта при выполнении оптимизации градиентного спуска
      learning_rate_schedule: linear # Определяет, как скорость обучения меняется с течением времени
    network_settings: # здесь создаем сетевые настройки
      normalize: false # Применяется ли нормализация к входным данным векторного наблюдения
      hidden_units: 128 # Количество единиц в скрытых слоях нейронной сети
      num_layers: 2 # Количество скрытых слоев в нейронной сети
    reward_signals: # Создаем сигналы вознаграждения
      extrinsic: # его внешние свойства
        gamma: 0.99 # гамма, Коэффициент дисконтирования для будущих вознаграждений, поступающих от окружающей среды
        strength: 1.0 # сила
    max_steps: 500000 # макс количество допустимых шагов
    time_horizon: 64 # временный горизонт(границы)
    summary_freq: 10000 # Суммарная частота

```

Decision Requester:

запрос на принятие решения вызывает CollectObservation, а затем получает последнее действие в OnActionReceived, основанное на этом новом собранном наблюдении. С действиями из TakeActionBetweenDecisions он только снова вызовет OnActionReceived без сбора новых наблюдений и выведет последнее действие, которое он получил от NN.

Behavior Parameters:

Параметры поведения — У каждого Агента должно быть определенное поведение. Поведение определяет, как Агент принимает решения. Максимальный шаг — Определяет, сколько шагов моделирования может произойти до окончания эпизода Агента.


## Задание 3
### Доработайте сцену и обучите ML-Agent таким образом, чтобы шар перемещался между двумя кубами разного цвета. Кубы должны, как и в первом задании, случайно изменяют координаты на плоскости.

Доработал сцену и обучил ML-Agent таким образом, чтобы шар перемещался между двумя кубами разного цвета. 

```py

using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using Unity.MLAgents;
using Unity.MLAgents.Sensors;
using Unity.MLAgents.Actuators;

public class RollerAgent : Agent
{
    Rigidbody rBody;
    // Start is called before the first frame update
    void Start()
    {
        
        rBody = GetComponent<Rigidbody>();
    }

    public Transform Target1;
    public Transform Target2;
    private float speedMove;
    private bool isTrue = true;
    public override void OnEpisodeBegin()
    {
        if (this.transform.localPosition.y < 0)
        {
            this.rBody.angularVelocity = Vector3.zero;
            this.rBody.velocity = Vector3.zero;
            this.transform.localPosition = new Vector3(0, 0.5f, 0);
        }
        Target1.localPosition = new Vector3(Random.value * 8-4, 0.5f, Random.value * 8-4);
        Target2.localPosition = new Vector3(Random.value * 8-4, 0.5f, Random.value * 8-4);   
    }
    public override void CollectObservations(VectorSensor sensor)
    {       
        sensor.AddObservation(Target1.localPosition);
        sensor.AddObservation(this.transform.localPosition);
        sensor.AddObservation(rBody.velocity.x);
        sensor.AddObservation(rBody.velocity.z);
    }
    public float forceMultiplier = 10;
    public override void OnActionReceived(ActionBuffers actionBuffers)
    {
        speedMove = Mathf.Clamp(actionBuffers.ContinuousActions[0], 1f, 10f);
        Vector3 controlSignal = Vector3.zero;
        controlSignal.x = actionBuffers.ContinuousActions[0];
        controlSignal.z = actionBuffers.ContinuousActions[1];
        rBody.AddForce(controlSignal * forceMultiplier);
        if (transform.position != Target1.transform.position & isTrue == true)
        {
            transform.position = Vector3.MoveTowards(transform.position, Target1.transform.position, Time.deltaTime * speedMove);
        }

        if (transform.position == Target1.transform.position & isTrue == true)
        {
            isTrue = false;
        }

        if (transform.position != Target2.transform.position & isTrue == false)
        {
            transform.position = Vector3.MoveTowards(transform.position, Target2.transform.position, Time.deltaTime * speedMove);
        }

        if (transform.position == Target2.transform.position & isTrue == false)
        {
            isTrue = true;
        }

        if (this.transform.localPosition.y < 0)
        {
            EndEpisode();
        }
    }
}


```


![Снимок экрана (694)](https://user-images.githubusercontent.com/102538132/197058922-0cff9982-b5d3-47a5-a918-b4223e765ef5.png)


## Выводы
Игровой баланс - в играх равновесие между персонажами, командами, тактиками игры. Баланс важен для многопользовательских игр. Чем в игре лучше проработан баланс, тем больше игра становится понятной и интересной. Есть 2 парадигмы баланса: 1. метод от образа, создание характеристик от уже нарисованного персонажа по внешнему виду; 2. от характеристик.
Машинное обучение позволяет более точно распределять игровые механики, которые балансируют игру. Например, чтоб бот выполнял более точно свои задачи, для этого машинное обучение и нужно. Оно увеличивает шансы, чтобы бот не сломался.


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
