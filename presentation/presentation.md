---
marp: true
backgroundColor: blue
---
<!-- backgroundColor: lightblue -->

<style>
 h1{
    font-size:60px;
    color:black
    text-align: center;
}

 h2{
    font-size: 40px;
    color: blue
    text-align: center;
}

 h3{
    font-size: 20px;
    color: black
    text-align: center;
}

</style>

# Лабораторная работа №3.
##  Дискреционное разграничение прав в Linux. Два пользователя
### Абакумова О.М., НКАбд-01-22

---

<style>
 h1{
    font-size:60px;
    color:black
    text-align: center;
}

 h2{
    font-size: 40px;
    color: blue
    text-align: center;
}

</style>

# Цель работы
## Получить практические навыки работы в консоли с атрибутами файлов для групп пользователей
---

<style>
 h1{
    font-size:60px;
    color:black
    text-align: center;
}

 h2{
    font-size: 40px;
    color: blue
    text-align: center;
}

</style>

# Задание
## Поэтапно выполнить все пункты лабораторной работы(15)

---

<style>
 h1{
    font-size:60px;
    color:black
    text-align: center;
}

 h2{
    font-size: 40px;
    color: blue
    text-align: center;
}

</style>

# Теоретическое введение

Права доступа определяют, какие действия конкретный пользователь может или не может совершать с определенными файлами и каталогами. С помощью разрешений можно создать безопасную среду, где защищены ваши документы и системные файлы.

В Linux существует несколько групп пользователей помимо стандартных root и users. Некоторые из них включают:

- daemon: запускает сервисы, требующие запись на диск.
- sys: предоставляет доступ к исходникам ядра и файлам include.
- sync: позволяет выполнить команду /bin/sync.
- games: разрешает играм записывать файлы настроек в определенную папку.
- man: добавляет страницы в директорию /var/cache/man.
- lp: использует устройства параллельных портов.
- mail: записывает данные в почтовые ящики /var/mail/.
- proxy: используется прокси-серверами без доступа к записи файлов на диск.
- www-data: запускает веб-сервер с доступом на запись /var/www для файлов веб-документов.
- и другие.

Каждая группа предоставляет определенные привилегии пользователям, регулируя их доступ к различным ресурсам системы.

---

<style>
 h1{
    font-size:60px;
    color:black
    text-align: center;
}

 h2{
    font-size: 40px;
    color: blue
    text-align: center;
}

</style>

# Выполнение лабораторной работы
 1. В установленной операционной системе создайте учётную запись поль-
зователя guest (использую учётную запись администратора):
useradd guest
2. Задайте пароль для пользователя guest (использую учётную запись ад-
министратора):
passwd guest
3. Аналогично создайте второго пользователя guest2.
4. Добавьте пользователя guest2 в группу guest:
gpasswd -a guest2 guest
5. Осуществите вход в систему от двух пользователей на двух разных кон-
солях: guest на первой консоли и guest2 на второй консоли.
6. Для обоих пользователей командой pwd определите директорию, в кото-
рой вы находитесь. Сравните её с приглашениями командной строки.
7. Уточните имя вашего пользователя, его группу, кто входит в неё
и к каким группам принадлежит он сам. Определите командами
groups guest и groups guest2, в какие группы входят пользовате-
ли guest и guest2. Сравните вывод команды groups с выводом команд
id -Gn и id -G.
8. Сравните полученную информацию с содержимым файла /etc/group.
Просмотрите файл командой
cat /etc/group
9. От имени пользователя guest2 выполните регистрацию пользователя
guest2 в группе guest командой
newgrp guest
10. От имени пользователя guest измените права директории /home/guest,
разрешив все действия для пользователей группы:
chmod g+rwx /home/guest
11. От имени пользователя guest снимите с директории /home/guest/dir1
все атрибуты командой
chmod 000 dirl

---

## 1. В установленной операционной системе создайте учётную запись пользователя guest2 (используя учётную запись администратора)+2.Задайте пароль для пользователя guest2
   

(guest был создан в предыдущей лабораторной.)

![](lab3/images/1.png)

Создание пользователя guest2 и пароля

---

<style>
 h1{
    font-size:60px;
    color:black
    text-align: center;
}


</style>

# 2. Добавьте пользователя guest2 в группу guest


![](lab3/images/2.png)
Добавление пользователя guest2 в группу guest

---

<style>
 h1{
    font-size:60px;
    color:black
    text-align: center;
}


</style>

# 3. Осуществите вход в систему от двух пользователей на двух разных консолях: guest на первой консоли и guest2 на второй консоли.


