# Домашнее задание День1
- Реши задачи с помощью нейросети: 
1. При заданном целом числе n посчитайте n + nn + nnn.
```python
# Ввод целого числа n
n = int(input("Введите число n: "))
# Преобразование числа n в строку для дальнейшей конкатенации
str_n = str(n)
# Формирование чисел nn и nnn путем конкатенации строк
nn = int(str_n + str_n)
nnn = int(str_n + str_n + str_n)
# Вычисление результата
result = n + nn + nnn
# Вывод результата
print(f"Результат вычисления n + nn + nnn: {result}")
```
<p align="right"> <img width="346" alt="image" src="https://github.com/W1ckedS1ck/ChatGPT_Prompting/assets/61629889/1a461e34-37ac-4d7d-a996-fb43ee68c65b"> </p>

2. Напишите программу, которая выводит чётные числа из заданного списка и останавливается, если встречает число 237.
```python   
# Запрос ввода чисел от пользователя, разделенных пробелом
user_input = input("Введите числа через пробел и нажмите Enter: ")
# Преобразование строки введенной пользователем в список чисел
numbers = [int(number) for number in user_input.split()]
# Цикл для перебора элементов списка
for number in numbers:
    # Проверка на четность числа
    if number % 2 == 0:
        print(number)
    # Если встретится число 237, цикл прервется
    if number == 237:
        break
```
<p align="right"> <img width="580" alt="image" src="https://github.com/W1ckedS1ck/ChatGPT_Prompting/assets/61629889/71fc193f-fad3-4f87-97e5-e59fa4eca898"> </p>

3. Найдите наименьшую обыкновенную дробь, равную вещественному числу 14.375, и выведите ее на экран в формате '14.375 = числитель/знаменатель'
```python
from fractions import Fraction

# Заданное вещественное число
float_number = 14.375

# Преобразование вещественного числа в обыкновенную дробь
fraction = Fraction(float_number).limit_denominator()

# Вывод результата
print(f"{float_number} = {fraction.numerator}/{fraction.denominator}")
```
<p align="right"> <img width="225" alt="image" src="https://github.com/W1ckedS1ck/ChatGPT_Prompting/assets/61629889/888881f5-6a55-4946-9ff0-37e16c2f4cc3"> </p>

4. Сделайте так, чтобы число секунд отображалось в виде дни:часы:минуты:секунды.
```python
# Запрашиваем у пользователя количество секунд
total_seconds = int(input("Введите число секунд: "))

# Вычисляем количество дней, часов, минут и секунд
days = total_seconds // (24 * 3600) # Количество секунд в одном дне - 24*3600
remaining_seconds = total_seconds % (24 * 3600)
hours = remaining_seconds // 3600
remaining_seconds %= 3600
minutes = remaining_seconds // 60
seconds = remaining_seconds % 60

# Выводим результат
print(f"Дни:Часы:Минуты:Секунды = {days}:{hours}:{minutes}:{seconds}")
```
<p align="right"> <img width="301" alt="image" src="https://github.com/W1ckedS1ck/ChatGPT_Prompting/assets/61629889/6f5b3df0-f869-4c7f-82fd-e73e91eab6bd"> </p>

5. Напишите программу, которая принимает на вход целое число и определяет, является ли оно четным или нечетным.
```python
# Запрос числа у пользователя
num = int(input("Введите целое число: "))

# Проверка числа на четность/нечетность
if num % 2 == 0:
    print(f"Число {num} является четным.")
else:
    print(f"Число {num} является нечетным.")
```
<p align="right"> <img width="224" alt="image" src="https://github.com/W1ckedS1ck/ChatGPT_Prompting/assets/61629889/ffb7383a-0919-40cc-b916-d31095874d27"> </p>

