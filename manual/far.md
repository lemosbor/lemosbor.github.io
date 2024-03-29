## Файловый менеджер FAR
   Помню, как в 1995 году отец установил на домашнем ПК Windows 95.  Проснувшись
утром,  я  запустил  компьютер  и  каково  было  моё  удивление,   когда   вместо
стандартного синего экрана запустилась какая-то «игра» с папочками и корзинками.
Помню, как я злился, от того, что не могу зайти обратно в привычную операционную
систему с синим экраном. Так я отвык от Norton Commander-а.

## Базовые настройки
### Ретранслитерация набранного текста с русского на английский алфавит
Функция установлена в FAR по-умолчанию. 
Для активации необходимо записать один из макросов горячих клавиш (например Far\Addons\XLat\Russian\AltR.lua) в папку 
\Profile\Macros\scripts
Для замены соответствия букв необходимо пересапоставить их в файле Far\Addons\XLat\Russian\Qwerty.farconfig

	<setting key="XLat" name="Table1" type="text" value="АБВГДЕЖЗИЙКЛМНОПРСТУФХЦШЩЫЬЯабвгдежзийклмнопрстуфхцшщыья" /> <!-- Non-english symbols -->
        <setting key="XLat" name="Table2" type="text" value="ABWGDEVZIJKLMNOPRSTUFHC{}YXQabwgdevzijklmnoprstufhc[]yxq" /> <!-- English symbols -->


После этого запустить команду для обновления настроек Far.exe /import Qwerty.farconfig
Для отключения автоматического переключения системной раскладки после ретранслитерации
необходим заменить параметр в строке <setting key="XLat" name="Flags" type="qword" value="0000000000010001" />
с 0000000000010001 на 0000000000010002.

### Подписи линейки функциональных клавиш
Замена подписей функциональных кловиш осуществляется с помощью файла Addons\SetUp\KeyBarLabels.farconfig
Для применения измнений запустить команду для обновления настроек Far.exe /import KeyBarLabels.farconfig

	<setting key="KeyBarLabels.Russian.Shell" name="F1" type="text" value="Справка" />
        <setting key="KeyBarLabels.Russian.Shell" name="F2" type="text" value="Команды" />
        <setting key="KeyBarLabels.Russian.Shell" name="F9" type="text" value="Меню" />
        <setting key="KeyBarLabels.Russian.Shell" name="ShiftF1" type="text" value="Архив" />
        <setting key="KeyBarLabels.Russian.Shell" name="ShiftF4" type="text" value="Создать" />
        <setting key="KeyBarLabels.Russian.Editor" name="F3" type="text" value="Расположен" />
        <setting key="KeyBarLabels.Russian.Editor" name="F9" type="text" value="Орфография" />

### Редактор конфигурации
Запуск редактора конфигурации осуществляется из командной строки по команде far:config
Чтобы файлы всегда создавались без BOM, можно задать специальный параметр Editor.AddUnicodeBOM = false


## Почему я стал использовать FAR
   В 2021 году я решил максимально использовать клавиатуру, чтобы не отвлекаться
на мышку и не тратить драгоценное время на перетаскивание файликов из папочки  в
папочку. Постоянное перетаскивание файлов  и  блуждание  по  папкам  очень  меня
нервировали в то время. Хотелось минимализма и простоты. Тогда  я  вспомнил  про
старый добрый Norton Commander, а вернее его реинкорнацию —  FAR  Manager.  Весь
январь 2021 года я переучивался использовать его вместо стандартного  проводника
и стал перемещаться по директориям и  перемещать  файлы  с  невиданной  до  того
скоростью. Простота и минимализм FAR-а, в сочетании  с  ностальгией  о  детстве
покорили меня. Вскоре  я  понял,  что  FAR  можно  использовать  не  только  как
стандартный  файловый  менеджер,  но  и  как  стандартный  текстовый   редактор,
стандартный плеер, просмоторщик изображений и пр.

