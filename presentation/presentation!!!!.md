---
marp: true
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

 h3{
    font-size: 20px;
    color: black
    text-align: center;
}

</style>

# Лабораторная работа №2.
##  Дискреционноеразграничение прав в Linux. Основные атрибуты
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
## Получение практических навыков работы в консоли с атрибутами файлов, закрепление теоретических основ дискреционного разграничения доступа в современных системах с открытым кодом на базе ОС Linux .

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
## Дискреционное управление доступом - права доступа состоят из трех компонентов: владелец файла, группа владельца и остальные пользователи. Каждому компоненту присваивается разрешение на чтение (r), запись (w) и выполнение (x). Для управления правами доступа в Linux используются команды chmod, chown и chgrp.

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
 ## 1.В установленной при выполнении предыдущей лабораторной работы операционной системе создайте учётную запись пользователя guest (использую учётную запись администратора):useradd guest
## 2. Задаем пароль для пользователя guest (использую учётную запись администратора):passwd guest

---

![Создание учетной записи](1.png)

---

<style>
 h1{
    font-size:60px;
    color:black
    text-align: center;
}


</style>

# 3.Входим в систему от имени guest.

---

![Успешный вход в новую учетную запись и переход в терминал](2.png)

---

<style>
 h1{
    font-size:60px;
    color:black
    text-align: center;
}


</style>

# 4. Определяем директорию, в которой находимся, командой pwd.

---

![Использование команды pwd](3.png)

---

<style>
 h1{
    font-size:60px;
    color:black
    text-align: center;
}


</style>

# 5. Уточняем имя пользователя командой whoami.

---

![Использование команды whoami](4.png)

---

<style>
 h1{
    font-size:60px;
    color:black
    text-align: center;
}


</style>

# 6.Уточняем имя пользователя, его группу, а также группы, куда входит пользователь, командой id. Выведенные значения uid, gid и др. запоминаем.

---

![Использование команды id для получения необходимой информации](5.png)

---

<style>
 h1{
    font-size:60px;
    color:black
    text-align: center;
}


</style>

# 7.Просматриваем файл /etc/passwd командой cat /etc/passwd.Дополнительно используем команду cat /etc/passwd | grep guest вкачестве фильтра для вывода только строк, содержащих определённыебуквенные сочетания

---

![Используем команду cat /etc/passwd и находим нашу учетную запись,uid,gid(часть1)](6.png)

---

![Используем команду cat /etc/passwd и находим нашу учетную запись,uid,gid(часть2)](7.png)

---

<style>
 h1{
    font-size:60px;
    color:black
    text-align: center;
}


</style>

# 8.Grep

![Используем команду grep](8.png)

---

<style>
 h1{
    font-size:60px;
    color:black
    text-align: center;
}

</style>

#  Определяем существующие в системе директории командой ls -l /home/

---

![Используем команду ls -l /home/](9.png)

---

<style>
 h1{
    font-size:60px;
    color:black
    text-align: center;
}

</style>

# 10. Проверим, какие расширенные атрибуты установлены на поддиректориях, находящихся в директории /home, командой:lsattr /home

---

![Используем команду lsattr /home](10.png)

---

<style>
 h1{
    font-size:60px;
    color:black
    text-align: center;
}

</style>

# 11. Создаем в домашней директории поддиректорию dir1 командой mkdir dir1.Определяем командами ls -l и lsattr, какие права доступа и расширенные атрибуты были выставлены на директорию dir1.

---

![Создаем поддиректорию dir1 командой mkdir dir1,задействуем команды ls -l и lsattr](11.png)

---

<style>
 h1{
    font-size:60px;
    color:black
    text-align: center;
}

</style>

# 12. Снимаем с директории dir1 все атрибуты командой chmod 000 dir1 и проверяем с её помощью правильность выполнения команды ls -l.

---

![Использование команд chmod 000 dir1 и ls -l](12.png)

---

<style>
 h1{
    font-size:60px;
    color:black
    text-align: center;
}

</style>

# 13. Попытка создать в директории dir1 файл file1 командой echo "test" > /home/guest/dir1/file1.

![Использование команды echo "test" > /home/guest/dir1/file1](13.png)

---

<style>
 h1{
    font-size:60px;
    color:black
    text-align: center;
}

</style>

# Мы получили отказ в связи с тем,что сняли все атрибуты с этой директории в прошлом пункте.Проверка командой ls -l /home/guest/dir1

![Использование команды ls -l /home/guest/dir1](14.png)

---

<style>
 h1{
    font-size:60px;
    color:black
    text-align: center;
}

</style>

# 14. Заполняем таблицу «Установленные права и разрешённые действия»(см. табл. 2.1), выполняя действия от имени владельца директории (файлов), определив опытным путём, какие операции разрешены, а какие нет.Если операция разрешена, заносим в таблицу знак «+», если не разрешена, знак «-».
Таблица получилась очень большой,не было смысла ее дробить,поэтому она есть в полном размере в отчете.

---

<style>
 h1{
    font-size:60px;
    color:black
    text-align: center;
}

</style>

# Пример таблицы

![Пример таблицы "Установленные права и разрешённые действия"](15.png)

---

<style>
 h1{
    font-size:60px;
    color:black
    text-align: center;
}

</style>

# 15. На основании заполненной таблицы определяем те или иные минимально необходимые права для выполнения операций внутри директории dir1.

---

<style>
 h1{
    font-size:60px;
    color:black
    text-align: center;
}

</style>

# Пример таблицы 

![Пример таблицы "Минимальные права для совершения операций"](16.png)

---

![Таблица](image.png)

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

# Выводы
## Выполняя данную лабораторную работы,мы получили практические навыки работы в консоли с атрибутами файлов и закрепили теоретические основы дискреционного разграничения доступа в современных системах с открытым кодом на базе ОС Linux.

---

<style>
 h1{
    font-size:60px;
    color:black
    text-align: center;
}

</style>

# Список литературы

#1.О правах доступа в ОС
(https://vk.com/away.php?utf=1&to=https%3A%2F%2Fhabr.com%2Fru%2Farticles%2F469667%2F)
 2.Подробнее о дискреционном разграничении прав
(https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=&cad=rja&uact=8&ved=2ahUKEwjjnvnGlNSEAxUmLhAIHY2AD5wQFnoECA0QAw&url=https%3A%2F%2Fitcloud-edu.ru%2Finfo%2Farticles%2Fupravlenie-dostupom-v-gnu-linux%2F&usg=AOvVaw0AZKOfJmBKY3JGoaVnzpqQ&opi=89978449)

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