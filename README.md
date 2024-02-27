# PYTHON PROGRAMMING INTENSIVE WITH CHATGPT

 1. Введение в Python-разработку с помощью ChatGPT
 - Задача 1. Подсчет факториала заданного числа. Решение:
Промт  
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
 - Задача 2. Подсчет простых чисел. Решение:
Промт  
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
Промт
Задача Есть список a = [1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89]. Выведите все элементы, которые меньше 5. Напиши код на пайтоне для решения
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
Промт  
"Копируем задачу и добавляем "Напиши код на пайтоне для решения""
```python
a = [1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89]
b = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13]

# Используем генератор списка для создания списка общих элементов,
# причем преобразуем оба списка в множества для исключения повторений и более эффективного поиска
common_elements = [element for element in set(a) if element in set(b)]

print(common_elements)
```
 - Задача 4. 
Есть массив со словами, в котором есть хотя бы одно слово. Надо найти максимально длинное общее начало каждого слова. Если такого нет — вывести пустую строку. Решение:
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
   Промпт для создания Telegram-бота “напиши код для создания Telegram-бота на языке программирования Python с использованием библиотеки telebot, который сможет отвечать на простые вопросы привет","как дела?"”
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

 - Разработаешь более сложного Telegram-бота
 - Подключишь искусственный интеллект к программе
3. Модификация Telegram-бота
 - Подключишь искусственный интеллект к Telegram-боту
 - Добавишь в Telegram-бота возможность отвечать голосовыми сообщениями
