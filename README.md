# vimetop-guild-statements-manager
Бот-управляющий заявками в гильдию через внутреннее API VimeTop

## Как работает?
![gif-guide-1](https://cdn.discordapp.com/attachments/678992634387365908/852483250868846592/666121006211443.gif)

## Как запустить?
* Node.js скачивается здесь: https://nodejs.org/en/

1. Переименуй `config.example.json` в `config.json` и отредактируй под себя

* `vk.token` - токен от сообщества ВКонтакте (с правами на управление сообществом и сообщениями)
* `vk.group_id` - ID сообщества
* `vimetop.cookie` - требуемые для авторизации куки-данные от аккаунта **VimeTop**
* `vimetop.guild_id` - ID гильдии на VimeWorld. А откуда брать данные-то о заявках?
* `bot.allowed` - массив ID'шников людей, которые могут управлять ботом (самый первый ID является администратором и может управлять заявками)
* `bot.prefix` - желательно не менять (по-умолчанию стоит `/`), поскольку ВКонтакте разрешает ботам с таким префиксом просмотр сообщений без выдачи доступа к полной переписке

**Важно!** Куки-данные никуда не отсылаются, аккаунт не подвергается взлому, а самое главное, что перед вами исходный код, в котором не проблема найти что-либо.

![png-guide-2](https://i.imgur.com/If3ZTK8.png)

**Ещё кое-что!** Если нужно разрешить доступ к принятию/отклонению заявок всем тем, кто указан в `bot.allowed` - [эту строчку](https://github.com/vlfz/vimetop-guild-statements-manager/blob/master/index.js#L52) нужно заменить на это:
```js
if(command == "заявка" && config.bot.allowed.includes(messageAuthorID)) {
```

2. Установи нужные библиотеки командой `npm install` (если **yarn** - `yarn install`)
3. Запусти через `node index.js` (если **nodemon** - `nodemon index.js` | если **pm2** - `pm2 start index.js --name vt-bot`)

**Важно!** Бот тестировался на Node.js версии **12.6.0**. Версия ниже, вполне возможно, не поддерживается.
