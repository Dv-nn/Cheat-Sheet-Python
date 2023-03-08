## SQL
____

**SQL** — это язык структурированных запросов (Structured Query Language), позволяющий хранить, манипулировать и извлекать данные из реляционных баз данных.
____

**Таблица** - это коллекция связанных между собой данных и состоит из определенного количества колонок и строк.  

**Поле** — это колонка таблицы, предназначенная для хранения определенной информации о каждой записи в таблице.  

**Запись или строка** (record/row) — это любое единичное вхождение (entry), существующее в таблице.  

**Колонка** (column) — это вертикальное вхождение в таблице, содержащее всю информацию, связанную с определенным полем.

**Нулевое значение** (NULL) — это значение поля, которое является пустым, т.е. нулевое значение — это значение поля, не имеющего значения.
____  

****Команды SQL****
CREATE - создает новую таблицу, представление таблицы или другой объект в БД  
ALTER - модифицирует существующий в БД объект, такой как таблица  
DROP - удаляет существующую таблицу, представление таблицы или другой объект в БД  
SELECT - извлекает записи из одной или нескольких таблиц  
INSERT - создает записи  
UPDATE - модифицирует записи  
DELETE - удаляет записи  
GRANT - наделяет пользователя правами  
REVOKE - отменяет права пользователя  
____  

**Логические операторы**
ALL - сравнивает все значения  
AND - объединяет условия (все условия должны совпадать)  
ANY - сравнивает одно значение с другим, если последнее совпадает с условием  
BETWEEN - проверяет вхождение значения в диапазон от минимального до максимального  
EXISTS - определяет наличие строки, соответствующей определенному критерию  
IN - выполняет поиск значения в списке значений  
LIKE - сравнивает значение с похожими с помощью операторов подстановки  
NOT - инвертирует (меняет на противоположное) смысл других логических операторов, например, NOT EXISTS, NOT IN и т.д.  
OR - комбинирует условия (одно из условий должно совпадать)  
IS NULL - определяет, является ли значение нулевым  
UNIQUE - определяет уникальность строки  

```
-- выборка
SELECT col1, col2, ...colN
FROM tableName;

SELECT DISTINCT col1, col2, ...colN
FROM tableName;

SELECT col1, col2, ...colN
FROM tableName
WHERE condition;

SELECT col1, col2, ...colN
FROM tableName
WHERE condition1 AND|OR condition2;

SELECT col2, col2, ...colN
FROM tableName
WHERE colName IN (val1, val2, ...valN);

SELECT col1, col2, ...colN
FROM tableName
WHERE colName BETWEEN val1 AND val2;

SELECT col1, col2, ...colN
FROM tableName
WHERE colName LIKE pattern;

SELECT col1, col2, ...colN
FROM tableName
WHERE condition
ORDER BY colName [ASC|DESC];

SELECT SUM(colName)
FROM tableName
WHERE condition
GROUP BY colName;

SELECT COUNT(colName)
FROM tableName
WHERE condition;

SELECT SUM(colName)
FROM tableName
WHERE condition
GROUP BY colName
HAVING (function condition);

-- создание таблицы
CREATE TABLE tableName (
  col1 datatype,
  col2 datatype,
  ...
  colN datatype,
  PRIMARY KEY (одна или более колонка)
);

-- удаление таблицы
DROP TABLE tableName;

-- создание индекса
CREATE UNIQUE INDEX indexName
ON tableName (col1, col2, ...colN);

-- удаление индекса
ALTER TABLE tableName
DROP INDEX indexName;

-- получение описания структуры таблицы
DESC tableName;

-- очистка таблицы
TRUNCATE TABLE tableName;

-- добавление/удаление/модификация колонок
ALTER TABLE tableName ADD|DROP|MODIFY colName [datatype];

-- переименование таблицы
ALTER TABLE tableName RENAME TO newTableName;

-- вставка значений
INSERT INTO tableName (col1, col2, ...colN)
VALUES (val1, val2, ...valN)

-- обновление записей
UPDATE tableName
SET col1 = val1, col2 = val2, ...colN = valN
[WHERE condition];

-- удаление записей
DELETE FROM tableName
WHERE condition;

-- создание БД
CREATE DATABASE [IF NOT EXISTS] dbName;

-- удаление БД
DROP DATABASE [IF EXISTS] dbName;

-- выбор БД
USE dbName;

-- завершения транзакции
COMMIT;

-- отмена изменений
ROLLBACK;
```
____

