---
## Front matter
title: "Отчёт по лабораторной работе №4


Информационная безопасность"
subtitle: "Дискреционное разграничение прав в Linux. Расширенные атрибуты"
author: "Выполнила: Абакумова Олеся Максимовна, 


НКАбд-01-22, 1132220832"

## Generic otions
lang: ru-RU
toc-title: "Содержание"

## Bibliography
bibliography: bib/cite.bib
csl: pandoc/csl/gost-r-7-0-5-2008-numeric.csl

## Pdf output format
toc: true # Table of contents
toc-depth: 2
lof: true # List of figures
fontsize: 12pt
linestretch: 1.5
papersize: a4
documentclass: scrreprt
## I18n polyglossia
polyglossia-lang:
  name: russian
  options:
	- spelling=modern
	- babelshorthands=true
polyglossia-otherlangs:
  name: english
## I18n babel
babel-lang: russian
babel-otherlangs: english
## Fonts
mainfont: PT Serif
romanfont: PT Serif
sansfont: PT Sans
monofont: PT Mono
mainfontoptions: Ligatures=TeX
romanfontoptions: Ligatures=TeX
sansfontoptions: Ligatures=TeX,Scale=MatchLowercase
monofontoptions: Scale=MatchLowercase,Scale=0.9
## Biblatex
biblatex: true
biblio-style: "gost-numeric"
biblatexoptions:
  - parentracker=true
  - backend=biber
  - hyperref=auto
  - language=auto
  - autolang=other*
  - citestyle=gost-numeric
## Pandoc-crossref LaTeX customization
figureTitle: "Рис."
tableTitle: "Таблица"
listingTitle: "Листинг"
lofTitle: "Список иллюстраций"
lolTitle: "Листинги"
## Misc options
indent: true
header-includes:
  - \usepackage{indentfirst}
  - \usepackage{float} # keep figures where there are in the text
  - \floatplacement{figure}{H} # keep figures where there are in the text
---

# Цель работы

Получить практические навыки работы в консоли с расширенными атрибутами файлов

# Теоретическое введение

**Права доступа** определяют, какие действия конкретный пользователь может или не может совершать с определенным файлами и каталогами. С помощью разрешений можно создать надежную среду — такую, в которой никто не может поменять содержимое ваших документов или повредить системные файлы. [1]

**Расширенные атрибуты файлов Linux** — это поддерживаемая некоторыми файловыми системами возможность ассоциировать с файловыми объектами произвольные метаданные.

**Некоторые из них,использованные в ходе работы**

*Установить атрибуты:*

- chattr filename

*Значения:*

- chattr +a # только добавление. Удаление и переименование запрещено;

- chattr +i # неизменяемый файл


*Просмотреть атрибуты:*

- lsattr filename

*Опции:*

- lsattr -a # вывести все файлы (включая скрытые)


# Выполнение лабораторной работы

1. От имени пользователя guest определите расширенные атрибуты файла /home/guest/dir1/file1 командой
lsattr /home/guest/dir1/file1

![](images/1.jpg)

***Определение расширенных атрибуты файла /home/guest/dir1/file1 командой
lsattr /home/guest/dir1/file1***

2. Установите командой chmod 600 file1 на файл file1 права, разрешающие чтение и запись для владельца файла.

![](images/2.jpg)

***Команда chmod 600 file1***


3. Попробуйте установить на файл /home/guest/dir1/file1 расширенный атрибут a от имени пользователя guest:
chattr +a /home/guest/dir1/file1
В ответ вы должны получить отказ от выполнения операции.

![](images/3.jpg)

***chattr +a /home/guest/dir1/file1 расширенный атрибут***

4. Зайдите на третью консоль с правами администратора либо повысьте свои права с помощью команды su. Попробуйте установить расширенный атрибут a на файл /home/guest/dir1/file1 от имени суперпользователя:
chattr +a /home/guest/dir1/file1

![](images/4.jpg)

***Установка расширенного атрибута от имени суперпользователя***

5. От пользователя guest проверьте правильность установления атрибута: lsattr /home/guest/dir1/file1

![](images/5.jpg)

***Проверка правильности установки атрибута***


6. Выполните дозапись в файл file1 слова «test» командой
echo "test" /home/guest/dir1/file1
После этого выполните чтение файла file1 командой 
cat /home/guest/dir1/file1
Убедитесь, что слово test было успешно записано в file1.

![](images/6.jpg)

***дозапись в файл file1 слова «test» командой
echo "test" /home/guest/dir1/file1***

![](images/7.jpg)

***Чтение файла file1 командой 
cat /home/guest/dir1/file1***


7. Попробуйте удалить файл file1 либо стереть имеющуюся в нём информацию командой echo "abcd" > /home/guest/dirl/file1
Попробуйте переименовать файл.

![](images/8.jpg)

***echo "abcd" > /home/guest/dirl/file1(не удалось)***


8. Попробуйте с помощью команды chmod 000 file1
установить на файл file1 права, например, запрещающие чтение и запись для владельца файла. Удалось ли вам успешно выполнить указанные команды?

![](images/9.jpg)

***chmod 000 file1(Этого сделать не удалось.)***

9. Снимите расширенный атрибут a с файла /home/guest/dirl/file1 от имени суперпользователя командой
chattr -a /home/guest/dir1/file1
Повторите операции, которые вам ранее не удавалось выполнить. 

![](images/10.jpg)

***Успешно сняли атрибут(Теперь все операции выполняются.)***

10. Повторите ваши действия по шагам, заменив атрибут «a» атрибутом «i».
Удалось ли вам дозаписать информацию в файл? 

![](images/11.jpg)
***Повторяем все этапы,но только уже с атрибутом i(Дозаписать информацию в файл не удалось.)***

# Вывод

Были получены практические навыки работы в консоли с расширенными атрибутами файлов

# Список литературы. Библиография

[0] Методические материалы курса

[1] Права доступа: https://codechick.io/tutorials/unix-linux/unix-linux-permissions

[2] Расширенные атрибуты: https://ru.manpages.org/xattr/7

[3] Операции с расширенными атрибутами: https://p-n-z-8-8.livejournal.com/64493.html