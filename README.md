# PYTHON PROGRAMMING INTENSIVE WITH CHATGPT

 1. Введение в Python-разработку с помощью ChatGPT
 - Задача 1. Подсчет факториала заданного числа.  
Решение: Промт  
"Напиши программу на языке программирования Python, для нахождения факториала заданного числа"
```python
def factorial(n):
    # Базовый случай: факториал 0 или 1 равен 1
    if n == 0 or n == 1:
        return 1
    # Рекурсивный случай: n! = n * (n-1)!
    else:
        return n * factorial(n-1)

# Попробуем найти факториал числа 5
number = 5
print(f"Факториал числа {number} равен {factorial(number)}")
```
 - Задача 2. Подсчет простых чисел.  
Решение: Промт  
“Напиши код на языке программирования Python, который будет выводить в консоль первые 20 простых чисел”  
```python
def is_prime(n):
    """Проверка числа на простоту."""
    if n <= 1:
        return False
    for i in range(2, int(n**0.5) + 1):
        if n % i == 0:
            return False
    return True

def find_first_20_primes():
    """Вывод первых 20 простых чисел."""
    count = 0  # Счетчик найденных простых чисел
    number = 2  # Начальное число для проверки на простоту
    while count < 20:
        if is_prime(number):
            print(number, end=" ")
            count += 1
        number += 1

# Вызов функции для вывода первых 20 простых чисел
find_first_20_primes()
```
 - Задача 3. Есть список a = [1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89]. Выведите все элементы, которые меньше 5.  
Решение: Промт "Есть список a = [1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89]. Выведите все элементы, которые меньше 5. Напиши код на пайтоне для решения."
```python
# Заданный список
a = [1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89]
# Вывод элементов списка, которые меньше 5
for element in a:
    if element < 5:
        print(element)
```
- Задача 4.
Даны списки:
a = [1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89];
b = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13].
Нужно вернуть список, который состоит из элементов, общих для этих двух списков.   
Решение: Промт "Копируем задачу и добавляем "Напиши код на пайтоне для решения""
```python
a = [1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89]
b = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13]
# Используем генератор списка для создания списка общих элементов,
# причем преобразуем оба списка в множества для исключения повторений и более эффективного поиска
common_elements = [element for element in set(a) if element in set(b)]

print(common_elements)
```
 - Задача 4. 
Есть массив со словами, в котором есть хотя бы одно слово. Надо найти максимально длинное общее начало каждого слова. Если такого нет — вывести пустую строку.  
Решение:
```python
def longest_common_prefix(words):
    if not words:
        return ""
    # Начинаем с предположения, что самый длинный общий префикс - это первое слово
    prefix = words[0]
    for word in words[1:]:
        # Сокращаем префикс, пока он не станет общим для текущего слова
        while not word.startswith(prefix):
            prefix = prefix[:-1]
            # Если префикс стал пустой строкой, общего префикса нет
            if not prefix:
                return ""
    return prefix
# Пример массива слов
words = ["flower", "flow", "flight"]
print(longest_common_prefix(words))
```
2. Разработка Telegram-бота  
   Промт для создания Telegram-бота “напиши код для создания Telegram-бота на языке программирования Python с использованием библиотеки telebot, который сможет отвечать на простые вопросы "привет","как дела?"”  
Сперва ставим pyTelegramBotAPI, чтобы работать с библиотекой telebot  
```sh
pip install pyTelegramBotAPI
```
Дальше нужно будет создать бота в Telegram через BotFather и получить токен для вашего бота.
```python
import telebot

# Замените 'YOUR_BOT_TOKEN' на токен вашего бота, полученный от BotFather
TOKEN = 'YOUR_BOT_TOKEN'
bot = telebot.TeleBot(TOKEN)
@bot.message_handler(commands=['start', 'help'])
def send_welcome(message):
    bot.reply_to(message, "Привет! Как я могу помочь тебе?")
@bot.message_handler(func=lambda message: True)
def echo_all(message):
    text = message.text.lower()
    if "привет" in text:
        bot.reply_to(message, "Привет! Рад тебя видеть.")
    elif "как дела?" in text:
        bot.reply_to(message, "Все хорошо, спасибо! А у тебя?")
    else:
        bot.reply_to(message, "Извини, я не понимаю этот вопрос.")

# Запускаем бота
bot.polling()
```
* Поэтапно просим AI добавлять функции
1) /start - Начать общение с ботом /help - Получить список доступных команд
2) /caps - Преобразовать текст в заглавные буквы
3) /perevorot - Перевернуть отправленный текст
4) /remove_vowels - Удалить все гласные из сообщения

