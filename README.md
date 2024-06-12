Шпаргалка по Git
----

**Git** — самая популярная система контроля версий, которая позволяет отслеживать изменения в проекте.

### Пошаговая инструкция по работе с Git ###

#### Инициализируем репозиторий ####

**Сделать папку репозиторием** — `git init`

Чтобы Git начал отслеживать изменения в проекте, папку с файлами этого проекта нужно сделать Git-репозиторием (от англ. repository — «хранилище»). Для этого следует переместиться в неё и ввести команду `git init` (от англ. initialize — «инициализировать»).

**Проверить состояние репозитория** — `git status`
 
После инициализации репозитория `first-project` запустите команду `git status` (от англ. status, «статус», «состояние») — она показывает текущее состояние репозитория.
 

#### Добавляем файлы в репозиторий ####

**Подготовить файлы к сохранению** — `git add`

Если провести аналогию, команду `git add` можно сравнить с добавлением товаров в корзину в интернет-магазине, а коммит — с оформлением и оплатой заказа.


#### Делаем первый коммит ####

**Выполнить коммит** — `git commit`

Сделать коммит можно командой `git commit` c ключом `-m` (от англ. message — «сообщение»), который присваивает коммиту сообщение.

Обычно в таком сообщении поясняется, в чём именно состояли изменения. Это как заметки на полях: благодаря им проще читать и понимать текст. Сообщение коммита выполняет те же функции — улучшает понимание и упрощает навигацию. Оно пишется после ключа `-m` в кавычках.

**Ещё раз о разнице между `git add` и `git commit`**

Сначала команда `git add` сообщает `Git`, какие именно файлы нужно сохранить и какую их версию. Затем с помощью команды `git commit` происходит само сохранение. 


#### Просматриваем историю коммитов ####

**Просмотреть историю коммитов** — `git log`

Чтобы увидеть коммиты, введите команду `git log` (от англ. log — «журнал [записей]»). Обратите внимание, что по умолчанию `git log` выводит коммиты в обратном хронологическом порядке — последние коммиты оказываются первыми сверху. В этом можно убедиться, если посмотреть на дату и время их создания.


Знакомство с GitHub
----

**GitHub** — платформа для хранения IT-проектов и их командной разработки с использованием Git. По сути, это сайт, куда можно загрузить файлы своего проекта для обмена с другими людьми.


### Git и платформы для удалённой работы ### 

Git и GitHub — это два разных проекта, которые развиваются независимо друг от друга. 

Git:
* консольный инструмент для работы с локальными и удалёнными репозиториями;
* проект с открытым исходным кодом.

GitHub:
* платформа для размещения удалённых репозиториев;
* принадлежит компании Microsoft.


### Регистрируемся на GitHub и создаём удалённый репозиторий ###

#### Инструкция по регистрации ####

1. В правом верхнем углу главной страницы GitHub нажмите на Sign up (англ. «зарегистрироваться»).

2. На экране будут последовательно появляться поля для ввода.

2.1 Введите адрес электронной почты (англ. Enter your email).

2.2 Придумайте пароль (англ. Create a password).

2.3 Введите имя пользователя (англ. Enter a username).

2. Платформа спросит, хотите ли вы получать на почту рассылку с обновлениями и новостями (англ. Would you like to receive product updates and announcements via email?). Введите `y`, если хотите получать рассылку, или `n`, если не хотите.

4. Нажмите кнопку Continue (англ. «продолжить»).

5. GitHub предложит вам пройти капчу. Сделайте это.

6. После прохождения капчи нажмите Create account (англ. «создать аккаунт»).

7. Введите короткий код, который будет отправлен на указанный вами почтовый адрес.

#### Инструкция по созданию репозитория на GitHub ####

1. Зайдите в свой профиль по ссылке `https://github.com/username`, где `username` — имя, которое вы указали при регистрации.

