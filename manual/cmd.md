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
