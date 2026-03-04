# Домашнее задание к занятию 15.4 "`Инструменты Git`" - `Чеботников М.Б.`


## Задание

В клонированном репозитории:

1. Найдите полный хеш и комментарий коммита, хеш которого начинается на `aefea`.

### Ответ:
`Код:`
```
git show aefea
# или
git rev-parse aefea
```

<img width="951" height="291" alt="1" src="https://github.com/user-attachments/assets/ab58d281-5387-41f1-a1cd-f30839d2f6ce" />


2. Ответьте на вопросы.

* Какому тегу соответствует коммит `85024d3`?
`Код:`
```
git tag --points-at 85024d3
git describe --tags 85024d3
```

<img width="413" height="53" alt="2" src="https://github.com/user-attachments/assets/56370ae7-59db-49af-8f08-d66175f568d7" />


* Сколько родителей у коммита `b8d720`? Напишите их хеши.

`Код:`
```
git log --pretty=%P -n 1 b8d720

git show b8d720^ --format="%H" -s
git show b8d720^2 --format="%H" -s

git cat-file -p b8d720
```

<img width="471" height="279" alt="3" src="https://github.com/user-attachments/assets/589be4db-427c-4133-8d30-1dcdee99cc23" />


* Перечислите хеши и комментарии всех коммитов, которые были сделаны между тегами  v0.12.23 и v0.12.24.

`Код:`
```
git log v0.12.24 --not v0.12.23 --oneline
git log v0.12.23..v0.12.24 --oneline
```

<img width="511" height="287" alt="4" src="https://github.com/user-attachments/assets/b0bc3a3b-f549-42b6-9387-6d2559d4222b" />


* Найдите коммит, в котором была создана функция `func providerSource`, её определение в коде выглядит так: `func providerSource(...)` (вместо троеточия перечислены аргументы).

`Код:`
```
git log -S "func providerSource(" --oneline
```

<img width="498" height="26" alt="5" src="https://github.com/user-attachments/assets/a9dc11b8-97fe-43c9-a5b1-71c7fe17cad3" />


* Найдите все коммиты, в которых была изменена функция `globalPluginDirs`.

`Код:`
```
git log -S "globalPluginDirs" --oneline
```

<img width="491" height="118" alt="6" src="https://github.com/user-attachments/assets/3093c86f-7f00-48f7-851c-fc9dcadf0078" />


* Кто автор функции `synchronizedWriters`?

`Код:`
```
git log -S "synchronizedWriters" --oneline
git show 5ac311e2a9 --format="%an" -s
```

<img width="487" height="79" alt="7" src="https://github.com/user-attachments/assets/0ee1c175-4ea9-4429-968f-cc80dda6907d" />


*В качестве решения ответьте на вопросы и опишите, как были получены эти ответы.*

`Как шпоргалка для себя с информацией из лекции:`
```
git show <hash> — показывает информацию о конкретном коммите
git tag --points-at <hash> — показывает теги, указывающие на коммит
git log --pretty=%P — показывает хеши родителей коммита
git log <tag1>..<tag2> — показывает коммиты в диапазоне между тегами
git log -S "<строка>" — ищет коммиты, где изменялось количество вхождений строки (поиск создания/изменения функции)
git log -L :<функция>:<файл> — показывает историю изменений конкретной функции в файле
git grep — поиск строк в коде репозитория
```

---
