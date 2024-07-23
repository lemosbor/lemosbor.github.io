### Обрезать видео с 1 секунды по 5 минуту
    ffmpeg -i input.mp4 -ss 00:00:01 -to 00:05:00 -c copy output.mp4 
    ffmpeg -ss 00:00:01 -i input.mp3 -t 5*60 result.mp3
### Обрезать (сохранить) первые 40 секунд
    ffmpeg -i input.mkv -t 40 result.mp4
### Обрезать (пропустить) первые 40 секунд
    ffmpeg -ss 40 -i input.mp4 -c copy result.mp4
### Обрезать (сохранить) последние 40 секунд
    ffmpeg -sseof 40 -i input.mp4 result.mp4
    
### Мульти-резка видео в ffmpeg
1. Создать файл list.txt:  
	file video.mp4
	inpoint 34.5
	outpoint 55.1
	file video.mp4
	inpoint 111.0
	outpoint 155.3

2. Запустить команду  
    ffmpeg -f concat -i list.txt -c copy output.mp4
    ffmpeg -f concat -i list.txt  -c:v copy -c:a copy output.avi    
    
-c copy — сохранить видеокодек и аудиокодек,
-c:v copy — сохранить только видеокодеки,
-c:a copy — сохранить только аудиокодеки.

### Уменьшить размер кадра в 2 раза
    ffmpeg -i input.mp4 -vf scale=iw*0.5:ih*0.5 output.mp4
### Уменьшить формат до заданного разрешения
    ffmpeg -i input.mp4 -vf scale=360:288 output.mp4
    ffmpeg -i input.mp4 -s 1280x720 result.mp4
    ffmpeg -i input.png -s 320 result.png
    
можно уменьшать и картинки
### Извлечь аудио из видео
    ffmpeg -i in.mp4 -c:a copy out.aac
    ffmpeg -i input.mpg -map 0:1 bbb_audio.mp3
    
В mp4 для аудио используется кодек aac.
### Изменить битрейт видео до 16Мб/с и битрейт аудио до 192кб/с
    ffmpeg -i input.mkv -b:v 16M -b:a 192k result.mp4
### Изменить частоту кадров до 25
    ffmpeg -i input.mp4 -r 25 result.mp4
### Ускорить/замедлить видео в 4 раза
    ffmpeg -i input.mp4 -an -vf setpts=0.25*PTS result.mp4
    ffmpeg -i input.mp4 -an -vf setpts=4*PTS result.mp4
### Ускорить/замедлить аудио в 4 раза
    ffmpeg -i input.wav -af atempo=5 result.mp3 
    ffmpeg -i input.wav -af atempo=0.5 result.mp3

## Цветокоррекция
### Изменить Яркость (от -1.0 до 1.0)
    ffmpeg -i input.mp4 -vfeq=brightness=-0.5 result.mp4
### Изменить Яркость с гаммой (0.1 до 10.0)
    ffmpeg -i input.mp4 -vfeq=gamma=0.5  result.mp4
### Изменить контраст (-1000.0 до 1000.0)
    ffmpeg -i input.mp4 -vfeq=contrast=-0.5  result.mp4
### Изменить насыщенность (0 до 3.0)
    ffmpeg -i input.mp4 -vfeq=saturation=0.5  result.mp4
### Изменить цветовую температуру без с сохранением яркости 
    ffmpeg -i input.mp4 -vf colortemperature=2000:pl=0.2 result.mp4
    
### Добавить эффект виньетирования
    ffmpeg -i input.mp4 -filter_complex vignette=PI/4 output.mp4
### добавить цветовой-эффект
    ffmpeg -i input.mp4 -filter_complex [0:v]hue=h=80:s=1 output.mp4
    ffmpeg -i input.mp4 -color_primaries:v bt709 -color_trc:v bt709 -colorspace:v bt709 output.mp4

