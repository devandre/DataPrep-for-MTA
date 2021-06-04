# DataPrep-for-MTA

Цель проекта: подготовка пользовательского набора данных и анализ взаимодействия пользователей и каналов/рекламных кампаний в цепочках конверсии при помощи различных моделей атрибуции из библиотеки анализа пользовательских последовательностей. Это поможет практически оценить эффективность самых популярных моделей атрибуции и визуализировать полученные результаты.
Был проведен анализ последовательностей по следующим моделям:
- Атрибуция по первому клику
- Атрибуция по последнему клику
- Атрибуция с учетом давности взаимодействий
- Атрибуция на основе цепей Маркова
- Атрибуция с использованием вектора Шепли

Использованная библиотека для анализа цепочек взаимодействия:
- https://github.com/eeghor/mta

Данные для проекта взяты с сервиса Kaggle:
- https://www.kaggle.com/bigquery/google-analytics-sample

Пример использованных исходных данных с сервиса Kaggle:

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

Результат обработки данных:

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

Результат аллоцирования ценности при помощи различных моделей атрибуции:


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





