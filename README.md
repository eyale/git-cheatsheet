# git-cheatsheet

добавляем локальные файлы в чистый(новый) репозиторий
```
git remote add origin git@bitbucket.org:logicitsolutions/ald-carmarket.git
git add .   
git commit -m 'first commit' 
git push -u origin --all # pushes up the repo and its refs for the first time
```

добавляем локальный проект под именем origin
во внешний репозиторий по ссылке
```
git remote add origin url
```

создаем локальный репозиторий
```
git init
```

проверка статуса с прошлого изменения
```
git status
```

добавление файла в песочницу (stage)
```
git add some.html
```

добавляет измененные файлы
```
git add —-all
```

добавляем и новые и измененные файлы
```
git add .
```

показывает изменения которые происходили с веткой
```
git log
```

показываем  изменения со времени последнего фиксирования commit, или с последнего добавления в песочницу(git add —all)
```
git diff
```

удаляем измененный файл из песочницы (stage)
```
git reset HEAD some.html
```

откатывает файл до последнего commit 
```
git checkout —- some.html
```

добавляем в песочницу (stage) и делаем фиксацию commit, но не добавляем untracked(не добавленные в песочницу) файлы
```
git commit -a -m “description”
```

сбрасываем изменения файла
```
git reset some.html
```

сбрасываем изменения к состоянию песочницы
```
git reset —soft HEAD^
```

перезаписываем последний commit 
```
git commit —amend -m “description”
```

отменяем последний коммит и изменения
```
git reset —-hard HEAD^ 
```

отменяем два последних коммита и изменения
```
git reset —hard HEAD^^
```

показывает внешние репозитории
```
git remote -v
```

пуш в нелокальный мастер
```
git push -u origin master
```

переходим с ветки someBranch и сливаем ее с мастером
```
git checkout master
git merge someBranch
```

локально удаляем ветку someBranch
```
git branch -d someBranch
```

показывает внешние ветки
```
git branch -r
```

удаляем внешнюю ветку someBranch
```
git push origin -delete someBranch
```

показывает изменения в ветках состояние слежения
```
git remote show origin
```

удаляем ветки которых нет во внешнем репозитории
```
git remote prune origin
```

```
//переходим на ветку someBranch
git checkout someBranch
//забираем изменения с мастера
//изменения станут под наши изменения
git rebase master
//переходим на ветку master
git checkout master
//и сливаем ветки
git merge admin
```

забираем все данные со внешнего репозитория
но не сливаем с локальным
```
git fetch origin
```

//ставит локальные commit сверху забранных
```
git rebase —-continue 
```

конфликт
```
<==HEAD
наш код
==
не наш код
==>
```

настройка цветных логов
```
git config —-global color.ui true
```

показывает коммиты в одну линию
```
git log —-pretty=oneline
```

показывает ветвления визуально
```
git log —-oneline —-graph
```

показывает изменения ветки
```
git log -p
```

показывает разницу между двумя последними кометами
```
git deff HEAD~2
```

показывает разницу между master и someBranch
```
git diff master someBranch
```

показывает изменения index.html по дате
```
git blame index.html
```

удаления файла из репозитория, после нужен commit
```
git rm some.html
```

удаляет файл локально и перестает следить за изменениями
```
git rm —cached some.html
```

настройка сокращений
```
git config —-global alias.ci commit
```

отменяет изменения до последнего коммита
```
git reset --hard HEAD
```

отменяет изменения файла до коммита
```
git checkout HEAD file.txt
```

исправить сообщение предидущего коммита
```
git commit --amend -m "initial commit to add README.md file"
```

Use the command `git stash` to stash your changes, and `git stash apply` to re-apply your changes after your pull.

You can also type git add -A . where the dot stands for the current directory, so everything in and beneath it is added. The -A ensures even file deletions are included.

If you happen to delete a file without using `git rm` you'll find that you still have to `git rm` the deleted files from the working tree. You can save this step by using the `-a` option on `git commit`, which auto removes deleted files with the commit.
```
git commit -am "Delete stuff”
```
 
What if you have been working on a feature branch and you decide you really don't want this feature anymore? 
You might decide to delete the branch since you're scrapping the idea. 
You'll notice that `git branch -d bad_feature` doesn't work. This is because `-d` won't let you delete something that hasn't been merged.
You can either `add` the `--force` (-f)option or use `-D` which combines `-d -f` together into one command.

пушим коммит из ветки `develop` в ветку `dailyFix`
```
git push origin develop:dailyFix
```
