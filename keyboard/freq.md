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
321 раз. После отчистки корпуса от географических названий, аббревиатур и пр. не характерных для русского языка слов, основной корпус составил 300 тыс. слов.
Самым распространенным словом (предлогом) является `и` и `в` (по одной букве), затем идут слова (предлоги) `не` и `на` (по две буквы). 
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

Как видно, самые частые в русском языке слова это союзы и предлоги, состоящие из 1—3 букв:
- однобуквенные (и, в, с, я, к, а, о, у, б, ж)
- двубуквенные (на, по, он, но, то, из, за, от, же, до, вы, бы, их, ее, ты, да, мы, ни, во, ли, со, об, ей, ну, им, уж, ко, те, ах, та, ту, ею)
- трехбуквенные (`что как его для это все так или она при был мне ему они еще нет уже вот под чем без где том вас тем вам раз кто них нас лет там сам ним ней эти тут мой тот два над нам мог год нее эта три нем эту оно тех про дня всю моя`)

## Длина слов
А вот статистика по длине слова в процентах. Средняя длина срова составляет 5,5 буквы, а 80 % слов имеют длину до 9 букв.
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


Часто-встречающиеся короткие слова сильно влияют на статистику.
Вот распределение для уникальных слов (то есть каждое слово считается только один раз, независимо от 
того, сколько раз оно упоминается). Теперь в среднем длина составляет 7,60 букв, а 80 % имеют длину 
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
<b><u>% слов с буквой в начале  </u></b>
<img src="/img/o.jpg" height=12 width=78 >  7,0 %  
<img src="/img/o.jpg" height=12 width=35 >  3,1 %  
<img src="/img/o.jpg" height=12 width=83 >  7,4 %  
<img src="/img/o.jpg" height=12 width=21 >  1,8 %  
<img src="/img/o.jpg" height=12 width=15 >  1,2 %  
<img src="/img/o.jpg" height=12 width=122> 10,7 %  
<img src="/img/o.jpg" height=12 width=150> 13,4 %  
<img src="/img/o.jpg" height=12 width=69 >  6,0 %  
<img src="/img/o.jpg" height=12 width=4  >  0,3 %  
<img src="/img/o.jpg" height=12 width=53 >  4,5 %  
<img src="/img/o.jpg" height=12 width=55 >  4,9 %  
<img src="/img/o.jpg" height=12 width=68 >  5,9 %  
<img src="/img/o.jpg" height=12 width=34 >  3,0 %  
<img src="/img/o.jpg" height=12 width=0  >  0,0 %  
<img src="/img/o.jpg" height=12 width=65 >  5,7 %  
<img src="/img/o.jpg" height=12 width=0  >  0,0 %  
<img src="/img/o.jpg" height=12 width=22 >  1,8 %  
<img src="/img/o.jpg" height=12 width=50 >  4,4 %  
<img src="/img/o.jpg" height=12 width=46 >  4,0 %  
<img src="/img/o.jpg" height=12 width=11 >  0,9 %  
<img src="/img/o.jpg" height=12 width=33 >  3,0 %  
<img src="/img/o.jpg" height=12 width=0  >  0,0 %  
<img src="/img/o.jpg" height=12 width=36 >  3,3 %  
<img src="/img/o.jpg" height=12 width=35 >  3,0 %  
<img src="/img/o.jpg" height=12 width=1  >  0,1 %  
<img src="/img/o.jpg" height=12 width=21 >  1,9 %  
<img src="/img/o.jpg" height=12 width=10 >  0,9 %  
<img src="/img/o.jpg" height=12 width=11 >  0,9 %  
<img src="/img/o.jpg" height=12 width=6  >  0,5 %  
<img src="/img/o.jpg" height=12 width=6  >  0,5 %  
<img src="/img/o.jpg" height=12 width=0  >  0,0 %  
</pre>
</td>
<td>
<pre>
<b><u>БУКВА   % слов с буквой в конце</u></b>
о      11,2 %  <img src="/img/o.jpg" height=12 width=126>
и       9,9 %  <img src="/img/o.jpg" height=12 width=112>
в       2,3 %  <img src="/img/o.jpg" height=12 width=28>
е      11,2 %  <img src="/img/o.jpg" height=12 width=126>
а      	9,1 %  <img src="/img/o.jpg" height=12 width=108>
с      	0,7 %  <img src="/img/o.jpg" height=12 width=9>
п      	0,1 %  <img src="/img/o.jpg" height=12 width=2>
н      	1,2 %  <img src="/img/o.jpg" height=12 width=15>
я      	9,0 %  <img src="/img/o.jpg" height=12 width=100>
м      	6,0 %  <img src="/img/o.jpg" height=12 width=68>
т      	4,5 %  <img src="/img/o.jpg" height=12 width=51>
к      	2,3 %  <img src="/img/o.jpg" height=12 width=26>
у      	3,5 %  <img src="/img/o.jpg" height=12 width=40>
ь      	6,4 %  <img src="/img/o.jpg" height=12 width=71>
д      	0,9 %  <img src="/img/o.jpg" height=12 width=11>
й      	6,9 %  <img src="/img/o.jpg" height=12 width=78>
л      	3,2 %  <img src="/img/o.jpg" height=12 width=36>
р      	0,8 %  <img src="/img/o.jpg" height=12 width=10>
б      	0,1 %  <img src="/img/o.jpg" height=12 width=2>
х      	3,9 %  <img src="/img/o.jpg" height=12 width=43>
з      	0,5 %  <img src="/img/o.jpg" height=12 width=6>
ы      	3,0 %  <img src="/img/o.jpg" height=12 width=34>
ч      	0,2 %  <img src="/img/o.jpg" height=12 width=3>
г      	0,4 %  <img src="/img/o.jpg" height=12 width=5>
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


## Двухбуквенная последовательность (биграмма)
Рассмотрим сочетания нескольких букв в слове. Начнем с двух последовательных букв — биграмм.
Математически в руссом языке возможны 33*33=1089 биграммы.  На практике в 99 % случаев встречаются только 500 биграмм.
То есть такие биграммы как `ЦК` `ЭЦ` встречаются только в аббревиатурах, а такие биграммы как `ЙЬ` `ЬЪ` не встречаются вовсе.
Вот 50 самых частых биграмм в русском языке:
<pre>
<b><u>БГ   %    ДГР</u></b>
ст    1,9 <img src="/img/o.jpg" height=12 width=300>
то    1,5 <img src="/img/o.jpg" height=12 width=250>
ни    1,5 <img src="/img/o.jpg" height=12 width=250>
но    1,5 <img src="/img/o.jpg" height=12 width=244>
ен    1,5 <img src="/img/o.jpg" height=12 width=244>
на    1,4 <img src="/img/o.jpg" height=12 width=222>
по    1,3 <img src="/img/o.jpg" height=12 width=208>
ов    1,3 <img src="/img/o.jpg" height=12 width=205>
ра    1,3 <img src="/img/o.jpg" height=12 width=203>
ко    1,1 <img src="/img/o.jpg" height=12 width=184>
ро    1,1 <img src="/img/o.jpg" height=12 width=183>
пр    1,1 <img src="/img/o.jpg" height=12 width=183>
не    1,1 <img src="/img/o.jpg" height=12 width=182>
го    1,1 <img src="/img/o.jpg" height=12 width=172>
ре    1,0 <img src="/img/o.jpg" height=12 width=157>
ос    1,0 <img src="/img/o.jpg" height=12 width=155>
во    0,9 <img src="/img/o.jpg" height=12 width=147>
от    0,9 <img src="/img/o.jpg" height=12 width=147>
та    0,9 <img src="/img/o.jpg" height=12 width=145>
ор    0,9 <img src="/img/o.jpg" height=12 width=141>
ер    0,9 <img src="/img/o.jpg" height=12 width=141>
ан    0,9 <img src="/img/o.jpg" height=12 width=138>
ал    0,8 <img src="/img/o.jpg" height=12 width=138>
од    0,8 <img src="/img/o.jpg" height=12 width=137>
те    0,8 <img src="/img/o.jpg" height=12 width=136>
ка    0,8 <img src="/img/o.jpg" height=12 width=135>
ет    0,8 <img src="/img/o.jpg" height=12 width=134>
ва    0,8 <img src="/img/o.jpg" height=12 width=134>
ол    0,8 <img src="/img/o.jpg" height=12 width=132>
ли    0,8 <img src="/img/o.jpg" height=12 width=131>
ел    0,8 <img src="/img/o.jpg" height=12 width=122>
ом    0,7 <img src="/img/o.jpg" height=12 width=118>
ны    0,7 <img src="/img/o.jpg" height=12 width=118>
ес    0,7 <img src="/img/o.jpg" height=12 width=118>
ве    0,7 <img src="/img/o.jpg" height=12 width=116>
ри    0,7 <img src="/img/o.jpg" height=12 width=113>
де    0,7 <img src="/img/o.jpg" height=12 width=112>
ле    0,7 <img src="/img/o.jpg" height=12 width=112>
ть    0,7 <img src="/img/o.jpg" height=12 width=112>
ог    0,7 <img src="/img/o.jpg" height=12 width=111>
ат    0,7 <img src="/img/o.jpg" height=12 width=110>
ла    0,7 <img src="/img/o.jpg" height=12 width=108>
за    0,7 <img src="/img/o.jpg" height=12 width=107>
ло    0,7 <img src="/img/o.jpg" height=12 width=107>
он    0,7 <img src="/img/o.jpg" height=12 width=107>
ль    0,7 <img src="/img/o.jpg" height=12 width=106>
ме    0,6 <img src="/img/o.jpg" height=12 width=105>
ти    0,6 <img src="/img/o.jpg" height=12 width=104>
да    0,6 <img src="/img/o.jpg" height=12 width=100>
ит    0,6 <img src="/img/o.jpg" height=12 width=98>
</pre>

Примечание: указана частота для последовательности биграмм в предложениях, то есть учитываются биграммы с пробелами (буквы в конце и в начале слова). Если их не учитывать, указанная частота будет больше.
Примечание: Перед подсчетом биграм и триграм важно отчистить их от аббревиатур. Не существующие биграммы полезны для автозамен.

Обратите внимание, что биграммы `ст` `то` `на` `но` встречаются чаще, чем буквы `й ж х ш ю ё ц ф щ э ъ`.  
**Исторический пример**. Если бы Карамзин в 1797 году вместе с заменой диграфа `ио` на букву `ё` пошел бы дальше и заменил бы также диграф `ст` на букву `c̄`, то толку было бы больше: измеряемый в буквах объем книг и текстов уменьшился бы почти на один процент. Примерно на это же значение увеличится скорость набора и чтения текста.

Если представить биграммы в виде тепловой карты с частотой встречаемости, то она будет выглядеть следующим образом:

