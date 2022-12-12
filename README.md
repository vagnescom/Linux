1. Посмотреть где я 
  + `pwd`

2. Создать папку 
  + `mkdir folder`
  + `rm folder` — удалить пустую папку folder
  + `rm -r folder` — удалить папку folder с файлами внутри неё 

3. Зайти в папку 
  + `cd c:/` — gерейти в конкретный диск
  + `cd !$` — перейти в только что созданную папку
  + `cd folder`
  + `cd ~/Documents/folder_1/group_26/folder` — полный путь 
  + если в названии каталога есть пробелы, их нужно экранировать используя "`\`" (`cd /folder/новая\ папка/`) или обернуть путь в кавычки `cd "/folder/новая папка/"`

4. Создать 3 папки 
  + `mkdir folder1 folder2 folder3`
  + `mkdir folder{1..3}`
  + для создания вложенных папок — `mkdir -p folder{1..5}/folder_{1..3}`
  + или — `mkdir -p folder/folder1/folder2`

5. Зайти в папку 
  + `cd folder1`

6. Создать 5 файлов (3 txt, 2 json) 
  + `touch {name1.txt,name2.txt,name3.txt,name1.json,name2.json}`
  + `touch name1.txt name2.txt name3.txt name1.json name2.json`
  + `touch name{1..3}.txt name{1..2}.json`
  + `file name2.json` — узнать информацию о типе файла

7. Создать 3 папки 
  + `mkdir folder_1 folder_2 folder_3`
  + или — `mkdir folder_{1..3}`

8. Вывести содержимое директории
  + `ls`
  + `ls -1` — выведет список файлов построчно
  + `ls -F` с отображением типа файла
    + `*` — исполняемый файл
    + `/` — каталог
    + `=` — сокет 
    + `@` — ссылка
    + `|` — канал FIFO (First-In, First-Out — первым пришел, первым обслужен)
    + `без знака` - обычные файлы (текстовые, медиа и т.д.)
  + `ls -aF` — выведет все файлы и их тип
  + `ls -r` — с сортировкой в обратном порядке
  + `ls -R` — вместе с содержимым поддиректорий
  + `ls -A` — влючая скрытые файлы (файлы с точкой перед названием)
  + `ls -lAh` — с отображением размера файлов
  + `ls -lSh` — с сортировкой по размеру файлов и его отображением
  + `ls -ld */` — отобразит только вложенные директории внутри текущей
  + `ls -lt` — с сортировкой по дате создания файлов
  + `ls -lu` — с сортировкой по дате обращения к файлам
  + `ls -la` — расширенный вывод всех файлов (разрешения, владелец, размер, дата изменения)

9. Открыть любой txt файл 
  + `vim name1.txt`

10. добавить любой текст 
  + `i` — перейти в режим редактирования

Lorem ipsum dolor sit amet, consectetur adipiscing elit. 
Suspendisse tempus ipsum et nibh pulvinar tempor. 
Vivamus placerat nec quam sed pellentesque. 
In sollicitudin fermentum sem interdum sodales. 
Etiam faucibus lacus.

11. сохранить и выйти из vim
  + `esc` — выйти из режима редактирования
  + `:wq` — записать изменения и выйти из vim

12. Выйти из папки на уровень выше 
  + `cd ..`
  + `cd -` 
  + `cd ../..` — на 2 уровня вверх

13. переместить любые 2 файла, которые вы создали, в любую другую папку
  + `mv folder1/{name2.txt,name1.json} folder1/folder_1`
  + `mv folder1/*.* folder2` — переместить все файлы из папки app1 в папку app2

14. скопировать любые 2 файла, которые вы создали, в любую другую папку
  + `cp folder1/{name3.txt,name2.json} folder1/folder_2`

15. Найти файл по имени
  + `find . -name "name1*"`

16. просмотреть содержимое в реальном времени после указанного значения
  + `tail -f name1.txt | grep faucibus`
  + отредактировать name1.txt в блокноте и сохранить 
  + посмотреть изменения в терминале
  + `tail -f name1.txt | grep --line-buffered faucibus >> test_log.txt` — с записью в файл
  + `tail -f name1.txt | grep --line-buffered сюда_паттерн >> test_log.txt | tail -f test_log.txt` — с записью в файл и отображением в терминале

17. вывести несколько первых строк из текстового файла
  + `head -2 name1.txt`

18. вывести несколько последних строк из текстового файла
  + `tail -2 name1.txt`

19. просмотреть содержимое длинного файла
  + `less name1.txt`
  + `q` для выхода из режима просмотра

20. вывести дату и время
  + `date`

Задание *
1. Отправить http запрос на сервер.
`http://162.55.220.72:5005/terminal-hw-request`

  + `curl "http://162.55.220.72:5005/terminal-hw-request"`

Ответ
{"Intro":"Hello!! This is your the first response from server","Tasks":{"Task_1":"Send the next URL in terminal: `http://162.55.220.72:5005/get_method?name=(set_your_String)&age=(set_your_number)","result":["Your_String","Your_number"]`}}

выполняем Task1:)
  + `curl "http://162.55.220.72:5005/get_method?name=(set_your_String)&age=(set_your_number)"`

вместо `(set_your_String)` пишем имя 
вместо `(set_your_number)` пишем возраст 

Ответ
`["имя","возраст"]`

2. Написать скрипт который выполнит автоматически пункты 3, 4, 5, 6, 7, 8, 13
```css
cat > script.sh << EOF
#!/bin/bash
pwd 
mkdir folder_script
cd folder_script
mkdir folder1 folder2 folder3
cd folder3
touch {text4.txt,text5.txt,text6.txt,json3.json,json4.json}
mkdir script_folder1 script_folder2 script_folder3
ls -la
mv text4.txt json3.json script_folder2
mv folder3/{text4.txt,json3.json} folder3/script_folder2
curl "http://162.55.220.72:5005/terminal-hw-request"
curl "http://162.55.220.72:5005/get_method?name=(leshenkov)&age=(30)"
date 
EOF
```
  + `Enter`

`chmod +x script.sh`

`./script.sh`
