# МІНІСТЕРСТВО ОСВІТИ І НАУКИ УКРАЇНИ  
## КИЇВСЬКИЙ ФАХОВИЙ КОЛЕДЖ ЗВ’ЯЗКУ  

---

# ЗВІТ  
## про виконання лабораторної роботи №7
### з дисципліни «Операційні системи»

---

**Тема:**  
Створення скриптових сценаріїв та визначення апаратної конфігурації системи

---

**Виконала:**  
студентка групи **БІКС-33**  
**Сербіна Ярослава Вячеславівна**

---

**Перевірила:**  
**Сушанова Вікторія Сергіївна**

---

**Київ - 2026**

---

# Лабораторна робота №7
## Операційні системи

---

## Тема
Створення скриптових сценаріїв та визначення апаратної конфігурації системи

---

## Мета роботи
1. Отримання практичних навиків роботи з командною оболонкою Bash.
2. Знайомство знайомство з базовими діями при роботі зі скриптовими сценаріями.


---

## Матеріальне забезпечення занять:
1. ЕОМ типу IBM PC.  
2. ОС сімейства Windows та віртуальна машина VirtualBox (Oracle).  
3. ОС GNU/Linux (будь-який дистрибутив).  
4. Сайт мережевої академії Cisco netacad.com та його онлайн курси по Linux.

---

## Завдання для попередньої підготовки
### Glossary of Basic English Terms

**Shell - a command-line interface that allows users to interact with the operating system.**

**Shell script - a file that contains a sequence of commands executed automatically by the shell.**

**Command - an instruction given to the system to perform a specific operation.**

**Terminal - a program used to access and work with the command-line interface.**

**Interpreter - a program that reads and executes commands from a script (e.g., Bash).**