### Параметры — Режим панели файлов

	 ╔══════════════════════════════ Полный ══════════════════════════════╗
	 ║ Имя                                                                ║
	 ║                                                                    ║
	 ║ Типы колонок                     Типы колонок строки статуса       ║
	 ║ NO,DMB,SEF,Z                     DC,NRN,X,Z,O                      ║
	 ║ Ширина колонок                   Ширина колонок строки статуса     ║
	 ║ 0,0,5,20%                        14,50%,4,0,0                      ║
	 ╟────────────────────────────────────────────────────────────────────╢
	 ║ [ ] Полноэкранный режим                                            ║
	 ║ [x] Выравнивать расширения файлов                                  ║
	 ║ [ ] Выравнивать расширения папок                                   ║
	 ║ [ ] Показывать папки заглавными буквами                            ║
	 ║ [ ] Показывать файлы строчными буквами                             ║
	 ║ [ ] Показывать имена файлов из заглавных букв строчными буквами    ║
	 ╟────────────────────────────────────────────────────────────────────╢
	 ║                   { OK } [ Сбросить ] [ Отмена ]                   ║
	 ╚════════════════════════════════════════════════════════════════════╝

## Необходимые плагины
   Как  и   многие   другие   программы,   разрабатываемые   энтузиастами,   FAR
устанавливается без лишних примочек в чистом  виде,  а  все  необходимые  плагины
необходимо устанавливать самому.  Большинство  пользователей  останавливается  в
освоении FARа на стадии непонимания  того,  как  сделать  из  этого  привета  из
далёкого прошлого программу, которая могла бы  заменить  стандартный  пoровдник.
Кроме плагинов в  FARе  устанавливаются  всевозможные  макросы,  упрощающие  его
использование. Сперва перечислю плагины, которые использую я.

### [LuaSpell](https://github.com/Raidar/LuaSpell/tree/master) — проверка орфографии в редакторе
После включения (посредствам горячей клавиши) подсвечивает не корректные слова.
Для установки необходимо:
1. Записать файл LuaSpell.lua в папку \Profile\Macros\scripts\
2. Сохранить словари ru_RU.dic, ru_RU.aff в папку \Profile\Dictionaries
3. Сохранить исполняемые файлы F:\Far\hunspellx64.dll и F:\Far\hunspellx86.dll в корень папки FAR
4. Сохранить файлы hunspell.lua и userdict.lua в папку \Profile\Macros\modules\
5. Создать пользовательский словарь исключений в папке \Profile\Dictionaries под названием
User_Dict.dic и с следующей структурой:
	
		OOoUserDict1
		lang: rus
		type: positive
		---
		Абракадабра 
		Броведено

6. В файле добавить LuaSpell.lua:  

		lng = "rus",
		desc = "OOoUserDict",
		Type = "UserDict",
		WordType = "enabled",
		StrToPath = false,
		path = DictionaryPath,
		filename = "User_Dict",
		match = DicMatch,
		Enabled = true,
		BreakOnMatch = true,

Для подсветки задать цвет:

	ForegroundColor = 0xFF00000F,
	BackgroundColor = 0xFF000004,

Задать горячие клавиши:

	CheckSpell  = "Apps",            -- - проверка текущего слова.
	SwitchCheck = "F9",     		  -- - переключение подсветки ошибочных слов.
	UnloadSpell = "LCtrlLAltShiftF12",  -- - завершение проверки (выгрузка).
	FindNext    = "F16",           --   - следующее ошибочное слово.
	FindPrev    = "ShiftF16",      --   - предыдущее ошибочное слово.

https://kitscenarist.ru/downloads/hunspell/
https://github.com/LibreOffice/dictionaries/tree/master

### MoreHistory - продвинутая история просмотра  папок  и  файлов.  Продвинутость
заключается в том, что после того, как ты запустил  плагин,  начинаешь  печатать
название необходимой папки, а  плагин  сам  предлагает  тебе  варианты  из  тех,
которые ты просматривал в последнее время. Благодаря этому плагину  всевозможные
ярлыки (ссылки на нужные папки) стали не нужны. Я просто вбиваю название папки и
плагин меня туда тут же перемещает.

	╔ История активн папок [заме] (9/391) ╗
	║ Сегодня, Пт 27 (1)                  ║
	║  C:\Заметки                    1:20 ║
	║                                     ║
	║ Ранее на этой неделе (1)            ║
	║  C:\Заметки\Дом               Ср,25 ║
	║                                     ║
	║ Ранее в этом месяце (5)             ║
	║  C:\Заметки\Номера            Вт,17 ║
	║  C:\Заметки\Увлечения         Вт,10 ║
	║  C:\Заметки\Купить            Вс,08 ║
	║  C:\Заметки\Справочная        Сб,07 ║
	║  C:\Заметки\Поливаново        Сб,07 ║
	║                                     ║
	║ В прошедшем году (2)                ║
	║  C:\Заметки\Мысли             31/12 ║
	║  C:\Заметки\Работа            23/12 ║
	╚═════════════════════════════════════╝

