## Пользователи

```
$ rails generate model User name:string email:string
$ rake db:migrate
# Если нужно проводить тесты на тестовой базе
$ rake test:prepare
```

```
# Gemfile
gem 'bcrypt', '~> 3.1.7' # раскомментировать, там уже есть
```

Для использования рельсовой has_secure_password добавим поле password_digest:

```
$ rails g migration add_password_digest_to_users password_digest:string
```

Полная модель пользователя с реализацией безопасных паролей
```
# app/models/user.rb
class User < ActiveRecord::Base
  before_save { self.email = email.downcase }
  validates :name, presence: true, length: { maximum: 50 }
  VALID_EMAIL_REGEX = /\A[\w+\-.]+@[a-z\d\-.]+\.[a-z]+\z/i
  validates :email, presence:   true,
                    format:     { with: VALID_EMAIL_REGEX },
                    uniqueness: { case_sensitive: false }
  has_secure_password
  validates :password, length: { minimum: 6 }
end
```