![](lab3/images/3.png)
Вход с guest

![](lab3/images/4.png)
вход с guest2

---

<style>
 h1{
    font-size:60px;
    color:black
    text-align: center;
}


</style>

# 4. Для обоих пользователей командой pwd определите директорию, в которой вы находитесь. Сравните её с приглашениями командной строки. Уточните имя вашего пользователя, его группу, кто входит в неё и к каким группам принадлежит он сам. Определите командами groups guest и groups guest2, в какие группы входят пользователи guest и guest2. Сравните вывод команды groups с выводом команд id -Gn и id -G.


![](lab3/images/5.png)

![](lab3/images/6.png)

![](lab3/images/7.png)

![](lab3/images/8.png)

![](lab3/images/9.png)

![](lab3/images/10.png)

Команды pwd,groups guest и groups guest2,id -Gn и id -G)

---

<style>
 h1{
    font-size:60px;
    color:black
    text-align: center;
}


</style>

# 5. Сравните полученную информацию с содержимым файла /etc/group Просмотрите файл командой cat /etc/group

![](lab3/images/11.png)
cat /etc/group для guest
![](lab3/images/12.png)
cat /etc/group для guest2

---

<style>
 h1{
    font-size:60px;
    color:black
    text-align: center;
}


</style>

## 6. От имени пользователя guest2 выполните регистрацию пользователя guest2 в группе guest командой newgrp guest.

![](lab3/images/13.png)
Команда newgrp guest


---

<style>
 h1{
    font-size:60px;
    color:black
    text-align: center;
}


</style>

## 7. От имени пользователя guest измените права директории /home/guest,разрешив все действия для пользователей группы: chmod g+rwx /home/guest

![](lab3/images/14.png)
Команда chmod g+rwx /home/guest

---

<style>
 h1{
    font-size:60px;
    color:black
    text-align: center;
}

</style>

# 8. От имени пользователя guest снимите с директории /home/guest/dir1 все атрибуты командой chmod 000 dir1

![](lab3/images/15.png)
chmod 000 dir1

---


<style>
 h1{
    font-size:60px;
    color:black
    text-align: center;
}

</style>

# 9. Заполнение таблицы 3.1.9. Меняя атрибуты у директории dir1 и файла file1 от имени пользователя guest и делая проверку от пользователя guest2, заполните табл. 3.1, определив опытным путём, какие операции разрешены, а какие нет. Если операция разрешена, занесите в таблицу знак «+», если не разрешена, знак «-».Сравните табл. 2.1 (из лабораторной работы № 2) и табл. 3.1.

---

![](lab3/images/16.png)

---

<style>
 h1{
    font-size:60px;
    color:black
    text-align: center;
}

</style>


![](lab3/images/17.png)

---

<style>
 h1{
    font-size:60px;
    color:black
    text-align: center;
}

</style>


![](lab3/images/18.png)

---

<style>
 h1{
    font-size:60px;
    color:black
    text-align: center;
}

</style>



![](lab3/images/19.png)

---

<style>
 h1{
    font-size:60px;
    color:black
    text-align: center;
}

</style>



![](lab3/images/20.png)

---

<style>
 h1{
    font-size:60px;
    color:black
    text-align: center;
}

</style>

# 10. Заполнение таблицы 3.2.На основании заполненной таблицы определите те или иные минимально необходимые права для выполнения пользователем guest2 операций внутри директории dir1 и заполните табл. 3.2



<style>
 h1{
    font-size:60px;
    color:black
    text-align: center;
}

</style>

![](lab3/images/21.png)
Сравнивая таблицу 3.1. с таблицей 2.1, можно сказать, что они одинаковы. Единственное различие в том, что в предыдущий раз мы присваивали права владельцу, а в этот раз группе.


---

# Выводы
### Были получены практические навыки работы в консоли с атрибутами файлов для групп пользователей

---

<style>
 h1{
    font-size:60px;
    color:black
    text-align: center;
}

</style>

# Список литературы

1. Права доступа: https://codechick.io/tutorials/unix-linux/unix-linux-permissions

2. Группы пользователей: https://losst.pro/gruppy-polzovatelej-linux#%D0%A7%D1%82%D0%BE_%D1%82%D0%B0%D0%BA%D0%BE%D0%B5_%D0%B3%D1%80%D1%83%D0%BF%D0%BF%D1%8B

---

<!-- _backgroundColor: lightblue -->

<style>
 h1{
    font-size:60px;
    color: red
    text-align: center;
}

</style>

# Спасибо за внимание!