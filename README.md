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

# Необходимые установки!

Что бы установить Redis-server надо запустить Unbutu, вас попросят создать имя и пароль, пароль не показывает при вводе и надо его вводить на память.

потом пишем туда команды ```sudo apt update``` потом ```sudo apt install redis```, для проверки напишите ```redis-server```

2 Шаг: вот ссылки на необходимые программы

node.js: ```https://nodejs.org/dist/v18.16.1/node-v18.16.1-x64.msi```

postgreSQL: ```https://sbp.enterprisedb.com/getfile.jsp?fileid=1258627```

Dotnet 6: ```https://dotnet.microsoft.com/en-us/download/dotnet/thank-you/sdk-6.0.412-windows-x64-installer```

Go lang: ```https://go.dev/dl/go1.20.6.windows-amd64.msi```

# Создания, и Настройка Сайта, базы данных!

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

Шаг 4: вернись в папку, **services/Roblox/Roblox.Website** открой комадную строку, как на прошлом шаге, и введи команду ```dotnet run```. Если всё получилось, то можешь зайти на свой сайт http://localhost:5000. если он не зашел то у тебя значит какая то ошибка. (Можно написать в Issues) 

Шаг 5: нужно создать админ панель, зайди в папку **services/admin** и снова открывай комадную строку, и пиши туда ```npm i```, снова установка модулей! потом не закрывай а пиши, ```npm run build```

 Шаг 6: надо запустить сам сайт где находится вся основа ревивала, зайди в папку **services/2016-roblox-main/docs/** и прочитай **get-started.md** это гайд по начального использования.

создай файл **config.json** в **services/2016-roblox-main** и туда напиши вот это:

```
{
  "serverRuntimeConfig": {
    "backend": {"csrfKey":"g0qiiDZw7jM2l54+7qsuRaymx6nBGdCKT9Kc0bqJB3aZ26rSsPMXfg8uWfUBtTqWenDVy+AQS1jkdrgvUwVSsw=="}
  },
  "publicRuntimeConfig": {
    "backend": {
      "proxyEnabled": true,
      "flags": {
        "myAccountPage2016Enabled": true,
        "catalogGenreFilterSupported": true,
        "catalogPageLimit": 28,
        "catalogSaleCountVisibleFromDetailsEndpoint": true,
        "commentsEndpointHasAreCommentsDisabledProp": true,
        "catalogDetailsPageResellerLimit": 10,
        "avatarPageInventoryLimit": 10,
        "friendsPageLimit": 25,
        "settingsPageThemeSelectorEnabled": true,
        "tradeWindowInventoryCollectibleLimit": 10,
        "moneyPagePromotionTabVisible": true,
        "gameGenreFilterSupported": true,
        "avatarPageOutfitCreatedAtAvailable": true,
        "catalogDetailsPageOwnersTabEnabled": true,
        "launchUsingEsURI": true
      },
      "baseUrl": "https://your.domain/",
      "apiFormat": "https://your.domain/apisite/{0}{1}"
    }
  }
}
```

 Если прочитал, то начнём дальше! открой комадную строку, ну думаю ты уже знаешь как, и напиши туда это: ```npm i``` потом ```npm run build``` а потом ```npm run start``` 

дальше надо запустить сайт, и зайти и создать аккаунт в http://localhost:5000/auth/application, Что нужно для создания аккаунта?

- Что бы твоему рб аккаунту было 1 год
- или 20к визитов или админ бейдж или 3 не бесплатных вещи от роблокса, 1к визитов на одном плейсе, или премиум, или 2 раза менял никнейм за робуксы.

  если нету всего из этого перечисленого то, найди файл по этому путю, **services/Roblox/Roblox.Services/Users/** и найди файл **ApplicationProcessorService.cs** потом на номере строчки **99**, надо поменять вместо true на **false**

  если твоя заявка была принята ботом, то создай аккаунт под именем ```ROBLOX``` и придумай сложный пароль, **ОБЯЗАТЕЛЬНО НИК ДОЛЖЕН БЫТЬ БОЛЬШИМИ БУКВАМИ!!**

  создал? тогда переходи по ссылке для открытия панели http://localhost:5000/admin, дальше надо создать несколько аккаунтов которые я написал!

перейди в админ панели во вкладку **Create player**, и создай аккаунт с **ID 2**, и никнейм должен быть **UGC** а потом, обнули пароль но кнопке **nullify password** у аккаунта UGC

дальше создай в той же папки аккаунт с любым айди который не занят (я брал айди 12), и поставь ник ```BadDecisions``` этот ник будет закидывать вещи того, кого аккаунт был удалён по GDPR 

сайт был сделан! теперь его надо настроить для онлайна!

Шаг 7: перейди в папку **services/AssetValidationServiceV2** и запусти комадную строку, запусти команду ```go run main.go```, он позволит выкладывать вещи!

Шаг 8: 	Редеринг! вещей и карт, и т.д, перейди в папку **services/RCCService** запусти комадную строку и введи команду, ```RCCService.exe -console -placeid:1818```.

Дальше иди в папку **services/game-server**, и создай файл с названием ```config.json```, дальше в него вставь это:

```
{
    "rcc": "rcc path here", -- если менять тут, то и в appsettings.json
    "authorization": "render auth here", -- если менять тут, то и в appsettings.json
    "baseUrl": "http://localhost:5000",
    "rccPort": 64989,
    "port": 3040,
    "websiteBotAuth": "bot auth here", -- если менять тут, то и в appsettings.json
    "thumbnailWebsocketPort": 3189,
    "dockerDisabled": true
}
```
почти всё, вернись в папку **services/game-server**, и открой комадную строку, и туда напиши эту команду ```npm i``` потом ```npm run build``` потом ```npm run start```

Если он в комадной строке напишет **[info] new connection** То всё прошло успешно)

можешь пользоватся как хочешь.

Скриншоты как это должно выглядить:

![{557BC8F3-3966-47AE-AC5B-1003C927583D}](https://github.com/user-attachments/assets/6a153d02-1c67-45c4-ab1a-86c36118acbe)


# Если есть ошибки((

Напиши мне ошибку в Issues я обязательно посмотрю и помогу.
