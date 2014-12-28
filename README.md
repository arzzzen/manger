# Создание приложения "НИЦ менеджер"

Приложение необходимо для ускорения работы по сайту НИЦ и постепенному переводу его информациии в базу данных.

### Инструменты
- Ruby on Rails
- EmberJS
- jQuery
- Bootstrap SASS

Для сборки будет использоваться **Grunt**. Управление front-end зависимостями - **Bower**.

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