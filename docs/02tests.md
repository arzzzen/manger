## Тестирование

```
# Gemfile
...
group :development, :test do
  gem 'sqlite3', '1.3.8'
  gem 'rspec-rails', '2.13.1'
end

group :test do
  gem 'selenium-webdriver', '2.35.1'
  gem 'capybara', '2.1.0'
end
...
```

```
$ bundle install --without production
$ bundle update
$ rails generate rspec:install # сконфигурировать Rails для использования RSpec вместо Test::Unit
```

Добавление Capybara
```
# spec/spec_helper.rb
...
  config.include Capybara::DSL
end
```

> TODO
> [Автоматизировать тесты с Guard и Spork](http://railstutorial.ru/chapters/4_0/static-pages#sec-guard)