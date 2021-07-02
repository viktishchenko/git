# Git & Command line basic

## _Базовые команды и прочие штуки_

[![Last update](https://img.shields.io/badge/update-02.07.21-brightgreen)](https://github.com/viktishchenko)

## Термины

- Репозиторий — папка с файлами и настройками Git. Настройки расположены в скрытой папке .git.

- Форк ( fork ) — копия репозитория. GitHub создаст копию фокрнутого репозитория у вас на аккаунте. После этого в копию репозитория можно будет вносить изменения. Внесенные изменения можно предложить добавить в основной репозиторий через пул реквест.
- Клонить ( clone ) — скачивать репозиторий с удалённого сервера на локальный компьютер.

- Ветка / бранч ( branch ) — это параллельная версия репозитория. Ветки можно объединять между собой, например соединять параллельную версию с главной версией репозитория.
- Мастер ( master ) — главная или основная ветка репозитория.
- Коммит ( commit ) — фиксация изменений или запись изменений в репозиторий. Коммит происходит на локальном компьютере.
- Пул (pull ) — получение последних изменений с удалённого сервера репозитория.
- Пуш ( push ) — отправка всех неотправленных коммитов на удалённый сервер репозитория.
- Пул реквест ( pull request ) — запрос на слияние форка репозитория с основным репозиторием. Пул реквест может быть принят или отклонён владельцем репозитория.
- Мёрдж ( merge ) — слияние изменений из какой-либо ветки репозитория с любой веткой этого же репозитория. Чаще всего — слияние изменений из ветки репозитория с основной веткой репозитория.
- Код ревью ( code review ) — процесс проверки кода на соответствие определённым требованиям, задачам и внешнему виду.
- Обновиться из апстрима — обновить свою локальную версию форка до последней версии основного репозитория, от которого сделан форк.
- Обновиться из ориджина — обновить свою локальную версию репозитория до последней удалённой версии этого репозитория.

## Работа с Git

# А. Настройка корфига

### 1. Настройка имени

```javascript
git config --global user.name "YourName"
```

- git — все команды для Git начинаются с этого слова.
- config — конфигурация.
- --global — означает, что настройка будет применена для всех проектов.
- user.name — настройка, которую нужно установить.
- YourName — имя, которое нужно установить.

### 2. Настройка электронной почты

```javascript
git config --global user.email "name@mail.ru"
```

### 3. Проверить, что настройки сохранились

_( имя и электронная почта )_

```javascript
git config --global --list

(--global, если настройки имени задавались для всех проектов и нужно вывести именно их)
```

### 4. Открыть файл с настройками

_Настройки хранятся в файле .gitconfig_

```javascript
cat ~/.gitconfig

(такого файла может не быть, если изначально не прописать настройки)
```

### 5. Узнать, как работает команда в консоли

_Настройки хранятся в файле .gitconfig_

```javascript
git help название_команды

(показать справку по выбранной команде)
```

```javascript
git help

(покажутся самые популярные команды)
```

```javascript
git help config

(покажется справка для команды config)
```

# B. Работа с локальными папками

### 1. Перемещение по папкам

`pwd` — узнать полный путь к папке, в которой сейчас находимся.

`cd` — название_папки — для перехода в выбранную папку.

`cd ..` — переместиться на одну папку назад.

`сd /` — переместиться на одну папку вперед.

`cd -` — вернуться к предыдущей папке.

`cd ~` — перейти в папку, которая назначена домашней.

Пример:

```javascript
cd /d

(перейти на диск D)
```

```javascript
cd code/'some folder'

( перейти в папку "code", а затем в папку "some folder" — в коде она указана в кавычках, так как содержит пробелы )
```

### 2. Обзор папки

`ls` — какие файлы есть в папке(список файлов).

`ls -1` — какие файлы есть в папке, вывод в столбик.

`ls -1 -a` — какие файлы есть в папке, вывод в столбик, в том числе скрытых файлов.
`cd ..` — подняться на уровень выше
`cd ../..` — подняться на 2 уровеня выше

Быстрые клавиши:

`cd ~/D + tab` — покажет, какие папки начинаются на букву "D".

`cd ~/Des + tab` — терминал сам допишет вместо "Des" — "Desktop".

### 3. Открыть папку

`start .` — открыть папку, в которой сейчас находимся.

`code .` — открыть папку в редакторе кода.

### 4. Создание файлов и папок через консоль

`start .` — открыть папку, в которой сейчас находимся.
`start . ~/Desctop/Project/index.js` — открыть файл в редакторе, назначенном по умолчанию для файлов данного типа.

`code .` — открыть папку в редакторе кода.

# С. Привязать папку с проектом к Git

_(превратить проект в репозиторий)_

### 1. Подготовить к работе репозиторий

_( если недавно его создали / он ещё не привязан к Git )_

```javascript
git init
```

После этого в папке с проектом появится скрытая папка `.git`, в которой содержится вся история изменений.

### 2. Посмотреть состояние репозитория

_( проверяем, были ли добавлены новые изменения, которые ещё не внесены в историю изменений )_

```javascript
git status

(эта команда может использоваться довольно часто для проверки состояния репозитория)
```

Возможные варианты:

- Если выводятся файлы, выделенные красным — значит есть новые изменения, которые не добавлены. Иначе говоря — есть не отслеживаемые Git файлы.
- Если файлы выводятся зеленым — недавно измененные файлы добавлены. Иначе говоря — все файлы отслеживаются Git.
- Если нет подсвеченных файлов и надпись такого плана: `"nothing to commit, working tree clean"` — значит новых не внесенных изменений нет. Все файлы отслеживаются Git.

### 3. Проиндексировать новые или измененные файлы

_( для последующего сохранения состояния )_

```javascript
git add .

(проиндексировать все файлы в папке)
```

```javascript
git add index.html

(проиндексировать только файл index.html)
```

```javascript
git add css/button.css css/main.css

(проиндексировать сразу 2 файла, которые находятся в папке "css": button.css и main.css, указанные через пробел)
```

После: `git status` — можно проверить, проиндексировались ли все файлы.

### 4. Зафиксировать изменения

_( — закоммитить, сделать новые изменения отслеживаемыми )_

Благодаря этой процедуре, в случае надобности — можно откатиться к предыдущему закоммиченному изменению. Иначе говоря: коммит — это как save в игре.

```javascript
git commit -m "Описание, что изменилось"
```

После: `git status` — проверить, закоммитились ли файлы. Если да, будет сообщения такого плана: `"nothing to commit, working tree clear"`.

Дополнительно:

### 5. Посмотреть, что изменилось

_Посмотреть непроиндексированные изменения:_

```javascript
git diff

(гит покажет, что именно изменилось в файле: красным — удаленное, зеленым — добавленное)
```

_Посмотреть проиндексированные изменения:_

```javascript
git diff --staged
```

### 6. Посмотреть историю коммитов

```javascript
git log

(покажет всю историю коммитов этого репозитория, если она есть)
```

```javascript
git log -2

(покажет 2 последних коммита этого репозитория)
```

В консоли появится информация подобного рода:

```javascript
commit c73af11e0830fe25cv4648c2356742f253cc000d (HEAD -> master, origin/master)
Author: YourName <name@mail.com>
Date:   Sun Feb 24 22:01:09 2019 +0300

    second commit

commit e5cdl7321di6love8the2rs1school687dde6282
Author: YourName <name@mail.com>
Date:   Sun Feb 24 21:50:20 2019 +0300

    first commit
```

`c73af11e0830fe25cv4648c2356742f253cc000d` — хэш второго коммита. Зная хэш коммита, можно заглянуть в лог коммита или откатиться к этому коммиту.

Также можно вывести историю всех коммитов в одну строку.

```javascript
git log --oneline
```

Появится информация такого плана:

```javascript
5c71719 (HEAD -> master) Уменьшили шрифт на кнопках
b69e1e8 Уменьшили шрифт телефона
2c8bd55 Заменили span на botton в кнопках для лучшей доступности
6bf8b41 Сделали рефакторинг
0c5e111 Починили ошибку фильтрации
5949091 Изменили основной шрифт
5d33d23 Установили цвет кнопок и фона
4f485ba Начали вести историю
```

### 7. Узнать, какие изменения были внесены в определенном коммите

```javascript
git show e5mnd6f07fb3n72f9ccc3b24839687d61cde6282
```

# D. Если нужно что-то восстановить

### 1. Откатить файл до последнего коммита

_(Вернуть файл в то состояние, в котором он был в последнем коммите. Например, если файл удален)_

```javascript
git checkout index.js

(теперь, если прописать git status, то будет видно, что файл не изменен)
```

### 2. Откатить файл до определенного коммита

```javascript
git checkout c73af1de0877fe25eb4648c2356742f253cc000d index.js
```

### 3. Убрать файл из индекса (перед коммитом)

_(Когда изменения подготовлены и уже добавлены в индекс (git add), но выяснилось, что какой-то файл индексировать не нужно)_

```javascript
git reset HEAD index.js

(теперь, после проверки изменений git status, файл index.js не будет включен в индекс)
```

### 4. Отменить последний коммит

_(Когда изменения подготовлены и уже добавлены в индекс (git add), но выяснилось, что какой-то файл индексировать не нужно)_

```javascript
git revert HEAD

(HEAD указывает на последний коммит, поэтому выполнили команду через него)
```

Но команда `revert` оставляет историю, показывающую, что был и оригинальный и отмененный коммит. А иногда ненужный (или добавленный с ошибке) коммит нужно удалить из истории.

### 5. Исправить последний коммит

_(Например, текст коммита был добавлен с ошибкой.)_

```javascript
git commit --amend -m "Правильное сообщение коммита"

(после этого последний коммит с неправильным текстом исчезнет из логов и хэш последнего коммита изменится — то есть не старый коммит поменялся, а создался новый коммит вместо старого)
```

### 6. Убрать файл из последнего коммита и **удалить этот файл**

```javascript
git rm index.js
```

Осталось внести изменения в коммит, без внесения изменений в комментарий к нему:

```javascript
Если прописать git status, будет следующее сообщение:

deleted: index.js

Поэтому можно изменить предыдущий коммит, убрав из него изменения:

git commit --amend --no-edit
```

### 7. Убрать файл из последнего коммита, но не удалять этот файл.

```javascript
git rm --сached index.js
```

Снова можно изменить прошлый коммит от внесения в него изменений:

```javascript
Если прописать git status, будет такого плана информация:

deleted: index.js
Untrasked file: index.js

(файл останется, но от теперь будет неотслеживаемым)

git commit --amend --no-edit
```

# E. Появление веток, слияние

`Ветки` — это когда в некоторой точке история коммитов разделяется. Они помогают разным людям работать параллельно над одним проектом — каждый в своей ветке. А затем эти ветки соединяются воедино — в один проект.

_Вывести содержимое коммита в удобном для чтения виде:_

```javascript
git log --oneline

(вывести коммит в 1 строку, а не в 5 как обычно)
git cat-file -p b69e1e8
```

`-p` — выводит данные в удобном для чтения виде.

`b69e1e8` — хэш коммита.

Выведется информация такого плана:

```javascript
tree 9f390a90d40889a27d85910cb8b4530a02fd441e (состояние файлов на момент коммита)
parent 4f585bafe99v8bd57e2c82cf6a8b07569df8b810 (хэш родительского коммита)
author Viktor Tishchenko <name@mail.com> 1518978605 +0300 (два числа - это время ... )
committer Viktor Tishchenko <name@mail.com> 1518978828 +0300 (... когда был создан коммит )
```

- Обычно `author` и `committer` совпадают. Но это могут быть разные люди, если один разработчик изменил коммит другого.
- Коммит хранит не только состояние, но и: кто, когда, почему его сохранил. И ещё знает предыдущий коммит — коммит родителя.
- У самого первого коммита не будет родительского.

## Визуальные примеры

### 1. Расположение коммитов

Если есть 3 коммита — мы по умолчанию находимся в последнем.

![brunch](https://content.evernote.com/shard/s368/sh/b1359883-2b9e-419a-b9de-dd959fc05f05/97c0f19486d851b3/res/3359f214-a26d-42d6-aee6-ec2ab7831aa5)

### 2. Новый коммит

Когда мы коммитим — фиксируем состояние, то создается новый коммит и мы перемещаемся в него.

```javascript
git commit -m "Описание, что изменилось"
```

![brunch](https://content.evernote.com/shard/s368/sh/b1359883-2b9e-419a-b9de-dd959fc05f05/97c0f19486d851b3/res/8f203df1-44a0-4759-a9f7-c24ba8aebac4)

### 3. Вернуться на любой прошлый коммит

Мы в любое время можем переместиться в состояние коммитов, которые остались позади.

```javascript
git commit -m "Описание, что изменилось"
```

![brunch](https://content.evernote.com/shard/s368/sh/b1359883-2b9e-419a-b9de-dd959fc05f05/97c0f19486d851b3/res/11a25362-8d63-46b5-8b75-406ba2f03940)

Если теперь запросить историю коммитов (git cat-file -p 8d54f00), то будет видна история только до 2-го коммита. Но это не значит, что все последующие коммиты исчезли.

**Посмотреть все коммиты.**

```javascript
git log --oneline --all
```

**Посмотреть все коммиты в виде схемы.**

```javascript
git log --oneline --all --graph
```

### 4. Возвратиться к последнему коммиту

```javascript
git checkout хэш_последнего_коммита
```

![brunch](https://content.evernote.com/shard/s368/sh/b1359883-2b9e-419a-b9de-dd959fc05f05/97c0f19486d851b3/res/2eb6df40-1619-4a0f-8150-288b66b90961)

`Git` хранит кодовое слово, которое является указателем на последний коммит. Поэтому последнему коммиту всегда легко вернуться. По умолчанию это кодовое слово — `master`. А для сервера кодовое слово удаленного репозитория по умолчанию — `origin`.

### 5. Создать новую ветку (создать указатель на коммит)

_(На любой коммит можно создать указатель)_

```javascript
git checkout -b yellow-design

(yellow-design — имя новой ветки)
```

Создать указатель на один из прошлых коммитов:

```javascript
git checkout -b yellow-design хэш_коммита_которому_нужно_создать_указатель
```

![brunch](https://content.evernote.com/shard/s368/sh/b1359883-2b9e-419a-b9de-dd959fc05f05/97c0f19486d851b3/res/b2fc0f1b-f460-402b-8399-a0e7c126e91e)

### 6. Создание нового коммита из другого указателя

При создании нового коммита с нового указателя, происходит ветвление коммитов и появляются ветки.

![brunch](https://content.evernote.com/shard/s368/sh/b1359883-2b9e-419a-b9de-dd959fc05f05/97c0f19486d851b3/res/4754fe4f-3ce8-4b67-b2c2-28dc2d502bba)

### 7. Понятие веток

Ветка — вся история коммитов, приводящая в текущую точку.

Одна ветка `master`:

![brunch](https://content.evernote.com/shard/s368/sh/b1359883-2b9e-419a-b9de-dd959fc05f05/97c0f19486d851b3/res/dccfc876-8cbc-45f4-83da-b2ec3b42d289)

Вторая ветка yellow-design:

![brunch](https://content.evernote.com/shard/s368/sh/b1359883-2b9e-419a-b9de-dd959fc05f05/97c0f19486d851b3/res/f90429b2-4266-43d7-98c7-d0f536a7df4d)

### 8. Перемещение на другую ветку

```javascript
git checkout master

(перейти к ветке master)
```

![brunch](https://content.evernote.com/shard/s368/sh/b1359883-2b9e-419a-b9de-dd959fc05f05/97c0f19486d851b3/res/f90429b2-4266-43d7-98c7-d0f536a7df4d)

**Как понять, где мы находимся?**

В логах. При запрашивании логов (`git log --oneline`), можно посмотреть по слову `HEAD`.
Слово `HEAD` в логах показывает на наше текущее положение. Например:

```javascript
(HEAD -> yellow-design)

(показывает, что мы находимся в ветке yellow-design)

```

В текущем состоянии. При запрашивании текущего состояние (git status) будет сообщение такого плана:

```javascript
On branch yellow-design

(находимся в ветке yeallow-design)
...
```

### 9. Слияние веток (мёрдж)

```javascript
git merge yellow-design -m "Объединили желтый дизайн и мастер"
```

![brunch](https://content.evernote.com/shard/s368/sh/b1359883-2b9e-419a-b9de-dd959fc05f05/97c0f19486d851b3/res/f5f71c1d-7a33-4191-b182-491c4e84ef43)

У нового коммита имя указателя будет тем, от которого мы шагнули при слиянии веток. То есть мы шагнули от ветки `master`, поэтому и имя у нового указателя такое же.

Обычно основной веткой считается ветка `master`. От этой ветки могут отводиться другие ветвления. Которые в конечном счете могут снова объединиться в одну примкнув к основной ветке `master`.

# F. Конфликты веток

`Конфликт` — это когда один и тот же файл, в одном и том же месте, но в разных ветках, менялся по-разному. Например, в ветке `master` первая строчка была изменена, а в ветке `yellow-design` — удалена. При слиянии таких веток возникнет конфликт.
Git сам не знает, какие изменения — правильные. Он предложит решить конфликт участвующим.

При слиянии веток будет информация такого плана:

```javascript
CONFLICT (content): merge conflict in index.js
```

В этой ситуации есть 2 решения:

### 1. Исправить конфликты и закоммитить.

Для этого нужно отредактировать конфликтующие файлы вручную.

При решении вручную, в редакторе можно увидеть оформление кода такого плана:

```javascript
<html>
  <head>
<<<<<<< HEAD
    <link rel="stylesheet" type="text/css" href="css/style.css" />
=======
    <link type="text/css" rel="stylesheet" href="style.css" />
>>>>>>> master
  </head>
  <body>
    <h1>Hello,World!</h1>
  </body>
</html>
```

Нужно убрать `информацию от Git`, а затем решить, какую строчку кода оставить.

После этого закоммитить изменения:

```javascript
git commit -m "Решил конфликт при слиянии веток"
```

### 2. Отменить слияние

(например, если оно было вызвано по ошибке) следующей командой:

```javascript
git merge --abort
```

# G. Перебазирование веток

_(совмещение / преобразование)_

Есть 2 ветки: `master` и `feature`.

```javascript
git checkout feature

(переходим на ветку feature)
```

![brunch](https://content.evernote.com/shard/s368/sh/b1359883-2b9e-419a-b9de-dd959fc05f05/97c0f19486d851b3/res/ad8a6cb3-1bcd-430b-b399-70e3b1fe2790)

### 1. Совместить ветки

```javascript
git rebase master

(перенести изменения из master в ветку yellow-design)
```

Теперь хэш коммитов C', D', E' не равен старому хэшу коммитов C, D, E в ветке feature. Но изменения в коммитах остались ровно такие же.

### 2. Слияние vs Преобразование

Преобразование делает дерево коммитов более линейным и красивым. Но оно не всегда уместно.

Когда НЕ использовать преобразование (git rebase):

- Если ветка является публичной и расшаренной. Переписывание общих веток будет мешать работе других членов команды.
- Когда важна точная история коммитов ветки (так как команда rebase переписывает историю коммитов).

### 3. Подтверждение при отправке на удаленный сервер

Так как коммиты одной из веток полностью новые (с новым хэшем), может понадобиться дополнительное подтверждение при отправке на уделенный сервер. Следующей командой мы принимаем риски, связанные с перезаписью коммитов:

```javascript
git push --force
```

С этим флагом нужно работать аккуратно, потому что могут случайно уничтожиться какие-то важные файлы.

[Подробнее про перебазирование веток.](https://habr.com/ru/post/161009/)

# H. Работа с GitHub

_(или другим сервисом, работающим с Git)_

Чтобы добавить файлы на удаленный сервер, нужно проделать 3 операции: сперва — проиндексировать, затем — закоммитить, а только потом — отправлять на сервер.

`Удаленная ветка` — не от слова `"удалена"`, а от `"удаленный сервер"`.

### 1. Добавить удаленный репозиторий

```javascript
git remote add origin *ссылка*
```

`origin` — имя основного удаленного репозитория. Это не какое-то ключевое слово, так принято его называть.

Проверяем, что репозиторий добавился:

```javascript
git remote -v (-v — значит подробный)

Выведет:
origin *ссылка* (fetch) (забирать из него изменения)
origin *ссылка* (push) (отправлять туда изменения)
```

Также можно проверить или получить ссылку на добавленный репозиторий:

```javascript
git remote get-url origin
```

### 2. Отправить изменения в удаленный репозиторий

```javascript
git remote get-url origin
```

`-u` — в случае, если находимся, например в не основной ветке `yellow-design`, но хотим установить связь с основной веткой `master`.

Если же находимся в основной ветке, можно приписывать команды без `-u`:

```javascript
git push origin master
```

Проиндексированные файлы, новые коммиты, новые ветки будут доступны только на компьютере, пока мы не отправим (`запушим`) изменения на удаленный сервер (например, на `GitHub`). Только после этого их можно будет увидеть в браузере, на сайте в аккаунте.

### 3. SSH-ключ

Если нет авторизации в консоли, при попытке запушить изменения в удаленный репозиторий (`git push origin master)`, Git может выдать подобную ошибку:

```javascript
Permission denied (publickey).

fatal: Could not read from remote repository.
Please make sure you have the correct access rights and the repository exists.
```

Но так обычно происходит, если при установке GitBash не был включен пункт "Enable Git Credential Meneger". Тогда некоторые средства авторизации, в том числе логин и пароль при каждом запросе понадобится вводить заново.

![gitbush install](https://content.evernote.com/shard/s368/sh/b1359883-2b9e-419a-b9de-dd959fc05f05/97c0f19486d851b3/res/f70ad215-4fee-4dbd-ab4c-1ff62b5eb47e)

[Как установить SSH-ключ.](https://www.youtube.com/watch?v=KqzVaUTCPbQ)

### 4. Если новая ветка создана с опечаткой

Например, хотели назвать `comments`, а напечатали `cmments`.

### 4a. Запушить с одной локальной ветки в другую удаленную ветку

```javascript
git push origin cmments:comments
```

`cmments` — имя локальной ветки, которую создали с ошибкой.
`comments` — имя ветки на удаленном сервере с уже правильным названием, куда нужно запушить файлы.

Так можно отправить любую локальную ветку на любую удаленную на ветку.

### 4b. Удалить неправильную/ненужную ветку: на сервере

Ведь после того, как мы запушили в правильно написанную ветку, старая ветка никуда не делась.

```javascript
git push origin :сmments
```

### 4c. Переименовать неправильную ветку: на компьютере

Ведь неправильная написанная ветка всё ещё осталась на компьютере.

```javascript
git branch -m comments
```

Команда `git branch` может: переименовывать, **удалять** и **создавать** ветки.

Скачивание и запись на сервер изменений.

![git brunch](https://content.evernote.com/shard/s368/sh/b1359883-2b9e-419a-b9de-dd959fc05f05/97c0f19486d851b3/res/8bd93979-1b48-49c3-ba0d-2881ee6a028d)

На темном фоне — изменения, которые внесены на удаленном сервере.

На светлом фоне — изменения, которые есть на локальном компьютере.

### 5. Скачать изменения с сервера

_( получить изменения из удаленного репозитория )_

Например, кто-то ещё работает над теми же файлами. И пока нас не было, он внес какие-то изменения. Чтобы начать работать с уже измененным репозиторием, нам нужно получить изменения. Поэтому команда git clone здесь может быть неудобна — придется заново копировать весь проект, хотя достаточно получить только те фрагменты, которые изменились.

```javascript
git pull origin master

(забирает и сливает коммиты и ветки)
```

Получится:

![git brunch](https://content.evernote.com/shard/s368/sh/b1359883-2b9e-419a-b9de-dd959fc05f05/97c0f19486d851b3/res/d44362fa-ef72-42dd-b198-73ed5ee4481c)

Но эта команда скачивает только ту ветку, которую указали — ветку `master`. В случае, если появились новые ветки и коммиты вне основной ветки — они не будет забраны на компьютер.

### 6. Скачать коммиты и ветки с сервера

```javascript
git fetch origin

(только забирает коммиты и ветки)
```

Это нужно в том случае, если в репозитории на GitHub были внесены новые ветки и коммиты с другого компьютера. Если не забрав их на свой компьютер, попробовать закоммитить в новую ветку, то ничего не получится.

Команда `git pull` эквивалентна комбинации `git fetch` и `git merge`.

### 7. Связать локальную ветку с удаленной

```javascript
git branch --set-upstrim-to=origin/comments
```

### 8. Посмотреть, какие локальные ветки связаны с удаленными

```javascript
git branch -vv
```

-v — подробно.
-vv — очень подробно.

# I. Упрощение работы с консолью

### Если редактирование текстовых файлов проходит в консоли GitBash.

`Vim` — по умолчанию редактор текстовых файлов в GitBash.

`:q` — выйти с редактора

`:q!` — выйти с редактора, если через него что-то менялось

### Создать удобное имя для команды - алиас.

`Алиас` — простое кодовое значение команды или нескольких команд.
Некоторые команды в консоли вводить долго и неудобно. Поэтому можно создать их алиас.

```javascript
git config --global alias.с config
```

`с` — теперь эта команда в консоли будет работать также, как команда config.

Другой пример:

```javascript
git config --global alias.сg 'config --global'
```

`cg` — теперь набирая эту одну команду будут срабатывать сразу две команды `config --global`.

### Полезные ресурсы.

1. Уроки: https://githowto.com/ru
2. Руководство: https://github.com/k88hudson/git-flight-rules/blob/master/README_ru.md
3. Ещё руководство: http://firstaidgit.ru/#/
4. Большое руководство Стэнфорда: http://www-cs-students.stanford.edu/~blynn/gitmagic/intl/ru/
5. Книга: https://git-scm.com/book/ru/v2
6. Скринкасты: https://www.youtube.com/playlist?list=PLDyvV36pndZHkDRik6kKF6gSb0N0W995h

[Original work link →](https://www.evernote.com/shard/s368/client/snv?noteGuid=b1359883-2b9e-419a-b9de-dd959fc05f05&noteKey=97c0f19486d851b3&sn=https%3A%2F%2Fwww.evernote.com%2Fshard%2Fs368%2Fsh%2Fb1359883-2b9e-419a-b9de-dd959fc05f05%2F97c0f19486d851b3&title=Git)
