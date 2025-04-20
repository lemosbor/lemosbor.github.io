Создать в корневой папке файл с настройками xpdfrc
со следующим содержиым:

# описание http://www.xpdfreader.com/xpdfrc-man.html  http://www.xpdfreader.com/xpdf-man.html
initialDisplayMode continuous # horizontalContinuous — в полоску по-горизонтали
initialToolbarState no
initialSidebarState no

psDuplex yes            # двухсторонняя печать
psPaperSize match       # размер бумаги соответствует оригиналу

# масштаб при расширении окна
initialZoom page

# масштаб при открытии
defaultFitZoom page

# цвет бумаги
paperColor #ebe6e1

bind m any toggleMenuBar # скрыть меню

bind o any nextPageNoScroll # след страница
bind r any prevPage # пред страница

bind home any gotoPage(1) # перейти к первой странице
bind end any gotoLastPage # перейти к последней странице

bind ctrl-f any showToolbar find # найти
bind ctrl-P any showToolbar focusToPageNum # перейти
bind ctrl-g any showToolbar focusToPageNum # перейти
bind esc any hideToolbar focusToDocWin # закрть панель
bind ctrl-f4 any closeTabOrQuit # выйти
bind alt-f4 any closeTabOrQuit # выйти

bind f7 any findFirst # первое вхождение
bind f20 any findNext # след вхождение
bind f17 any findPrevious # пред вхождение
bind f11 any toggleFullScreenMode # полный экран

popupMenuCmd "Копировать" copy
popupMenuCmd "Повернуть по часовой" rotateCW
popupMenuCmd "Повернуть против часовой" rotateCCW
popupMenuCmd "Высота под размер окна" zoomFitPage
popupMenuCmd "Ширина под размер окна" zoomFitWidth
popupMenuCmd "Сраницы вдоль" horizontalContinuousMode
popupMenuCmd "Сраницы поперёк" continuousMode