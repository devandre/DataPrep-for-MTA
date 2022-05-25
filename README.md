# DataPrep-for-MTA

## Цель проекта:

Подготовка пользовательского набора данных и анализ взаимодействия пользователей и каналов/рекламных кампаний в цепочках конверсии при помощи различных моделей атрибуции из библиотеки анализа пользовательских последовательностей. Это поможет практически оценить эффективность наиболее популярных моделей атрибуции, визуализировать полученные результаты, а также произвести [комплексную оценку](https://github.com/devandre/ModelComparison-for-MTA) точности алгоритмов атрибуции по показателю ROC AUC и произвести [сравнительный анализ](https://github.com/devandre/ModelComparison-for-MTA) времени работы всех рассмотренных алгоритмов.

## Результаты

Был проведен анализ последовательностей по следующим моделям атрибуции:
- Атрибуция по первому клику
- Атрибуция по последнему клику
- Атрибуция с учетом давности взаимодействий
- Атрибуция на основе цепей Маркова
- Атрибуция с использованием вектора Шепли

### Пример использованных исходных данных (Каналы):

| Google_client_Id    | Channel_funnel                                              | Medium_funnel                                        | Source_funnel                                                 | Campaign_funnel                                                       | Transactions | Revenue |
| ------------------- | ----------------------------------------------------------- | ---------------------------------------------------- | ------------------------------------------------------------- | --------------------------------------------------------------------- | ------------ | ------- |
| 0000197671390269035 | Social                                                      | referral                                             | m.facebook.com                                                | (not set)                                                             |              |         |
| 0000458812883559498 | Organic Search                                              | organic                                              | google                                                        | (not set)                                                             |              |         |
| 0000572434142265465 | Referral                                                    | (none)                                               | (direct)                                                      | (not set)                                                             |              |         |
| 0001436786657417059 | Organic Search                                              | organic                                              | google                                                        | (not set)                                                             |              |         |
| 0001611849527956932 | Direct                                                      | (none)                                               | (direct)                                                      | (not set)                                                             |              |         |
| 0002071854063058685 | Organic Search                                              | organic                                              | google                                                        | (not set)                                                             |              |         |
| 0002272296402119960 | Direct                                                      | (none)                                               | (direct)                                                      | (not set)                                                             |              |         |
| 0002380026400689835 | Direct                                                      | (none)                                               | (direct)                                                      | (not set)                                                             |              |         |
| 0002564246398068164 | Organic Search                                              | organic                                              | google                                                        | (not set)                                                             |              |         |
| 0002793999826216383 | Organic Search                                              | organic                                              | google                                                        | (not set)                                                             |              |         |
| 0002793999826216383 | Organic Search > Direct                                     | organic > (none)                                     | google > (direct)                                             | (not set) > (not set)                                                 |              |         |
| 0002793999826216383 | Organic Search > Direct > Direct                            | organic > (none) > (none)                            | google > (direct) > (direct)                                  | (not set) > (not set) > (not set)                                     |              |         |
| 0002793999826216383 | Organic Search > Direct > Direct > Direct                   | organic > (none) > (none) > (none)                   | google > (direct) > (direct) > (direct)                       | (not set) > (not set) > (not set) > (not set)                         |              |         |
| 0002793999826216383 | Organic Search > Direct > Direct > Direct > Direct          | organic > (none) > (none) > (none) > (none)          | google > (direct) > (direct) > (direct) > (direct)            | (not set) > (not set) > (not set) > (not set) > (not set)             |              |         |
| 0002793999826216383 | Organic Search > Direct > Direct > Direct > Direct > Direct | organic > (none) > (none) > (none) > (none) > (none) | google > (direct) > (direct) > (direct) > (direct) > (direct) | (not set) > (not set) > (not set) > (not set) > (not set) > (not set) |              |         |

### Результат обработки данных (Каналы):

|path                                                                                                                                                                                                                                                                                                                                                                                            |total_conversions|total_null|total_conversion_value|
|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------|----------|----------------------|
|Affiliates                                                                                                                                                                                                                                                                                                                                                                                      |0.0              |969.0     |0                     |
|Affiliates > Direct                                                                                                                                                                                                                                                                                                                                                                             |0.0              |109.0     |0                     |
|Affiliates > Direct > Direct                                                                                                                                                                                                                                                                                                                                                                    |0.0              |26.0      |0                     |
|Affiliates > Direct > Direct > Direct                                                                                                                                                                                                                                                                                                                                                           |0.0              |8.0       |0                     |
|Affiliates > Direct > Direct > Direct > Direct                                                                                                                                                                                                                                                                                                                                                  |0.0              |2.0       |0                     |
|Affiliates > Direct > Direct > Direct > Direct > Direct                                                                                                                                                                                                                                                                                                                                         |0.0              |1.0       |0                     |
|Affiliates > Direct > Direct > Direct > Direct > Direct > Direct                                                                                                                                                                                                                                                                                                                                |0.0              |1.0       |0                     |
|Affiliates > Direct > Direct > Referral                                                                                                                                                                                                                                                                                                                                                         |0.0              |1.0       |0                     |
|Affiliates > Direct > Referral                                                                                                                                                                                                                                                                                                                                                                  |0.0              |7.0       |0                     |
|Affiliates > Direct > Referral > Direct                                                                                                                                                                                                                                                                                                                                                         |0.0              |2.0       |0                     |
|Affiliates > Direct > Referral > Direct > Direct                                                                                                                                                                                                                                                                                                                                                |0.0              |2.0       |0                     |
|Affiliates > Direct > Referral > Direct > Direct > Direct                                                                                                                                                                                                                                                                                                                                       |0.0              |2.0       |0                     |
|Affiliates > Direct > Referral > Direct > Direct > Direct > Direct                                                                                                                                                                                                                                                                                                                              |0.0              |1.0       |0                     |
|Affiliates > Organic Search                                                                                                                                                                                                                                                                                                                                                                     |0.0              |2.0       |0                     |
|Affiliates > Organic Search > Affiliates                                                                                                                                                                                                                                                                                                                                                        |0.0              |1.0       |0                     |

### Результат аллоцирования ценности при помощи различных моделей атрибуции (Каналы):


|channels      |first_touch|last_touch|time_decay|markov  |shapley |shao    |
|--------------|-----------|----------|----------|--------|--------|--------|
|(Other)       |0.0        |0.0       |          |0.0     |0.0     |        |
|Affiliates    |0.0        |0.0       |          |0.0     |0.0     |        |
|Direct        |0.51085    |0.665461  |0.60217   |0.579698|0.544822|0.607559|
|Display       |0.003617   |0.003617  |0.004521  |0.004347|0.006195|0.003448|
|Organic Search|0.207957   |0.138336  |0.165763  |0.209225|0.184215|0.036668|
|Paid Search   |0.028933   |0.022604  |0.024864  |0.024245|0.026763|0.016022|
|Referral      |0.228752   |0.152803  |0.183996  |0.163929|0.218768|0.330202|
|Social        |0.019892   |0.017179  |0.018686  |0.018556|0.019236|0.006101|

### Результат аллоцирования ценности при помощи различных моделей атрибуции (Канал:Рекламные кампании):


|campaigns                                               |last_touch |linear    |time_decay|markov  |shapley |shao    |first_touch|
|--------------------------------------------------------|-----------|----------|----------|--------|--------|--------|-----------|
|(Other) : (not set)                                     |0.0        |          |          |0.0     |0.0     |        |0.0        |
|Affiliates : Data Share Promo                           |0.0        |          |          |0.0     |0.0     |        |0.0        |
|Direct : (not set)                                      |0.665461   |0.579641  |0.602049  |0.580107|0.546879|0.603441|0.51085    |
|Display : (not set)                                     |0.003617   |0.00437   |0.004521  |0.004353|0.00601 |0.003423|0.003617   |
|Organic Search : (not set)                              |0.138336   |0.175934  |0.165582  |0.209126|0.183059|0.03705 |0.207957   |
|Paid Search : (not set)                                 |0.0        |          |          |0.0     |0.0     |        |0.0        |
|Paid Search : AW - Accessories                          |0.018987   |0.020268  |0.019952  |0.019249|0.021792|0.017087|0.0217     |
|Paid Search : AW - Apparel                              |0.0        |          |          |0.0     |0.0     |        |0.0        |
|Paid Search : AW - Dynamic Search Ads Whole Site        |0.003617   |0.005651  |0.005214  |0.00442 |0.006693|0.005154|0.007233   |
|Paid Search : AW - Electronics                          |0.0        |          |          |0.0     |0.0     |        |0.0        |
|Referral : (not set)                                    |0.152803   |0.195148  |0.183996  |0.164163|0.216366|0.327789|0.228752   |
|Social : (not set)                                      |0.017179   |0.018987  |0.018686  |0.018583|0.019201|0.006056|0.019892   |


## Ссылки
Библиотека для анализа цепочек взаимодействия:
- [Multi-Touch Attribution (mta)](https://github.com/eeghor/mta)

Исходные данные (Kaggle):
- [Google Analytics Sample (BigQuery)](https://www.kaggle.com/bigquery/google-analytics-sample)