<table>
<tr height=12><td width=12 class="comp"></td><td width=12 class="comp">_</td><td width=12 class="comp">о</td><td width=12 class="comp">е</td><td width=12 class="comp">а</td><td width=12 class="comp">и</td><td width=12 class="comp">у</td><td width=12 class="comp">ю</td><td width=12 class="comp">я</td><td width=12 class="comp">ё</td><td width=12 class="comp">э</td><td width=12 class="comp">ы</td><td width=12 class="comp">ь</td><td width=12 class="comp">ъ</td><td width=12 class="comp">й</td><td width=12 class="comp">щ</td><td width=12 class="comp">ч</td><td width=12 class="comp">ф</td><td width=12 class="comp">ц</td><td width=12 class="comp">ш</td><td width=12 class="comp">х</td><td width=12 class="comp">ж</td><td width=12 class="comp">б</td><td width=12 class="comp">г</td><td width=12 class="comp">з</td><td width=12 class="comp">п</td><td width=12 class="comp">д</td><td width=12 class="comp">м</td><td width=12 class="comp">к</td><td width=12 class="comp">р</td><td width=12 class="comp">в</td><td width=12 class="comp">л</td><td width=12 class="comp">с</td><td width=12 class="comp">т</td><td width=12 class="comp">н</td></tr>
<tr height=12><td width=12 class="comp">_</td><td width=12 bgcolor="#8e8c8c" title="__: 0 %"></td><td width=12 bgcolor="#ca5949" title="о_: 1,715 %"></td><td width=12 bgcolor="#ca5949" title="е_: 1,622 %"></td><td width=12 bgcolor="#ca5949" title="а_: 1,49 %"></td><td width=12 bgcolor="#ca5949" title="и_: 1,819 %"></td><td width=12 bgcolor="#fe715d" title="у_: 0,466 %"></td><td width=12 bgcolor="#fd9b8d" title="ю_: 0,268 %"></td><td width=12 bgcolor="#ca5949" title="я_: 1,161 %"></td><td width=12 bgcolor="#fd9b8d" title="ё_: 0,014 %"></td><td width=12 bgcolor="#cac8c8" title="э_: 0 %"></td><td width=12 bgcolor="#fe715d" title="ы_: 0,466 %"></td><td width=12 bgcolor="#fe715d" title="ь_: 0,749 %"></td><td width=12 bgcolor="#8e8c8c" title="ъ_: 0 %"></td><td width=12 bgcolor="#fe715d" title="й_: 0,819 %"></td><td width=12 bgcolor="#d0afaa" title="щ_: 0,001 %"></td><td width=12 bgcolor="#fd9b8d" title="ч_: 0,025 %"></td><td width=12 bgcolor="#d0afaa" title="ф_: 0,004 %"></td><td width=12 bgcolor="#fd9b8d" title="ц_: 0,031 %"></td><td width=12 bgcolor="#d0afaa" title="ш_: 0,007 %"></td><td width=12 bgcolor="#fe715d" title="х_: 0,487 %"></td><td width=12 bgcolor="#fd9b8d" title="ж_: 0,027 %"></td><td width=12 bgcolor="#fd9b8d" title="б_: 0,04 %"></td><td width=12 bgcolor="#fd9b8d" title="г_: 0,052 %"></td><td width=12 bgcolor="#fd9b8d" title="з_: 0,12 %"></td><td width=12 bgcolor="#fd9b8d" title="п_: 0,01 %"></td><td width=12 bgcolor="#fd9b8d" title="д_: 0,1 %"></td><td width=12 bgcolor="#fe715d" title="м_: 0,72 %"></td><td width=12 bgcolor="#fe715d" title="к_: 0,368 %"></td><td width=12 bgcolor="#fd9b8d" title="р_: 0,095 %"></td><td width=12 bgcolor="#fe715d" title="в_: 0,801 %"></td><td width=12 bgcolor="#fe715d" title="л_: 0,377 %"></td><td width=12 bgcolor="#fd9b8d" title="с_: 0,281 %"></td><td width=12 bgcolor="#fe715d" title="т_: 0,588 %"></td><td width=12 bgcolor="#fd9b8d" title="н_: 0,242 %"></td></tr>
<tr height=12><td width=12 class="comp">о</td><td width=12 bgcolor="#fe715d" title="_о: 1,058 %"></td><td width=12 bgcolor="#fd9b8d" title="оо: 0,042 %"></td><td width=12 bgcolor="#fd9b8d" title="ео: 0,036 %"></td><td width=12 bgcolor="#d0afaa" title="ао: 0,002 %"></td><td width=12 bgcolor="#fd9b8d" title="ио: 0,064 %"></td><td width=12 bgcolor="#d0afaa" title="уо: 0 %"></td><td width=12 bgcolor="#cac8c8" title="юо: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="яо: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="ёо: 0 %"></td><td width=12 bgcolor="#cac8c8" title="эо: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="ыо: 0 %"></td><td width=12 bgcolor="#d0afaa" title="ьо: 0,001 %"></td><td width=12 bgcolor="#8e8c8c" title="ъо: 0 %"></td><td width=12 bgcolor="#d0afaa" title="йо: 0,005 %"></td><td width=12 bgcolor="#d0afaa" title="що: 0 %"></td><td width=12 bgcolor="#d0afaa" title="чо: 0,004 %"></td><td width=12 bgcolor="#fd9b8d" title="фо: 0,058 %"></td><td width=12 bgcolor="#fd9b8d" title="цо: 0,014 %"></td><td width=12 bgcolor="#fd9b8d" title="шо: 0,017 %"></td><td width=12 bgcolor="#fd9b8d" title="хо: 0,187 %"></td><td width=12 bgcolor="#d0afaa" title="жо: 0,003 %"></td><td width=12 bgcolor="#fd9b8d" title="бо: 0,288 %"></td><td width=12 bgcolor="#fe715d" title="го: 0,745 %"></td><td width=12 bgcolor="#fd9b8d" title="зо: 0,089 %"></td><td width=12 bgcolor="#fe715d" title="по: 0,898 %"></td><td width=12 bgcolor="#fe715d" title="до: 0,407 %"></td><td width=12 bgcolor="#fd9b8d" title="мо: 0,33 %"></td><td width=12 bgcolor="#fe715d" title="ко: 0,795 %"></td><td width=12 bgcolor="#fe715d" title="ро: 0,793 %"></td><td width=12 bgcolor="#fe715d" title="во: 0,636 %"></td><td width=12 bgcolor="#fe715d" title="ло: 0,461 %"></td><td width=12 bgcolor="#fd9b8d" title="со: 0,334 %"></td><td width=12 bgcolor="#fe715d" title="то: 1,08 %"></td><td width=12 bgcolor="#fe715d" title="но: 1,056 %"></td></tr>
<tr height=12><td width=12 class="comp">е</td><td width=12 bgcolor="#fd9b8d" title="_е: 0,265 %"></td><td width=12 bgcolor="#fd9b8d" title="ое: 0,204 %"></td><td width=12 bgcolor="#fd9b8d" title="ее: 0,12 %"></td><td width=12 bgcolor="#fd9b8d" title="ае: 0,153 %"></td><td width=12 bgcolor="#fd9b8d" title="ие: 0,345 %"></td><td width=12 bgcolor="#fd9b8d" title="уе: 0,037 %"></td><td width=12 bgcolor="#d0afaa" title="юе: 0 %"></td><td width=12 bgcolor="#fd9b8d" title="яе: 0,042 %"></td><td width=12 bgcolor="#8e8c8c" title="ёе: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="эе: 0 %"></td><td width=12 bgcolor="#fd9b8d" title="ые: 0,154 %"></td><td width=12 bgcolor="#fd9b8d" title="ье: 0,031 %"></td><td width=12 bgcolor="#fd9b8d" title="ъе: 0,029 %"></td><td width=12 bgcolor="#d0afaa" title="йе: 0 %"></td><td width=12 bgcolor="#fd9b8d" title="ще: 0,161 %"></td><td width=12 bgcolor="#fe715d" title="че: 0,425 %"></td><td width=12 bgcolor="#fd9b8d" title="фе: 0,031 %"></td><td width=12 bgcolor="#fd9b8d" title="це: 0,115 %"></td><td width=12 bgcolor="#fd9b8d" title="ше: 0,16 %"></td><td width=12 bgcolor="#d0afaa" title="хе: 0,006 %"></td><td width=12 bgcolor="#fd9b8d" title="же: 0,321 %"></td><td width=12 bgcolor="#fd9b8d" title="бе: 0,162 %"></td><td width=12 bgcolor="#fd9b8d" title="ге: 0,045 %"></td><td width=12 bgcolor="#fd9b8d" title="зе: 0,039 %"></td><td width=12 bgcolor="#fd9b8d" title="пе: 0,243 %"></td><td width=12 bgcolor="#fe715d" title="де: 0,485 %"></td><td width=12 bgcolor="#fe715d" title="ме: 0,453 %"></td><td width=12 bgcolor="#fd9b8d" title="ке: 0,056 %"></td><td width=12 bgcolor="#fe715d" title="ре: 0,679 %"></td><td width=12 bgcolor="#fe715d" title="ве: 0,499 %"></td><td width=12 bgcolor="#fe715d" title="ле: 0,485 %"></td><td width=12 bgcolor="#fd9b8d" title="се: 0,289 %"></td><td width=12 bgcolor="#fe715d" title="те: 0,59 %"></td><td width=12 bgcolor="#fe715d" title="не: 0,785 %"></td></tr>
<tr height=12><td width=12 class="comp">а</td><td width=12 bgcolor="#fd9b8d" title="_а: 0,236 %"></td><td width=12 bgcolor="#d0afaa" title="оа: 0,001 %"></td><td width=12 bgcolor="#fd9b8d" title="еа: 0,018 %"></td><td width=12 bgcolor="#cac8c8" title="аа: 0 %"></td><td width=12 bgcolor="#fd9b8d" title="иа: 0,047 %"></td><td width=12 bgcolor="#fd9b8d" title="уа: 0,019 %"></td><td width=12 bgcolor="#d0afaa" title="юа: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="яа: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="ёа: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="эа: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="ыа: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="ьа: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="ъа: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="йа: 0 %"></td><td width=12 bgcolor="#fd9b8d" title="ща: 0,036 %"></td><td width=12 bgcolor="#fd9b8d" title="ча: 0,211 %"></td><td width=12 bgcolor="#fd9b8d" title="фа: 0,024 %"></td><td width=12 bgcolor="#fd9b8d" title="ца: 0,054 %"></td><td width=12 bgcolor="#fd9b8d" title="ша: 0,059 %"></td><td width=12 bgcolor="#fd9b8d" title="ха: 0,045 %"></td><td width=12 bgcolor="#fd9b8d" title="жа: 0,092 %"></td><td width=12 bgcolor="#fd9b8d" title="ба: 0,068 %"></td><td width=12 bgcolor="#fd9b8d" title="га: 0,115 %"></td><td width=12 bgcolor="#fe715d" title="за: 0,464 %"></td><td width=12 bgcolor="#fd9b8d" title="па: 0,15 %"></td><td width=12 bgcolor="#fe715d" title="да: 0,432 %"></td><td width=12 bgcolor="#fd9b8d" title="ма: 0,256 %"></td><td width=12 bgcolor="#fe715d" title="ка: 0,583 %"></td><td width=12 bgcolor="#fe715d" title="ра: 0,878 %"></td><td width=12 bgcolor="#fe715d" title="ва: 0,579 %"></td><td width=12 bgcolor="#fe715d" title="ла: 0,468 %"></td><td width=12 bgcolor="#fd9b8d" title="са: 0,151 %"></td><td width=12 bgcolor="#fe715d" title="та: 0,625 %"></td><td width=12 bgcolor="#fe715d" title="на: 0,961 %"></td></tr>
<tr height=12><td width=12 class="comp">и</td><td width=12 bgcolor="#fe715d" title="_и: 1,095 %"></td><td width=12 bgcolor="#fd9b8d" title="ои: 0,098 %"></td><td width=12 bgcolor="#fd9b8d" title="еи: 0,011 %"></td><td width=12 bgcolor="#fd9b8d" title="аи: 0,022 %"></td><td width=12 bgcolor="#fd9b8d" title="ии: 0,206 %"></td><td width=12 bgcolor="#d0afaa" title="уи: 0,001 %"></td><td width=12 bgcolor="#d0afaa" title="юи: 0 %"></td><td width=12 bgcolor="#d0afaa" title="яи: 0,002 %"></td><td width=12 bgcolor="#8e8c8c" title="ёи: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="эи: 0 %"></td><td width=12 bgcolor="#d0afaa" title="ыи: 0,001 %"></td><td width=12 bgcolor="#d0afaa" title="ьи: 0,007 %"></td><td width=12 bgcolor="#8e8c8c" title="ъи: 0 %"></td><td width=12 bgcolor="#cac8c8" title="йи: 0 %"></td><td width=12 bgcolor="#fd9b8d" title="щи: 0,105 %"></td><td width=12 bgcolor="#fd9b8d" title="чи: 0,176 %"></td><td width=12 bgcolor="#fd9b8d" title="фи: 0,054 %"></td><td width=12 bgcolor="#fd9b8d" title="ци: 0,187 %"></td><td width=12 bgcolor="#fd9b8d" title="ши: 0,106 %"></td><td width=12 bgcolor="#fd9b8d" title="хи: 0,019 %"></td><td width=12 bgcolor="#fd9b8d" title="жи: 0,135 %"></td><td width=12 bgcolor="#fd9b8d" title="би: 0,072 %"></td><td width=12 bgcolor="#fd9b8d" title="ги: 0,097 %"></td><td width=12 bgcolor="#fd9b8d" title="зи: 0,054 %"></td><td width=12 bgcolor="#fd9b8d" title="пи: 0,109 %"></td><td width=12 bgcolor="#fd9b8d" title="ди: 0,247 %"></td><td width=12 bgcolor="#fd9b8d" title="ми: 0,294 %"></td><td width=12 bgcolor="#fd9b8d" title="ки: 0,298 %"></td><td width=12 bgcolor="#fe715d" title="ри: 0,489 %"></td><td width=12 bgcolor="#fd9b8d" title="ви: 0,279 %"></td><td width=12 bgcolor="#fe715d" title="ли: 0,567 %"></td><td width=12 bgcolor="#fd9b8d" title="си: 0,161 %"></td><td width=12 bgcolor="#fe715d" title="ти: 0,449 %"></td><td width=12 bgcolor="#fe715d" title="ни: 1,08 %"></td></tr>
<tr height=12><td width=12 class="comp">у</td><td width=12 bgcolor="#fe715d" title="_у: 0,408 %"></td><td width=12 bgcolor="#d0afaa" title="оу: 0,006 %"></td><td width=12 bgcolor="#d0afaa" title="еу: 0,007 %"></td><td width=12 bgcolor="#fd9b8d" title="ау: 0,014 %"></td><td width=12 bgcolor="#d0afaa" title="иу: 0,002 %"></td><td width=12 bgcolor="#d0afaa" title="уу: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="юу: 0 %"></td><td width=12 bgcolor="#cac8c8" title="яу: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="ёу: 0 %"></td><td width=12 bgcolor="#cac8c8" title="эу: 0 %"></td><td width=12 bgcolor="#d0afaa" title="ыу: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="ьу: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="ъу: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="йу: 0 %"></td><td width=12 bgcolor="#d0afaa" title="щу: 0,008 %"></td><td width=12 bgcolor="#fd9b8d" title="чу: 0,035 %"></td><td width=12 bgcolor="#fd9b8d" title="фу: 0,01 %"></td><td width=12 bgcolor="#fd9b8d" title="цу: 0,013 %"></td><td width=12 bgcolor="#fd9b8d" title="шу: 0,018 %"></td><td width=12 bgcolor="#fd9b8d" title="ху: 0,011 %"></td><td width=12 bgcolor="#fd9b8d" title="жу: 0,019 %"></td><td width=12 bgcolor="#fd9b8d" title="бу: 0,09 %"></td><td width=12 bgcolor="#fd9b8d" title="гу: 0,046 %"></td><td width=12 bgcolor="#fd9b8d" title="зу: 0,044 %"></td><td width=12 bgcolor="#fd9b8d" title="пу: 0,069 %"></td><td width=12 bgcolor="#fd9b8d" title="ду: 0,17 %"></td><td width=12 bgcolor="#fd9b8d" title="му: 0,161 %"></td><td width=12 bgcolor="#fd9b8d" title="ку: 0,153 %"></td><td width=12 bgcolor="#fd9b8d" title="ру: 0,272 %"></td><td width=12 bgcolor="#fd9b8d" title="ву: 0,065 %"></td><td width=12 bgcolor="#fd9b8d" title="лу: 0,133 %"></td><td width=12 bgcolor="#fd9b8d" title="су: 0,095 %"></td><td width=12 bgcolor="#fd9b8d" title="ту: 0,138 %"></td><td width=12 bgcolor="#fd9b8d" title="ну: 0,147 %"></td></tr>
<tr height=12><td width=12 class="comp">ю</td><td width=12 bgcolor="#fd9b8d" title="_ю: 0,01 %"></td><td width=12 bgcolor="#fd9b8d" title="ою: 0,04 %"></td><td width=12 bgcolor="#fd9b8d" title="ею: 0,018 %"></td><td width=12 bgcolor="#fd9b8d" title="аю: 0,096 %"></td><td width=12 bgcolor="#fd9b8d" title="ию: 0,063 %"></td><td width=12 bgcolor="#fd9b8d" title="ую: 0,108 %"></td><td width=12 bgcolor="#d0afaa" title="юю: 0,002 %"></td><td width=12 bgcolor="#fd9b8d" title="яю: 0,025 %"></td><td width=12 bgcolor="#cac8c8" title="ёю: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="эю: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="ыю: 0 %"></td><td width=12 bgcolor="#fd9b8d" title="ью: 0,038 %"></td><td width=12 bgcolor="#d0afaa" title="ъю: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="йю: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="щю: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="чю: 0 %"></td><td width=12 bgcolor="#d0afaa" title="фю: 0 %"></td><td width=12 bgcolor="#cac8c8" title="цю: 0 %"></td><td width=12 bgcolor="#d0afaa" title="шю: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="хю: 0 %"></td><td width=12 bgcolor="#d0afaa" title="жю: 0 %"></td><td width=12 bgcolor="#d0afaa" title="бю: 0,003 %"></td><td width=12 bgcolor="#cac8c8" title="гю: 0 %"></td><td width=12 bgcolor="#d0afaa" title="зю: 0,001 %"></td><td width=12 bgcolor="#d0afaa" title="пю: 0 %"></td><td width=12 bgcolor="#d0afaa" title="дю: 0,001 %"></td><td width=12 bgcolor="#d0afaa" title="мю: 0 %"></td><td width=12 bgcolor="#d0afaa" title="кю: 0 %"></td><td width=12 bgcolor="#d0afaa" title="рю: 0,01 %"></td><td width=12 bgcolor="#d0afaa" title="вю: 0 %"></td><td width=12 bgcolor="#fd9b8d" title="лю: 0,106 %"></td><td width=12 bgcolor="#d0afaa" title="сю: 0,01 %"></td><td width=12 bgcolor="#d0afaa" title="тю: 0,005 %"></td><td width=12 bgcolor="#fd9b8d" title="ню: 0,01 %"></td></tr>
<tr height=12><td width=12 class="comp">я</td><td width=12 bgcolor="#fd9b8d" title="_я: 0,158 %"></td><td width=12 bgcolor="#fd9b8d" title="оя: 0,07 %"></td><td width=12 bgcolor="#fd9b8d" title="ея: 0,021 %"></td><td width=12 bgcolor="#fd9b8d" title="ая: 0,17 %"></td><td width=12 bgcolor="#fe715d" title="ия: 0,367 %"></td><td width=12 bgcolor="#d0afaa" title="уя: 0,004 %"></td><td width=12 bgcolor="#cac8c8" title="юя: 0 %"></td><td width=12 bgcolor="#d0afaa" title="яя: 0,007 %"></td><td width=12 bgcolor="#8e8c8c" title="ёя: 0 %"></td><td width=12 bgcolor="#cac8c8" title="эя: 0 %"></td><td width=12 bgcolor="#d0afaa" title="ыя: 0,003 %"></td><td width=12 bgcolor="#fd9b8d" title="ья: 0,029 %"></td><td width=12 bgcolor="#d0afaa" title="ъя: 0,01 %"></td><td width=12 bgcolor="#cac8c8" title="йя: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="щя: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="чя: 0 %"></td><td width=12 bgcolor="#d0afaa" title="фя: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="ця: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="шя: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="хя: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="жя: 0 %"></td><td width=12 bgcolor="#fd9b8d" title="бя: 0,038 %"></td><td width=12 bgcolor="#cac8c8" title="гя: 0 %"></td><td width=12 bgcolor="#fd9b8d" title="зя: 0,023 %"></td><td width=12 bgcolor="#fd9b8d" title="пя: 0,019 %"></td><td width=12 bgcolor="#fd9b8d" title="дя: 0,034 %"></td><td width=12 bgcolor="#fd9b8d" title="мя: 0,038 %"></td><td width=12 bgcolor="#8e8c8c" title="кя: 0 %"></td><td width=12 bgcolor="#fd9b8d" title="ря: 0,09 %"></td><td width=12 bgcolor="#fd9b8d" title="вя: 0,03 %"></td><td width=12 bgcolor="#fd9b8d" title="ля: 0,215 %"></td><td width=12 bgcolor="#fd9b8d" title="ся: 0,327 %"></td><td width=12 bgcolor="#fd9b8d" title="тя: 0,04 %"></td><td width=12 bgcolor="#fd9b8d" title="ня: 0,129 %"></td></tr>
<tr height=12><td width=12 class="comp">ё</td><td width=12 bgcolor="#d0afaa" title="_ё: 0 %"></td><td width=12 bgcolor="#d0afaa" title="оё: 0,002 %"></td><td width=12 bgcolor="#d0afaa" title="её: 0,007 %"></td><td width=12 bgcolor="#d0afaa" title="аё: 0,002 %"></td><td width=12 bgcolor="#d0afaa" title="иё: 0,001 %"></td><td width=12 bgcolor="#cac8c8" title="уё: 0 %"></td><td width=12 bgcolor="#cac8c8" title="юё: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="яё: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="ёё: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="эё: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="ыё: 0 %"></td><td width=12 bgcolor="#d0afaa" title="ьё: 0,001 %"></td><td width=12 bgcolor="#d0afaa" title="ъё: 0,002 %"></td><td width=12 bgcolor="#8e8c8c" title="йё: 0 %"></td><td width=12 bgcolor="#d0afaa" title="щё: 0,004 %"></td><td width=12 bgcolor="#d0afaa" title="чё: 0,006 %"></td><td width=12 bgcolor="#d0afaa" title="фё: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="цё: 0 %"></td><td width=12 bgcolor="#d0afaa" title="шё: 0,002 %"></td><td width=12 bgcolor="#cac8c8" title="хё: 0 %"></td><td width=12 bgcolor="#d0afaa" title="жё: 0,002 %"></td><td width=12 bgcolor="#d0afaa" title="бё: 0,001 %"></td><td width=12 bgcolor="#cac8c8" title="гё: 0 %"></td><td width=12 bgcolor="#d0afaa" title="зё: 0 %"></td><td width=12 bgcolor="#d0afaa" title="пё: 0 %"></td><td width=12 bgcolor="#d0afaa" title="дё: 0,004 %"></td><td width=12 bgcolor="#d0afaa" title="мё: 0,001 %"></td><td width=12 bgcolor="#cac8c8" title="кё: 0 %"></td><td width=12 bgcolor="#d0afaa" title="рё: 0,002 %"></td><td width=12 bgcolor="#d0afaa" title="вё: 0,002 %"></td><td width=12 bgcolor="#d0afaa" title="лё: 0,005 %"></td><td width=12 bgcolor="#d0afaa" title="сё: 0,004 %"></td><td width=12 bgcolor="#d0afaa" title="тё: 0,002 %"></td><td width=12 bgcolor="#d0afaa" title="нё: 0,003 %"></td></tr>
<tr height=12><td width=12 class="comp">э</td><td width=12 bgcolor="#fd9b8d" title="_э: 0,217 %"></td><td width=12 bgcolor="#fd9b8d" title="оэ: 0,011 %"></td><td width=12 bgcolor="#d0afaa" title="еэ: 0 %"></td><td width=12 bgcolor="#d0afaa" title="аэ: 0,001 %"></td><td width=12 bgcolor="#d0afaa" title="иэ: 0 %"></td><td width=12 bgcolor="#d0afaa" title="уэ: 0,001 %"></td><td width=12 bgcolor="#cac8c8" title="юэ: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="яэ: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="ёэ: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="ээ: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="ыэ: 0 %"></td><td width=12 bgcolor="#cac8c8" title="ьэ: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="ъэ: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="йэ: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="щэ: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="чэ: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="фэ: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="цэ: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="шэ: 0 %"></td><td width=12 bgcolor="#d0afaa" title="хэ: 0 %"></td><td width=12 bgcolor="#cac8c8" title="жэ: 0 %"></td><td width=12 bgcolor="#cac8c8" title="бэ: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="гэ: 0 %"></td><td width=12 bgcolor="#cac8c8" title="зэ: 0 %"></td><td width=12 bgcolor="#cac8c8" title="пэ: 0 %"></td><td width=12 bgcolor="#cac8c8" title="дэ: 0 %"></td><td width=12 bgcolor="#d0afaa" title="мэ: 0 %"></td><td width=12 bgcolor="#cac8c8" title="кэ: 0 %"></td><td width=12 bgcolor="#cac8c8" title="рэ: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="вэ: 0 %"></td><td width=12 bgcolor="#cac8c8" title="лэ: 0 %"></td><td width=12 bgcolor="#d0afaa" title="сэ: 0 %"></td><td width=12 bgcolor="#cac8c8" title="тэ: 0 %"></td><td width=12 bgcolor="#cac8c8" title="нэ: 0 %"></td></tr>
<tr height=12><td width=12 class="comp">ы</td><td width=12 bgcolor="#8e8c8c" title="_ы: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="оы: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="еы: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="аы: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="иы: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="уы: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="юы: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="яы: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="ёы: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="эы: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="ыы: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="ьы: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="ъы: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="йы: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="щы: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="чы: 0 %"></td><td width=12 bgcolor="#d0afaa" title="фы: 0,001 %"></td><td width=12 bgcolor="#fd9b8d" title="цы: 0,017 %"></td><td width=12 bgcolor="#8e8c8c" title="шы: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="хы: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="жы: 0 %"></td><td width=12 bgcolor="#fd9b8d" title="бы: 0,25 %"></td><td width=12 bgcolor="#8e8c8c" title="гы: 0 %"></td><td width=12 bgcolor="#fd9b8d" title="зы: 0,047 %"></td><td width=12 bgcolor="#fd9b8d" title="пы: 0,031 %"></td><td width=12 bgcolor="#fd9b8d" title="ды: 0,059 %"></td><td width=12 bgcolor="#fd9b8d" title="мы: 0,108 %"></td><td width=12 bgcolor="#cac8c8" title="кы: 0 %"></td><td width=12 bgcolor="#fd9b8d" title="ры: 0,133 %"></td><td width=12 bgcolor="#fd9b8d" title="вы: 0,251 %"></td><td width=12 bgcolor="#fd9b8d" title="лы: 0,047 %"></td><td width=12 bgcolor="#fd9b8d" title="сы: 0,035 %"></td><td width=12 bgcolor="#fd9b8d" title="ты: 0,141 %"></td><td width=12 bgcolor="#fe715d" title="ны: 0,508 %"></td></tr>
<tr height=12><td width=12 class="comp">ь</td><td width=12 bgcolor="#8e8c8c" title="_ь: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="оь: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="еь: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="аь: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="иь: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="уь: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="юь: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="яь: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="ёь: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="эь: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="ыь: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="ьь: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="ъь: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="йь: 0 %"></td><td width=12 bgcolor="#d0afaa" title="щь: 0,004 %"></td><td width=12 bgcolor="#fd9b8d" title="чь: 0,015 %"></td><td width=12 bgcolor="#d0afaa" title="фь: 0,001 %"></td><td width=12 bgcolor="#8e8c8c" title="ць: 0 %"></td><td width=12 bgcolor="#fd9b8d" title="шь: 0,029 %"></td><td width=12 bgcolor="#cac8c8" title="хь: 0 %"></td><td width=12 bgcolor="#d0afaa" title="жь: 0,003 %"></td><td width=12 bgcolor="#d0afaa" title="бь: 0,003 %"></td><td width=12 bgcolor="#8e8c8c" title="гь: 0 %"></td><td width=12 bgcolor="#fd9b8d" title="зь: 0,013 %"></td><td width=12 bgcolor="#d0afaa" title="пь: 0,007 %"></td><td width=12 bgcolor="#fd9b8d" title="дь: 0,036 %"></td><td width=12 bgcolor="#d0afaa" title="мь: 0,007 %"></td><td width=12 bgcolor="#cac8c8" title="кь: 0 %"></td><td width=12 bgcolor="#fd9b8d" title="рь: 0,045 %"></td><td width=12 bgcolor="#fd9b8d" title="вь: 0,015 %"></td><td width=12 bgcolor="#fe715d" title="ль: 0,458 %"></td><td width=12 bgcolor="#fd9b8d" title="сь: 0,161 %"></td><td width=12 bgcolor="#fe715d" title="ть: 0,484 %"></td><td width=12 bgcolor="#fd9b8d" title="нь: 0,078 %"></td></tr>
<tr height=12><td width=12 class="comp">ъ</td><td width=12 bgcolor="#8e8c8c" title="_ъ: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="оъ: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="еъ: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="аъ: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="иъ: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="уъ: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="юъ: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="яъ: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="ёъ: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="эъ: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="ыъ: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="ьъ: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="ъъ: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="йъ: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="щъ: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="чъ: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="фъ: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="цъ: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="шъ: 0 %"></td><td width=12 bgcolor="#d0afaa" title="хъ: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="жъ: 0 %"></td><td width=12 bgcolor="#fd9b8d" title="бъ: 0,031 %"></td><td width=12 bgcolor="#8e8c8c" title="гъ: 0 %"></td><td width=12 bgcolor="#d0afaa" title="зъ: 0,002 %"></td><td width=12 bgcolor="#8e8c8c" title="пъ: 0 %"></td><td width=12 bgcolor="#d0afaa" title="дъ: 0,003 %"></td><td width=12 bgcolor="#8e8c8c" title="мъ: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="къ: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="ръ: 0 %"></td><td width=12 bgcolor="#d0afaa" title="въ: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="лъ: 0 %"></td><td width=12 bgcolor="#d0afaa" title="съ: 0,002 %"></td><td width=12 bgcolor="#d0afaa" title="тъ: 0,001 %"></td><td width=12 bgcolor="#cac8c8" title="нъ: 0 %"></td></tr>
<tr height=12><td width=12 class="comp">й</td><td width=12 bgcolor="#d0afaa" title="_й: 0,005 %"></td><td width=12 bgcolor="#fe715d" title="ой: 0,37 %"></td><td width=12 bgcolor="#fd9b8d" title="ей: 0,224 %"></td><td width=12 bgcolor="#fd9b8d" title="ай: 0,059 %"></td><td width=12 bgcolor="#fd9b8d" title="ий: 0,176 %"></td><td width=12 bgcolor="#d0afaa" title="уй: 0,008 %"></td><td width=12 bgcolor="#d0afaa" title="юй: 0 %"></td><td width=12 bgcolor="#d0afaa" title="яй: 0,006 %"></td><td width=12 bgcolor="#d0afaa" title="ёй: 0 %"></td><td width=12 bgcolor="#d0afaa" title="эй: 0 %"></td><td width=12 bgcolor="#fd9b8d" title="ый: 0,148 %"></td><td width=12 bgcolor="#8e8c8c" title="ьй: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="ъй: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="йй: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="щй: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="чй: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="фй: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="цй: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="шй: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="хй: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="жй: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="бй: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="гй: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="зй: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="пй: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="дй: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="мй: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="кй: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="рй: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="вй: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="лй: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="сй: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="тй: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="нй: 0 %"></td></tr>
<tr height=12><td width=12 class="comp">щ</td><td width=12 bgcolor="#d0afaa" title="_щ: 0,005 %"></td><td width=12 bgcolor="#fd9b8d" title="ощ: 0,021 %"></td><td width=12 bgcolor="#fd9b8d" title="ещ: 0,053 %"></td><td width=12 bgcolor="#fd9b8d" title="ащ: 0,029 %"></td><td width=12 bgcolor="#fd9b8d" title="ищ: 0,014 %"></td><td width=12 bgcolor="#fd9b8d" title="ущ: 0,042 %"></td><td width=12 bgcolor="#fd9b8d" title="ющ: 0,068 %"></td><td width=12 bgcolor="#fd9b8d" title="ящ: 0,033 %"></td><td width=12 bgcolor="#cac8c8" title="ёщ: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="эщ: 0 %"></td><td width=12 bgcolor="#d0afaa" title="ыщ: 0,001 %"></td><td width=12 bgcolor="#d0afaa" title="ьщ: 0,001 %"></td><td width=12 bgcolor="#8e8c8c" title="ъщ: 0 %"></td><td width=12 bgcolor="#d0afaa" title="йщ: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="щщ: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="чщ: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="фщ: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="цщ: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="шщ: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="хщ: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="жщ: 0 %"></td><td width=12 bgcolor="#fd9b8d" title="бщ: 0,039 %"></td><td width=12 bgcolor="#8e8c8c" title="гщ: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="зщ: 0 %"></td><td width=12 bgcolor="#d0afaa" title="пщ: 0 %"></td><td width=12 bgcolor="#cac8c8" title="дщ: 0 %"></td><td width=12 bgcolor="#d0afaa" title="мщ: 0,001 %"></td><td width=12 bgcolor="#8e8c8c" title="кщ: 0 %"></td><td width=12 bgcolor="#d0afaa" title="рщ: 0,001 %"></td><td width=12 bgcolor="#d0afaa" title="вщ: 0,003 %"></td><td width=12 bgcolor="#d0afaa" title="лщ: 0,003 %"></td><td width=12 bgcolor="#cac8c8" title="сщ: 0 %"></td><td width=12 bgcolor="#d0afaa" title="тщ: 0,001 %"></td><td width=12 bgcolor="#d0afaa" title="нщ: 0,008 %"></td></tr>
<tr height=12><td width=12 class="comp">ч</td><td width=12 bgcolor="#fe715d" title="_ч: 0,386 %"></td><td width=12 bgcolor="#fd9b8d" title="оч: 0,159 %"></td><td width=12 bgcolor="#fd9b8d" title="еч: 0,107 %"></td><td width=12 bgcolor="#fd9b8d" title="ач: 0,107 %"></td><td width=12 bgcolor="#fd9b8d" title="ич: 0,177 %"></td><td width=12 bgcolor="#fd9b8d" title="уч: 0,127 %"></td><td width=12 bgcolor="#fd9b8d" title="юч: 0,025 %"></td><td width=12 bgcolor="#fd9b8d" title="яч: 0,011 %"></td><td width=12 bgcolor="#cac8c8" title="ёч: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="эч: 0 %"></td><td width=12 bgcolor="#fd9b8d" title="ыч: 0,019 %"></td><td width=12 bgcolor="#d0afaa" title="ьч: 0,004 %"></td><td width=12 bgcolor="#8e8c8c" title="ъч: 0 %"></td><td width=12 bgcolor="#d0afaa" title="йч: 0,008 %"></td><td width=12 bgcolor="#8e8c8c" title="щч: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="чч: 0 %"></td><td width=12 bgcolor="#cac8c8" title="фч: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="цч: 0 %"></td><td width=12 bgcolor="#cac8c8" title="шч: 0 %"></td><td width=12 bgcolor="#cac8c8" title="хч: 0 %"></td><td width=12 bgcolor="#d0afaa" title="жч: 0,003 %"></td><td width=12 bgcolor="#d0afaa" title="бч: 0,001 %"></td><td width=12 bgcolor="#d0afaa" title="гч: 0,002 %"></td><td width=12 bgcolor="#d0afaa" title="зч: 0,005 %"></td><td width=12 bgcolor="#d0afaa" title="пч: 0,002 %"></td><td width=12 bgcolor="#d0afaa" title="дч: 0,006 %"></td><td width=12 bgcolor="#d0afaa" title="мч: 0,002 %"></td><td width=12 bgcolor="#cac8c8" title="кч: 0 %"></td><td width=12 bgcolor="#d0afaa" title="рч: 0,008 %"></td><td width=12 bgcolor="#d0afaa" title="вч: 0,003 %"></td><td width=12 bgcolor="#d0afaa" title="лч: 0,008 %"></td><td width=12 bgcolor="#fd9b8d" title="сч: 0,041 %"></td><td width=12 bgcolor="#fd9b8d" title="тч: 0,025 %"></td><td width=12 bgcolor="#fd9b8d" title="нч: 0,017 %"></td></tr>
<tr height=12><td width=12 class="comp">ф</td><td width=12 bgcolor="#fd9b8d" title="_ф: 0,108 %"></td><td width=12 bgcolor="#fd9b8d" title="оф: 0,023 %"></td><td width=12 bgcolor="#fd9b8d" title="еф: 0,019 %"></td><td width=12 bgcolor="#fd9b8d" title="аф: 0,018 %"></td><td width=12 bgcolor="#fd9b8d" title="иф: 0,014 %"></td><td width=12 bgcolor="#d0afaa" title="уф: 0,002 %"></td><td width=12 bgcolor="#d0afaa" title="юф: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="яф: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="ёф: 0 %"></td><td width=12 bgcolor="#d0afaa" title="эф: 0,008 %"></td><td width=12 bgcolor="#cac8c8" title="ыф: 0 %"></td><td width=12 bgcolor="#d0afaa" title="ьф: 0,001 %"></td><td width=12 bgcolor="#8e8c8c" title="ъф: 0 %"></td><td width=12 bgcolor="#d0afaa" title="йф: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="щф: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="чф: 0 %"></td><td width=12 bgcolor="#d0afaa" title="фф: 0,008 %"></td><td width=12 bgcolor="#8e8c8c" title="цф: 0 %"></td><td width=12 bgcolor="#cac8c8" title="шф: 0 %"></td><td width=12 bgcolor="#cac8c8" title="хф: 0 %"></td><td width=12 bgcolor="#cac8c8" title="жф: 0 %"></td><td width=12 bgcolor="#cac8c8" title="бф: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="гф: 0 %"></td><td width=12 bgcolor="#cac8c8" title="зф: 0 %"></td><td width=12 bgcolor="#cac8c8" title="пф: 0 %"></td><td width=12 bgcolor="#cac8c8" title="дф: 0 %"></td><td width=12 bgcolor="#d0afaa" title="мф: 0,001 %"></td><td width=12 bgcolor="#cac8c8" title="кф: 0 %"></td><td width=12 bgcolor="#d0afaa" title="рф: 0,002 %"></td><td width=12 bgcolor="#cac8c8" title="вф: 0 %"></td><td width=12 bgcolor="#d0afaa" title="лф: 0 %"></td><td width=12 bgcolor="#d0afaa" title="сф: 0,005 %"></td><td width=12 bgcolor="#d0afaa" title="тф: 0,001 %"></td><td width=12 bgcolor="#fd9b8d" title="нф: 0,018 %"></td></tr>
<tr height=12><td width=12 class="comp">ц</td><td width=12 bgcolor="#fd9b8d" title="_ц: 0,063 %"></td><td width=12 bgcolor="#fd9b8d" title="оц: 0,034 %"></td><td width=12 bgcolor="#fd9b8d" title="ец: 0,034 %"></td><td width=12 bgcolor="#fd9b8d" title="ац: 0,099 %"></td><td width=12 bgcolor="#fd9b8d" title="иц: 0,09 %"></td><td width=12 bgcolor="#d0afaa" title="уц: 0,001 %"></td><td width=12 bgcolor="#d0afaa" title="юц: 0,003 %"></td><td width=12 bgcolor="#fd9b8d" title="яц: 0,01 %"></td><td width=12 bgcolor="#cac8c8" title="ёц: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="эц: 0 %"></td><td width=12 bgcolor="#d0afaa" title="ыц: 0,001 %"></td><td width=12 bgcolor="#d0afaa" title="ьц: 0,006 %"></td><td width=12 bgcolor="#8e8c8c" title="ъц: 0 %"></td><td width=12 bgcolor="#d0afaa" title="йц: 0,003 %"></td><td width=12 bgcolor="#8e8c8c" title="щц: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="чц: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="фц: 0 %"></td><td width=12 bgcolor="#cac8c8" title="цц: 0 %"></td><td width=12 bgcolor="#d0afaa" title="шц: 0 %"></td><td width=12 bgcolor="#cac8c8" title="хц: 0 %"></td><td width=12 bgcolor="#cac8c8" title="жц: 0 %"></td><td width=12 bgcolor="#d0afaa" title="бц: 0,001 %"></td><td width=12 bgcolor="#8e8c8c" title="гц: 0 %"></td><td width=12 bgcolor="#d0afaa" title="зц: 0,002 %"></td><td width=12 bgcolor="#d0afaa" title="пц: 0,002 %"></td><td width=12 bgcolor="#fd9b8d" title="дц: 0,014 %"></td><td width=12 bgcolor="#d0afaa" title="мц: 0,002 %"></td><td width=12 bgcolor="#fd9b8d" title="кц: 0,025 %"></td><td width=12 bgcolor="#d0afaa" title="рц: 0,005 %"></td><td width=12 bgcolor="#d0afaa" title="вц: 0,002 %"></td><td width=12 bgcolor="#cac8c8" title="лц: 0 %"></td><td width=12 bgcolor="#d0afaa" title="сц: 0,006 %"></td><td width=12 bgcolor="#d0afaa" title="тц: 0,006 %"></td><td width=12 bgcolor="#fd9b8d" title="нц: 0,039 %"></td></tr>
<tr height=12><td width=12 class="comp">ш</td><td width=12 bgcolor="#fd9b8d" title="_ш: 0,054 %"></td><td width=12 bgcolor="#fd9b8d" title="ош: 0,063 %"></td><td width=12 bgcolor="#fd9b8d" title="еш: 0,065 %"></td><td width=12 bgcolor="#fd9b8d" title="аш: 0,062 %"></td><td width=12 bgcolor="#fd9b8d" title="иш: 0,033 %"></td><td width=12 bgcolor="#fd9b8d" title="уш: 0,051 %"></td><td width=12 bgcolor="#d0afaa" title="юш: 0,003 %"></td><td width=12 bgcolor="#d0afaa" title="яш: 0,001 %"></td><td width=12 bgcolor="#d0afaa" title="ёш: 0 %"></td><td width=12 bgcolor="#d0afaa" title="эш: 0 %"></td><td width=12 bgcolor="#fd9b8d" title="ыш: 0,035 %"></td><td width=12 bgcolor="#fd9b8d" title="ьш: 0,037 %"></td><td width=12 bgcolor="#8e8c8c" title="ъш: 0 %"></td><td width=12 bgcolor="#d0afaa" title="йш: 0,01 %"></td><td width=12 bgcolor="#8e8c8c" title="щш: 0 %"></td><td width=12 bgcolor="#fd9b8d" title="чш: 0,011 %"></td><td width=12 bgcolor="#cac8c8" title="фш: 0 %"></td><td width=12 bgcolor="#cac8c8" title="цш: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="шш: 0 %"></td><td width=12 bgcolor="#d0afaa" title="хш: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="жш: 0 %"></td><td width=12 bgcolor="#d0afaa" title="бш: 0,001 %"></td><td width=12 bgcolor="#d0afaa" title="гш: 0 %"></td><td width=12 bgcolor="#d0afaa" title="зш: 0 %"></td><td width=12 bgcolor="#d0afaa" title="пш: 0 %"></td><td width=12 bgcolor="#d0afaa" title="дш: 0,007 %"></td><td width=12 bgcolor="#cac8c8" title="мш: 0 %"></td><td width=12 bgcolor="#d0afaa" title="кш: 0,001 %"></td><td width=12 bgcolor="#fd9b8d" title="рш: 0,02 %"></td><td width=12 bgcolor="#fd9b8d" title="вш: 0,038 %"></td><td width=12 bgcolor="#d0afaa" title="лш: 0,001 %"></td><td width=12 bgcolor="#d0afaa" title="сш: 0,01 %"></td><td width=12 bgcolor="#d0afaa" title="тш: 0 %"></td><td width=12 bgcolor="#d0afaa" title="нш: 0,001 %"></td></tr>
<tr height=12><td width=12 class="comp">х</td><td width=12 bgcolor="#fd9b8d" title="_х: 0,109 %"></td><td width=12 bgcolor="#fd9b8d" title="ох: 0,039 %"></td><td width=12 bgcolor="#fd9b8d" title="ех: 0,072 %"></td><td width=12 bgcolor="#fd9b8d" title="ах: 0,094 %"></td><td width=12 bgcolor="#fd9b8d" title="их: 0,189 %"></td><td width=12 bgcolor="#fd9b8d" title="ух: 0,033 %"></td><td width=12 bgcolor="#d0afaa" title="юх: 0,001 %"></td><td width=12 bgcolor="#fd9b8d" title="ях: 0,028 %"></td><td width=12 bgcolor="#d0afaa" title="ёх: 0,001 %"></td><td width=12 bgcolor="#d0afaa" title="эх: 0,001 %"></td><td width=12 bgcolor="#fd9b8d" title="ых: 0,208 %"></td><td width=12 bgcolor="#d0afaa" title="ьх: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="ъх: 0 %"></td><td width=12 bgcolor="#cac8c8" title="йх: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="щх: 0 %"></td><td width=12 bgcolor="#cac8c8" title="чх: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="фх: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="цх: 0 %"></td><td width=12 bgcolor="#cac8c8" title="шх: 0 %"></td><td width=12 bgcolor="#cac8c8" title="хх: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="жх: 0 %"></td><td width=12 bgcolor="#fd9b8d" title="бх: 0,013 %"></td><td width=12 bgcolor="#8e8c8c" title="гх: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="зх: 0 %"></td><td width=12 bgcolor="#cac8c8" title="пх: 0 %"></td><td width=12 bgcolor="#d0afaa" title="дх: 0,004 %"></td><td width=12 bgcolor="#cac8c8" title="мх: 0 %"></td><td width=12 bgcolor="#cac8c8" title="кх: 0 %"></td><td width=12 bgcolor="#fd9b8d" title="рх: 0,015 %"></td><td width=12 bgcolor="#d0afaa" title="вх: 0,009 %"></td><td width=12 bgcolor="#d0afaa" title="лх: 0 %"></td><td width=12 bgcolor="#fd9b8d" title="сх: 0,026 %"></td><td width=12 bgcolor="#d0afaa" title="тх: 0,001 %"></td><td width=12 bgcolor="#d0afaa" title="нх: 0 %"></td></tr>
<tr height=12><td width=12 class="comp">ж</td><td width=12 bgcolor="#fd9b8d" title="_ж: 0,163 %"></td><td width=12 bgcolor="#fd9b8d" title="ож: 0,182 %"></td><td width=12 bgcolor="#fd9b8d" title="еж: 0,081 %"></td><td width=12 bgcolor="#fd9b8d" title="аж: 0,116 %"></td><td width=12 bgcolor="#fd9b8d" title="иж: 0,029 %"></td><td width=12 bgcolor="#fd9b8d" title="уж: 0,113 %"></td><td width=12 bgcolor="#d0afaa" title="юж: 0,003 %"></td><td width=12 bgcolor="#fd9b8d" title="яж: 0,014 %"></td><td width=12 bgcolor="#d0afaa" title="ёж: 0,001 %"></td><td width=12 bgcolor="#cac8c8" title="эж: 0 %"></td><td width=12 bgcolor="#d0afaa" title="ыж: 0,002 %"></td><td width=12 bgcolor="#cac8c8" title="ьж: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="ъж: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="йж: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="щж: 0 %"></td><td width=12 bgcolor="#cac8c8" title="чж: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="фж: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="цж: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="шж: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="хж: 0 %"></td><td width=12 bgcolor="#d0afaa" title="жж: 0,001 %"></td><td width=12 bgcolor="#d0afaa" title="бж: 0,002 %"></td><td width=12 bgcolor="#cac8c8" title="гж: 0 %"></td><td width=12 bgcolor="#d0afaa" title="зж: 0,006 %"></td><td width=12 bgcolor="#8e8c8c" title="пж: 0 %"></td><td width=12 bgcolor="#d0afaa" title="дж: 0,006 %"></td><td width=12 bgcolor="#cac8c8" title="мж: 0 %"></td><td width=12 bgcolor="#fd9b8d" title="кж: 0,017 %"></td><td width=12 bgcolor="#fd9b8d" title="рж: 0,04 %"></td><td width=12 bgcolor="#cac8c8" title="вж: 0 %"></td><td width=12 bgcolor="#fd9b8d" title="лж: 0,04 %"></td><td width=12 bgcolor="#d0afaa" title="сж: 0,002 %"></td><td width=12 bgcolor="#d0afaa" title="тж: 0 %"></td><td width=12 bgcolor="#d0afaa" title="нж: 0,003 %"></td></tr>
<tr height=12><td width=12 class="comp">б</td><td width=12 bgcolor="#fe715d" title="_б: 0,511 %"></td><td width=12 bgcolor="#fe715d" title="об: 0,405 %"></td><td width=12 bgcolor="#fd9b8d" title="еб: 0,105 %"></td><td width=12 bgcolor="#fd9b8d" title="аб: 0,132 %"></td><td width=12 bgcolor="#fd9b8d" title="иб: 0,045 %"></td><td width=12 bgcolor="#fd9b8d" title="уб: 0,061 %"></td><td width=12 bgcolor="#fd9b8d" title="юб: 0,033 %"></td><td width=12 bgcolor="#d0afaa" title="яб: 0,007 %"></td><td width=12 bgcolor="#d0afaa" title="ёб: 0 %"></td><td width=12 bgcolor="#cac8c8" title="эб: 0 %"></td><td width=12 bgcolor="#fd9b8d" title="ыб: 0,016 %"></td><td width=12 bgcolor="#fd9b8d" title="ьб: 0,01 %"></td><td width=12 bgcolor="#8e8c8c" title="ъб: 0 %"></td><td width=12 bgcolor="#d0afaa" title="йб: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="щб: 0 %"></td><td width=12 bgcolor="#cac8c8" title="чб: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="фб: 0 %"></td><td width=12 bgcolor="#cac8c8" title="цб: 0 %"></td><td width=12 bgcolor="#cac8c8" title="шб: 0 %"></td><td width=12 bgcolor="#cac8c8" title="хб: 0 %"></td><td width=12 bgcolor="#d0afaa" title="жб: 0,008 %"></td><td width=12 bgcolor="#d0afaa" title="бб: 0,001 %"></td><td width=12 bgcolor="#d0afaa" title="гб: 0 %"></td><td width=12 bgcolor="#fd9b8d" title="зб: 0,013 %"></td><td width=12 bgcolor="#cac8c8" title="пб: 0 %"></td><td width=12 bgcolor="#d0afaa" title="дб: 0,002 %"></td><td width=12 bgcolor="#d0afaa" title="мб: 0,003 %"></td><td width=12 bgcolor="#cac8c8" title="кб: 0 %"></td><td width=12 bgcolor="#d0afaa" title="рб: 0,009 %"></td><td width=12 bgcolor="#d0afaa" title="вб: 0,001 %"></td><td width=12 bgcolor="#d0afaa" title="лб: 0,002 %"></td><td width=12 bgcolor="#d0afaa" title="сб: 0,01 %"></td><td width=12 bgcolor="#d0afaa" title="тб: 0,004 %"></td><td width=12 bgcolor="#d0afaa" title="нб: 0 %"></td></tr>
<tr height=12><td width=12 class="comp">г</td><td width=12 bgcolor="#fd9b8d" title="_г: 0,348 %"></td><td width=12 bgcolor="#fe715d" title="ог: 0,479 %"></td><td width=12 bgcolor="#fd9b8d" title="ег: 0,246 %"></td><td width=12 bgcolor="#fd9b8d" title="аг: 0,069 %"></td><td width=12 bgcolor="#fd9b8d" title="иг: 0,052 %"></td><td width=12 bgcolor="#fd9b8d" title="уг: 0,088 %"></td><td width=12 bgcolor="#d0afaa" title="юг: 0,001 %"></td><td width=12 bgcolor="#d0afaa" title="яг: 0,007 %"></td><td width=12 bgcolor="#d0afaa" title="ёг: 0 %"></td><td width=12 bgcolor="#d0afaa" title="эг: 0,001 %"></td><td width=12 bgcolor="#d0afaa" title="ыг: 0,008 %"></td><td width=12 bgcolor="#d0afaa" title="ьг: 0,005 %"></td><td width=12 bgcolor="#8e8c8c" title="ъг: 0 %"></td><td width=12 bgcolor="#cac8c8" title="йг: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="щг: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="чг: 0 %"></td><td width=12 bgcolor="#cac8c8" title="фг: 0 %"></td><td width=12 bgcolor="#cac8c8" title="цг: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="шг: 0 %"></td><td width=12 bgcolor="#d0afaa" title="хг: 0,004 %"></td><td width=12 bgcolor="#d0afaa" title="жг: 0,001 %"></td><td width=12 bgcolor="#d0afaa" title="бг: 0 %"></td><td width=12 bgcolor="#cac8c8" title="гг: 0 %"></td><td width=12 bgcolor="#fd9b8d" title="зг: 0,02 %"></td><td width=12 bgcolor="#cac8c8" title="пг: 0 %"></td><td width=12 bgcolor="#d0afaa" title="дг: 0,008 %"></td><td width=12 bgcolor="#d0afaa" title="мг: 0,003 %"></td><td width=12 bgcolor="#d0afaa" title="кг: 0,001 %"></td><td width=12 bgcolor="#fd9b8d" title="рг: 0,044 %"></td><td width=12 bgcolor="#d0afaa" title="вг: 0,003 %"></td><td width=12 bgcolor="#fd9b8d" title="лг: 0,012 %"></td><td width=12 bgcolor="#d0afaa" title="сг: 0,001 %"></td><td width=12 bgcolor="#d0afaa" title="тг: 0,001 %"></td><td width=12 bgcolor="#fd9b8d" title="нг: 0,012 %"></td></tr>
<tr height=12><td width=12 class="comp">з</td><td width=12 bgcolor="#fe715d" title="_з: 0,41 %"></td><td width=12 bgcolor="#fd9b8d" title="оз: 0,127 %"></td><td width=12 bgcolor="#fd9b8d" title="ез: 0,123 %"></td><td width=12 bgcolor="#fd9b8d" title="аз: 0,315 %"></td><td width=12 bgcolor="#fd9b8d" title="из: 0,279 %"></td><td width=12 bgcolor="#fd9b8d" title="уз: 0,029 %"></td><td width=12 bgcolor="#d0afaa" title="юз: 0,003 %"></td><td width=12 bgcolor="#fd9b8d" title="яз: 0,043 %"></td><td width=12 bgcolor="#d0afaa" title="ёз: 0,001 %"></td><td width=12 bgcolor="#d0afaa" title="эз: 0,001 %"></td><td width=12 bgcolor="#d0afaa" title="ыз: 0,005 %"></td><td width=12 bgcolor="#fd9b8d" title="ьз: 0,028 %"></td><td width=12 bgcolor="#8e8c8c" title="ъз: 0 %"></td><td width=12 bgcolor="#d0afaa" title="йз: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="щз: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="чз: 0 %"></td><td width=12 bgcolor="#cac8c8" title="фз: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="цз: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="шз: 0 %"></td><td width=12 bgcolor="#cac8c8" title="хз: 0 %"></td><td width=12 bgcolor="#cac8c8" title="жз: 0 %"></td><td width=12 bgcolor="#d0afaa" title="бз: 0,001 %"></td><td width=12 bgcolor="#cac8c8" title="гз: 0 %"></td><td width=12 bgcolor="#d0afaa" title="зз: 0,001 %"></td><td width=12 bgcolor="#8e8c8c" title="пз: 0 %"></td><td width=12 bgcolor="#d0afaa" title="дз: 0,003 %"></td><td width=12 bgcolor="#d0afaa" title="мз: 0 %"></td><td width=12 bgcolor="#d0afaa" title="кз: 0,002 %"></td><td width=12 bgcolor="#d0afaa" title="рз: 0,003 %"></td><td width=12 bgcolor="#fd9b8d" title="вз: 0,03 %"></td><td width=12 bgcolor="#d0afaa" title="лз: 0,001 %"></td><td width=12 bgcolor="#d0afaa" title="сз: 0,001 %"></td><td width=12 bgcolor="#d0afaa" title="тз: 0,001 %"></td><td width=12 bgcolor="#d0afaa" title="нз: 0,006 %"></td></tr>
<tr height=12><td width=12 class="comp">п</td><td width=12 bgcolor="#ca5949" title="_п: 1,679 %"></td><td width=12 bgcolor="#fd9b8d" title="оп: 0,169 %"></td><td width=12 bgcolor="#fd9b8d" title="еп: 0,081 %"></td><td width=12 bgcolor="#fd9b8d" title="ап: 0,088 %"></td><td width=12 bgcolor="#fd9b8d" title="ип: 0,024 %"></td><td width=12 bgcolor="#fd9b8d" title="уп: 0,094 %"></td><td width=12 bgcolor="#d0afaa" title="юп: 0 %"></td><td width=12 bgcolor="#d0afaa" title="яп: 0,003 %"></td><td width=12 bgcolor="#d0afaa" title="ёп: 0 %"></td><td width=12 bgcolor="#d0afaa" title="эп: 0,003 %"></td><td width=12 bgcolor="#fd9b8d" title="ып: 0,024 %"></td><td width=12 bgcolor="#d0afaa" title="ьп: 0,001 %"></td><td width=12 bgcolor="#8e8c8c" title="ъп: 0 %"></td><td width=12 bgcolor="#d0afaa" title="йп: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="щп: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="чп: 0 %"></td><td width=12 bgcolor="#cac8c8" title="фп: 0 %"></td><td width=12 bgcolor="#cac8c8" title="цп: 0 %"></td><td width=12 bgcolor="#d0afaa" title="шп: 0,001 %"></td><td width=12 bgcolor="#cac8c8" title="хп: 0 %"></td><td width=12 bgcolor="#cac8c8" title="жп: 0 %"></td><td width=12 bgcolor="#d0afaa" title="бп: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="гп: 0 %"></td><td width=12 bgcolor="#cac8c8" title="зп: 0 %"></td><td width=12 bgcolor="#fd9b8d" title="пп: 0,015 %"></td><td width=12 bgcolor="#fd9b8d" title="дп: 0,017 %"></td><td width=12 bgcolor="#fd9b8d" title="мп: 0,045 %"></td><td width=12 bgcolor="#d0afaa" title="кп: 0 %"></td><td width=12 bgcolor="#fd9b8d" title="рп: 0,012 %"></td><td width=12 bgcolor="#fd9b8d" title="вп: 0,018 %"></td><td width=12 bgcolor="#d0afaa" title="лп: 0,002 %"></td><td width=12 bgcolor="#fd9b8d" title="сп: 0,195 %"></td><td width=12 bgcolor="#d0afaa" title="тп: 0,008 %"></td><td width=12 bgcolor="#cac8c8" title="нп: 0 %"></td></tr>
<tr height=12><td width=12 class="comp">д</td><td width=12 bgcolor="#fe715d" title="_д: 0,728 %"></td><td width=12 bgcolor="#fe715d" title="од: 0,592 %"></td><td width=12 bgcolor="#fe715d" title="ед: 0,359 %"></td><td width=12 bgcolor="#fd9b8d" title="ад: 0,161 %"></td><td width=12 bgcolor="#fd9b8d" title="ид: 0,114 %"></td><td width=12 bgcolor="#fd9b8d" title="уд: 0,154 %"></td><td width=12 bgcolor="#fd9b8d" title="юд: 0,033 %"></td><td width=12 bgcolor="#fd9b8d" title="яд: 0,044 %"></td><td width=12 bgcolor="#d0afaa" title="ёд: 0 %"></td><td width=12 bgcolor="#d0afaa" title="эд: 0 %"></td><td width=12 bgcolor="#fd9b8d" title="ыд: 0,013 %"></td><td width=12 bgcolor="#d0afaa" title="ьд: 0,002 %"></td><td width=12 bgcolor="#8e8c8c" title="ъд: 0 %"></td><td width=12 bgcolor="#fd9b8d" title="йд: 0,011 %"></td><td width=12 bgcolor="#8e8c8c" title="щд: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="чд: 0 %"></td><td width=12 bgcolor="#cac8c8" title="фд: 0 %"></td><td width=12 bgcolor="#cac8c8" title="цд: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="шд: 0 %"></td><td width=12 bgcolor="#cac8c8" title="хд: 0 %"></td><td width=12 bgcolor="#fd9b8d" title="жд: 0,094 %"></td><td width=12 bgcolor="#d0afaa" title="бд: 0,001 %"></td><td width=12 bgcolor="#fd9b8d" title="гд: 0,071 %"></td><td width=12 bgcolor="#fd9b8d" title="зд: 0,087 %"></td><td width=12 bgcolor="#d0afaa" title="пд: 0 %"></td><td width=12 bgcolor="#d0afaa" title="дд: 0,006 %"></td><td width=12 bgcolor="#cac8c8" title="мд: 0 %"></td><td width=12 bgcolor="#d0afaa" title="кд: 0 %"></td><td width=12 bgcolor="#fd9b8d" title="рд: 0,023 %"></td><td width=12 bgcolor="#fd9b8d" title="вд: 0,02 %"></td><td width=12 bgcolor="#d0afaa" title="лд: 0,004 %"></td><td width=12 bgcolor="#fd9b8d" title="сд: 0,019 %"></td><td width=12 bgcolor="#fd9b8d" title="тд: 0,015 %"></td><td width=12 bgcolor="#fd9b8d" title="нд: 0,048 %"></td></tr>
<tr height=12><td width=12 class="comp">м</td><td width=12 bgcolor="#fe715d" title="_м: 0,554 %"></td><td width=12 bgcolor="#fe715d" title="ом: 0,511 %"></td><td width=12 bgcolor="#fe715d" title="ем: 0,392 %"></td><td width=12 bgcolor="#fd9b8d" title="ам: 0,288 %"></td><td width=12 bgcolor="#fd9b8d" title="им: 0,292 %"></td><td width=12 bgcolor="#fd9b8d" title="ум: 0,095 %"></td><td width=12 bgcolor="#d0afaa" title="юм: 0,002 %"></td><td width=12 bgcolor="#fd9b8d" title="ям: 0,052 %"></td><td width=12 bgcolor="#d0afaa" title="ём: 0,006 %"></td><td width=12 bgcolor="#d0afaa" title="эм: 0,003 %"></td><td width=12 bgcolor="#fd9b8d" title="ым: 0,126 %"></td><td width=12 bgcolor="#fd9b8d" title="ьм: 0,022 %"></td><td width=12 bgcolor="#8e8c8c" title="ъм: 0 %"></td><td width=12 bgcolor="#d0afaa" title="йм: 0,004 %"></td><td width=12 bgcolor="#8e8c8c" title="щм: 0 %"></td><td width=12 bgcolor="#d0afaa" title="чм: 0 %"></td><td width=12 bgcolor="#d0afaa" title="фм: 0 %"></td><td width=12 bgcolor="#d0afaa" title="цм: 0 %"></td><td width=12 bgcolor="#d0afaa" title="шм: 0,001 %"></td><td width=12 bgcolor="#d0afaa" title="хм: 0,002 %"></td><td width=12 bgcolor="#d0afaa" title="жм: 0,001 %"></td><td width=12 bgcolor="#d0afaa" title="бм: 0,004 %"></td><td width=12 bgcolor="#d0afaa" title="гм: 0,002 %"></td><td width=12 bgcolor="#fd9b8d" title="зм: 0,052 %"></td><td width=12 bgcolor="#8e8c8c" title="пм: 0 %"></td><td width=12 bgcolor="#d0afaa" title="дм: 0,009 %"></td><td width=12 bgcolor="#fd9b8d" title="мм: 0,023 %"></td><td width=12 bgcolor="#d0afaa" title="км: 0,001 %"></td><td width=12 bgcolor="#fd9b8d" title="рм: 0,069 %"></td><td width=12 bgcolor="#fd9b8d" title="вм: 0,014 %"></td><td width=12 bgcolor="#d0afaa" title="лм: 0,001 %"></td><td width=12 bgcolor="#fd9b8d" title="см: 0,07 %"></td><td width=12 bgcolor="#d0afaa" title="тм: 0,007 %"></td><td width=12 bgcolor="#d0afaa" title="нм: 0 %"></td></tr>
<tr height=12><td width=12 class="comp">к</td><td width=12 bgcolor="#fe715d" title="_к: 0,793 %"></td><td width=12 bgcolor="#fd9b8d" title="ок: 0,209 %"></td><td width=12 bgcolor="#fd9b8d" title="ек: 0,177 %"></td><td width=12 bgcolor="#fe715d" title="ак: 0,388 %"></td><td width=12 bgcolor="#fd9b8d" title="ик: 0,211 %"></td><td width=12 bgcolor="#fd9b8d" title="ук: 0,094 %"></td><td width=12 bgcolor="#d0afaa" title="юк: 0,001 %"></td><td width=12 bgcolor="#fd9b8d" title="як: 0,013 %"></td><td width=12 bgcolor="#d0afaa" title="ёк: 0 %"></td><td width=12 bgcolor="#fd9b8d" title="эк: 0,022 %"></td><td width=12 bgcolor="#fd9b8d" title="ык: 0,019 %"></td><td width=12 bgcolor="#fd9b8d" title="ьк: 0,072 %"></td><td width=12 bgcolor="#8e8c8c" title="ък: 0 %"></td><td width=12 bgcolor="#d0afaa" title="йк: 0,008 %"></td><td width=12 bgcolor="#8e8c8c" title="щк: 0 %"></td><td width=12 bgcolor="#fd9b8d" title="чк: 0,025 %"></td><td width=12 bgcolor="#cac8c8" title="фк: 0 %"></td><td width=12 bgcolor="#d0afaa" title="цк: 0,004 %"></td><td width=12 bgcolor="#fd9b8d" title="шк: 0,034 %"></td><td width=12 bgcolor="#d0afaa" title="хк: 0 %"></td><td width=12 bgcolor="#d0afaa" title="жк: 0,009 %"></td><td width=12 bgcolor="#d0afaa" title="бк: 0,008 %"></td><td width=12 bgcolor="#d0afaa" title="гк: 0,007 %"></td><td width=12 bgcolor="#fd9b8d" title="зк: 0,013 %"></td><td width=12 bgcolor="#fd9b8d" title="пк: 0,012 %"></td><td width=12 bgcolor="#fd9b8d" title="дк: 0,029 %"></td><td width=12 bgcolor="#fd9b8d" title="мк: 0,011 %"></td><td width=12 bgcolor="#d0afaa" title="кк: 0,002 %"></td><td width=12 bgcolor="#fd9b8d" title="рк: 0,032 %"></td><td width=12 bgcolor="#fd9b8d" title="вк: 0,047 %"></td><td width=12 bgcolor="#fd9b8d" title="лк: 0,025 %"></td><td width=12 bgcolor="#fe715d" title="ск: 0,397 %"></td><td width=12 bgcolor="#fd9b8d" title="тк: 0,062 %"></td><td width=12 bgcolor="#fd9b8d" title="нк: 0,045 %"></td></tr>
<tr height=12><td width=12 class="comp">р</td><td width=12 bgcolor="#fe715d" title="_р: 0,51 %"></td><td width=12 bgcolor="#fe715d" title="ор: 0,611 %"></td><td width=12 bgcolor="#fe715d" title="ер: 0,608 %"></td><td width=12 bgcolor="#fd9b8d" title="ар: 0,246 %"></td><td width=12 bgcolor="#fd9b8d" title="ир: 0,126 %"></td><td width=12 bgcolor="#fd9b8d" title="ур: 0,087 %"></td><td width=12 bgcolor="#d0afaa" title="юр: 0,007 %"></td><td width=12 bgcolor="#d0afaa" title="яр: 0,01 %"></td><td width=12 bgcolor="#d0afaa" title="ёр: 0,003 %"></td><td width=12 bgcolor="#d0afaa" title="эр: 0,002 %"></td><td width=12 bgcolor="#fd9b8d" title="ыр: 0,02 %"></td><td width=12 bgcolor="#8e8c8c" title="ьр: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="ър: 0 %"></td><td width=12 bgcolor="#d0afaa" title="йр: 0 %"></td><td width=12 bgcolor="#d0afaa" title="щр: 0 %"></td><td width=12 bgcolor="#d0afaa" title="чр: 0,006 %"></td><td width=12 bgcolor="#fd9b8d" title="фр: 0,015 %"></td><td width=12 bgcolor="#cac8c8" title="цр: 0 %"></td><td width=12 bgcolor="#d0afaa" title="шр: 0,001 %"></td><td width=12 bgcolor="#fd9b8d" title="хр: 0,023 %"></td><td width=12 bgcolor="#d0afaa" title="жр: 0,001 %"></td><td width=12 bgcolor="#fd9b8d" title="бр: 0,11 %"></td><td width=12 bgcolor="#fd9b8d" title="гр: 0,114 %"></td><td width=12 bgcolor="#fd9b8d" title="зр: 0,033 %"></td><td width=12 bgcolor="#fe715d" title="пр: 0,79 %"></td><td width=12 bgcolor="#fd9b8d" title="др: 0,11 %"></td><td width=12 bgcolor="#d0afaa" title="мр: 0,003 %"></td><td width=12 bgcolor="#fd9b8d" title="кр: 0,137 %"></td><td width=12 bgcolor="#fd9b8d" title="рр: 0,01 %"></td><td width=12 bgcolor="#fd9b8d" title="вр: 0,071 %"></td><td width=12 bgcolor="#cac8c8" title="лр: 0 %"></td><td width=12 bgcolor="#fd9b8d" title="ср: 0,043 %"></td><td width=12 bgcolor="#fe715d" title="тр: 0,351 %"></td><td width=12 bgcolor="#d0afaa" title="нр: 0,006 %"></td></tr>
<tr height=12><td width=12 class="comp">в</td><td width=12 bgcolor="#ca5949" title="_в: 1,445 %"></td><td width=12 bgcolor="#fe715d" title="ов: 0,884 %"></td><td width=12 bgcolor="#fd9b8d" title="ев: 0,133 %"></td><td width=12 bgcolor="#fd9b8d" title="ав: 0,307 %"></td><td width=12 bgcolor="#fd9b8d" title="ив: 0,21 %"></td><td width=12 bgcolor="#fd9b8d" title="ув: 0,04 %"></td><td width=12 bgcolor="#d0afaa" title="юв: 0 %"></td><td width=12 bgcolor="#fd9b8d" title="яв: 0,045 %"></td><td width=12 bgcolor="#d0afaa" title="ёв: 0,001 %"></td><td width=12 bgcolor="#d0afaa" title="эв: 0,001 %"></td><td width=12 bgcolor="#fd9b8d" title="ыв: 0,081 %"></td><td width=12 bgcolor="#d0afaa" title="ьв: 0,002 %"></td><td width=12 bgcolor="#8e8c8c" title="ъв: 0 %"></td><td width=12 bgcolor="#d0afaa" title="йв: 0 %"></td><td width=12 bgcolor="#cac8c8" title="щв: 0 %"></td><td width=12 bgcolor="#d0afaa" title="чв: 0,001 %"></td><td width=12 bgcolor="#8e8c8c" title="фв: 0 %"></td><td width=12 bgcolor="#fd9b8d" title="цв: 0,01 %"></td><td width=12 bgcolor="#d0afaa" title="шв: 0,002 %"></td><td width=12 bgcolor="#fd9b8d" title="хв: 0,011 %"></td><td width=12 bgcolor="#cac8c8" title="жв: 0 %"></td><td width=12 bgcolor="#d0afaa" title="бв: 0,006 %"></td><td width=12 bgcolor="#d0afaa" title="гв: 0,001 %"></td><td width=12 bgcolor="#fd9b8d" title="зв: 0,097 %"></td><td width=12 bgcolor="#8e8c8c" title="пв: 0 %"></td><td width=12 bgcolor="#fd9b8d" title="дв: 0,062 %"></td><td width=12 bgcolor="#d0afaa" title="мв: 0,001 %"></td><td width=12 bgcolor="#fd9b8d" title="кв: 0,034 %"></td><td width=12 bgcolor="#fd9b8d" title="рв: 0,044 %"></td><td width=12 bgcolor="#d0afaa" title="вв: 0,009 %"></td><td width=12 bgcolor="#d0afaa" title="лв: 0,002 %"></td><td width=12 bgcolor="#fd9b8d" title="св: 0,135 %"></td><td width=12 bgcolor="#fe715d" title="тв: 0,376 %"></td><td width=12 bgcolor="#d0afaa" title="нв: 0,007 %"></td></tr>
<tr height=12><td width=12 class="comp">л</td><td width=12 bgcolor="#fd9b8d" title="_л: 0,226 %"></td><td width=12 bgcolor="#fe715d" title="ол: 0,569 %"></td><td width=12 bgcolor="#fe715d" title="ел: 0,529 %"></td><td width=12 bgcolor="#fe715d" title="ал: 0,595 %"></td><td width=12 bgcolor="#fe715d" title="ил: 0,35 %"></td><td width=12 bgcolor="#fd9b8d" title="ул: 0,081 %"></td><td width=12 bgcolor="#d0afaa" title="юл: 0,003 %"></td><td width=12 bgcolor="#fd9b8d" title="ял: 0,045 %"></td><td width=12 bgcolor="#d0afaa" title="ёл: 0,004 %"></td><td width=12 bgcolor="#fd9b8d" title="эл: 0,013 %"></td><td width=12 bgcolor="#fd9b8d" title="ыл: 0,136 %"></td><td width=12 bgcolor="#8e8c8c" title="ьл: 0 %"></td><td width=12 bgcolor="#8e8c8c" title="ъл: 0 %"></td><td width=12 bgcolor="#d0afaa" title="йл: 0,005 %"></td><td width=12 bgcolor="#8e8c8c" title="щл: 0 %"></td><td width=12 bgcolor="#d0afaa" title="чл: 0,006 %"></td><td width=12 bgcolor="#d0afaa" title="фл: 0,004 %"></td><td width=12 bgcolor="#cac8c8" title="цл: 0 %"></td><td width=12 bgcolor="#fd9b8d" title="шл: 0,033 %"></td><td width=12 bgcolor="#d0afaa" title="хл: 0,009 %"></td><td width=12 bgcolor="#d0afaa" title="жл: 0,001 %"></td><td width=12 bgcolor="#fd9b8d" title="бл: 0,094 %"></td><td width=12 bgcolor="#fd9b8d" title="гл: 0,097 %"></td><td width=12 bgcolor="#fd9b8d" title="зл: 0,023 %"></td><td width=12 bgcolor="#fd9b8d" title="пл: 0,099 %"></td><td width=12 bgcolor="#fd9b8d" title="дл: 0,099 %"></td><td width=12 bgcolor="#fd9b8d" title="мл: 0,02 %"></td><td width=12 bgcolor="#fd9b8d" title="кл: 0,075 %"></td><td width=12 bgcolor="#d0afaa" title="рл: 0,005 %"></td><td width=12 bgcolor="#fd9b8d" title="вл: 0,153 %"></td><td width=12 bgcolor="#fd9b8d" title="лл: 0,017 %"></td><td width=12 bgcolor="#fd9b8d" title="сл: 0,265 %"></td><td width=12 bgcolor="#fd9b8d" title="тл: 0,019 %"></td><td width=12 bgcolor="#d0afaa" title="нл: 0 %"></td></tr>
<tr height=12><td width=12 class="comp">с</td><td width=12 bgcolor="#ca5949" title="_с: 1,468 %"></td><td width=12 bgcolor="#fe715d" title="ос: 0,671 %"></td><td width=12 bgcolor="#fe715d" title="ес: 0,508 %"></td><td width=12 bgcolor="#fe715d" title="ас: 0,381 %"></td><td width=12 bgcolor="#fd9b8d" title="ис: 0,322 %"></td><td width=12 bgcolor="#fd9b8d" title="ус: 0,137 %"></td><td width=12 bgcolor="#d0afaa" title="юс: 0,008 %"></td><td width=12 bgcolor="#fd9b8d" title="яс: 0,029 %"></td><td width=12 bgcolor="#d0afaa" title="ёс: 0,001 %"></td><td width=12 bgcolor="#d0afaa" title="эс: 0,002 %"></td><td width=12 bgcolor="#fd9b8d" title="ыс: 0,054 %"></td><td width=12 bgcolor="#fd9b8d" title="ьс: 0,088 %"></td><td width=12 bgcolor="#8e8c8c" title="ъс: 0 %"></td><td width=12 bgcolor="#fd9b8d" title="йс: 0,069 %"></td><td width=12 bgcolor="#8e8c8c" title="щс: 0 %"></td><td width=12 bgcolor="#cac8c8" title="чс: 0 %"></td><td width=12 bgcolor="#d0afaa" title="фс: 0,001 %"></td><td width=12 bgcolor="#cac8c8" title="цс: 0 %"></td><td width=12 bgcolor="#d0afaa" title="шс: 0 %"></td><td width=12 bgcolor="#d0afaa" title="хс: 0,005 %"></td><td width=12 bgcolor="#d0afaa" title="жс: 0,002 %"></td><td width=12 bgcolor="#fd9b8d" title="бс: 0,02 %"></td><td width=12 bgcolor="#d0afaa" title="гс: 0,002 %"></td><td width=12 bgcolor="#d0afaa" title="зс: 0,003 %"></td><td width=12 bgcolor="#d0afaa" title="пс: 0,003 %"></td><td width=12 bgcolor="#fd9b8d" title="дс: 0,061 %"></td><td width=12 bgcolor="#fd9b8d" title="мс: 0,01 %"></td><td width=12 bgcolor="#fd9b8d" title="кс: 0,036 %"></td><td width=12 bgcolor="#fd9b8d" title="рс: 0,053 %"></td><td width=12 bgcolor="#fd9b8d" title="вс: 0,196 %"></td><td width=12 bgcolor="#fd9b8d" title="лс: 0,071 %"></td><td width=12 bgcolor="#fd9b8d" title="сс: 0,111 %"></td><td width=12 bgcolor="#fd9b8d" title="тс: 0,204 %"></td><td width=12 bgcolor="#fd9b8d" title="нс: 0,076 %"></td></tr>
<tr height=12><td width=12 class="comp">т</td><td width=12 bgcolor="#fe715d" title="_т: 0,678 %"></td><td width=12 bgcolor="#fe715d" title="от: 0,634 %"></td><td width=12 bgcolor="#fe715d" title="ет: 0,58 %"></td><td width=12 bgcolor="#fe715d" title="ат: 0,475 %"></td><td width=12 bgcolor="#fe715d" title="ит: 0,426 %"></td><td width=12 bgcolor="#fd9b8d" title="ут: 0,12 %"></td><td width=12 bgcolor="#fd9b8d" title="ют: 0,076 %"></td><td width=12 bgcolor="#fd9b8d" title="ят: 0,133 %"></td><td width=12 bgcolor="#d0afaa" title="ёт: 0,009 %"></td><td width=12 bgcolor="#fd9b8d" title="эт: 0,169 %"></td><td width=12 bgcolor="#fd9b8d" title="ыт: 0,067 %"></td><td width=12 bgcolor="#fd9b8d" title="ьт: 0,024 %"></td><td width=12 bgcolor="#8e8c8c" title="ът: 0 %"></td><td width=12 bgcolor="#fd9b8d" title="йт: 0,022 %"></td><td width=12 bgcolor="#8e8c8c" title="щт: 0 %"></td><td width=12 bgcolor="#fd9b8d" title="чт: 0,213 %"></td><td width=12 bgcolor="#fd9b8d" title="фт: 0,016 %"></td><td width=12 bgcolor="#cac8c8" title="цт: 0 %"></td><td width=12 bgcolor="#d0afaa" title="шт: 0,008 %"></td><td width=12 bgcolor="#d0afaa" title="хт: 0,001 %"></td><td width=12 bgcolor="#d0afaa" title="жт: 0 %"></td><td width=12 bgcolor="#d0afaa" title="бт: 0 %"></td><td width=12 bgcolor="#d0afaa" title="гт: 0,001 %"></td><td width=12 bgcolor="#d0afaa" title="зт: 0,001 %"></td><td width=12 bgcolor="#d0afaa" title="пт: 0,008 %"></td><td width=12 bgcolor="#fd9b8d" title="дт: 0,011 %"></td><td width=12 bgcolor="#d0afaa" title="мт: 0,001 %"></td><td width=12 bgcolor="#fd9b8d" title="кт: 0,147 %"></td><td width=12 bgcolor="#fd9b8d" title="рт: 0,077 %"></td><td width=12 bgcolor="#fd9b8d" title="вт: 0,03 %"></td><td width=12 bgcolor="#d0afaa" title="лт: 0,008 %"></td><td width=12 bgcolor="#ca5949" title="ст: 1,297 %"></td><td width=12 bgcolor="#d0afaa" title="тт: 0,005 %"></td><td width=12 bgcolor="#fd9b8d" title="нт: 0,143 %"></td></tr>
<tr height=12><td width=12 class="comp">н</td><td width=12 bgcolor="#ca5949" title="_н: 1,276 %"></td><td width=12 bgcolor="#fe715d" title="он: 0,461 %"></td><td width=12 bgcolor="#fe715d" title="ен: 1,055 %"></td><td width=12 bgcolor="#fe715d" title="ан: 0,596 %"></td><td width=12 bgcolor="#fd9b8d" title="ин: 0,334 %"></td><td width=12 bgcolor="#fd9b8d" title="ун: 0,037 %"></td><td width=12 bgcolor="#d0afaa" title="юн: 0,005 %"></td><td width=12 bgcolor="#fd9b8d" title="ян: 0,053 %"></td><td width=12 bgcolor="#d0afaa" title="ён: 0,009 %"></td><td width=12 bgcolor="#d0afaa" title="эн: 0,006 %"></td><td width=12 bgcolor="#fd9b8d" title="ын: 0,02 %"></td><td width=12 bgcolor="#fd9b8d" title="ьн: 0,2 %"></td><td width=12 bgcolor="#8e8c8c" title="ън: 0 %"></td><td width=12 bgcolor="#fd9b8d" title="йн: 0,032 %"></td><td width=12 bgcolor="#d0afaa" title="щн: 0,005 %"></td><td width=12 bgcolor="#fd9b8d" title="чн: 0,092 %"></td><td width=12 bgcolor="#d0afaa" title="фн: 0,001 %"></td><td width=12 bgcolor="#cac8c8" title="цн: 0 %"></td><td width=12 bgcolor="#fd9b8d" title="шн: 0,027 %"></td><td width=12 bgcolor="#fd9b8d" title="хн: 0,033 %"></td><td width=12 bgcolor="#fd9b8d" title="жн: 0,099 %"></td><td width=12 bgcolor="#fd9b8d" title="бн: 0,03 %"></td><td width=12 bgcolor="#fd9b8d" title="гн: 0,019 %"></td><td width=12 bgcolor="#fd9b8d" title="зн: 0,159 %"></td><td width=12 bgcolor="#fd9b8d" title="пн: 0,011 %"></td><td width=12 bgcolor="#fd9b8d" title="дн: 0,171 %"></td><td width=12 bgcolor="#fd9b8d" title="мн: 0,109 %"></td><td width=12 bgcolor="#fd9b8d" title="кн: 0,041 %"></td><td width=12 bgcolor="#fd9b8d" title="рн: 0,095 %"></td><td width=12 bgcolor="#fd9b8d" title="вн: 0,145 %"></td><td width=12 bgcolor="#fd9b8d" title="лн: 0,056 %"></td><td width=12 bgcolor="#fd9b8d" title="сн: 0,106 %"></td><td width=12 bgcolor="#fd9b8d" title="тн: 0,148 %"></td><td width=12 bgcolor="#fe715d" title="нн: 0,355 %"></td></tr>
</table>

