## Задание

В клонированном репозитории:

1. Найдите полный хеш и комментарий коммита, хеш которого начинается на `aefea`.

`git log -1 --format="%H %s" aefea`
```
Вывод: aefead2207ef7e2aa5dc81a34aedf0cad4c32545 Update CHANGELOG.md
```

2. Ответьте на вопросы.

* Какому тегу соответствует коммит `85024d3`?

`git tag --points-at 85024d3`
```
Вывод: v0.12.23
```

* Сколько родителей у коммита `b8d720`? Напишите их хеши.

`git show -s --format="%P" b8d720`
```
Вывод: 56cd7859e05c36c06b56d013b55a252d0bb7e158 9ea88f22fc6269854151c571162c5bcf958bee2b
```
* Перечислите хеши и комментарии всех коммитов, которые были сделаны между тегами  v0.12.23 и v0.12.24.

`git log v0.12.23..v0.12.24 --oneline`

Вывод:
```
33ff1c03bb (tag: v0.12.24) v0.12.24
b14b74c493 [Website] vmc provider links
3f235065b9 Update CHANGELOG.md
6ae64e247b registry: Fix panic when server is unreachable
5c619ca1ba website: Remove links to the getting started guide's old location
06275647e2 Update CHANGELOG.md
d5f9411f51 command: Fix bug when using terraform login on Windows
4b6d06cc5d Update CHANGELOG.md
dd01a35078 Update CHANGELOG.md
225466bc3e Cleanup after v0.12.23 release
```

* Найдите коммит, в котором была создана функция `func providerSource`, её определение в коде выглядит так: `func providerSource(...)` (вместо троеточия перечислены аргументы).

`git log -S "func providerSource(" --oneline`
```
Вывод: 8c928e8358 main: Consult local directories as potential mirrors of providers
```
* Найдите все коммиты, в которых была изменена функция `globalPluginDirs`.

```
git grep "globalPluginDirs"
git log -L :globalPluginDirs:XXX
```
Не найдена функция, видимо удалена с новых релизов

* Кто автор функции `synchronizedWriters`?

`git log -S "func synchronizedWriters" --reverse --pretty=format:"%h %an %ad %s"`

```
Martin Atkins
```