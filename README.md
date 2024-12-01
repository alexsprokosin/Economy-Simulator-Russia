# Economy-Simulator-Russia
  ![DSFAD](https://github.com/user-attachments/assets/918305e6-b1df-49fe-a840-a1a016b640eb)


исходник сайта, Economy Simulator, 2016 роблокс ревивал.

# Информация
- floatzel - Создатель Оригинального Economy Simulator
- alexsprokosin - Переводчик этого туторила
- tenshi - помогал создателю исходника с сервером игры

- Ролик, с тутрорилоам - Скоро

# Что нужно для работы сайта и серверов/Базы данных
Тебе нужно что бы было:
- WSL (Это для Windows, Установить можно через команнду в PowerShell wsl --install)
- PostgreSQL (Версии 13 или больше)
- Redis-Server (устонавливать его надо через WSL)
- Node.js (Версии 18.XX или больше)
- Go/GoLang (версии 1.18+)
- .NET/dotnet ( рекомендуется 6 версия )

  1 шаг: Создай базу данных в PostgreSQL (pgAdmin4), это для создания аккаунта, и фукционала сайта. Если вы создали, **ЗАПОМНИТЕ ПАРОЛЬ** и в **services/api** создайте файл, **config.json** и вставте туда этот текст:

```
{
    "knex": {
	"client": "pg",
        "connection": {
        "host": "127.0.0.1",
        "user": "postgres",
        "password": "postgres",
        "database": "Названия базы данных сюда!"
        }
    }
}
```
можно приступать ко 2 шагу!

Шаг 2: Возращяйтесь в **services/api** и откройте комаднную строку:
![{59DD5396-A3F4-4833-B4B6-6DF191997DA3}](https://github.com/user-attachments/assets/40436007-a997-4b46-91d9-17d056af87f8)
и напишите в этом окне **cmd**, потом напишите команнду ```npm i```. эта команда установит все нужные модули, после завершения загрузки. Нужно будет запустить команду ```npx knex migrate:latest```, если прошло всё успешно, то я вас поздравляю вы создали базу данных.

Шаг 3: Переходи в **services/Roblox/Roblox.Website**, и переменуй файл **appsettings.example.json** на **appsettings.json**, дальше зайди туда, и найди ```"Postgres": "Host=127.0.0.1; Database=my_db_name; Password=postgres; Username=postgres; Maximum Pool Size=20"```,
и в **my_db_name** поставь имя своей базы данных.

Найди строку **"OwnerUserId": "12",** и замени 12 на **1**

Создай папку **storage** в **services/api** а в storage создай ещё одну **asset**

ещё создай папки в **services/api/public/images**, это **thumbnails** и **groups**

**Если они уже есть, то тебе повезло, и я их сам тебе создал)**

**И НЕ ЗАБУДЬ!!!** замени все пути ```/home/my_username/source-code/services/api/storage/``` на свои.



