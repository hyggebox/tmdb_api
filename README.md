# TMDB API

Отправляет запросы к базе данных с фильмами [TMDB](https://www.themoviedb.org/) (The Movie Database)

## Установка и запуск

- Для работы со скриптами необходим api-ключ TMDB, который можно получить после регистрации
на [сайте TMDB](https://www.themoviedb.org/signup).


- Скачайте файлы. 
- Python3 должен быть уже установлен. Используйте `pip` (или `pip3`, если есть конфликт с Python2) для установки зависимостей:

```
pip install -r requirements.txt
```

- Запустите нужный скрипт командой `python` (или `python3`, если есть конфликт с Python2). Например:


```
python main.py
```
________

## find_similar

Скрипт, который ищет фильмы с похожими параметрами, как у введенного пользователем фильма.

Первым делом просит пользователя ввести путь к базе данных. Если БД не найдена,
выводит сообщение "*File not found, sorry...*" и завершает действие.

Если БД найдена, просит ввести название фильма. Ищет среди фильмов из БД фильм с данным названием.
Если в БД есть такой фильм, ищет фильмы в аналогичными параметрами и выводит список
наиболее схожих по параметрам фильмов в алфавитном порядке (по умолчанию 8 фильмов).
 

## hello_api_TMDB

Скрипт просит пользователя ввести api-ключ и проверяет его. Если ключ действителен, делает
запрос к базе данных TMDB о фильме "*Saw II*" ("*Пила II*"). Выводит
в консоль бюджет фильма.

## make_own_db

Скрипт, который выгружает базу данных, содержащую до 1000 фильмов по api-ключу пользователя.

Просит у пользователя ввести api-ключ и проверяет его с помощью функции `get_user_api_key()`.
При действительном api-ключе, делает запрос к БД TMDB и пытается выгрузить фильмы 
с первыми 1000 id. Успешно выгруженные данные записывает в файл `MyFilmDB.json`


## search_in_db

Скрипт, который ищет фильмы по введенным ключевым словам и выводит список
найденных фильмов.

При запуске скрипт просит ввести путь к базе данных. Если БД не найдена,
выводит сообщение "*File not found, sorry...*" и завершает действие.
Если БД найдена, просит ввести название фильма.
Ищет среди фильмов из БД фильмы, в названиях которых содержатся введеные слова.
Выводит список найденных фильмов в алфавитном порядке.

____________

### own_db_helpers

Файл содержит функцию `load_data()`, которая загружает данные о фильмах из 
указанного файла.


### tmdb_helpers

Файл содержит функции:

`make_tmdb_api_request()` -- "собирает" данные для запроса
к базе данных TMDB (api-ключ, конечный url, параметры).

`load_json_data_from_url()` -- делает запрос к базе данных TMDB и выгружает данные
из неё данные по заданным параметрам в формате .json 

`get_user_api_key()` -- получает api-ключ от пользователя и проверяет, действителен ли он.