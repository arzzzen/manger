## Новости

```
$ bin/rails g controller welcome index
$ bin/rails g controller news
```

```
# config/routes.rb
...
  root 'welcome#index'
  resources :news
...
```