## Перерывы в работе
Для эффективной работы необходимо делать регулярные перерывы. Чтобы перерывы были неотложными, ПК должен самосоятельно блокироваться через определеннные
промежутки времени. 
Проще всего это сделать с помощью Планировщика заданий. Выбрать в меню Действие→Создать задачу. Имя: Отдых; Триггеры: При разблокировании рабочей станции; Отложить
задачу на 30 минут (время рабоды до перерыва). Действия: Запуск программы. Программа или сценарий: %windir%\System32\rundll32.exe; Добавить аргумент: user32.dll,LockWorkStation  
Теперь после разблокировании ПК через 30 минут он будет снова заблокирован, что будет означать, что нужно прогуляться на 5 минут.

## Установка не системной раскладки
В папке amd64 скопиравать файл и переименовать его в KBDUSX.DLL

После этого скопировать его в системную папку С: \\Windows\\System32

Не системную раскладку настраивать здесь:
p\\HKEY\_LOCAL\_MACHINE\\SYSTEMNCurrentControlSet\\Contra/KeyboardLayouts\\a0000c00


## Outlook
Для того, чтобы курсор выделения автоматически не перемещался, необходимо снять настройку Параметры редактора→Дополнительно→Автоматически выделять слова
[коды клавиш в Windows](https://docs.microsoft.com/en-us/dotnet/api/system.windows.forms.keys?view=windowsdesktop-6.0)

## Увеличение скороси мигания курсора
команда из консоли: control keyboard
HKEY_CURRENT_USER\Control Panel\Desktop\CaretTimeout задается таймаут мигания курсора
 в формате DWORD. По умолчанию там стоит 5000мс, надо поменять за ffffffff
в firefox about:config  ui.caretWidth поменя на 2

## Увеличение скорости движения курсора
Перейти к Computer\HKEY_CURRENT_USER\Control Panel\Accessibility\Keyboard Response
Установите следующие значения:
    AutoRepeatDelay= 200
    AutoRepeatRate= 10
    Flags= 59
https://superuser.com/questions/1058474/increase-keyboard-repeat-rate-beyond-control-panel-limits-in-windows-10

## Авто-активаци окна под курсором
Window+r, then type “control panel” to open it.
Double click “Ease of Access Center”
Click “Make the mouse easier to use”
Checkbox “Activate a window by hovering over it with a mouse.”

## Обновление системы
- авто-вход. Зайти в HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon
 - AutoAdminLogon поменять на 1
 - создать запись DefaultUserName и указать имя пользователя
- гибернация. В настройках кнопок питания от батареи выбрать гибернацию (отключение ПК с сохранением состояния системы)
                                          от сети    выбрать сон
  если гибернации нет, запустить команду: powercfg -h on
- отключение экрана блокировки: зайти в редактор групповой политики gpedit.msc, Конфигурация компьютера» — «Административные шаблоны» — «Панель управления» — «Персонализация»
  включить пункт Запрет отображения экрана блокировки.
- установить раскладку и убрать сочетания на переключения раскладки (рег+доп)

- если вы хотите временно отказаться от обновлений Windows и возможных сопутствующих перезагрузок, то просто включите Metered connection для сетевого адаптера

## ПО
  - браузер
  - фар
  - Fusion 360
  - CHITUBOX
  - AVTOадаптер VAG 18.9.1
  - QMK
  - Photoshop
  - DOSbox
  - BaseCamp
  - FontForge (редактирование шрифтов)
  - Офис (Microsoft Excel и оутлук)
  - автокад (2021)
  - ffmpeg
  - typst
  - приложение для оперативного рисования (One Note?)
  - Betaflight Configurator (прошивка дронов)
  - Audacity (редактирование аудио)
  - qBittorrent (торрент)
  - GestureSign (управлене жестами)
  - расширения FireFox
    - РуТрекер
    - Скачать музыку из ВК
    - Image Pica
    - TWP (Translate)
    - uBlock Origin
    - Planet VPN