(если навести курсор на карту, то отобразятся заначения частоты биграммы).
Яркие биграммы наиболее частые, а темно-серые не встречающиеся.


## Трехбуквенная последовательность (триграмма)
По аналогии с биграммами рассмотрим частоту триграмм в русском языке.
Математически в русском языке возможны 33^3=35 937. На практике в 99 % случаев встречаются только 4400 триграмм.
Вот 50 самых частых триграмм в русском языке:
<pre>
<b><u>ТГ   %    ДГР</u></b>
ени    0,8 <img src="/img/o.jpg" height=12 width=300>
ост    0,6 <img src="/img/o.jpg" height=12 width=230>
про    0,5 <img src="/img/o.jpg" height=12 width=210>
ств    0,5 <img src="/img/o.jpg" height=12 width=200>
ого    0,5 <img src="/img/o.jpg" height=12 width=200>
ния    0,4 <img src="/img/o.jpg" height=12 width=176>
ани    0,4 <img src="/img/o.jpg" height=12 width=171>
при    0,4 <img src="/img/o.jpg" height=12 width=169>
ста    0,4 <img src="/img/o.jpg" height=12 width=157>
енн    0,4 <img src="/img/o.jpg" height=12 width=151>
ест    0,4 <img src="/img/o.jpg" height=12 width=146>
ние    0,4 <img src="/img/o.jpg" height=12 width=145>
льн    0,4 <img src="/img/o.jpg" height=12 width=140>
ова    0,4 <img src="/img/o.jpg" height=12 width=139>
что    0,3 <img src="/img/o.jpg" height=12 width=138>
его    0,3 <img src="/img/o.jpg" height=12 width=135>
тел    0,3 <img src="/img/o.jpg" height=12 width=130>
тор    0,3 <img src="/img/o.jpg" height=12 width=127>
сти    0,3 <img src="/img/o.jpg" height=12 width=122>
мен    0,3 <img src="/img/o.jpg" height=12 width=119>
сто    0,3 <img src="/img/o.jpg" height=12 width=116>
нно    0,3 <img src="/img/o.jpg" height=12 width=113>
ать    0,3 <img src="/img/o.jpg" height=12 width=113>
лен    0,3 <img src="/img/o.jpg" height=12 width=112>
пол    0,3 <img src="/img/o.jpg" height=12 width=111>
ель    0,3 <img src="/img/o.jpg" height=12 width=108>
ред    0,3 <img src="/img/o.jpg" height=12 width=107>
ров    0,3 <img src="/img/o.jpg" height=12 width=106>
пер    0,3 <img src="/img/o.jpg" height=12 width=105>
оль    0,3 <img src="/img/o.jpg" height=12 width=105>
оро    0,3 <img src="/img/o.jpg" height=12 width=104>
раз    0,3 <img src="/img/o.jpg" height=12 width=104>
ово    0,3 <img src="/img/o.jpg" height=12 width=103>
тся    0,3 <img src="/img/o.jpg" height=12 width=103>
пре    0,3 <img src="/img/o.jpg" height=12 width=102>
ото    0,3 <img src="/img/o.jpg" height=12 width=101>
ско    0,3 <img src="/img/o.jpg" height=12 width=100>
нны    0,2 <img src="/img/o.jpg" height=12 width=99>
ных    0,2 <img src="/img/o.jpg" height=12 width=97>
нос    0,2 <img src="/img/o.jpg" height=12 width=95>
ван    0,2 <img src="/img/o.jpg" height=12 width=95>
стр    0,2 <img src="/img/o.jpg" height=12 width=93>
ног    0,2 <img src="/img/o.jpg" height=12 width=93>
ере    0,2 <img src="/img/o.jpg" height=12 width=92>
тве    0,2 <img src="/img/o.jpg" height=12 width=91>
это    0,2 <img src="/img/o.jpg" height=12 width=89>
ите    0,2 <img src="/img/o.jpg" height=12 width=88>
как    0,2 <img src="/img/o.jpg" height=12 width=88>
дел    0,2 <img src="/img/o.jpg" height=12 width=87>
нов    0,2 <img src="/img/o.jpg" height=12 width=87>
</pre>

