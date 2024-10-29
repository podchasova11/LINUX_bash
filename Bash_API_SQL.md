Вот несколько примеров сценариев на Bash, которые могут автоматизировать задачи взаимодействия с API и базами данных.

### Пример 1: Взаимодействие с API

Этот скрипт позволяет получить данные с API и сохранить их в файл.

```bash
#!/bin/bash

# URL API
API_URL="https://api.example.com/data"

# Файл для сохранения данных
OUTPUT_FILE="output.json"

# Запрос к API
curl -s -o "$OUTPUT_FILE" "$API_URL"

# Проверка успешности запроса
if [ $? -eq 0 ]; then
  echo "Данные успешно получены и сохранены в $OUTPUT_FILE"
else
  echo "Ошибка при получении данных"
fi
```

### Пример 2: Вставка данных в базу данных MySQL

Этот скрипт позволяет вставить данные в таблицу MySQL.

```bash
#!/bin/bash

# Параметры подключения к базе данных
DB_HOST="localhost"
DB_USER="username"
DB_PASS="password"
DB_NAME="database"

# Данные для вставки
DATA="Sample data"

# SQL-запрос
SQL="INSERT INTO my_table (my_column) VALUES ('$DATA');"

# Выполнение SQL-запроса
mysql -h "$DB_HOST" -u "$DB_USER" -p"$DB_PASS" -D "$DB_NAME" -e "$SQL"

# Проверка успешности
if [ $? -eq 0 ]; then
  echo "Данные успешно вставлены"
else
  echo "Ошибка при вставке данных"
fi
```

### Пример 3: Экспорт данных из базы данных PostgreSQL в CSV

Этот скрипт экспортирует данные из таблицы PostgreSQL в файл CSV.

```bash
#!/bin/bash

# Параметры подключения к базе данных
DB_HOST="localhost"
DB_USER="username"
DB_PASS="password"
DB_NAME="database"
OUTPUT_FILE="output.csv"

# SQL-запрос для экспорта
SQL="COPY (SELECT * FROM my_table) TO STDOUT WITH CSV HEADER;"

# Экспорт данных
PGPASSWORD="$DB_PASS" psqll -h "$DB_HOST" -U "$DB_USER" -d "$DB_NAME" -c "$SQL" > "$OUTPUT_FILE"

# Проверка успешности
if [ $? -eq 0 ]; then
  echo "Данные успешно экспортированы в $OUTPUT_FILE"
else
  echo "Ошибка при экспорте данных"
fi
```

Эти примеры демонстрируют, как можно использовать Bash для автоматизации задач, связанных с API и базами данных. Не забудьте заменить параметры подключения, названия таблиц и другие значения на свои собственные.