Несколько фильтров вставляются конструкциями команд (https://annimon.com/article/4000)    

### Стабилизация
    ffmpeg -i input.mp4 -vf deshake result.mp4
    
сравнить видео без и с фильтром можно командой

    ffplay -i input.mp4 -vf split[orig][proc];[proc]deshake[proc];[orig][proc]hstack
    
### Стабилизация (глубокая)
    ffmpeg -i input.mp4 -vf vidstabdetect -f null -
    ffmpeg -i input.mp4 -vf vidstabtransform result.mp4

хороший рецепт

    ffmpeg -i input.mp4 -vf vidstabdetect=shakiness=3:accuracy=15 -f null -
    ffmpeg -i input.mp4 -vf vidstabtransform=smoothing=3:zoom=-3 step1.mp4
    ffmpeg -i step1.mp4 -vf vidstabdetect=shakiness=4:accuracy=15 -f null -
    ffmpeg -i step1.mp4 -vf vidstabtransform=smoothing=12:zoom=0 result.mp4

### Объединить файл (способ 1 видео с разными кодеками)
    ffmpeg -i "concat:input.mp4|input2.mp4" -codec copy output.mp4

### Объединить файл (способ 2)
Создаем файл mylist.txt:

    file '/path/to/file1.wav'  
    file '/path/to/file2.wav'
    file '/path/to/file3.wav'
Лист можно быстро сделать командой

    (for %i in (*.mp4) do @echo file '%i') > list.txt 
Выполняем команду (с и без копирования потоков):

    ffmpeg -f concat -safe 0 -i mylist.txt -c copy output.wav
    ffmpeg -f concat -safe 0 -i mylist.txt -c output.wav
### Объединить файл (способ 3 через транспортные потоки)
    ffmpeg -i input1.mp4 -c copy intermediate1.ts
    ffmpeg -i input2.mp4 -c copy intermediate2.ts
    ffmpeg -i "concat:in1.ts|in2.ts" -c copy output.mp4

### Объединить файл (способ 4)
    mkfifo temp1 temp2
    ffmpeg -y -i input1.mp4 -c copy -bsf:v h264_mp4toannexb -f mpegts temp1 2> /dev/null & \
    ffmpeg -y -i input2.mp4 -c copy -bsf:v h264_mp4toannexb -f mpegts temp2 2> /dev/null & \
    ffmpeg -f mpegts -i "concat:temp1|temp2" -c copy -bsf:a aac_adtstoasc output.mp4
### Объединить файл (способ 5)
    mkvmerge -o file.mkv file1 + file2 + fileN
### Объединить файл (способ 6 не для всех форматов)
    copy /b video1.ts + video2.ts result.ts

### Добавить эффект проявления на первые/последние 50 кадров
    ffmpeg -i input.mp4 -vf fade=in:0:50 result.mp4
    ffmpeg -i input.mp4 -vf fade=out:750:50 result.mp4

### Добавить эффект проявления/затухания звука на первые/последние 5 секунд без перекодирования видео
    ffmpeg -i input.mp4 -af afade=in:0:d=5 -c:v copy result.mp4
    ffmpeg -i input.mp4 -af afade=out:5:d=3 -c:v copy result.mp4
### Убрать звуковую дорожку
    ffmpeg -i input.mkv -an result.mp4
### Добавить звуковую дорожку
    ffmpeg -i video.mkv -i audio.mp3 -map 0 -map 1:a -c:v copy -shortest output.mkv
    ffmpeg -i video.mkv -i audio.m4a -filter_complex "[0:a][1:a]amerge=inputs=2[a]" -map 0:v -map "[a]" -c:v copy -ac 2 -shortest output.mkv
### Заменить звуковую дорожку
    ffmpeg -i video.mp4 -i audio.wav -map 0:v -map 1:a -c:v copy -shortest output.mp4
    
### Конвертировать flac в mp3 с битрейтом 128кб/с
    ffmpeg -i input.flac -ab 320k result.mp3
    for %A IN (*.flac) DO ffmpeg -i "%~nA.flac" -ab 320k "%~nA.mp3"
    
### Объединить mp3 файлы (из перечня list.txt) в один файл
    ffmpeg -f concat -i list.txt out.mp3    
    
### Скачать видео
    ffmpeg -i "https://sample-videos.com/video123/mp4/480/big_buck_bunny_480p_10mb.mp4" -c copy out.mp4
  
### Встроить субтитры
    ffmpeg -i input.mp4 -vf subtitles=1.srt result.mp4

структура формата .srt

    1
    00:05:00,400 --> 00:05:15,300
    This is an example of
    a subtitle.
    
    2
    00:05:16,400 --> 00:05:25,300
    This is an example of
    a subtitle - 2nd subtitle.

### Получить информацию о видео
    ffprobe video.mp4 -v error -show_format
