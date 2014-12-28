## Начало
### Ruby on Rails
```
$ rails new manager
$ cd manager
$ bin/rails server # проверка
```
### Bower
```
$ bower init
$ touch .bowerrc
```
Изменим директорию для компонентов:
```
# .bowerrc
{
	"directory": "public/bower_components"
}
```
Пропишем зависимости проекта:
```
# bower.json
...
  "dependencies": {
    "jquery": "latest",
    "ember": "latest",
    "bootstrap-sass-official": "latest"
  }
...
```

```
$ bower i
```

### Grunt
> TODO

### Git

```
$ git init
$ git add .
$ git commit -m "Initial commit"
$ git remote add origin https://github.com/arzzzen/manger.git
$ git push -u origin master
```