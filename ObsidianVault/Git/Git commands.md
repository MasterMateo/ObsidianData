#git

- `git status` - показывает состояние текущей директории и состояние staging area
- `git diff <file name>` - сравнить последнюю закоммиченную версию файла с текущей версией (изменения которой еще не добавлены в гит - unstaged file)
-  `git diff -r HEAD <file name>` - сравнить последнюю закоммиченную версию файла с версией добалвенной в гит с помощью git add (staged file) 
- `git diff -r HEAD` - сравнить ВСЕ staged файлы с закоммиченными
	- `HEAD~1` - сравнить изменения с предпоследним коммитом
	- `HEAD~2` - сравнить изменения с коммитом до предпоследнего
- `git diff <hash1> <hash2>` (`git diff HEAD~3 HEAD~2`) - сравнить два коммита между собой
- `git log` - покажет все сделанные коммиты в хронологическом порядке. Покажет хеш коммита, автора, дату и сообщение(space - для перемещения дальше по списку коммитов, q - выход из логов)
	- `git log -3` - покажет последние 3 коммита в ветке
	- `git log -3 <file name>` - последние 3 коммита в ветке для конкретного файла
	- `git log --since='Month Day Year` - покажет последние коммиты с указанной даты (--since='Apr 2 2022')
	- `git log --since='Apr 2 2022 --until='Apr 11 2022` - коммиты с 2 апреля по 11
- `git show <first commit hash code symbols>` - выведет информацию о выбранном коммите
	- `git show HEAD~3` - информация о четвертом коммите с конца
- `git annotate <file Name>` - изменение в файле по строкам, кто конкретно и в каком коммите менял строку
- `git reset HEAD` - вытащить из add все файлы
	- `git reset HEAD <file name>` -  вытащить файл если добавил его с помощью add (un-stage)
- `git checkout .` - отменит ВСЕ не добавленные изменения (unstaged files) в директории и под директориях 
	- `git checkout -- <file name>` - возвращает выбранный файл к его состоянию в последнем коммите(все внесенные изменения будут потеряны навсегда)
	- `git checkout <git hash> <file name>` - вернет указанный файл к указанному хешем коммиту
	- `git checkout HEAD~1 <file name>` - вернет файл к последнему коммиту
	- `git checkout <git hash>` - вернет репозиторий к указанному коммиту
	- `git checkout HEAD~1` - вернет репозиторий к предыдущему коммиту
- `git clean -n` - выведет все файлы изменения в которых не отслеживаются(создали новые или скопировали с другого проекта)
- `git clean -f` - удалит все файлы изменения в которых не отслеживаются(будут утеряны навсегда)
