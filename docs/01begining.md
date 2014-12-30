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

### Heroku

```
# Gemfile
ruby '2.0.0'
...
group :development do
  gem 'sqlite3', '1.3.8'
end
...
group :production do
  gem 'pg', '0.15.1'
  gem 'rails_12factor', '0.0.2'
end
...
```

```
$ bundle install --without production
```

```
# Это должно быть использовано только если вы не можете задеплоить на Heroku.
$ rake assets:precompile
$ git add .
$ git commit -m "Add precompiled assets for Heroku"
```

```
$ heroku login
$ heroku create
$ git push heroku master
$ heroku open
```