**Shebang (#!) - the first line in a script that specifies which interpreter should execute the script.**

**Executable file - a file that has permission to be run as a program.**

**Permission - rules that determine who can read, write, or execute a file.**

**chmod - a command used to change file permissions in Linux.**

**Text editor - a program used to create and edit text files.**

**nano - a simple command-line text editor used for editing scripts.**

**echo - a command used to display text or messages in the terminal.**

**Variable - a named storage location used to hold data in a script.**

**Environment variable - a variable that stores system-wide information (e.g., $USER).**

**Command substitution - a method of inserting the output of one command into another (e.g., $(date)).**

**uname - a command that displays information about the system.**

**date - a command that shows the current date and time.**

**lscpu - a command that provides detailed information about the CPU.**

**free - a command that displays information about system memory (RAM).**

**lsblk - a command that lists information about storage devices.**

**Conditional statement - a control structure that allows execution of commands based on conditions (if, else).**

**Loop - a structure that repeats a set of commands multiple times.**

**Input (read) - a command that allows the user to enter data into a script.**

**CPU (Central Processing Unit) - the main processor responsible for executing instructions.**

**RAM (Random Access Memory) - temporary memory used to store data during program execution.**

**Storage device - hardware used to store data permanently (e.g., hard drive, SSD).**

**Hardware configuration - information about the physical components of a computer system.**

## Відповіді на теоретичні питання

### 1. Що таке скриптовий сценарій у командній оболонці

Скриптовий сценарій - це текстовий файл, який містить послідовність команд, що виконуються автоматично командною оболонкою (наприклад, Bash).

Він використовується для:
- автоматизації повторюваних дій;
- спрощення роботи користувача;
- об’єднання кількох команд в одну.

Скрипти дозволяють додавати логіку (умови, цикли, змінні) та керувати виконанням команд.

### 2. Як створюються, редагуються та запускаються скрипти

Скрипти створюються за допомогою текстових редакторів, наприклад nano або vim.

Основні кроки:

1. Створення файлу:
```bash
nano script.sh
```

2. Додавання команд у файл:
```bash
#!/bin/bash
echo "Hello, World!"
```
3. Збереження файлу (Ctrl + X → Y → Enter)
   
4. Надання прав на виконання:
```bash
chmod +x script.sh
```

5. Запуск скрипта:
```bash
./script.sh
```

### 3. Основні компоненти материнської плати

Материнська плата - це головна плата комп’ютера, яка з’єднує всі його компоненти.

Основні складові:
- CPU (процесор) - виконує обчислення;
- RAM (оперативна пам’ять) - зберігає тимчасові дані;
- чипсет - керує взаємодією компонентів;
- слоти розширення (PCI, PCIe) - для підключення відеокарт та інших пристроїв;
- роз’єми для накопичувачів (SATA, NVMe);
- BIOS/UEFI - базова система керування;
- порти вводу/виводу (USB, HDMI тощо).

### 4. Для яких пристроїв використовуються MBR та GPT

MBR і GPT - це способи розмітки дисків.

Використовуються для:
- жорстких дисків (HDD);
- твердотільних накопичувачів (SSD).

Особливості:
- MBR - старіший стандарт, підтримує до 2 ТБ і максимум 4 розділи;
- GPT - сучасний стандарт, підтримує великі диски і багато розділів, використовується разом з UEFI.

### 5. Суть операції монтування

Монтування - це процес підключення файлової системи пристрою до операційної системи.

Це потрібно для:
- доступу до файлів на диску або флешці;
- роботи з каталогами пристрою;
- інтеграції зовнішніх носіїв у файлову систему Linux.

Без монтування операційна система не може працювати з даними на пристрої.

## Хід роботи
### 1.1 Запуск операційної системи

Для виконання лабораторної роботи було запущено віртуальну машину VM2_Linux_CLI у середовищі VirtualBox. Після запуску відбулося завантаження операційної системи Linux Ubuntu в режимі командного рядка (CLI)

### 1. Опрацювання команд Lab 11 - Basic Scripting

| Назва команди | Її призначення та функціональність |
|---|---|
| vi myfile / vi sample.sh | Команда **vi** використовується для створення та редагування текстових файлів (скриптів). |
| i / I / a / A / o / O | Команди переходу в режим вставки (insert mode) у різних позиціях рядка. |
| ESC | Вихід з режиму вставки у командний режим. |
| :w | Зберігає файл. |
| :q! | Вихід без збереження змін. |
| :wq / :x / ZZ | Збереження файлу та вихід з редактора. |
| h / j / k / l | Переміщення курсора (вліво, вниз, вгору, вправо). |
| w / e / b | Навігація по словах (вперед, кінець слова, назад). |
| 0 / $ | Перехід на початок або кінець рядка. |
| G / nG (1G, 3G, 2G) | Перехід до певного рядка або кінця файлу. |
| dw / 2dw | Видалення одного або кількох слів. |
| x / X / 14x / 5X | Видалення символів праворуч або ліворуч. |
| dd / 2dd | Видалення одного або кількох рядків. |
| D / d$ | Видалення тексту від курсора до кінця рядка. |
| u / 4u | Скасування останніх дій (undo). |
| p / P | Вставка (paste) тексту після або перед курсором. |
| yw | Копіювання (yank) слова. |
| J / 3J | Об’єднання рядків. |
| /word / ?word | Пошук слова вперед або назад у файлі. |
| n | Перехід до наступного/попереднього результату пошуку. |
| cw | Заміна слова та перехід у режим вставки. |
| ~ | Зміна регістру символу. |
| :%s/text //g | Пошук і видалення слова у всьому файлі. |
| echo | Виведення тексту у термінал. |
| cal | Відображення календаря. |
| date +%A | Виведення поточного дня тижня. |
| `команда` / $(команда) | Підстановка результату команди в іншу команду. |
| #!/bin/bash | Вказує, що скрипт виконується інтерпретатором Bash. |
| bash script.sh | Запуск скрипта через Bash. |
| chmod a+x script.sh | Надання прав на виконання файлу. |
| ./script.sh | Запуск скрипта з поточної директорії. |
| ls -l | Відображає детальну інформацію про файли. |
| cat файл | Виводить вміст файлу. |
| echo $PATH | Показує змінну середовища PATH. |
| mkdir bin | Створення директорії. |
| mv файл каталог | Переміщення файлу в іншу директорію. |
| test | Команда для перевірки умов (порівняння значень). |
| read змінна | Зчитування введених користувачем даних. |
| if [ умова ] | Умовний оператор для виконання дій за умовою. |
| then / else / fi | Ключові слова для побудови умовного блоку. |
| grep | Пошук тексту у файлі. |
| > /dev/null | Приховування виводу команди. |
| while [ умова ] | Цикл, що виконується поки умова істинна. |
| do / done | Початок і кінець циклу. |
| for змінна in список | Цикл для перебору значень. |
| wc файл | Підрахунок рядків, слів і символів у файлі. |
| seq 1 12 | Генерація послідовності чисел. |
| touch файл | Створення порожнього файлу. |

### 2. Опрацювання команд Lab 12 - Understanding Computer Hardware

| Назва команди | Її призначення та функціональність |
|---|---|
| lscpu | Відображає детальну інформацію про процесор (архітектура, ядра, частота, кеш тощо). |
| head -n 20 /proc/cpuinfo | Виводить перші 20 рядків файлу **/proc/cpuinfo**, який містить детальну інформацію про CPU та його характеристики. |
| free -m | Показує використання оперативної пам’яті (RAM) у мегабайтах. |
| free -g | Показує використання оперативної пам’яті (RAM) у гігабайтах. |
| lspci | Відображає список пристроїв, підключених до PCI-шини. |
| lspci -k | Показує пристрої PCI разом із драйверами ядра, які їх обслуговують. |
| lsusb | Відображає список підключених USB-пристроїв. |
| lsmod | Показує список завантажених модулів ядра Linux. |
| fdisk -l | Виводить інформацію про диски та їх розділи (partition table) у неінтерактивному режимі. |
| /proc/cpuinfo | Системний файл, що містить детальну інформацію про процесор. |

### 3. Створення скриптових сценаріїв з виводом текстових повідомлень для користувача

#### Сценарій 1: Виведення привітання для користувача

У цьому завданні було створено скриптовий сценарій, який виводить привітання для поточного користувача, поточну дату та базову інформацію про систему.

**Хід виконання**

Створення нового файлу скрипта:
```bash
nano greeting.sh
```

<img width="872" height="565" alt="image" src="https://github.com/user-attachments/assets/1b43a640-c358-4ed0-b7c5-8c334c903afe" />

Скрін 1: відкритий редактор nano з назвою файлу greeting.sh

Додавання коду у файл:
```bash
#!/bin/bash

echo "Hello, $USER!"
echo "Today is: $(date)"
echo "System information:"
uname -a
```

<img width="337" height="164" alt="image" src="https://github.com/user-attachments/assets/4b87e920-75b0-41a2-a7e9-1e57ff9f451d" />

Скрін 2: код скрипта у редакторі nano

Збереження файлу:
```bash
Ctrl + O → Enter

Ctrl + X
```

Надання прав на виконання:
```bash
chmod +x greeting.sh
```

<img width="754" height="49" alt="image" src="https://github.com/user-attachments/assets/bb742868-6f4b-46a7-a80c-860e924892b9" />

Скрін 3: команда chmod у терміналі

Запуск скрипта:
```bash
./greeting.sh
```

<img width="1206" height="249" alt="image" src="https://github.com/user-attachments/assets/8924f886-aa18-451d-9363-cf0eda59ac7a" />

Скрін 4: результат виконання скрипта

Пояснення коду
- #!/bin/bash - вказує, що скрипт виконується у оболонці Bash
- echo "Hello, $USER!" - виводить привітання з ім’ям користувача
- $(date) - підставляє поточну дату і час
- uname -a - виводить інформацію про систему (ОС, ядро, архітектура)
  
#### Сценарій 2: Виведення інформації про апаратну конфігурацію системи

У цьому завданні було створено скриптовий сценарій, який виводить основну інформацію про апаратну конфігурацію поточної системи. Для цього були використані команди, розглянуті в Lab 12: Understanding Computer Hardware.

**Хід виконання**

Створення нового файлу скрипта:
```bash
nano hardware.sh
```

<img width="511" height="38" alt="image" src="https://github.com/user-attachments/assets/817b66a1-d41a-4ea1-aa75-33df4c427931" />

Скрін 1: відкритий редактор nano з назвою файлу hardware.sh

Додавання коду у файл:
```bash
#!/bin/bash

echo "===== HARDWARE INFORMATION ====="

echo ""
echo "CPU INFORMATION:"
lscpu

echo ""
echo "MEMORY INFORMATION:"
free -h

echo ""
echo "PCI DEVICES:"
lspci

echo ""
echo "USB DEVICES:"
lsusb

echo ""
echo "DISK INFORMATION:"
sudo fdisk -l
```

<img width="881" height="623" alt="image" src="https://github.com/user-attachments/assets/3d58ef8a-4bb5-48ec-86ce-ef36d0f7065c" />

Скрін 2: код скрипта у редакторі nano

Збереження файлу:
```bash
Ctrl + O → Enter

Ctrl + X
```

Надання прав на виконання:
```bash
chmod +x hardware.sh
```

<img width="501" height="36" alt="image" src="https://github.com/user-attachments/assets/6abcfb4c-343f-48d2-97cf-99b9036b9eac" />

Скрін 3: команда chmod +x hardware.sh у терміналі

Запуск скрипта:
```bash
./hardware.sh
```
Оскільки команда fdisk -l потребує прав адміністратора, під час виконання скрипта вводиться пароль користувача.

<img width="892" height="610" alt="image" src="https://github.com/user-attachments/assets/397f282b-fea7-4cc5-a4a9-72812e8ac40b" />

Скрін 4: початок виконання скрипта

<img width="860" height="611" alt="image" src="https://github.com/user-attachments/assets/10926268-a09c-4c04-b94c-35b6ad210f0e" />

Скрін 5: виведення інформації про процесор і пам’ять

<img width="875" height="618" alt="image" src="https://github.com/user-attachments/assets/3e42eea6-42df-4520-b256-238b43a5231e" />
<img width="873" height="619" alt="image" src="https://github.com/user-attachments/assets/61885d67-7fbb-497d-8a9f-66ca68e91317" />

Скрін 6: виведення інформації про PCI- та USB-пристрої

<img width="880" height="596" alt="image" src="https://github.com/user-attachments/assets/cecd588c-a445-4323-878c-1006a4dab066" />

Скрін 7: виведення інформації про диски та розділи

Пояснення коду
- #!/bin/bash - вказує, що файл є Bash-скриптом
- echo "===== HARDWARE INFORMATION =====" - виводить заголовок сценарію
- lscpu - відображає інформацію про процесор
- free -h - показує використання оперативної пам’яті у зручному форматі
- lspci - виводить список пристроїв, підключених до PCI-шини
- lsusb - показує USB-пристрої, підключені до системи
- sudo fdisk -l - відображає інформацію про диски та їхні розділи
