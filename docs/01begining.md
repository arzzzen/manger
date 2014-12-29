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
	"directory": "vendor/assets/bower_components"
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

```
# config/application.rb
...
  config.assets.paths << Rails.root.join("vendor","assets","bower_components")
...
```

```
# app/assets/stylesheets/application.css.scss
...
  @import "bootstrap-sass-official/assets/stylesheets/_bootstrap";
...
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