### Really Quick Player - плеер для воспроизведения mp3 файлов. Имеет  лаконичное
окно проигрывания и позволяет воспроизводить автоматически все песни из папки.
Для чтобы файл mp3 открывался плагином Really Quick Player, а не системным пле
ером, В ассоциации для *.mp3 укажи строку rqp:"!.!"

	╔════════════════════ 05 - Carry You Home.mp3 ════════════════[]═╗
	║                                                                  ║
	║      0:05.747 [=|----------------------------------------------] ║
	║                                                                  ║
	║  <   ║   >   ■   Демо   Авто-След.    .....::____  L=====C=====R ║
	║                                                                  ║
	║ Circa Waves - Carry You Home - Never Going Unde                  ║
	║ MP3, 44100 Hz, 2 ch, 325 kbps, 3:19.066                          ║
	║  Внеш. плеер                                                     ║
	╚══════════════════════════════════════════════════════════════════╝

### LFBlock - выравнивание текста в редакторе по ширине страницы. Заменяет Microsoft Word.

	╔════════════ Форматирование блока ═════════════╗
	║ Левая граница  1                              ║
	║ Первая строка  4                              ║
	║ Правая граница 80                             ║
	╟───────────────────────────────────────────────╢
	║ Выравнивание         Обнаружение абзацев      ║
	║   ( ) По левой          ( ) Выкл              ║
	║   ( ) По правой         ( ) Каждая строка     ║
	║   ( ) По центру         ( ) По пустой строке  ║
	║   (•) По ширине         ( ) По отступу        ║
	║   ( ) Полностью         (•) Отступ и строка   ║
	╟───────────────────────────────────────────────╢
	║      [ ] Пустая строка после параграфа        ║
	╟───────────────────────────────────────────────╢
	║               { Ok } [ Отмена ]               ║
	╚═══════════════════════════════════════════════╝

### LuaFAR Search - продвинутый поиск  в  тексте.  Позволяет  искать  и  заменять
переменные. 
Примеры
1. заменить  все  вхождения  х  в  строках  на
порядковые номера выделяю в редакторе блок. Вызываю диалог замены плагина. Искать: х Заменить на: \R 
Настрока: [x] Регулярное выражение
	
		╔═══════════════════════ Многострочная замена ═══════════════════════╗
		║ Искать:                                                            ║
		║ х                                                                 ↓║
		║ Заменить на:                                                       ║
		║ \R                                                                ↓║
		║     [ ] Режим функции                                              ║
		╟────────────────────────────────────────────────────────────────────╢
		║ [x] Регулярное выражение          Библиотека: Far regex    ↓       ║
		║ [ ] Учитывать регистр             [ ] Файл как строка              ║
		║ [ ] Целые слова                   [ ] Многострочный режим          ║
		║ [ ] Игнорировать пробелы                                           ║
		╟────────────────────────────────────────────────────────────────────╢
		║ [ ] Дополнительно                                                  ║
		║ Начальный код:                    Конечный код:                    ║
		║                                 ↓                                 ↓║
		╟────────────────────────────────────────────────────────────────────╢
		║                { Заменить } [ Подсчёт ] [ Отмена ]                 ║
		╚════════════════════════════════════════════════════════════════════╝

2. Заменить переносы строк в определенных местах на символ
   
		# Кедрова 
		21

Искать `\n+(?=\d)` (найти перенос сроки до цифры идущей следом) заменить на ` | ` в режиме регулярных выражений.
Получаем

		# Кедрова | 21

3. Для редактирования текста из pdf заменить переносы строк после которых идут строчные буквы на пробелы `\n+(?=\l)`

