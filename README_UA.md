# Початок розробки Discord-бота.

_!Замовити Discord-бота: (https://t.me/admirall_times)!_

![Untitled-1](https://github.com/AndreMuhamed/pogadon/assets/128980327/23b64a91-e2c1-47cf-aeae-144db6563c08)

***Щоб створити свого першого Discord-бота, потрібно виконати кілька кроків:***

*Крок 1: Створення нового Discord-бота і отримання токену бота.*
1. Перейдіть на сайт розробника Discord (https://discord.com/developers/applications).
2. Увійдіть в свій обліковий запис або створіть новий.
3. Натисніть кнопку "New Application" (Нова програма) і введіть назву свого бота.

4. Перейдіть на вкладку "Bot" (Бот) у меню зліва.
5. Натисніть кнопку "Add Bot" (Додати бота) і підтвердьте створення бота.
6. В розділі "Token" (Токен) натисніть кнопку "Copy" (Скопіювати) для збереження токена бота. Зверніть увагу, що цей токен повинен зберігатись у таємниці, і не може бути розміщений у відкритому коді або відправлений комусь іншому.

*Крок 2: Запрошення бота на свій сервер Discord.*
1. Поверніться на вкладку "General Information" (Загальна інформація) вашої програми.
2. Знайдіть ваш Client ID (ідентифікатор клієнта) і скопіюйте його.
3. Увійдіть на свій Discord-сервер і перейдіть до вкладки "OAuth2" у налаштуваннях сервера.
4. У розділі "OAuth2 URL Generator" (Генератор URL для OAuth2) виберіть опцію "bot".
5. Під опцією "Scopes" (Сфери) оберіть "bot".
6. Під опцією "Bot Permissions" (Права бота) виберіть необхідні права для свого бота (наприклад, "Read Messages", "Send Messages" тощо).
7. Скопіюйте згенерований URL-адресу OAuth2 і відкрийте його у веб-браузері.
8. Виберіть сервер, на який ви хочете запросити свого бота, і натисніть "Authorize" (Авторизувати).

*Крок 3: Написання коду для бота.*
Вам потрібно використовувати бібліотеку, яка надає зручний інтерфейс для роботи з API Discord. Наприклад, ви можете використовувати бібліотеку discord.py для Python.

Приклад коду для базового бота на discord.py:

```python
import discord
from discord.ext import commands

intents = discord.Intents.default()
intents.message_content = True

bot = commands.Bot(command_prefix='!', intents=intents)

@bot.event
async def on_ready():
    print(f'Logged in as {bot.user.name}')

@bot.event
async def on_message(message):
    if message.author.bot:
        return  # Ігнорувати повідомлення від ботів

    if message.content.lower().startswith('привіт'):
        await message.channel.send('Привіт! Я бот!')

    await bot.process_commands(message)

@bot.command(name='привіт')
async def say_hello(ctx):
    await ctx.send('Привіт! Я бот!')

bot.run('YOUR_BOT_TOKEN')
```

Вам також знадобиться встановити бібліотеку discord.py, якщо вона ще не встановлена, за допомогою команди `pip install discord.py`.

Після написання коду збережіть його в файлі з розширенням `.py`, наприклад `bot.py`.

*Крок 4: Запуск бота.*
Запустіть свого бота, виконавши файл `bot.py` з командного рядка або розмістивши його на хостинговому сервері. Коли бот буде запущений, ви побачите повідомлення "Logged in as..." у консолі.

# Тепер ваш Discord-бот повинен бути активний на сервері і готовий відповідати на команди і повідомлення!
