## Установка
1. Скачать дистрибутив Latex https://www.tug.org/texlive/acquire-netinstall.html и установить нужны компаненты
2. Установить Pandoc

## Верстка письма
1. Создаем файл  1.tex со следующим кодом:

\documentclass{article} 

\usepackage[T2A]{fontenc}
\usepackage[utf8]{inputenc}
\usepackage[russian]{babel}


\begin{document}

$secondpost$

$body$

\end{document}

2. Создаем файл 1.md (в кодировке utf8) со следующим кодом:
---
secondpost: Александр
lang: ru
mainfont: XITS
---

\today

Текстовка письма

3. Запускаем команду:

%"C:\Program Files\Pandoc\pandoc.exe" --pdf-engine=pdflatex --template=cltemplate.tex -s coverletter.md -f markdown -t latex -o coverletter.pdf