**Типы данных**  

| Тип данных | От | До |
| --- | --- | --- |
| bigint | -9,223,372,036,854,775,808 | 9,223,372,036,854,775,807 |
| int | -2,147,483,648 | 2,147,483,647 |
| smallint | -32,768 | 32,767 |
| tinyint | 0 | 255 |
| bit | 0 | 1 |
| decimal | -10^38 +1 | 10^38 -1 |
| numeric | -10^38 +1 | 10^38 -1 |
| money | -922,337,203,685,477.5808 | +922,337,203,685,477.5807 |
| smallmoney | -214,748.3648 | +214,748.3647 |
| float | -1.79E + 308 | 1.79E + 308 |
| real | -3.40E + 38 | 3.40E + 38 |
| datetime | Jan 1, 1753 | Dec 31, 9999 |
| smalldatetime | Jan 1, 1900 | Jun 6, 2079 |
| date | Дата сохраняется в виде June 30, 1991 |  |
| time | Время сохраняется в виде 12:30 P.M. |  |

| N | Тип данных | Описание |
| --- | --- | --- |
| 1 | char | Строка длиной до 8,000 символов (не-юникод символы, фиксированной длины) |
| 2 | varchar | Строка длиной до 8,000 символов (не-юникод символы, переменной длины) |
| 3 | text | Не-юникод данные переменной длины, длиной до 2,147,483,647 символов |
| 1 | nchar | Строка длиной до 4,000 символов (юникод символы, фиксированной длины) |
| 2 | nvarchar | Строка длиной до 4,000 символов (юникод символы, переменной длины) |
| 3 | ntext | Юникод данные переменной длины, длиной до 1,073,741,823 символ |
| 1 | binary | Данные размером до 8,000 байт (фиксированной длины) |
| 2 | varbinary | Данные размером до 8,000 байт (переменной длины) |
| 3 | image | Данные размером до 2,147,483,647 байт (переменной длины) |
| 1 | timestamp | Уникальные числа, обновляющиеся при каждом изменении строки |
| 2 | uniqueidentifier | Глобально-уникальный идентификатор (GUID) |
| 3 | cursor | Объект курсора |
| 4 | table | Промежуточный результат, предназначенный для дальнейшей обработки |
____  

**Ограничения** (constraints) — это правила, применяемые к данным. Они используются для ограничения данных, которые могут быть записаны в таблицу. 
Ограничения могут устанавливаться как на уровне колонки, так и на уровне таблицы.  
Удалить ограничение `ALTER TABLE`и `DROP CONSTRAINT`+ название ограничения  

- `NOT NULL` — колонка не может иметь нулевое значение  
- `DEFAULT` — значение колонки по умолчанию  
- `UNIQUE` — все значения колонки должны быть уникальными  
- `PRIMARY KEY` — первичный или основной ключ, уникальный идентификатор записи в текущей таблице  
- `FOREIGN KEY` — внешний ключ, уникальный идентификатор записи в другой таблице (таблице, связанной с текущей)  
- `CHECK` — все значения в колонке должны удовлетворять определенному условию  
- `INDEX` — быстрая запись и извлечение данных  
____

**Выражение** (expression) — это комбинация значений, операторов и функций, похожи на формулы, написанные на языке запросов.  

```
SELECT col1, col2, ...colN
FROM tableName
WHERE [condition|expression];
```

```
SELECT col1, col2, ...colN
FROM tableName
WHERE выражение для поиска совпадения с единичным значением;
```

```
**SELECT** * **FROM** users **WHERE** status = active;
```

```
**SELECT** (10 + 5) **AS** addition;
```
____

**Встроенные функции** - для выполнения вычислений данных таблицы или колонки  

```
SELECT COUNT(*) AS records FROM users;
```

`AVG()` — вычисляет среднее значение  
`SUM()` — вычисляет сумму значений  
`MIN()` — вычисляет наименьшее значение  
`MAX()` — вычисляет наибольшее значение  
`COUNT()` — вычисляет количество записей в таблице  
`CONCAT()` — объединение строк  
`LENGTH()` — возвращает количество символов в строке  
`TRIM()` — удаляет пробелы в начале и конце строки  
`SUBSTRING()` — извлекает подстроку из строки  
`REPLACE()` — заменяет подстроку в строке  
`LOWER()` — переводит символы строки в нижний регистр  
`UPPER()` — переводит символы строки в верхний регистр и т.д.  
`ROUND()` — округляет число  
`TRUNCATE()` — обрезает дробное число до указанного количества знаков после запятой  
`CEILING()` — возвращает наименьшее целое число, которое больше или равно текущему значению  
`FLOOR()` — возвращает наибольшее целое число, которое меньше или равно текущему значению  
`POWER()` — возводит число в указанную степень  
`SQRT()` — возвращает квадратный корень числа  
`RAND()` — генерирует случайное число с плавающей точкой в диапазоне от 0 до 1  
_____  

