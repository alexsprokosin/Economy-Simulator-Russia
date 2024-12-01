# Economy-Simulator-Russia
  ![DSFAD](https://github.com/user-attachments/assets/918305e6-b1df-49fe-a840-a1a016b640eb)


исходник сайта, Economy Simulator, 2016 роблокс ревивал.

# Информация
- floatzel - Создатель Оригинального Economy Simulator
- alexsprokosin - Переводчик этого туторила
- tenshi - помогал создателю исходника с сервером игры

# Что нужно для работы сайта и серверов/Базы данных
Тебе нужно что бы было:
- WSL (Это для Windows, Установить можно через команнду в PowerShell wsl --install)
- PostgreSQL (Версии 13 или больше)
- Redis-Server (устонавливать его надо через WSL)
- Node.js (Версии 18.XX или больше)
- Go/GoLang (версии 1.18+)
- .NET/dotnet ( рекомендуется 6 версия )

  1 шаг: Создай базу данных в PostgreSQL (pgAdmin4), это для создания аккаунта, и фукционала сайта. Если вы создали, **ЗАПОМНИТЕ ПАРОЛЬ** и в **service/api** создайте файл, **config.json** и вставте туда этот текст

  ```
{
    "knex": {
	"client": "pg",
        "connection": {
        "host": "127.0.0.1",
        "user": "postgres",
        "password": "postgres",
        "database": "db_name_here"
        }
    }
}
```
