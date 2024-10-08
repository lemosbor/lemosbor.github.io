## Удаление сджимого файла
@ECHO OFF 
FOR /R C:\01\05 %f IN (*.txt) DO TYPE NUL>%f

## Конвертация в flac
### Вариант 1 
for /r %i in (*.flac) do "C:\Program Files (x86)\FlacSquisher\flac.exe" -d -c "%i" | "C:\Program Files (x86)\FlacSquisher\lame.exe" 
--abr 320 --noreplaygain - "%~dpni.mp3"

### Вариант 2
ffmpeg -i "01 Pain.flac" -ab 320k -map_metadata 0 -id3v2_version 3 output.mp3

for %%f in (*.flac) do (ffmpeg -i "%%f" -ab 320k -map_metadata 0 -id3v2_version 3 "%%f.mp3")

## Разархивировать архивы в папку по дате
@ECHO OFF
set name=%date%
echo %name%
mkdir %name%
ROBOCOPY .  %name% *.zip *.7z *.rar *.mp3  /move /s /maxage:1
cd %name%
"C:\Program Files\7-Zip\7z.exe" e *.zip *.7z *.rar
del *.zip *.7z *.rar /s /f

#### выделить файлы по типу и перенести в папку (картинки в папку с картинками). Для перемещения файлов по типам:

	@echo off
	ROBOCOPY E:\Архив\2020\ E:\Архив\2020\архивы *.zip *.7z *.rar *.gz /MOV /IS /minage:1
	ROBOCOPY E:\Архив\2020\ E:\Архив\2020\Ворд *.doc /MOV /IS /minage:1
	ROBOCOPY E:\Архив\2020\ E:\Архив\2020\ПДФ *.pdf  /MOV /IS /minage:1
	ROBOCOPY E:\Архив\2020\ E:\Архив\2020\Ексель *.xls *.xlsx *.xlsb /MOV /IS /minage:1
	ROBOCOPY E:\Архив\2020\ E:\Архив\2020\Презы *.ppt *.pptx /MOV /IS /minage:1

#### Перееименовать файлы без расширений в файлы с расширениями:

	ren "*." "*.jpg"

mf.bat F:\Папка\01\ F:\Папка — извлечь все файлы и папки из папки и удалить её
где mf.bat:
echo off
for %%a in ("%1\*") do move /y "%%~fa" %2
for /d %%a in ("%1\*") do move /y "%%~fa" %2
rd %1
  
для последовательного запуска команд в одной строке используется оператор & 
чтобы вторая команда выполнялась только после успешного выполнения первой, используются формат &&
вторая команда будет выполнена, только если первая вернула ошибку ||