**Дата**  

```
SELECT CURRENT_TIMESTAMP;  
```  

`CURDATE`/`CURRENT_DATE` — возвращает текущую дату  
`CURTIME`/`CURRENT_TIME` — возвращает текущее время  
`DAYOFMONTH(date)` — возвращает день месяца в виде числа  
`DAYOFWEEK(date)` — возвращает день недели в виде числа  
`DAYOFYEAR(date)` — возвращает номер дня в году  
`MONTH(date)` — возвращает месяц  
`YEAR(date)` — возвращает год  
`LAST_DAY(date)` — возвращает последний день месяца в виде даты  
`HOUR(time)` — возвращает час  
`MINUTE(time)` — возвращает минуты  
`SECOND(time)` — возвращает секунды и др.  
`DATE_ADD(date, interval)` — выполняет сложение даты и определенного временного интервала  
`DATE_SUB(date, interval)` — выполняет вычитание из даты определенного временного интервала  
`DATEDIFF(date1, date2)` — возвращает разницу в днях между двумя датами  
`TO_DAYS(date)` — возвращает количество дней с 0-го дня года  
`TIME_TO_SEC(time)` — возвращает количество секунд с полуночи  
____  

**Создание БД**

```
CREATE DATABASE dbName;
# или
CREATE DATABASE IF NOT EXISTS dbName;
```
____
**Удаление БД**

```
**DROP** DATABASE testDB;
```  
____
**Выбор БД**

```
USE dbName;
```
____
****Создание таблицы****

```
CREATE TABLE tableName (
  col1 datatype,
  col2 datatype,
  ...
  colN datatype,
  PRIMARY KEY (хотя бы одна колонка)
);
```

Проверяем, что таблица была создана:  

```
DESC users;
```
____
**Удаление таблицы**

```
**DROP TABLE** users;
```
____
**Добавление колонок**

```
INSERT INTO tableName (col1, col2, ...colN)
VALUES (val1, val2, ...valN);
```

```
INSERT INTO users (userId, userName, age, city, status)
VALUES
(1, 'Igor', 25, 'Moscow', 'active'),
(2, 'Vika', 26, 'Ekaterinburg', 'inactive'),
(3, 'Elena', 27, 'Ekaterinburg', 'active');
```
____
**Заполнение таблицы с помощью другой таблицы**

```
INSERT INTO tableName [(col1, col2, ...colN)]
  SELECT col1, col2, ...colN
  FROM anotherTable
  [WHERE condition];
```
____
**Выборка полей**

```
SELECT col1, col2, ...colN
FROM tableName;
```
____
**Фильтрация данных**
**WHERE**

```
SELECT col1, col2, ...col2
FROM tableName
WHERE condition;
```

```
SELECT userId, userName, age
FROM users
WHERE status = 'active';
```
____
**AND / OR**

```
SELECT col1, col2, ...colN
FROM tableName
WHERE condition1 AND condition2 ...AND conditionN;
```

```
SELECT col1, col2, ...colN
FROM tableName
WHERE condition1 OR condition2 ...OR conditionN;
```
____
**Обновление полей**

```
UPDATE tableName
SET col1 = val1, col2 = val2, ...colN = valN
[WHERE condition];
```
____
**Удаление записей**

```
DELETE FROM tableName
[WHERE condition];
```
____
**REGEX**

```
SELECT col1, col2, ...colN FROM tableName
WHERE colName REGEXP регулярное выражение;
```

```
SELECT * FROM users
WHERE userName REGEXP 'Igor|Vika';
```

В регулярное выражении могут использоваться следующие специальные символы:  
- `^` — начало строки  
- `$` — конец строки  
- `.` — любой символ  
- `[символы]` — любой из указанных в скобках символов  
- `[начало-конец]` — любой символ из диапазона  
- `|` — разделяет шаблоны  
____
**Cравнение значений**  