## Репрезнетативность используемых корпусов текста на основе триграмм
Конечно используемые корпусы текстов являются специфическими, а результаты анализа не соответствуют 
статитике использования слов для каждого человека. Но чтобы оценить насколько используемые корпусы 
репрезентативны для моего личного корпуса я отранжиловал триграммы по частоте использования, 
сопоставил их с частотой встречаемости остальных корпусов. Коэффициент корреляции составил 97 %, то 
есть в 97 % случаев я набираю триграмы так же часто, как часто они встречаются в других корпусах.

## Практические возможности
Кроме возможной оптимизации расположения букв на клавиатуре, результат анализа дает несколько практических возможностей повышения удобства письма на компьютере.
1. Использование автозамен на основе неиспользуемых биграмм и триграм. Например слово `например` можно набирать триграммой `нпр`, автоматически заменяемой компьютером на слово.  
2. Запись букв `й` и `ъ` одной клавишей.
3. Использование аккордов для мгновенного набора частых биграмм и триграмм. Например биграмму `ия` с пробелом удобно вводить аккордом (одновременным нажатием) клавиш <kbd>и</kbd> <kbd>я</kbd> 

## Заключение
Представленный анализ позволяет вывести некоторые закономерности во взаимопоследовательности букв,
Учитывая эти закономерности можно оптимизировать расположение букв на клавиатуре, так, чтобы
движения пальцев было наиболее оптимальным (минимальным).
