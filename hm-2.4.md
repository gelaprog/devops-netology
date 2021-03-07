# Домашнее задание к занятию «2.4. Инструменты Git»

1. Найдите полный хеш и комментарий коммита, хеш которого начинается на aefea.
   * хеш: `aefead2207ef7e2aa5dc81a34aedf0cad4c32545`
   * комментарий: `Update CHANGELOG.md`
   * варианты команд: 
      * `git show aefea`
      * `git log -1 aefea`
   
2. Какому тегу соответствует коммит 85024d3?
   * тег: `tag: v0.12.23`
   * команда:
      * `git show 85024d3`
      * `git log -1 85024d3 --oneline`
   
3. Сколько родителей у коммита b8d720? Напишите их хеши.
   * родителей: 2
   * хешы: `56cd7859e05c36c06b56d013b55a252d0bb7e158` `9ea88f22fc6269854151c571162c5bcf958bee2b`
   * команда:
      * `git show b8d720`
      * `git log -1 b8d720`
      * `git log --pretty='%P' b8d720  -1`
   
4. Перечислите хеши и комментарии всех коммитов которые были сделаны между тегами v0.12.23 и v0.12.24. 
   * Хешы и комментарий:
      * `33ff1c03b (tag: v0.12.24) v0.12.24`
      * `b14b74c49 [Website] vmc provider links`
      * `3f235065b Update CHANGELOG.md`
      * `6ae64e247 registry: Fix panic when server is unreachable`
      * `5c619ca1b website: Remove links to the getting started guide's old location`
      * `06275647e Update CHANGELOG.md`
      * `d5f9411f5 command: Fix bug when using terraform login on Windows`
      * `4b6d06cc5 Update CHANGELOG.md`
      * `dd01a3507 Update CHANGELOG.md`
      * `225466bc3 Cleanup after v0.12.23 release`
   * команда: `git log --oneline v0.12.23..v0.12.24`
   
5. Найдите коммит в котором была создана функция func providerSource, ее определение в коде выглядит так func providerSource(...) (вместо троеточего перечислены аргументы).
   * Хеш: `5e06e39fcc86bb622b962c87da84213d3331ddf8`
   * команда: `git log -SproviderSource --oneline`
6. Найдите все коммиты в которых была изменена функция globalPluginDirs.
   * Хешы:
      * `78b122055`
      * `52dbf9483`
      * `41ab0aef7`
      * `66ebff90c`
      * `8364383c3`
   * команды:
      * нашел файл: `git grep -n --break --heading  'func globalPluginDirs('`
      * нашел изменения: 
        * `git log -L :globalPluginDirs:plugins.go --oneline`
        * `git log -L :globalPluginDirs:plugins.go --pretty=format:"%H"`
7. Кто автор функции synchronizedWriters? 
   * В текущем состоянии репозитория функция и файл содержащий функцию удалены, по этой причине grep не находит такую функцию `git grep -n --heading --break synchronizedWriters`, но если искать с помощью `git log -S synchronizedWriters --oneline`, то можно найти три коммита в котором присутствует вхождения с названием этой функции. После того как проанализировал коммиты с помощью `git diff <hash>` стало понятно, в каком файле, когда и кто писал эту функцию, что автор функции: `Author: Martin Atkins <mart@degeneration.co.uk>`. Также можно это увидеть уже с помощью `git blame 5ac311e2a -L 13,25 synchronized_writers.go`
   
   
   
