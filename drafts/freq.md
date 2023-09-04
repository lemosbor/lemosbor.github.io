# Частота букв русского алфавита

[по мотивам](http://www.norvig.com/mayzner.html)

## Предсловие
В 2021 году в ходе моих поисков лучшей клавиатуры озадачился вопросом, а какая русская раскладка является лушей с точки 
зрения удобства и максимально-возможной скорости набора. Для прикладного решения этой задачи требовался 
частотный анализ русских букв, двубукенных сочетаний (биграмм) и трехбуквенных сочетаний 
(триграмм). Я решил не полагаться на доступные в интернете статистические таблицы, а сделать свою на основе своих 
корпусов текста.

Для анализа я использовал 6 корпусов:

1. Личная переписка и публиликации на 200 000 слов
2. Русская литература XIX и начала ХХ века на 15 893 799 слов (lib.ru)
3. Техническая документация на 6 705 586 слов
4. Архив новостей за 2022 год (https://wortschatz.uni-leipzig.de/de/download/Russian)
5. Архив популярных публикаций за 2019 год (https://wortschatz.uni-leipzig.de/de/download/Russian)
6. Архив русской википедии (https://dumps.wikimedia.org/ruwiki/) на 560 000 000 слов

С помощью не хитрых программ на Питоне я посчитал все слова, буквы (пробелы и прочие знаки, примыкающие к словам я заменил на символ _ ) и все возможные биграммы 34^2 и 
триграммы 34^3.
Затем я составил таблицы частот слов, букв, биграмм, триграмм.

## Подсчет слов
Я насчитал более миллиона различных слов, которые были упомянуты 743 842 922 
321 раз. 
Самым распространенным словом (предлогом) является и и в (по одной букве), затем идут слова (предлоги) не и на (по две буквы). 
Вот 50 лучших слов с их доля от общего количества вхождений (выглядит как распределение Ципфа):

<pre>
<b><u>СЛОВО   %     ДГР</u></b>
и      4,03 %  <img src="/img/o.jpg" height=12 width=300>
в      3,42 %  <img src="/img/o.jpg" height=12 width=254>
не     1,51 %  <img src="/img/o.jpg" height=12 width=112>
на     1,50 %  <img src="/img/o.jpg" height=12 width=112>
с      1,27 %  <img src="/img/o.jpg" height=12 width=95>
что    1,08 %  <img src="/img/o.jpg" height=12 width=80>
по     0,79 %  <img src="/img/o.jpg" height=12 width=59>
я      0,76 %  <img src="/img/o.jpg" height=12 width=57>
он     0,67 %  <img src="/img/o.jpg" height=12 width=50>
к      0,66 %  <img src="/img/o.jpg" height=12 width=49>
а      0,63 %  <img src="/img/o.jpg" height=12 width=47>
как    0,59 %  <img src="/img/o.jpg" height=12 width=44>
его    0,51 %  <img src="/img/o.jpg" height=12 width=38>
но     0,47 %  <img src="/img/o.jpg" height=12 width=35>
то     0,47 %  <img src="/img/o.jpg" height=12 width=35>
для    0,46 %  <img src="/img/o.jpg" height=12 width=34>
это    0,44 %  <img src="/img/o.jpg" height=12 width=33>
из     0,42 %  <img src="/img/o.jpg" height=12 width=31>
за     0,42 %  <img src="/img/o.jpg" height=12 width=31>
от     0,40 %  <img src="/img/o.jpg" height=12 width=30>
о      0,40 %  <img src="/img/o.jpg" height=12 width=30>
все    0,38 %  <img src="/img/o.jpg" height=12 width=28>
так    0,32 %  <img src="/img/o.jpg" height=12 width=23>
у      0,31 %  <img src="/img/o.jpg" height=12 width=23>
же     0,31 %  <img src="/img/o.jpg" height=12 width=23>
или    0,30 %  <img src="/img/o.jpg" height=12 width=23>
она    0,29 %  <img src="/img/o.jpg" height=12 width=22>
было   0,26 %  <img src="/img/o.jpg" height=12 width=19>
при    0,26 %  <img src="/img/o.jpg" height=12 width=19>
до     0,24 %  <img src="/img/o.jpg" height=12 width=18>
был    0,24 %  <img src="/img/o.jpg" height=12 width=18>
только 0,24 %  <img src="/img/o.jpg" height=12 width=18>
вы     0,22 %  <img src="/img/o.jpg" height=12 width=16>
мне    0,21 %  <img src="/img/o.jpg" height=12 width=16>
бы     0,21 %  <img src="/img/o.jpg" height=12 width=16>
их     0,21 %  <img src="/img/o.jpg" height=12 width=15>
ее     0,20 %  <img src="/img/o.jpg" height=12 width=15>
меня   0,19 %  <img src="/img/o.jpg" height=12 width=14>
ты     0,18 %  <img src="/img/o.jpg" height=12 width=13>
да     0,18 %  <img src="/img/o.jpg" height=12 width=13>
если   0,17 %  <img src="/img/o.jpg" height=12 width=13>
когда  0,17 %  <img src="/img/o.jpg" height=12 width=12>
быть   0,16 %  <img src="/img/o.jpg" height=12 width=12>
ему    0,16 %  <img src="/img/o.jpg" height=12 width=12>
они    0,16 %  <img src="/img/o.jpg" height=12 width=12>
еще    0,16 %  <img src="/img/o.jpg" height=12 width=12>
мы     0,16 %  <img src="/img/o.jpg" height=12 width=12>
ни     0,14 %  <img src="/img/o.jpg" height=12 width=11>
года   0,14 %  <img src="/img/o.jpg" height=12 width=10>
нет    0,14 %  <img src="/img/o.jpg" height=12 width=10>
</pre>

## Длина слов
А вот статистика длине слова в процентах. Средняя длина срова составляет 5,5 буквы, а 80 % слов имеют длину до 9 букв.
Во дсех исследуемых корпусах наблюдается болшой процент слов из одной буквы (предлоги) и провал на словах из 4 букв:

<pre>
<b><u>ДЛИНА   %    ДГР</u></b>
1      12 %  <img src="/img/o.jpg" height=12 width=330>
2      10 %  <img src="/img/o.jpg" height=12 width=276>
3      10 %  <img src="/img/o.jpg" height=12 width=265>
4       8 %  <img src="/img/o.jpg" height=12 width=212>
5      10 %  <img src="/img/o.jpg" height=12 width=277>
6      10 %  <img src="/img/o.jpg" height=12 width=277>
7      10 %  <img src="/img/o.jpg" height=12 width=256>
8       8 %  <img src="/img/o.jpg" height=12 width=213>
9       6 %  <img src="/img/o.jpg" height=12 width=160>
10      5 %  <img src="/img/o.jpg" height=12 width=134>
11      4 %  <img src="/img/o.jpg" height=12 width=93>
12      3 %  <img src="/img/o.jpg" height=12 width=68>
13      2 %  <img src="/img/o.jpg" height=12 width=40>
14      1 %  <img src="/img/o.jpg" height=12 width=24>
15      1 %  <img src="/img/o.jpg" height=12 width=13>
</pre>


Часто-всеречающиеся короткие слова сильно влияют на статистику.
Вот распределение для уникальных слов (то есть каждое слово считается только один раз, независимо от 
того, сколько раз оно упоминается). Теперь в среднем длина составляет 7,60 букв, а 80% имеют длину 
от 4 до 10 букв:


Вот наиболее частые слова из более чем 20 букв:

	сельскохозяйственные
	достопримечательности
	нефтеперерабатывающий
	конкурентоспособность
	высокопревосходительство

## Частота букв
Но вернемся к основной задаче — подсчету букв и их сочитаний. Вот полученная частотность букв русского алфавита, используемая мною:

<pre>
<b><u>БУКВА   %    ДГР</u></b>
о     11,0 %  <img src="/img/o.jpg" height=12 width=330>
е      8,3 %  <img src="/img/o.jpg" height=12 width=249>
а      7,9 %  <img src="/img/o.jpg" height=12 width=237>
и      7,0 %  <img src="/img/o.jpg" height=12 width=210>
н      7,0 %  <img src="/img/o.jpg" height=12 width=210>
т      6,3 %  <img src="/img/o.jpg" height=12 width=189>
с      5,3 %  <img src="/img/o.jpg" height=12 width=159>
л      4,5 %  <img src="/img/o.jpg" height=12 width=135>
в      4,5 %  <img src="/img/o.jpg" height=12 width=135>
р      4,5 %  <img src="/img/o.jpg" height=12 width=135>
к      3,2 %  <img src="/img/o.jpg" height=12 width=96>
м      3,1 %  <img src="/img/o.jpg" height=12 width=93>
д      3,0 %  <img src="/img/o.jpg" height=12 width=90>
п      2,8 %  <img src="/img/o.jpg" height=12 width=84>
у      2,5 %  <img src="/img/o.jpg" height=12 width=75>
я      2,1 %  <img src="/img/o.jpg" height=12 width=63>
ь      1,9 %  <img src="/img/o.jpg" height=12 width=57>
ы      1,9 %  <img src="/img/o.jpg" height=12 width=57>
з      1,7 %  <img src="/img/o.jpg" height=12 width=51>
г      1,7 %  <img src="/img/o.jpg" height=12 width=51>
б      1,7 %  <img src="/img/o.jpg" height=12 width=51>
ч      1,5 %  <img src="/img/o.jpg" height=12 width=45>
й      1,2 %  <img src="/img/o.jpg" height=12 width=36>
ж      1,1 %  <img src="/img/o.jpg" height=12 width=33>
х      0,9 %  <img src="/img/o.jpg" height=12 width=27>
ш      0,8 %  <img src="/img/o.jpg" height=12 width=24>
ю      0,7 %  <img src="/img/o.jpg" height=12 width=20>
ё      0,6 %  <img src="/img/o.jpg" height=12 width=18>
ц      0,4 %  <img src="/img/o.jpg" height=12 width=12>
ф      0,3 %  <img src="/img/o.jpg" height=12 width=9>
щ      0,3 %  <img src="/img/o.jpg" height=12 width=9>
э      0,3 %  <img src="/img/o.jpg" height=12 width=9>
ъ      0,1 %  <img src="/img/o.jpg" height=12 width=2>
</pre>


Совпадающие частоты некоторых букв (и-н, л-в-р, ь-ы, з-г-б) не случайность, а намеренный шаг. Эти буквы 
постоянно меняются друг с другом местами в зависимости от анализирумого корпуса и расставить их в однозначном 
порядке для всех корпусов невозможно. 

## Частота букв в начале и в конце слова 
Теперь рассмотрим какие буквы чаще встречаются в начале слова, а какие в конце.
Самая распространенная первая буква — `п`, а самая распространенная последняя — `о`.
При этом буква `п` очень редко бывает в конце слова.
Обратный дисбаланс наблюдается с буквой `я`, которая редко бывает в начале слова, но очень часто в конце.

<table cellspacing="0" cellpadding="0" border="0">
<tr>
<td class="right">
<pre>
<b><u> </u></b>
<img src="/img/o.jpg" height=12 width=78 >  6,8 %
<img src="/img/o.jpg" height=12 width=35 >  3,1 %
<img src="/img/o.jpg" height=12 width=83 >  7,3 %
<img src="/img/o.jpg" height=12 width=21 >  1,8 %
<img src="/img/o.jpg" height=12 width=15 >  1,3 %
<img src="/img/o.jpg" height=12 width=122> 10,7 %
<img src="/img/o.jpg" height=12 width=150> 13,1 %
<img src="/img/o.jpg" height=12 width=69 >  6,0 %
<img src="/img/o.jpg" height=12 width=4  >  0,4 %
<img src="/img/o.jpg" height=12 width=53 >  4,6 %
<img src="/img/o.jpg" height=12 width=55 >  4,8 %
<img src="/img/o.jpg" height=12 width=68 >  5,9 %
<img src="/img/o.jpg" height=12 width=34 >  2,9 %
<img src="/img/o.jpg" height=12 width=0  >  0,0 %
<img src="/img/o.jpg" height=12 width=65 >  5,7 %
<img src="/img/o.jpg" height=12 width=0  >  0,0 %
<img src="/img/o.jpg" height=12 width=22 >  1,9 %
<img src="/img/o.jpg" height=12 width=50 >  4,4 %
<img src="/img/o.jpg" height=12 width=46 >  4,1 %
<img src="/img/o.jpg" height=12 width=11 >  0,9 %
<img src="/img/o.jpg" height=12 width=33 >  2,9 %
<img src="/img/o.jpg" height=12 width=0  >  0,0 %
<img src="/img/o.jpg" height=12 width=36 >  3,2 %
<img src="/img/o.jpg" height=12 width=35 >  3,1 %
<img src="/img/o.jpg" height=12 width=1  >  0,1 %
<img src="/img/o.jpg" height=12 width=21 >  1,9 %
<img src="/img/o.jpg" height=12 width=10 >  0,9 %
<img src="/img/o.jpg" height=12 width=11 >  1,0 %
<img src="/img/o.jpg" height=12 width=6  >  0,5 %
<img src="/img/o.jpg" height=12 width=6  >  0,5 %
<img src="/img/o.jpg" height=12 width=0  >  0,0 %
</pre>
</td>
<td>
<pre>
<b><u>БУКВА</u></b>
о      11,0 %  <img src="/img/o.jpg" height=12 width=126>
и       9,8 %  <img src="/img/o.jpg" height=12 width=112>
в       2,4 %  <img src="/img/o.jpg" height=12 width=28>
е      11,0 %  <img src="/img/o.jpg" height=12 width=125>
а      	9,4 %  <img src="/img/o.jpg" height=12 width=108>
с      	0,8 %  <img src="/img/o.jpg" height=12 width=9>
п      	0,1 %  <img src="/img/o.jpg" height=12 width=2>
н      	1,3 %  <img src="/img/o.jpg" height=12 width=15>
я      	8,8 %  <img src="/img/o.jpg" height=12 width=100>
м      	6,0 %  <img src="/img/o.jpg" height=12 width=68>
т      	4,4 %  <img src="/img/o.jpg" height=12 width=51>
к      	2,3 %  <img src="/img/o.jpg" height=12 width=26>
у      	3,5 %  <img src="/img/o.jpg" height=12 width=40>
ь      	6,3 %  <img src="/img/o.jpg" height=12 width=71>
д      	0,9 %  <img src="/img/o.jpg" height=12 width=11>
й      	6,8 %  <img src="/img/o.jpg" height=12 width=78>
л      	3,1 %  <img src="/img/o.jpg" height=12 width=36>
р      	0,9 %  <img src="/img/o.jpg" height=12 width=10>
б      	0,2 %  <img src="/img/o.jpg" height=12 width=2>
х      	3,8 %  <img src="/img/o.jpg" height=12 width=43>
з      	0,5 %  <img src="/img/o.jpg" height=12 width=6>
ы      	3,0 %  <img src="/img/o.jpg" height=12 width=34>
ч      	0,2 %  <img src="/img/o.jpg" height=12 width=3>
г      	0,5 %  <img src="/img/o.jpg" height=12 width=5>
ю      	2,3 %  <img src="/img/o.jpg" height=12 width=26>
э      	0,0 %  <img src="/img/o.jpg" height=12 width=0>
ж      	0,1 %  <img src="/img/o.jpg" height=12 width=1>
ф      	0,0 %  <img src="/img/o.jpg" height=12 width=1>
ц      	0,3 %  <img src="/img/o.jpg" height=12 width=3>
ш      	0,1 %  <img src="/img/o.jpg" height=12 width=1>
щ      	0,0 %  <img src="/img/o.jpg" height=12 width=0>
</pre>
</td>
</tr>
</table>
