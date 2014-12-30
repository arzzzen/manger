## Статические страницы

```
$ rails generate controller StaticPages home help --no-test-framework # используемую для подавления генерации дефолтных RSpec тестов
$ rails generate integration_test static_pages
```

Добавление Capybara
```
# spec/spec_helper.rb
...
  config.include Capybara::DSL
end
```