## Горячие клавиши
' - быстрый поиск и переход на необходимые ссылки
чтобы поасть на форму сделать быстрый поиск текста перед формой (через / или '), а затем нажать ТАБ
упр+г, ввод, ф3 - переход к следующему вхождению поиска
упр+р -- обновить
упр+рег+р -- обновить с перезагрузкой кэша
упр+0 -- сбросить масштаб
доп+↓  -- сменить поисковую систему в адресной строке
упр+рег+PgUp -- переместить вкладку влево
упр+рег+Нач -- переместить вкладку в начало
упр+м -- отключить звук
упр+рег+д -- создать папку закладок с открытыми вкладками
упр+рег+а -- панель расширений
упр+рег+с -- сохранить картинку скриншотом
рег+вых -- диспетчер процессов
рег+уд -- удалить значение в выпадающем списке
ф9 -- режим чтения
ф7 -- режим активного курсора
упл+→ -- перейти на 10 % вперед (в видеороликах)
## мышь
Доп+скроллВниз -- назад по истории
Рег+средняя клавиша -- Открыть ссыку в новой вкладке переднего плана
рег+клик -- переместится до нужного места полосы прокрутки (или просто включить параметр scrollToClick = 1)
клик, рег+клик в конце текста -- выделить текст
alt+клик  -- сохранить изображение или ссылку (включить параметр browser.altClickSave)
alt+win+выделение -- выделение текста ссылки
средний клик на панели вкладок -- новая вкладка

## На панели истории или закладок
доп+ввод -- скопировать адрес
упр+ввод -- открыть в новой вкладке
рег+ввод -- открыть в новом окне

## Поиск в google
site: - искать на сайте
-  - ислключить из результата поиска.
inurl: - искать в адресе
inurl:(lemos | leonov | ilya)
intext:
intitle:
inanchor:
cache: поиск удалённых страниц

## Настройки конфига
Набрать в адресной строке about:config и нажать Ввод
browser.bookmarks.editDialog.showForNewBookmarks - не показывать диалог сохранения закладки
devtools.toolbox.zoomValue = 1,2 - увеличивает размер текста по умолчанию в инструментах разработчика
browser.tabs.closeWindowWithLastTab = false - не закрывать браузер при закрытии последней вкладки
browser.tabs.loadDivertedInBackground - вкладка открывалется в фоновом режиме (так быстрее) 
browser.altClickSave - сохранять изображение или ссылку через доп+клик


Компактный заголовок и значки: about:config  browser.compactmode.show и browser.uidensity а потом в настройках понелей выбрать компактный вид
https://www.userchrome.org/firefox-89-styling-proton-ui.html#compactmode
Задание стилей css: Справка — Информация для решения проблем — Папка профиля. Создать папку и файл chrome\userChrome.css

menupopup:not(.in-menulist) > menuitem, 
menupopup:not(.in-menulist) > menu {
  padding-block: 1px !important;    /* высота пробела между пунктами меню */
  min-height: unset !important;
}
 
/* Minimize height of sidebar items */
.sidebar-placesTreechildren::-moz-tree-row {
	min-height: 17px !important;
}

## vim-режим
й - скролл вниз
5й - скролл вниз 5 раз
к - скролл вверх
	гг, д - наверх scrollToTop
Г - вниз
	д; н - скролл на пол экрана вниз scrollPageDown
	у; л - скролл на пол экрана вверх scrollPageUp
х - скролл влево
л - скролл вправо
р - обновить страницу
ыы - скопировать адресс текущей страницы
п - открыть страницу из клипборда
П - открыть страницу из клипборда в новой вкладке
	ги, и - перейти к строке ввода на видимом экране
	ф, e - открыть ссылку в текущей вкладке, LinkHints.activateMode
<a-f>   open multiple links in a new tab
гф - открыть следующий фрейм страницы
	о, п - открыть закладку или историю в текущей вкладке , Vomnibar.activateInNewTab
б - открыть закладку
	Т, г - открыть одну из вкадок , Vomnibar.activateTabSelection
	/, <c-f> - искать , enterFindMode
	н, a - искать дальше , performFind
	Н, о - искать обратно performBackwardsFind
Х - назад по истории
Л - вперед по истории
т - новая вкладка
	Й, т - на вкладку влево previousTab
	К, w - на вкладку вправо   nextTab
г0 - на первую вкладку
г$ - на последнюю вкадку
ыт - дублировать вкладку
доп+п - закрепить текущую вкадку
ь, х - закрыть текущую вкладку removeTab
Ь - отменить закрытие текущей вкладки
ma, mA  set local mark "a" (global mark "A")
`a, `A  jump to local mark "a" (global mark "A")
``      jump back to the position before the previous jump
]], [[  Follow the link labeled 'next' or '>' ('previous' or '<')
          - helpful for browsing paginated sites

Characters used for link hints: сеоаимтнлв

unmapAll
map / focusInput
map p Vomnibar.activateInNewTab
map п Vomnibar.activateInNewTab
map g Vomnibar.activateTabSelection
map г Vomnibar.activateTabSelection
map u visitPreviousTab
map q LinkHints.activateMode
map я LinkHints.activateMode
map Q LinkHints.activateModeToOpenInNewForegroundTab
map Я LinkHints.activateModeToOpenInNewForegroundTab
map x LinkHints.activateModeToDownloadLink
map <c-l> Vomnibar.activateEditUrl
map <c-л> Vomnibar.activateEditUrl
map <a-i> unmap v
map <a-w> goPrevious
map <a-в> goPrevious
map <a-p> goNext
map <a-п> goNext
map к goNext
map k goNext
map ; LinkHints.activateModeToOpenInNewTab

## Настройка сохранения изображений 
${index}-${pageName}-${name.slice(-20, -8)}${ext}