2. Создайте репозиторий. Для этого перейдите на вкладку **Repositories** (англ. «репозитории»), а затем нажмите на зелёную кнопку **New** (англ. «новый») справа. 



# Хеш, лог и HEAD

## Хеш — идентификатор коммита

**Хеширование** (от англ. hash, «рубить», «крошить», «мешанина») — это способ преобразовать набор данных и получить их «отпечаток» (англ. fingerprint).

Информация о коммите — это набор данных: когда был сделан коммит, содержимое файлов в репозитории на момент коммита и ссылка на предыдущий, или **родительский** (англ. parent), коммит. Git хеширует (преобразует) эту информацию с помощью алгоритма **SHA-1** (от англ. Secure Hash Algorithm — «безопасный алгоритм хеширования») и получает для каждого коммита свой уникальный хеш — результат хеширования.
В то время, как результат работы метода `hashCode()` — это целое число, результат хеширования в Git — символьная строка. Она относительно коротка (40 символов в случае SHA-1) и состоит из цифр 0—9 и латинских букв A—F (неважно, заглавных или строчных). Хеш обладает следующими важными свойствами:
* если хеш получить дважды для одного и того же набора входных данных, то результат будет гарантированно одинаковый;
* если хоть что-то в исходных данных поменяется (хотя бы один символ), то хеш тоже изменится (причём сильно).

Git хранит таблицу соответствий `хеш → информация о коммите`. Если вы знаете хеш, вы можете узнать всё остальное: автора и дату коммита и содержимое закоммиченных файлов. Можно сказать, что хеш — основной идентификатор коммита.

При работе с Git хеши будут встречаться вам регулярно. Их можно будет передавать в качестве параметра разным Git-командам, чтобы указать, с каким коммитом нужно произвести то или иное действие.

Все хеши и таблицу `хеш → информация` о коммите Git сохраняет в служебные файлы. Они находятся в скрытой папке `.git` в репозитории проекта.


## Исследуем лог

После вызова `git log` появляется список коммитов с их описанием.

Вот из каких элементов состоит описание:
 1. Строка из цифр и латинских букв после слова commit — это уже знакомый вам хеш коммита.
 2. **Author** — имя автора и его электронная почта.
 3. **Date** — дата и время создания коммита.
 4. Сообщение к коммиту.

Если в репозитории уже много коммитов — например, сотни или тысячи, — пригодится сокращённый лог. С ним можно быстро найти нужный коммит по описанию.

Сокращённый лог вызывают командой `git log` с флагом `--oneline` (англ. «одной строкой»). При этом в терминале появятся только первые несколько символов хеша каждого коммита и комментарии к ним.

Сокращённый хеш (первые несколько символов полного) можно использовать точно так же, как и полный. Для этого команда `git log --oneline` автоматически подбирает такую длину сокращённых хешей, чтобы они были уникальными в пределах репозитория и Git всегда мог понять, о каком коммите идёт речь.

Обратите внимание: если выход из просмотра логов не произошёл автоматически, нажмите клавишу `Q` (от англ. **Q**uit — «выйти») в английской раскладке клавиатуры.


## `HEAD` — всему голова

Файл `HEAD` (англ. «голова», «головной») — один из служебных файлов папки `.git`. Он указывает на коммит, который сделан последним (то есть на самый новый).

Внутри `HEAD` — ссылка на служебный файл: `refs/heads/master` (или `refs/heads/main` в зависимости от названия ветки). Если заглянуть в этот файл, можно увидеть хеш последнего коммита.

Когда вы делаете коммит, Git обновляет `refs/heads/master` — записывает в него хеш последнего коммита. Получается, что `HEAD` тоже обновляется, так как ссылается на `refs/heads/master`.

При работе с Git указатель `HEAD` используется довольно часто. Мы уже упоминали, что многие команды Git принимают в качестве параметра хеш коммита. Если нужно передать последний коммит, то вместо его хеша можно просто написать слово `HEAD` — Git поймёт, что вы имели в виду последний коммит.


