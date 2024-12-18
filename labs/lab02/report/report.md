---
## Front matter
title: "Отчёт по лабораторной работе №2"
subtitle: "Сетевые технологии"
author: "Ищенко Ирина НПИбд-02-22"

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
lot: true # List of tables
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
mainfont: IBM Plex Serif
romanfont: IBM Plex Serif
sansfont: IBM Plex Sans
monofont: IBM Plex Mono
mathfont: STIX Two Math
mainfontoptions: Ligatures=Common,Ligatures=TeX,Scale=0.94
romanfontoptions: Ligatures=Common,Ligatures=TeX,Scale=0.94
sansfontoptions: Ligatures=Common,Ligatures=TeX,Scale=MatchLowercase,Scale=0.94
monofontoptions: Scale=MatchLowercase,Scale=0.94,FakeStretch=0.9
mathfontoptions:
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
lotTitle: "Список таблиц"
lolTitle: "Листинги"
## Misc options
indent: true
header-includes:
  - \usepackage{indentfirst}
  - \usepackage{float} # keep figures where there are in the text
  - \floatplacement{figure}{H} # keep figures where there are in the text
---

# Цель работы

Изучение принципов технологий Ethernet и Fast Ethernet и практическое освоение методик оценки работоспособности сети, построенной на базе технологии Fast Ethernet.

# Задание

Требуется оценить работоспособность 100-мегабитной сети Fast Ethernet в соответствии с первой и второй моделями. Конфигурации сети (рис. [-@fig:1]). Топология сети  (рис. [-@fig:2]).

![Конфигурации сети](image/1.png){ #fig:1 width=80% }

![Топология сети](image/2.png){ #fig:2 width=80% }

# Выполнение лабораторной работы

Оценим работоспособность с помощью первой модели:

Вычислим диаметр домена коллизий и сравним его с референтным значением. По условию у нас имеются два повторителя класса II и все сегменты типа 100BASE-TX, в соответствии с таблицей (рис. [-@fig:3]) получаем, что предельно допустимый диаметр домена коллизий в Fast Ethernet 205 м.

![Предельно допустимый диаметр коллизий в Fast Ethernet](image/3.png){ #fig:3 width=80% }

Посчитаем суммы длин сегментов в каждой строке и сравним их с референтным значением. Значения сетей 1, 3 и 4 меньше 205, следовательно это работоспособные сети(рис. [-@fig:4]).

![Проверка работоспособности по первой модели](image/4.png){ #fig:4 width=80% }

Оценим работоспособность сети с помощью второй модели:

Для этого требуется найти наихудшие пути в домене коллизий. В нашей конфигурации все сегменты 100BASE-TX и используется витая пара категории 5 (рис. [-@fig:5]).

![Наихудшие пути](image/5.png){ #fig:5 width=80% }

Рассчитаем время для двойного оборота на сегментах, умножая длину сегмента на удельное время двойного оборота 1,112 би/м. Для каждой строки полученные значения сложим. Затем к получившейся сумме добавим время двойного оборота двух повторителей класса II (92 би/м для каждого) и пары терминалов с интерфейсами TX (100 би/м). Также добавим 4 битовых интервала для учета задержек и сравним результат с числом 511,96. Результаты меньше указанного значения являются показателем работоспособных сетей (рис. [-@fig:6]).

![Проверка работоспособности по второй модели](image/6.png){ #fig:6 width=80% }

В результате работоспособными являются те же варианты сетей, что и по первой модели (сети 1, 3 и 4).

# Выводы

В ходе лабораторной работы я изучила принципы технологий Ethernet и Fast Ethernet, на практике освоила методики оценки работоспособности сети, построенной на базе технологии Fast Ethernet. И первая, и вторая модели выявили работоспособные сети, результаты совпали.