### VisRen (Визуальное переименование файлов) - позволяет  переименовывать  файлы
по их внутренним тегам (например по названию и артисту, если файл mp3).

	╔═════════════════════ Визуальное переименование файлов ══════════════════[]╗
	║ Маска для имени файла:                 расширения:                         ║
	║ [a] - [t]                            ↓ [E]                                ↓║
	║ Шаблоны:                                                                   ║
	║ [N]    Имя                    ↓ [+]    [E]    Тип                    ↓ [+] ║
	╟────────────────────────────────────────────────────────────────────────────╢
	║ Найти:                               ↓ [x] Учитывать регистр               ║
	║ Заменить на:                         ↓ [ ] Регулярные выражения            ║
	╟────────────────────────────── имя до - после ──────────────────────────────╢
	║   10 - Hold On.mp3                   │Circa Waves - Hold On.mp3            ║
	║   11 - Living in the Grey.mp3        │Circa Waves - Living in the Grey.mp  ║
	║   07 - Electric City.mp3             │Circa Waves - Electric City.mp3      ║
	║   08 - Want It All Today.mp3         │Circa Waves - Want It All Today.mp3  ║
	║   09 - Golden Days.mp3               │Circa Waves - Golden Days.mp3        ║
	║   01 - Never Going Under.mp3         │Circa Waves - Never Going Under.mp3  ║
	║   02 - Do You Wanna Talk.mp3         │Circa Waves - Do You Wanna Talk.mp3  ║
	║   03 - Hell On Earth.mp3             │Circa Waves - Hell On Earth.mp3      ║
	║   04 - Your Ghost.mp3                │Circa Waves - Your Ghost.mp3         ║
	║   05 - Carry You Home.mp3            │Circa Waves - Carry You Home.mp3     ║
	║   06 - Northern Town.mp3             │Circa Waves - Northern Town.mp3      ║
	╟──────────────────────── √ Протокол переименования ─────────────────────────╢
	║     { Переименовать } [ F6-Откатить ] [ F4-В редакторе ] [ Отменить ]      ║
	╚════════════════════════════════════════════════════════════════════════════╝

### PortaDev plugin — просмотр фотографий с айфона

### LuaShell — запуск макросов из вызываемой отовсюду командной строки (альтернатива горячим клавишам)
Содержит полезные утилиты

#### В редакторе:
lineup_i.lua — выравнивание текста по символам
lineup_pipe.lua — выравнивание таблиц по линиям | | 
grep.lua — паказать все вхождения слова под курсором
dupfighter.lua — удаление дублирующихся строк
expr.lua — вычислениз записанных выражений
lf4ed.lua — сортировка строк, выравнивание текста и пр.
char.lua — таблица символов

#### В панелях:
pfilt.lua — быстрый фильтр по названию
cdup.lua — переход к родительской папке
envman.lua — перечень переменных окружения
disk.lua — быстрый выбор дисков
dbedit.lua — редактор БД (переменных) плагинов
cdd.lua — история команд текущего коталога

## Команды
set /? — справка по функции
Рекомендуется всегда использовать с командой опцию /d для смены одновременно и текущего диска. Например, "cd /d d:\delta". 
echo %cd%  — показать текущий путь
точка "." обозначает текущий каталог, а две точки ".." - каталог уровнем выше. Команда "cd ..\.." указывает, что нужно перейти двумя каталогами выше. 
http://dl.gsu.by/doc/use/ntcmds.htmе
macro: load - команда перезагрузки макросов
tmp: - открывает временную панель.
tmp: < dir /b - выводит на временную панель все файлы и папки активной панели.
tmp: < dir /b *.jpg - выводит на временную панель все файлы с расширением *.exe активной панели.  
tmp: < dir /b/s/a-d - выводит на временную панель все файлы в текущей папке и всех ее подпапках.
tmp: < dir /b/s/a-d *.jpg - выводит на временную панель все файлы в текущей папке и всех ее подпапках.
tmp: < dir C:\WINDOWS\*.dll 
whereis: — перейти к файлу
goto:  — перейти к файлу или папке
edit: — редактировать файл. edit: < help - отображение вывода команды help в редакторе FAR.
view: — просмотреть файл. view: < help - отображение вывода команды help в стандартном вьювере FAR.
far:regex  — тестирование регулярных выражений

[метасимволы](https://documentation.help/Far-Manager-ru/MetaSymbols.html)
http://xlench.bget.ru/doku.php/tools/far/comline
http://dl.gsu.by/doc/use/ntcmds.htmе

### регулярные выражения
^\s+ пробелы между абзацами
^\n пробелы между абзацами (пустые строки)
 \s+ множественные пробелы
 \n вводы
яблоки|груши - найти яблоки или груши
[0-9] числа

## Настройки интерфейса
Вид окна Полный
типы колонок: NO, DM, SEF, Z ширина: 0, 0, 5, 30% типы колонок строки: DC, A, Z, X

### Ассоциации файлов
#### Внутренний редактор
*.txt, *.md, *.lua, *.ahk, *.bas, *.ini
edit:"!.!"

#### Рисунки
*.jpg, *.jpeg, *.gif
"F:\JPEGViewPortable\JPEGViewPortable.exe" "!\!.!"
