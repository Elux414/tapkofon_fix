
<div align="center">

# 👞 Tapkofon Fix

![Telegram](https://img.shields.io/badge/Telegram-blue?style=flat&logo=telegram)
![CodeStyle](https://img.shields.io/badge/code%20style-black-black)
![GitHub contributors](https://img.shields.io/github/contributors/D4n13l3k00/tapkofon)
![GitHub](https://img.shields.io/github/license/D4n13l3k00/tapkofon)

[![DeepSource](https://deepsource.io/gh/D4n13l3k00/tapkofon.svg/?label=active+issues&token=zBpkbE5y6_lXYxJ6RtPVrJQ1)](https://deepsource.io/gh/D4n13l3k00/tapkofon/?ref=repository-badge)
[![DeepSource](https://deepsource.io/gh/D4n13l3k00/tapkofon.svg/?label=resolved+issues&token=zBpkbE5y6_lXYxJ6RtPVrJQ1)](https://deepsource.io/gh/D4n13l3k00/tapkofon/?ref=repository-badge)

### !!!Данный форк чинит конфиг Dockerfile, что исправляет ошибку при сборке контейнера (+ совместимость для разворачивания на [Render](https://render.com/); Исправляется main.py, что обеспечивает совместимость с контейнерами goorm.io (бесплатная альтернатива Okteto). Другие изменения не вносились!!!

### Представляю вам свой мини-проект **Tapkofon** - минималистичный веб-клиент Telegram'а на Telethon, FastAPI, сделанный преимущественно для кнопочных телефонов

</div>

[Идея взята отсюда](https://github.com/xadjilut/microclient)

### 📜 Для чего это / Где это можно использовать?

- Когда доступ только к кнопочному телефону `(ex. Гос.служба)`
- Устройство, поддерживающее только html и куки `(ex. Кнопочные телефоны)`
- Место с очень низкой скоростью интернета
- Для постоянного использования (мазохизм)

### 💖 Фишки

- Пароль доступа (cookie) ([config.py](/config.py#L11)). Пароль по умолчанию выключен, но вы можете его включить в конфиге.
- Система кэша (при загрузке файла он скачивается на сервер в кэш директорию, и оттуда отправляется вам)
- Конвертирование не mp3 аудио в mp3 для лучшей совместимости
- Распознавание речи в голосовых сообщениях
- Подгонка фото под определённый размер и сжатие([config.py](/config.py#L21)) для лучшей совместимости
- Смайлики в сообщениях превращаются в текст (тапики не поддерживают соверменные юникод смайлики)
- Возможность просмотра профиля пользователя (аватарка, юзерка , био)

### 😢 Баги (куда же без багов?)

- Не работает авторизация при включённом облачном пароле (только в вебе)
- Если найдешь баг, [пиши сюда](https://t.me/D4n13l3k00)

## 🔝 Быстрый старт

```bash
git clone https://github.com/Elux414/tapkofon_fix
cd tapkofon
apt install python3 python3-venv python3-pip python3-setuptools ffmpeg -y
chmod +x *.sh
./local_deploy.sh
./run.sh
```

## 🔻 Установка

### 1. Установите Python 🐍

[Python](https://www.python.org/downloads/)

### 2. Клонируйте репозиторий 📩

Клонируйте репозиторий

```bash
git clone https://github.com/Elux414/tapkofon_fix
cd tapkofon
```

### 3. Установите зависимости 📦

```bash
apt install ffmpeg -y

python3 -m pip install --user -r requirements.txt
```

### 4. Запуск 🚀

```bash
uvicorn main:app --host 0.0.0.0 --port 8000
```

Клиент будет доступен на порту `8000` (вы можете изменить его на любой другой)

Документация API на `/docs`

### 5 Докер 🐳

### Новая инструкция

1. Скачивайте образ `docker pull elux414/tapkofon-docker-fork`
2. Запускаете контейнер `docker run --name=tapik -itd -p 8888:8888 elux414/tapkofon-docker-fork`
Profit! Том для сессий создается автоматически, что удобно и для вас, и для разворачивания на облаке.

### Старая инструкция
Билд: `docker build -t tapik .`

Создаём volume для сохранения сессии: `docker volume create tapik-session` (уже неактуально, volume создается автоматически сам)

Запуск: `docker run -itd -p 8888:8888 -v tapik-session:/root/session tapik`

Можно использовать docker-compose: `docker-compose up -d`

P.S: доступен деплой на [Okteto](https://cloud.okteto.com/#/deploy?repository=https://github.com/D4n13l3k00/tapkofon) P.S2: Бесплатно не развернёте, нужны деньги :(

### АЛЬТЕРНАТИВА OKTETO

Имеется возможность развернуть tapkofon на [goorm.io](https://www.goorm.io/dashboard)

1. Перейдите по ссылке
2. Зарегистрируйте аккаунт
3. Перейдите в раздел IDE
4. Создайте контейнер на базе Ubuntu 20.04 LTS (Stack выбирайте "Python")
5. Склонируйте репозиторий:
   ```bash
   git clone https://github.com/Elux414/tapkofon_fix
   ```
   
6. Выполните:
   ```bash
   cd tapkofon
   ```
   
7. Выполните установку ffmpeg:
   ```bash
   apt install ffmpeg -y
   ```

8. Установите зависимости:
   ```bash
   python3 -m pip install -r requirements.txt
   
9. На всякий случай можете выполнить команду:
   ```bash
   pip install uvicorn
   ```
   
10. Далее выполните:
   ```bash
   cd tapkofon
   ```

11. И наконец:
   ```bash
   uvicorn main:app --host 0.0.0.0 --port 8000
   ```

12. В интерфейсе выберете Container -> Running URL and Port

Указываете любую ссылку, порт указываете 8000. После проделанных манипуляций перейдите по своей ссылке, которую указывали.

Profit! Всё должно работать, однако помните о том, что за работу списывается 2.25 кредита в час, так что останавливайте контейнер, если не пользуетесь им. Если найдёте аналог такой же бесплатный и более лучший, то сообщите об этом :)


### АЛЬТЕРНАТИВА OKTETO 2

Обновил Dockerfile, теперь есть возможность развернуть докер контейнер на [Render](https://render.com/)

1. Зарегистрируйтесь на Render
2. В Dashboard выберите "+New", далее "Web Service"
3. Внизу страницы будет "Public Git repository", в поле вставьте ссылку на репозиторий https://github.com/Elux414/tapkofon_fix
4. Далее задайте имя, регион сервера (советую европейский), instance type (берите free)
5. Нажмите "Create Web Service"
6. Ожидайте создания контейнера, ссылка на веб интерфейс тапкофона находится в верхнем левом углу.


### P.S 🤫 (при бесплатном разворачивании докер контейнера на Render данная инструкция неактуальна, отредактировать ничего нельзя)

Для корректной работы необходимо установить свои `api_id` и `api_hash` в `config.toml` (генерируется при запуске в папке session)

Из-за этого может не приходить код для авторизации (проверено лично)

Получить их можно [здесь](https://my.telegram.org/apps)
