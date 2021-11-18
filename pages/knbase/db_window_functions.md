---
title: window functions
keywords: db
summary: "This is just a sample topic..."
sidebar: knbase_sidebar
permalink: db_window_functions.html
folder: knbase
---

## LAG
Возвращает предыдущее значение

![alt text](images/knbase/db/wf_lag.png "Title")

пример:
```
SELECT ID, value, sale_year,
  LAG(value)
    OVER(
      PARTITION BY ID
      ORDER BY year
    ) AS prev_value
FROM sales;
```

## RANK
Применят ранг к каждой строке. Если в сортируемом столбце есть одинаковые значения, то ранг будет одним и тем же, но следующее значение ранга будет больше на количество одинаковых строк.

![alt text](images/knbase/db/wf_rank.png "Title")

```
SELECT
RANK() OVER(ORDER BY ranking_score) AS rank_number,
name, category, ranking_score
FROM product;
```

Поддерживает PARTITION BY

## DENSE_RANK
Работает также как и RANK, но не пропускает значения ранга при одинаковых строках в сортируемом столбце.

![alt text](images/knbase/db/wf_dense_rank.png "Title")

```
SELECT
DENSE_RANK() OVER(ORDER BY ranking_score DESC) AS dense_rank_number,
name, category, ranking_score
FROM product;
```

Поддерживает PARTITION BY

## ROW_NUMBER
Назначает порядковый номер каждой строке

![alt text](images/knbase/db/wf_row_number.png "Title")

```
SELECT
ROW_NUMBER() OVER(ORDER BY ranking_score) AS row_number,
name, category, ranking_score
FROM product;
```

## LEAD
Возвращает значение следующей строки

![alt text](images/knbase/db/wf_lead.png "Title")

```
SELECT
toy_name, month, sale_value,
LEAD(sale_value) OVER(PARTITION BY toy_name ORDER BY month)
AS next_month_value
FROM toys_sale;
```

## Running Total
![alt text](images/knbase/db/wf_running_total.png "Title")

```
SELECT toy_name, month, sale_value,
SUM(sale_value) OVER(PARTITION BY toy_name ORDER BY month) AS total_toy_value
FROM toys_sale;
```