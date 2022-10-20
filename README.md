# АНАЛИЗ ДАННЫХ И ИСКУССТВЕННЫЙ ИНТЕЛЛЕКТ [in GameDev]
Отчет по лабораторной работе #2 выполнил:
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
Познакомиться с программными средствами для организции передачи данных между инструментами google, Python и Unity.

## Задание 1
### Реализовать совместную работу и передачу данных в связке Python - Google-Sheets – Unity. При выполнении задания используйте видео-материалы и исходные данные, предоставленные преподавателя курса.
Ход работы:

- В облачном сервисе google console подключить API для работы с google sheets и google drive.

![GoogleColab](https://user-images.githubusercontent.com/102538132/194267037-72fec0de-66c0-4c56-b2db-23a0e96bd80e.png)
![Доступ](https://user-images.githubusercontent.com/102538132/194271960-0817146b-68cb-42da-a807-f069a2bd8184.png)


- Реализовать запись данных из скрипта на python в google-таблицу. Данные описывают изменение темпа инфляции на протяжении 11 отсчётных периодов, с учётом стоимости игрового объекта в каждый период.

![Python(1)](https://user-images.githubusercontent.com/102538132/194272038-761f1e51-34c2-4e52-a2c6-f697523e9c02.png)
![Python(2)](https://user-images.githubusercontent.com/102538132/194272068-55e72924-ea31-4f58-bb99-96d4ef8f0739.png)
![GoogleSheets](https://user-images.githubusercontent.com/102538132/194272101-2836a799-6456-4d4d-9f18-e285592c6f07.png)


- Создать новый проект на Unity, который будет получать данные из google-таблицы, в которую были записаны данные в предыдущем пункте.

![Unity](https://user-images.githubusercontent.com/102538132/194272366-4a4583b1-97d4-4254-b3b5-1db0804e9708.png)


- Написать функционал на Unity, в котором будет воспризводиться аудио-файл в зависимости от значения данных из таблицы.

![script(1)](https://user-images.githubusercontent.com/102538132/194272482-9214ef36-7d42-446b-b8c5-ff6674ddbae5.png)
![script(2)](https://user-images.githubusercontent.com/102538132/194272500-1de1643c-f1f8-4f49-8a18-f574892703b7.png)
![script(3)](https://user-images.githubusercontent.com/102538132/194272525-5c3cd39c-ec47-413b-8e68-d878bb657fd9.png)


## Задание 2
### Реализовать запись в Google-таблицу набора данных, полученных с помощью линейной регрессии из лабораторной работы № 1

На следующих скриншотах представлен код линейной регрессии. Изменим так, чтобы мы могли увидеть набор данных на консоли
и могли передать их в Google Sheets(строки: 61-63, 69-88): 


![Python(1)](https://user-images.githubusercontent.com/102538132/194334176-5d5a3eeb-9981-4f53-97ae-4fb4a55c1e26.png)
![Python(2)](https://user-images.githubusercontent.com/102538132/194334187-7bf06994-ae0e-40ad-84f2-48865a699d56.png)
![Python(3)](https://user-images.githubusercontent.com/102538132/194334201-897ab3be-b7ae-410e-9244-c531d680a0d6.png)
![Python(4)](https://user-images.githubusercontent.com/102538132/194334212-e56d0e62-e552-49fa-9d52-8716d585615b.png)

Проверим работоспособность кода. Заметим, что первое значение - a, второе - b, третье - loss:


![Python_Run](https://user-images.githubusercontent.com/102538132/194334229-ce23c867-3adc-4cd3-96f4-c7c76469ba9e.png)

Можем увидеть значения, полученные с помощью линейной регрессии из лабораторной работы № 1 в Google Sheets на следующем скриншоте. Первый столбец - количество итераций, второй - переменная a, третий - переменная b, четвертый - переменная loss:


![GoogleSheets](https://user-images.githubusercontent.com/102538132/194334244-c1aabe5e-4544-4195-b11c-4d9b552725a1.png)


## Задание 3
### Самостоятельно разработать сценарий воспроизведения звукового сопровождения в Unity в зависимости от изменения считанных данных в задании 2

В качестве входных данных я взял переменную loss(столбец 4). И сделал свой сценарий воспроизведения звукового сопровождения в Unity.
Если loss <= 1025,37, то будет восроизводиться аудиофайл "Хорошо"; 1025.37 < loss < 1150.034 "Средне"; loss >= 1150.034 "Плохо":

![Script(1)](https://user-images.githubusercontent.com/102538132/194337565-241fd797-6417-410a-b159-791f57c452bc.png)
![Script(2)](https://user-images.githubusercontent.com/102538132/194337581-d4518658-80d2-4e21-b27e-652d0d03e4aa.png)
![Script(4)](https://user-images.githubusercontent.com/102538132/194340662-a12a1e78-2ed3-4056-a152-a60c93c39dfd.png)
![Script(3)](https://user-images.githubusercontent.com/102538132/194337589-869b5ae6-7788-45a7-b8ec-642d0f0a2f86.png)
![Unity_answer](https://user-images.githubusercontent.com/102538132/194337608-ae151fb8-e038-448a-aab1-ee9bebdfaa4d.png)


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
