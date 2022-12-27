Проект 5 Такси

Задание:
Необходимо, используя таблицу поездок для каждого дня рассчитать процент поездок по количеству человек в машине (без пассажиров, 1, 2,3,4 и более пассажиров). По итогу должна получиться таблица (parquet) с колонками date, percentage_zero, percentage_1p, percentage_2p, percentage_3p, percentage_4p_plus. Технологический стек – sql,scala (что-то одно).
Также добавить столбцы к предыдущим результатам с самой дорогой и самой дешевой поездкой для каждой группы.

Дополнительно: 
также провести аналитику и построить график на тему “как пройденное расстояние и количество пассажиров влияет на чаевые” в любом удобном инструменте.

Скрипт работает локально при следующих параметрах проекта:
scalaVersion - "2.11.8"
sbt.version - "0.13.18"
temurin-1.8
spark-core - "2.3.2"
spark-sql - "2.3.2"
1) Скрипт расположен по умолчанию: TaxiTrip\src\main\scala\Main.scala
2) Файл с данными yellow_tripdata_2020-01.csv необходимо положить в папку TaxiTrip\src\main\data\
3) Все формируемые файлы в папке TaxiTrip\src\main\data\

Скрип выполняет следующее:

1)Читает файл с данными yellow_tripdata_2020-01.csv
  Формирует 5 групп по количеству пассажиров
  Из данных дата и время, получает дату
  Формирует набор данных из требуемых для дальнейшего анализа полей
  Сохраняет в формат parquet разделяя по дате (для дальнейшей работы с данными)

2)Читает данные с формата parquet
  По требуемым полям группировки, вычисляет агрегатные функции 
  Объединяет результаты вычислений в один набор данных
  Формирует итоговую таблицу
  Сохраняет результат в формат parquet

3)Формирует набор данных для построения графика
  Сохраняет в формат csv


В папке TaxiTrip\src\main\data\
- [tripdata.parquet] данные полученные из csv 
- [taxitripdata.parquet] итоговая таблица (ResultTable.csv - для наглядности)  
- [taxi.csv] данные для графика (yellow_taxi_grafic.csv) для загрузки в Colaboratory и построения графика
- Taxi_grafic.ipynb - графики зависимости размер чаевых в зависимости от пройденного расстояния и количества пассажиров. 


 