6. Создайте простой калькулятор, который позволяет пользователю вводить два числа и выполнять над ними основные арифметические операции (сложение, вычитание, умножение, деление).
```python
# Функция для сложения
def add(x, y):
    return x + y
# Функция для вычитания
def subtract(x, y):
    return x - y
# Функция для умножения
def multiply(x, y):
    return x * y
# Функция для деления
def divide(x, y):
    if y == 0:
        return "Ошибка: Деление на ноль!"
    else:
        return x / y
# Главная программа
print("Выберите операцию:")
print("1. Сложение")
print("2. Вычитание")
print("3. Умножение")
print("4. Деление")
while True:
    # Ввод пользователем выбора операции
    choice = input("Введите номер операции (1/2/3/4): ")
    # Проверка ввода
    if choice in ('1', '2', '3', '4'):
        num1 = float(input("Введите первое число: "))
        num2 = float(input("Введите второе число: "))
        if choice == '1':
            print(num1, "+", num2, "=", add(num1, num2))
        elif choice == '2':
            print(num1, "-", num2, "=", subtract(num1, num2))
        elif choice == '3':
            print(num1, "*", num2, "=", multiply(num1, num2))
        elif choice == '4':
            result = divide(num1, num2)
            print(num1, "/", num2, "=", result)
        # После выполнения одной операции спросить пользователя, хочет ли он продолжить
        another_operation = input("Хотите выполнить ещё одну операцию? (да/нет): ")
        if another_operation.lower() != 'да':
            break
    else:
        print("Неверный ввод. Пожалуйста, введите номер операции из предложенного списка.")
```
<p align="right"> <img width="409" alt="image" src="https://github.com/W1ckedS1ck/ChatGPT_Prompting/assets/61629889/c8e7c15b-5d4a-4cc6-bb56-7c87ded77822"> </p>

7. Напишите программу, которая принимает на вход температуру в градусах Цельсия и переводит ее в градусы Фаренгейта или наоборот, в зависимости от выбора пользователя.
```python
def celsius_to_fahrenheit(celsius):
    return (celsius * 9/5) + 32

def fahrenheit_to_celsius(fahrenheit):
    return (fahrenheit - 32) * 5/9

print("Какую конвертацию вы хотите выполнить?")
print("1. Цельсий в Фаренгейт")
print("2. Фаренгейт в Цельсий")
choice = input("Выберите 1 или 2: ")

if choice == '1':
    celsius = float(input("Введите температуру в градусах Цельсия: "))
    fahrenheit = celsius_to_fahrenheit(celsius)
    print(f"{celsius} градусов Цельсия равно {fahrenheit:.2f} градусов Фаренгейта.")
elif choice == '2':
    fahrenheit = float(input("Введите температуру в градусах Фаренгейта: "))
    celsius = fahrenheit_to_celsius(fahrenheit)
    print(f"{fahrenheit} градусов Фаренгейта равно {celsius:.2f} градусов Цельсия.")
else:
    print("Неверный выбор. Пожалуйста, введите 1 или 2.")
```
<p align="right"> <img width="453" alt="image" src="https://github.com/W1ckedS1ck/ChatGPT_Prompting/assets/61629889/3052730a-7663-4e94-b79b-43f11a30715e"> </p>

8. Создайте программу, которая генерирует случайное число в определенном диапазоне и выводит его на экран.
```python
import random

# Предлагаем пользователю ввести диапазон
min_value = int(input("Введите минимальное значение диапазона: "))
max_value = int(input("Введите максимальное значение диапазона: "))

# Проверяем, что минимальное значение меньше максимального
while min_value >= max_value:
    print("Ошибка: минимальное значение должно быть меньше максимального.")
    min_value = int(input("Введите минимальное значение диапазона: "))
    max_value = int(input("Введите максимальное значение диапазона: "))

# Генерация случайного числа
random_number = random.randint(min_value, max_value)

# Выводим результат
print(f"Случайное число в диапазоне от {min_value} до {max_value}: {random_number}")
```
<p align="right"> <img width="505" alt="image" src="https://github.com/W1ckedS1ck/ChatGPT_Prompting/assets/61629889/807f9181-9dfb-4cd9-839f-6572812db8f5"> </p>