## Зачем нужны статусы файлов и как читать git status

Частая ошибка при использовании Git — закоммитить лишнее или, наоборот, забыть добавить важный файл в коммит. Этого можно избежать, если не забывать проверять состояния (или статусы) файлов командой `git status`. В этом уроке разберём подробнее, в каких состояниях могут находиться файлы в репозитории и как читать вывод `git status`.

### Статусы `untracked`/`tracked`, `staged` и `modified`

Одна из ключевых задач Git — отслеживать изменения файлов в репозитории. Для этого каждый файл помечается каким-либо статусом. Рассмотрим основные.

* `untracked` (англ. «неотслеживаемый»)

Новые файлы в Git-репозитории помечаются как `untracked`, то есть неотслеживаемые. Git «видит», что такой файл существует, но не следит за изменениями в нём. У `untracked`-файла нет предыдущих версий, зафиксированных в коммитах или через команду git add.

* `staged` (англ. «подготовленный»)

После выполнения команды `git add` файл попадает в **staging area** (от англ. *stage* — «сцена», «этап [процесса]» и *area* — «область»), то есть в список файлов, которые войдут в коммит. В этот момент файл находится в состоянии `staged`.

💡 Staging area также называют **index** (англ. «каталог») или **cache** (англ. «кеш»), а состояние файла `staged` иногда называют `indexed` или `cached`. Все три варианта могут встречаться в документации и в качестве флагов команд Git. А также в интернете — например, в вопросах и ответах [на сайте Stack Overflow](https://stackoverflow.com/).

* `tracked` (англ. «отслеживаемый»)

Состояние `tracked` — это противоположность `untracked`. Оно довольно широкое по смыслу: в него попадают файлы, которые уже были зафиксированы с помощью `git commit`, а также файлы, которые были добавлены в staging area командой `git add`. То есть все файлы, в которых Git так или иначе отслеживает изменения.

* `modified` (англ. «изменённый»)

Состояние `modified` значит, что Git сравнил содержимое файла с последней сохранённой версией и нашёл отличия. Например, файл был закоммичен и после этого изменён.

Вот что ещё важно учесть:

* Для файлов в состояниях `staged` и `modified` обычно не указывается, что они также `tracked`, потому что это состояние подразумевается.

* Команда `git add` добавляет в staging area только текущее содержимое файла. Если вы, например, сделаете `git add file.txt`, а затем измените `file.txt`, то новое содержимое файла не будет находиться в staging. Git сообщит об этом с помощью статуса `modified`: файл изменён относительно той версии, которая уже в staging. Чтобы добавить в staging последнюю версию, нужно выполнить `git add file.txt` ещё раз.

### Типичный жизненный цикл файла в Git

Может показаться, что файлы в репозитории попадают в разные состояния хаотично. На практике это не так, и у большинства файлов вполне предсказуемый путь.



```mermaid
graph LR;
UNTRACKED--"git add"-->STAGED+TRACKED;
MODIFIED--"git add"-->STAGED+TRACKED;
STAGED+TRACKED--"git commit"-->TRACKED;
TRACKED--"изменения"-->MODIFIED;
STAGED+TRACKED-->MODIFIED;
```


1. Файл только что создали. Git ещё не отслеживает его содержимое. Состояние: `untracked`.
2. Файл добавили в staging area с помощью `git add`. Состояние: `staged` (+ `tracked`).

      a. Возможно, изменили файл ещё раз. Состояния: `staged`, `modified` (+ `tracked`).
 Обратите внимание: `staged` и `modified` у одного файла, но у разных его версий.  
      b. Ещё раз выполнили `git add`. Состояние: `staged` (+ `tracked`).
3. Сделали коммит с помощью `git commit`. Состояние: `tracked`.
4. Изменили файл. Состояние: modified (+ tracked).
5. Снова добавили в staging area с помощью `git add`. Состояния: `staged` (+ `tracked`).
6. Сделали коммит. Состояния: `tracked`.
7. Повторили пункты 4−7 много-много раз.

### Какие состояния показывает команда `git status`

Большинство файлов в типичном проекте будут находиться в состоянии `tracked` (то есть закоммичены и не изменены после коммита). Вы не увидите это состояние в выводе команды `git status` — иначе она бы каждый раз выводила список вообще всех файлов проекта. В итоге `git status` показывает только следующие состояния файлов:
* `staged` (`Changes to be committed` в выводе git status);
* `modified` (`Changes not staged for commit`);
* `untracked` (`Untracked files`).

Рассмотрим четыре примера состояний, в которых может находиться ваш репозиторий. Допустим, мы инициализировали новый репозиторий `~/dev/git-status-lesson`. Создали в нём файл `README.md` и закоммитили его.

1. **Нет ни `staged`-, ни `modified`-, ни `untracked`-файлов**.

Если ничего не менять в `git-status-lesson` после первого коммита, то в нём не должно быть ни изменённых файлов (`modified`), ни новых (`untracked`), ни добавленных в список на коммит (`staged`). 

2. **Найдены неотслеживаемые файлы.**

Создали в папке `~/dev/git-status-lesson` файл `fileA.txt`. Теперь в репозитории есть новый файл в состоянии `untracked`. Снова вызовем команду `git status`.

Файл `fileA.txt` отображается в секции неотслеживаемых файлов — `Untracked files`. Это значит, что он не был добавлен в репозиторий через `git add`.
В выводе `git status` есть подсказка, какую команду использовать, чтобы добавить файл в список на коммит: *Use git* `add <file>` *to include in what will be committed* (англ. «используйте `git add <file>`, чтобы добавить в список на коммит»). Добавьте `fileA.txt` в staging area с помощью `git add` и снова запросите git status.

Теперь `fileA.txt` находится в секции `Changes to be committed` (англ. «изменения, которые попадут в коммит»). Если сейчас выполнить коммит, то в репозитории будет зафиксирована текущая версия этого файла. Закоммитим его.

Вывод команды git status такой же, какой был после первого коммита: «Директория чиста».

3. **Найдены изменения, которые не войдут в коммит**

Теперь откройте файл `fileA.txt` и добавьте в него несколько слов — например, `Это файл A!`. Сохраните `fileA.txt` и вызовите команду `git status`. 

Файл `fileA.txt` был изменён, но не добавлен в staging area после этого. Так он оказался в секции `Changes not staged for commit` (англ. «изменения, которые не подготовлены к коммиту»), соответствующей статусу `modified`. Подготовьте правки к коммиту через `git add`.

Теперь в коммит попадёт уже новая версия файла `fileA.txt`. Обратите внимание: хотя вывод команды `git status` похож на тот, что был после первого добавления файла `fileA.txt`, они отличаются. Когда новый файл попадает в staging area, перед его названием указывается `new file: new file: fileA.txt`. Если файл уже однажды попадал в историю (с помощью коммита) и был изменён, после выполнения `git add` он будет записан уже так: `modified: fileA.txt`.

4. **Файл добавлен в staging area, но после этого изменён**

Вы добавили файл в staging area, но перед коммитом вспомнили нечто важное. Например, вместо одного восклицательного знака в конце строки `Это файл A!` нужно поставить три.

Откройте текстовый редактор и добавьте нужные правки. Теперь можно выполнить коммит, но в любой непонятной ситуации сначала стоит вызвать `git status`.

Файл попал и в `staged` (`Changes to be committed`), и в `modified` (`Changes not staged for commit`). В staging area находится версия файла с одним восклицательным знаком, а в `Changes not staged for commit` — уже изменённая версия, с тремя. Чтобы закоммитить самую свежую версию файла, нужно снова выполнить `git add` перед коммитом. Готово!