```python
import telebot

# Замените 'YOUR_TOKEN_HERE' на токен вашего бота
TOKEN = 'YOUR_TOKEN_HERE'
bot = telebot.TeleBot(TOKEN)
@bot.message_handler(commands=['start'])
def send_welcome(message):
    bot.reply_to(message, "Добро пожаловать! Я ваш помощник. Используйте команду /help, чтобы узнать, что я могу.")
@bot.message_handler(commands=['caps'])
def caps(message):
    text_caps = message.text[len('/caps '):].upper()
    if not text_caps:
        bot.reply_to(message, "Пожалуйста, отправьте текст после команды /caps.")
    else:
        bot.reply_to(message, text_caps)
@bot.message_handler(commands=['help'])
def send_help(message):
    help_text = ("Список доступных команд:\n"
                 "/start - Начать общение с ботом\n"
                 "/help - Получить список доступных команд\n"
                 "/caps - Преобразовать текст в заглавные буквы\n"
                 "/perevorot - Перевернуть отправленный текст\n"
                 "/remove_vowels - Удалить все гласные из сообщения\n")
    bot.reply_to(message, help_text)
@bot.message_handler(commands=['perevorot'])
def reverse_text(message):
    text_to_reverse = message.text[len('/perevorot '):]
    if not text_to_reverse:
        bot.reply_to(message, "Пожалуйста, отправьте текст после команды /perevorot.")
    else:
        reversed_text = text_to_reverse[::-1]
        bot.reply_to(message, reversed_text)
@bot.message_handler(commands=['remove_vowels'])
def remove_vowels(message):
    text_to_process = message.text[len('/remove_vowels '):]
    if not text_to_process:
        bot.reply_to(message, "Пожалуйста, отправьте текст после команды /remove_vowels.")
    else:
        vowels = 'aeiouAEIOUаеёиоуыэюяАЕЁИОУЫЭЮЯ' # Для поддержки и английского, и русского алфавитов
        no_vowels_text = ''.join([letter for letter in text_to_process if letter not in vowels])
        bot.reply_to(message, no_vowels_text)

# Запуск бота
bot.polling()
```
<p align="right"> <img width="680" alt="image" src="https://github.com/W1ckedS1ck/ChatGPT_Prompting/assets/61629889/03776d59-e1ab-463f-b5be-47eafc81d67f"> <p>

 - Подключишь искусственный интеллект к программе  
Сперва используем документацию https://proxyapi.ru/docs
Промт Это часть кода на языке программирования Python для подключения к нейросети, возьми код за основу и дополни его так, чтобы с нейросетью можно было общаться через консоль и отправлять ей запросы и получать ответы
```
from openai import OpenAI
client = OpenAI(
    api_key="{PROXY_API_KEY}",
    base_url="https://api.proxyapi.ru/openai/v1",
)
chat_completion = client.chat.completions.create(
    model="gpt-3.5-turbo", messages=[{"role": "user", "content": "Hello world"}]
)
```
```python
from openai import OpenAI
# Определяем ключ API и базовый URL
api_key = "sk-"
base_url = "https://api.proxyapi.ru/openai/v1"
# Инициализируем клиента OpenAI
client = OpenAI(api_key=api_key, base_url=base_url)
# Функция для общения с нейросетью
def chat_with_ai():
    # История сообщений в чате
    messages = []
    print("Чтобы закончить чат, введите 'выход'")
    while True:
        # Получаем ввод пользователя
        user_input = input("Вы: ")
        # Проверяем, хочет ли пользователь выйти
        if user_input.lower() == 'выход':
            print("Чат завершен.")
            break
        # Добавляем ввод пользователя в историю сообщений
        messages.append({"role": "user", "content": user_input})
        try:
            # Создаем запрос к нейросети
            chat_completion = client.chat.completions.create(
                model="gpt-3.5-turbo-1106", messages=messages
            )
            # Получаем и выводим ответ нейросети
            ai_response = chat_completion.choices[0].message.content
            print(f"AI: {ai_response}")
            # Добавляем ответ нейросети в историю сообщений
            messages.append({"role": "assistant", "content": ai_response})
        except Exception as e:
            print(f"Произошла ошибка: {e}")
            break

# Запускаем функцию для общения
chat_with_ai()
```
3. Модификация Telegram-бот  
 - Подключишь искусственный интеллект к Telegram-боту  