setx path "%PATH%;F:\JPEGViewPortable"
set path="%PATH%;F:\JPEGViewPortable"
mklink /j E:\Documents\Ярлыки\14 C:\02 — создать ссылку
copy C:\02\1.txt + E:\Documents\Ярлыки\6.txt C:\02\1.txt — соединить файлы
for /D %a in ("c:\01\*") do copy %a\1.txt + E:\6.txt %a\1.txt
ДУБЛИРОВАТЬ файл
setx path "%PATH%;C:\Users\____\AppData\Local\Programs\Python\Python37" создать path
attrib {+\|-}f Задает ( + ) или очищает ( - ) атрибут файл (attrib news86 — отобразить атрибуты файла)(attrib +r report.txt — присвоить атрибуту только для чтения) 
cd\ — вернуться к корневому каталогу (cd. > 01.txt — создать файл)
<command> | clip — (dir | clip — копирует список папок открытой директории)
clip < <filename> — (clip < readme.txt — копирует содержимое файла) 
copy con file.txt — создать файл и редактировать его (упр+з чтобы сохранить и выйти)
comp (comp c:\reports \\sales\backup\april — сравнивает две директории)
copy (copy robin.typ c:\birds — копирует файл из текущей директории в заданную) (copy mar89.rpt + apr89.rpt + may89.rpt Report — объединить файлы под именем Report)(copy report + mar89.rpt + apr89.rpt + may89.rpt — объединить файлы в существующем Report)(copy *.txt Combined.doc — объединить все текстовые в один док)
xcopy (xcopy \rawdata \reports /u — обновить файлы в папке rawdata с файлами в папке reports)(xcopy \rawdata \reports /d:12-29-1993 — обновить файлы в каталоге \репортс с файлами в каталоге \равдата, которые были изменены с 29 декабря 1993)(xcopy \rawdata \reports /d:12-29-1993 /l > xcopy.out — только получить список файлов для копирования)
Xcopy F:\Папка\01 F:\Папка /S /C /I копировать файлы из папки в папку со всем содержимым
move (move \data\*.xls \second_q\reports\ — переместить все файлы с расширением XLS из каталога \Data в каталог \ Second_Q)
del (del c:\test\*.*  удалить все файлы в папке с именем Test на диске C) (del *.bat удалить все файлы с расширением bat из текущего каталога) (del /a:r *.* удалить все файлы только для чтения в текущем каталоге)
dir c:\*.txt /w/o/s/p (отобразить список всех имен файлов с расширением txt во всех каталогах на диске C)
fc — сравнение файлов (fc /a monthly.rpt sales.rpt — выполнить сравнение в ASCII двух текстовых файлов)
find ""pencil sharpener"" pencil.txt отобразить все строки из Pencil.AD , которые содержат строку резкость карандаша
dir c:\ /s /b | find CPU  найти и отобразить имена файлов на диске C, которые содержат CPU
findstr Windows proposal.txt — найти все вхождения слова Windows
findstr /s /i Windows *.* Для поиска всех файлов в текущем каталоге и всех подкаталогах, содержащих слово Windows, независимо от регистра букв
findstr /s /i /m \<computer\> *.* получить список всех файлов, содержащих слово Computer в текущем каталоге и всех подкаталогах
findstr /s /i /m \<comp.*> *.* получить список всех файлов, содержащих слово Computer, и других слов, начинающихся с «Comp»
for %f in (*.doc *.txt) do type %f oтобразить содержимое всех файлов в текущем каталоге с расширением DOC или txt, используя заменяемую переменную % f
for /D %a in ("c:\0*") do copy E:\Documents\Ярлыки\6.txt %a — скопировать файл в несколько папок   (/y — без запроса)
for /D %a in ("c:\01\") do copy %a\1.txt + E:\Documents\Ярлыки\6.txt %a\1.txt — объединить файл 6.txt со всеми файлами 1.txt в папке 0*
for /D %a in ("c:\0*") do copy E:\Documents\Ярлыки\6.txt %a
FOR /F "tokens=1-2" %A IN ("fjhd dsdf asdf") DO @echo %B-%A — tokens определяет используемые ключи из множества
FOR /F "tokens=1-2 delims==," %A IN ("fjhd dsdf,asdf") DO @echo %B-%A — delims определяет разделитель; usebackq — опеределяет тип скобок
hostname — отобразить имя компьютера (hostname | clip — скопировать имя компьютера)
ipconfig — Отображает все текущие значения конфигурации сети TCP/IP (ipconfig /all — отобразить полную конфигурацию)
md Directory1 создать каталог с именем Directory1 в текущем каталоге
md \Taxes\Property\Current создать дерево каталогов
mklink Создает символьную или жесткую связь (mklink /j C:\01\Ж C:\02 — создать соединение с каталогом 02 в папке 01 с названием Ж)
mkdir создать папку
rmdir удалить папку
path - Установка значений переменных окружения (указание путей к каталогам)
rd /s test удалить каталог с именем Test (и все его подкаталоги и файлы) из текущего каталога
regsvr32 schmmgmt.dll — Регистрирует DLL-файлы в качестве компонентов команды в реестре.
ren *.txt *.doc изменить все расширения имени файла txt в текущем каталоге на расширения DOC
replace a:\phones.cli c:\ /s бновить все версии файла phones. CLI (который отображается в нескольких каталогах на диске C:) с последней версией файла phones. CLI с гибкого диска в дисководе a
runas /user:administrator "mklink args" — запуск от имени администратора
SET MyName=Vasya - установить значение переменной MyName
set PATH=%PATH%;C:\Documents and Settings\___\AppData\Local\Programs\Python\Python37 — 1добавить команду python в path / изменить значение переменной PATH, добавив
set PATH=%PATH%;C:\Users\___\AppData\Local\Continuum\anaconda3\
set PATH=%PATH%;C:\Documents and Settings\___\AppData\Local\Programs\Python\Python37\Scripts\
shutdown — выключить ПК
timeout /t 10 — приостановить обработчик команд в течение десяти секунд
tree \ отобразить имена всех подкаталогов на диске текущего диска
tree c:\ /f  prn — распечатать список всех каталогов на диске C
type holiday.mar —  отобразить содержимое файла
TASKLIST — перечень процессов
TASKKILL — завершить процесс tskill 6543 — завершить процесс 6543
where /r c:\ test — найти все файлы с именем Test на диске C текущего компьютера и его подкаталогов
for %a in (*.doc *.docx) do "C:\Program Files\Microsoft Office\Office15\WINWORD.EXE" /q /w "%a" /m"txt" перевод из .doc в txt
exit() выйти из команды Python
c\windows\system32\shutdown.exe -s -f -t {1800, 3600, 5400} автовыключение ПК

chcp 65001 - перевести кодировку терминала в юникод

две команды в одной:
You can use the special characters listed in the following table to pass multiple commands.

    & [...]
    command1 & command2
    Use to separate multiple commands on one command line. Cmd.exe runs the first command, and then the second command.

    && [...]
    command1 && command2
    Use to run the command following && only if the command preceding the symbol is successful. Cmd.exe runs the first command, and then runs the second command only if the first command completed successfully.

    || [...]
    command1 || command2
    Use to run the command following || only if the command preceding || fails. Cmd.exe runs the first command, and then runs the second command only if the first command did not complete successfully (receives an error code greater than zero).

    ( ) [...]
    (command1 & command2)
    Use to group or nest multiple commands.

    ; or ,
    command1 parameter1;parameter2
    Use to separate command parameters.

for /D %a in (*.txt) do copy %a + E:\1.txt — объединить файл 6.txt со всеми файлами 1.txt в папке copy *.txt E:\1.txt

| more 
| less - показать не весь вывод, а его частьz

CLS — очистить консоль
CHCP — сменить кодировку

Переменные
%CD% — название текущей папки
%date% — дата
%TIME% — время
%RANDOM% — случайное число 0...32767
echo %date%-%time:~-11,2%.%time:~-8,2% 01.01.2021-15.10


## Regex cmd (только для английского)  
findstr /r "[a-z]m[a-z]" test - найти вес строки начинающиеся со слова на m
findstr /r /v"[a-z]m[a-z]" test - найти вес строки не начинающиеся со слова на m

## Regex PowerShell  
Select-String -Pattern '^ожог' -Path 'f:\3\so'  — найти в фале so все слова, начинающиеся на ожог)
(Select-String -Pattern 'вх.*ди' -Path 'f:\3\so'|Measure-Object).Count — количество слов на вх..од..
Select-String -Pattern '\b[вход]+\b' -Path 'f:\3\so' | Select-Object -ExpandProperty line  — слова на буквы: вход
(Select-String -Pattern '^ожог' -Path 'f:\3\so' | Select-Object).line -replace "[\t\d]","" -join ' ' — вывести в строку слова по образцу
NotMatch - для  не совпадающих