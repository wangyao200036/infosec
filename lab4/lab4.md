---
title: "Отчёт по лабораторной работе №4"
author: "ван яо"

# 通用选项
lang: ru-RU
toc: true
toc-title: "Содержание"
toc-depth: 2
lof: true
lot: true
fontsize: 12pt
linestretch: 1.5
papersize: a4
documentclass: scrreprt

# 多语言支持
polyglossia-lang:
  name: russian
  options:
    - spelling=modern
    - babelshorthands=true
polyglossia-otherlangs:
  name: english

babel-lang: russian
babel-otherlangs: english

# 字体配置
mainfont: PT Serif
romanfont: PT Serif
sansfont: PT Sans
monofont: PT Mono
mainfontoptions: Ligatures=TeX
romanfontoptions: Ligatures=TeX
sansfontoptions: Ligatures=TeX,Scale=MatchLowercase
monofontoptions: Scale=MatchLowercase,Scale=0.9

# 引用管理
biblatex: true
biblio-style: "gost-numeric"
biblatexoptions:
  - parentracker=true
  - backend=biber
  - hyperref=auto
  - language=auto
  - autolang=other*
  - citestyle=gost-numeric

# 图表和代码片段标题
pandoc-crossref:
  figureTitle: "Рис."
  tableTitle: "Таблица"
  listingTitle: "Листинг"
  lofTitle: "Список иллюстраций"
  lotTitle: "Список таблиц"
  lolTitle: "Листинги"

# 其他选项
indent: true
header-includes:
  - \usepackage{indentfirst}
  - \usepackage{float} % 保持图片在文本中的位置
  - \floatplacement{figure}{H} % 保持图片在文本中的位置
---

# Цель работы
Получение практических навыков работы в консоли с расширенными
атрибутами файлов

# процесс выполнения задания

1. От имени пользователя guest определите расширенные атрибуты файла
/home/guest/dir1/file1 командой
lsattr /home/guest/dir1/file1

![](https://github.com/wangyao200036/infosec/raw/main/lab4_pic/1.png)
2. Установите командой
chmod 600 file1
на файл file1 права, разрешающие чтение и запись для владельца файла.

![](https://github.com/wangyao200036/infosec/raw/main/lab4_pic/2.png)

3. Попробуйте установить на файл /home/guest/dir1/file1 расширенный атрибут a от имени пользователя guest:
chattr +a /home/guest/dir1/file1
В ответ вы должны получить отказ от выполнения операции

![](https://github.com/wangyao200036/infosec/raw/main/lab4_pic/3.png)
4. Зайдите на третью консоль с правами администратора либо повысьте
свои права с помощью команды su. Попробуйте установить расширенный атрибут a на файл /home/guest/dir1/file1 от имени суперпользователя:
chattr +a /home/guest/dir1/file1

![](https://github.com/wangyao200036/infosec/raw/main/lab4_pic/4.png)
5. От пользователя guest проверьте правильность установления атрибута:
lsattr /home/guest/dir1/file1

![](https://github.com/wangyao200036/infosec/raw/main/lab4_pic/5.png)
6. Выполните дозапись в файл file1 слова «test» командой
echo "test" /home/guest/dir1/file1
После этого выполните чтение файла file1 командой
cat /home/guest/dir1/file1
Убедитесь, что слово test было успешно записано в file1.

![](https://github.com/wangyao200036/infosec/raw/main/lab4_pic/6.png)
7. Попробуйте удалить файл file1 либо стереть имеющуюся в нём информацию командой
echo "abcd" > /home/guest/dirl/file1
Попробуйте переименовать файл.
![](https://github.com/wangyao200036/infosec/raw/main/lab4_pic/7.png)
8. Попробуйте с помощью команды
chmod 000 file1
установить на файл file1 права, например, запрещающие чтение и запись для владельца файла. 
![](https://github.com/wangyao200036/infosec/raw/main/lab4_pic/8.png)
9. Снимите расширенный атрибут a с файла /home/guest/dirl/file1 от
имени суперпользователя командой
chattr -a /home/guest/dir1/file1
![](https://github.com/wangyao200036/infosec/raw/main/lab4_pic/9.png)
10. Повторите ваши действия по шагам, заменив атрибут «a» атрибутом «i».
Удалось ли вам дозаписать информацию в файл? Ваши наблюдения занесите в отчёт

![](https://github.com/wangyao200036/infosec/raw/main/lab4_pic/10.png)

| Свойства | Описание | Возможные действия |
|------|------|------------|
| `a` | Можно только добавлять данные, нельзя изменять или удалять файлы |
| `i` | Файлы не могут быть изменены или удалены | Файлы не могут быть добавлены, изменены или удалены |

# Выводы
Получил практические навыки работы в консоли с расширенными
атрибутами файлов