Промт: "Возьми данный код за основу и дополни его так, чтобы получился Telegram-бот, который может отвечать на любые сообщения с помощью нейронной сети. Используй библиотеку telebot"
```python
from telebot import TeleBot
from telebot.types import Message
from openai import OpenAI

# Определяем ключ API и базовый URL
api_key = "sk-"
base_url = "https://api.proxyapi.ru/openai/v1"
# Инициализируем клиента OpenAI
client = OpenAI(api_key=api_key, base_url=base_url)
bot = TeleBot("7024038282:AAGU_EO3dwJk-*")
@bot.message_handler(func=lambda message: True)
def reply_to_message(message: Message):
    # История сообщений в чате
    messages = []
    # Получаем ввод пользователя
    user_input = message.text
    # Добавляем ввод пользователя в историю сообщений
    messages.append({"role": "user", "content": user_input})
    try:
        # Создаем запрос к нейросети
        chat_completion = client.chat.completions.create(
            model="gpt-3.5-turbo-1106", messages=messages
        )
        # Получаем и выводим ответ нейросети
        ai_response = chat_completion.choices[0].message.content
        bot.reply_to(message, f"AI: {ai_response}")
        # Добавляем ответ нейросети в историю сообщений
        messages.append({"role": "system", "content": "отвечай в стиле веселого клоуна"})
    except Exception as e:
        bot.reply_to(message, f"Произошла ошибка: {e}")
bot.polling()
```
<p align="right"> <img width="669" alt="image" src="https://github.com/W1ckedS1ck/ChatGPT_Prompting/assets/61629889/879ddbb6-4ab5-47f4-8b1d-939cba679858"> </p>
 - Добавишь в Telegram-бота возможность отвечать голосовыми сообщениями

Промт: "Напиши программу для создания Telegram-бота с использованием языка программирования Python и библиотеки telebot, который будет озвучивать любые сообщения, которые мы ему отправим"
```bash
pip install gTTs
```

```python
from telebot import TeleBot
from telebot.types import Message
from openai import OpenAI
from gtts import gTTS
import os

# Определяем ключ API и базовый URL
api_key = "sk-ocZsDK2UM23MfVob1ncrgijjrEytVdeU"
base_url = "https://api.proxyapi.ru/openai/v1"
# Инициализируем клиента OpenAI
client = OpenAI(api_key=api_key, base_url=base_url)
bot = TeleBot("7024038282:AAGU_EO3dwJk-csa7KoiIcSV-6pgdSLmYmA")
# Устанавливаем желаемую скорость озвучки
speed = 4  # Значение от 0.1 до 1.0

@bot.message_handler(func=lambda message: True)
def reply_to_message(message: Message):
    # История сообщений в чате
    messages = []
    # Получаем ввод пользователя
    user_input = message.text
    # Добавляем ввод пользователя в историю сообщений
    messages.append({"role": "user", "content": user_input})
    try:
        # Создаем запрос к нейросети
        chat_completion = client.chat.completions.create(
            model="gpt-3.5-turbo-1106", messages=messages
        )
        # Получаем и выводим ответ нейросети
        ai_response = chat_completion.choices[0].message.content
        bot.reply_to(message, f"AI: {ai_response}")
        # Преобразуем текст ответа в голосовой файл
        tts = gTTS(text=ai_response, lang='ru')
        tts.speed = speed  # Задаем скорость озвучки
        tts.save("response.mp3")
        audio = open("response.mp3", "rb")
        # Отправляем голосовое сообщение пользователю
        bot.send_voice(message.chat.id, audio)
        # Удаляем временный файл
        os.remove("response.mp3")
        # Добавляем ответ нейросети в историю сообщений
        messages.append({"role": "system", "content": "отвечай в стиле веселого клоуна"})
    except Exception as e:
        bot.reply_to(message, f"Произошла ошибка: {e}")

bot.polling()
```