**LIKE  ‘%’ -** означает 0, 1 или более символов  
**LIKE ‘_’** - означает точно 1 символ  

```
SELECT col1, col2, ...colN FROM tableName
WHERE col LIKE 'xxx%'
# или
WHERE col LIKE '%xxx%'
# или
WHERE col LIKE '%xxx'
# или
WHERE col LIKE 'xxx_'
```

```
SELECT * FROM users
WHERE status LIKE 'in%';
```
____
**Cортировка данных**  
**ORDER BY** используется для сортировки данных по возрастанию (`ASC`) или убыванию (`DESC`)  

```
SELECT col1, col2, ...colN
FROM tableName
[WHERE condition]
[ORDER BY col1, col2, ...colN] [ASC | DESC];
```

```
SELECT * FROM users
ORDER BY city, age DESC;
```
____
**GROUP BY** используется совместно с инструкцией `SELECT`  
 для группировки записей  

```
SELECT col1, col2, ...colN
FROM tableName
WHERE condition
GROUP BY col1, col2, ...colN
ORDER BY col1, col2, ...colN;
```

```
SELECT city, COUNT(city) AS amount FROM users
WHERE status = active
GROUP BY city
ORDER BY city;
```
____
`НAVING` - используется для фильтрации результатов группировки. `WHERE`  
 используется для применения условий к колонкам, а `HAVING`  - к группам, созданным с помощью `GROUP BY`  
`HAVING` должно указываться после `GROUP BY,` но перед `ORDER BY`  

```
SELECT col1, col2, ...colN
FROM table1, table2, ...tableN
[WHERE condition]
GROUP BY col1, col2, ...colN
HAVING condition
ORDER BY col1, col2, ...colN;
```
____
**Предложение TOP/LIMIT/ROWNUM**  
Данные предложения позволяют извлекать указанное количество или процент записей с начала таблицы  

```
SELECT TOP number|percent col1, col2, ...colN
FROM tableName
[WHERE condition];
```

```
SELECT TOP 3 * FROM users;
```
____
****Ключевое слово DISTINCT**** используется совместно с инструкцией `SELECT` для возврата только уникальных записей (без дубликатов)  

```
SELECT DISTINCT col1, col2, ...colN
FROM tableName
[WHERE condition];
```

```
SELECT DISTINCT city
FROM users;
```
____
**Соединения** используются для комбинации записей двух и более таблиц  

```
SELECT userId, userName, age, amount
FROM users, orders
WHERE users.userId = orders.userId;
```  

`INNER JOIN` — возвращает записи, имеющиеся в обеих таблицах  
`LEFT JOIN` — возвращает записи из левой таблицы, даже если такие записи отсутствуют в правой таблице  
`RIGHT JOIN` — возвращает записи из правой таблицы, даже если такие записи отсутствуют в левой таблице  
`FULL JOIN` — возвращает все записи объединяемых таблиц  
`CROSS JOIN` — возвращает все возможные комбинации строк обеих таблиц  
`SELF JOIN` — используется для объединения таблицы с самой собой  
____
**Предложение UNION** используется для комбинации результатов двух и более инструкций `SELECT` , возвращаются только уникальные записи  
**UNION ALL** - возвращаются все записи, включая дубликаты  

```
SELECT col1, col2, ...colN
FROM table1
[WHERE condition]

UNION

SELECT col1, col2, ...colN
FROM table2
[WHERE condition];
```

```
SELECT userId, userName, amount, date
  FROM users
  LEFT JOIN orders
  ON users.useId = orders.userId
UNION
  SELECT userId, userName, amount, date
  FROM users
  RIGHT JOIN orders
  ON users.userId = orders.userId;
```  
____
**Синонимы**  
Синонимы (aliases) позволяют временно изменять названия таблиц и колонок. Новое название используется только в текущем запросе, в БД название остается прежним.  

```
SELECT col1, col2, ...colN
FROM tableName AS aliasName
[WHERE condition];
```

```
SELECT U.userId, U.userName, U.age, O.amount
FROM users AS U, orders AS O
WHERE U.userId = O.userId;
```
____
**Индексы -** это указатель или ссылка на данные в таблице  

```
CREATE INDEX indexName ON tableName;
```
___
Удаление индексов  

```
DROP INDEX indexName;
```  
____
**Обновление таблицы -** `ALTER TABLE`используется для добавления, удаления и модификации колонок существующей таблицы  

