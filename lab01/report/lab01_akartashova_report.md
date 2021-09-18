---
# Front matter
lang: ru-RU
title: "Отчет по лабораторной работе №1: Установка и конфигурация операционной системы на виртуальную машину"
subtitle: "*дисциплина: Информационная безопасность*"
author: "Каташова Алиса, НФИбд-03-18"

# Formatting
toc-title: "Содержание"
toc: true # Table of contents
toc_depth: 2
lof: true # List of figures
lot: true # List of tables
fontsize: 12pt
linestretch: 1.5
papersize: a4paper
documentclass: scrreprt
polyglossia-lang: russian
polyglossia-otherlangs: english
mainfont: PT Serif
romanfont: PT Serif
sansfont: PT Sans
monofont: PT Mono
mainfontoptions: Ligatures=TeX
romanfontoptions: Ligatures=TeX
sansfontoptions: Ligatures=TeX,Scale=MatchLowercase
monofontoptions: Scale=MatchLowercase
indent: true
pdf-engine: lualatex
header-includes:
  - \linepenalty=10 # the penalty added to the badness of each line within a paragraph (no associated penalty node) Increasing the value makes tex try to have fewer lines in the paragraph.
  - \interlinepenalty=0 # value of the penalty (node) added after each line of a paragraph.
  - \hyphenpenalty=50 # the penalty for line breaking at an automatically inserted hyphen
  - \exhyphenpenalty=50 # the penalty for line breaking at an explicit hyphen
  - \binoppenalty=700 # the penalty for breaking a line at a binary operator
  - \relpenalty=500 # the penalty for breaking a line at a relation
  - \clubpenalty=150 # extra penalty for breaking after first line of a paragraph
  - \widowpenalty=150 # extra penalty for breaking before last line of a paragraph
  - \displaywidowpenalty=50 # extra penalty for breaking before last line before a display math
  - \brokenpenalty=100 # extra penalty for page breaking after a hyphenated line
  - \predisplaypenalty=10000 # penalty for breaking before a display
  - \postdisplaypenalty=0 # penalty for breaking after a display
  - \floatingpenalty = 20000 # penalty for splitting an insertion (can only be split footnote in standard LaTeX)
  - \raggedbottom # or \flushbottom
  - \usepackage{float} # keep figures where there are in the text
  - \floatplacement{figure}{H} # keep figures where there are in the text
---

# Цель работы



Приобретение практических навыков установки операционной системы на виртуальную машину, настройки минимально необходимых для дальнейшей работы сервисов.

# Задание

Установить на вирутальную машину VirtualBox операционной системы Linux дистрибутив Centos


# Выполнение лабораторной работы


## Создание виртуальной машины

Создадим каталог для работы с виртуалной машиной.

Запустим менеджер virtualbox и провери  в свойствах месторасположение каталога для виртуальных машин.

Создадим новою виртуальную машину со следующими параметрами:

- имя виртуальной машины — IS  
- тип операционной системы — Linux, RedHat (рис. -@fig:001)  
- размер основной памяти виртуальной машины — 4096 МБ  
- конфигурация жёсткого диска — загрузочный, VDI (BirtualBox Disk Image), динамический виртуальный диск(рис. -@fig:002)(рис. -@fig:003)  
- размер диска - 40Гб  
- Выделим в окне менеджера VirtualBox виртуальную машину Information_Sequrity,  и открыть окно *Свойства*. Проверить, что папка для для снимком виртуальной машины имеет путь /var/tmp/akarta/Information_Sequrity/Snapshots.(рис. -@fig:004)  
- Во вкладке *Носители* виртуальной машины добавим новый привод оптических дисков и выберем необходимый образ.(рис. -@fig:005)  

![Окно «Имя машины и тип ОС»](lab01/screens/001.png){ #fig:001 width=70% }

![Окно «Тип жесткого диска»](lab01/screens/002.png){ #fig:002 width=70% }

![Окно "Формат хранения"»](lab01/screens/003.png){ #fig:003 width=70% }

![Окно «Свойства» виртуальной машины Base: путь к скриншотам](lab01/screens/004.png){ #fig:004 width=70% }

![Окно «Носители» виртуальной машины Base:выбор образа оптического диска](lab01/screens/005.png){ #fig:005 width=70% }





## Установка операционной системы

Запустим виртуальную машину и начнем установку системы:

- Установить русский язык для интерфейса и раскладки клавиатуры(-@fig:006)
- Указать *Стандартные накопители* для установки ОС. В окне конфигурации жесткого диска выбрать *Да, удалить данные*
- Имя машины *akartashova.localdomain*(-@fig:007)
- Часовой пояс "Москва"
- Установить пароль для root(-@fig:008)
- При конфигурации размера жесткого диска указать *Все пространство*
- Выбрать вариант стандартной установки CentOS
- Завершить установку операционной системы и перезагрузить ее


![Виртуальная машина: установка русского языка](lab01/screens/006.png){ #fig:006 width=70% }


![ Установка часового пояса](lab01/screens/007.png){ #fig:007 width=70% }


![Установка пароля для root и создание пользователя](lab01/screens/008.png){ #fig:008 width=70% }


Оптический диск для загрузки системы отключился автоматически




## Настройка виртуальной машины

Запустим виртуальную машину IS и настроим ее.

- подключимся к виртуальной машине с помощью созданой учетной записи
- Запустим терминал, перейдем под учетную запись root  с помощиью команды  *su*
- Обновим системные файлы и установим необходмые программы, например midnight commander:(рис. -@fig:009)

**Команды:**
```bash
yum update
yum install mc
```
После установки необходимых программ можно завершить работу виртуальной машины. Её конфигурация сохранится на жёстком диске в директории /var/tmp/имя_пользователя/Base.


![Обновление системных файлов и установка mc](lab01/screens/009.png){ #fig:009 width=70% }


В процессе установки я забыла изменить имя машины, поэтому поменяла его после установки(рис. -@fig:010)

![Измененение сетевого имени машины](lab01/screens/010.png){ #fig:010 width=70% }

Сетевое имя и имя хоста виртаульной машины было успешно изменено(рис. -@fig:011)

![lab01 is done](lab01/screens/011.png){ #fig:011 width=70% }



# Выводы

Мы установили операционную систему CentOS на нашу виртуальную машину.
