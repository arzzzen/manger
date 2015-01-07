## Начало
### Ruby on Rails
```
$ rails new manager --skip-test-unit # не генерировать папку test
$ cd manager
$ bin/rails server # проверка
```

#### Динамическая генерация секретного токена. Файл config/initializers/secret_token.rb

```
# Be sure to restart your server when you modify this file.

# Your secret key is used for verifying the integrity of signed cookies.
# If you change this key, all old signed cookies will become invalid!

# Make sure the secret is at least 30 characters and all random,
# no regular words or you'll be exposed to dictionary attacks.
# You can use `rake secret` to generate a secure secret key.

# Make sure your secret_key_base is kept private
# if you're sharing your code publicly.
require 'securerandom'

def secure_token
  token_file = Rails.root.join('.secret')
  if File.exist?(token_file)
    # Use the existing token.
    File.read(token_file).chomp
  else
    # Generate a new token and store it in token_file.
    token = SecureRandom.hex(64)
    File.write(token_file, token)
    token
  end
end

XXXApp::Application.config.secret_key_base = secure_token
```

```
# .gitignore
...
.secret
```


### Bower

```
# Gemfile
...
  gem 'bower'
...
```

```
$ rails generate bower:install
```

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

Bower + Heroku:

```
$ heroku config:set BUILDPACK_URL='git://github.com/qnyp/heroku-buildpack-ruby-bower.git#run-bower'
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