```
-- добавление новой колонки
ALTER TABLE tableName ADD colName datatype;

-- удаление колонки
ALTER TABLE tableName DROP COLUMN colName;

-- изменение типа данных колонки
ALTER TABLE tableName MODIFY COLUMN colName newDatatype;

-- добавление ограничения `NOT NULL`
ALTER TABLE tableName MODIFY colName datatype NOT NULL;

-- добавление ограничения `UNIQUE`
ALTER TABLE tableName
ADD CONSTRAINT myUniqueConstraint UNIQUE (col1, col2, ...colN);

-- добавление ограничения `CHECK`
ALTER TABLE tableName
ADD CONSTRAINT myUniqueConstraint CHECK (condition);

-- добавление первичного ключа
ALTER TABLE tableName
ADD CONSTRAINT myPrimaryKey PRIMARY KEY (col1, col2, ...colN);

-- удаление ограничения
ALTER TABLE tableName
DROP CONSTRAINT myUniqueContsraint;

-- mysql
ALTER TABLE tableName
DROP INDEX myUniqueContsraint;

-- удаление первичного ключа
ALTER TABLE tableName
DROP CONSTRAINT myPrimaryKey;

-- mysql
ALTER TABLE tableName
DROP PRIMARY KEY;
```  
____
**Очистка таблицы**  
`TRUNCATE TABLE`используется для очистки таблицы, сохраняя структуру таблицы  

```
TRUNCATE TABLE tableName;
```
____
**Представления**  - виртуальная таблица  
инструкция, записанная в БД под определенным названием  

`CREATE VIEW` - создание представвления  

```
CREATE VIEW viewName AS
SELECT col1, col2, ...colN
FROM tableName
[WHERE condition];
```  

`WITH CHECK OPTION` - настройка инструкции `CREATE VIEW` , позволяет обеспечить соответствие всех `UPDATE`и `INSERT`условию, определенном в представлении  

```
CREATE VIEW usersView AS
SELECT userName, age
FROM users
WHERE age IS NOT NULL
WITH CHECK OPTION;
```

`DROP VIEW` - удаление представления  

```python
DROP VIEW viewName;
```
____

**Транзакции**  
Транзакция — это применение одного или более изменения к БД. Например, при создании/обновлении/удалении записи мы выполняем транзакцию  

`BEGIN|START TRANSACTION` — запуск транзакции  
`COMMIT` — сохранение изменений  
`ROLLBACK / ROLLBACK TO` — отмена изменений  
`SAVEPOINT savepointName`   — контрольная точка для отмены изменений  
`RELEASE SAVEPOINT` - удаление контрольной точки  
`SET TRANSACTION` — установка характеристик текущей транзакции  

Команды для управления транзакцией могут использоваться только совместно с такими запросами как `INSERT`, `UPDATE`и `DELETE`.  

```
BEGIN TRANSACTION
DELETE FROM users
WHERE age = 26;
COMMIT;
```

```
START TRANSACTION
SAVEPOINT sp1;
DELETE FROM users
WHERE age = 26;

SAVEPOINT sp2;
DELETE FROM users
WHERE userName = 'Oleg';

SAVEPOINT sp3;
DELETE FROM users
WHERE status = 'inactive';
```
____

**Временные таблицы**  
позволяют хранить и обрабатывать промежуточные результаты с помощью таких же запросов, как и при работе с обычными таблицами.  
Особенностью таких таблиц является то, что они удаляются по завершении текущей сессии.  

`CREATE TEMPORARY TABLE` - создание временной таблицы  
`DROP TABLE` - удаление временной таблицы  
____

**Подзапросы**  
это внутренний (вложенный) запрос другого запроса, встроенный (вставленный) с помощью `WHERE` или других инструкций.  
Подзапрос используется для получения данных, которые будут использованы основным запросом в качестве условия для фильтрации возвращаемых записей.  

```
SELECT col1, col2, ...colN
FROM table1, table2, ...tableN
WHERE colName operator
  (SELECT col1, col2, ...colN
  FROM table1, table2, tableN
  [WHERE condition]);
```
____

**Последовательности**  
это набор целых чисел (1, 2, 3 и т.д.), генерируемых автоматически  
`AUTO_INCREMENT` - определения последовательности  

```
CREATE TABLE tableName (
  id INT UNSIGNED NOT NULL AUTO_INCREMENT,
  PRIMARY KEY (id),
  -- другие строки
);
```  
  
