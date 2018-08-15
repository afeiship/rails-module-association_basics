# book_author

## generator model:
```shell
rails g model book author_id:integer published_at:datetime
rails g model author name:string
rake db:migrate
```

## withtout associate:
```rb
class Book < ApplicationRecord
end
```
![](https://ws2.sinaimg.cn/large/0069RVTdgy1fua2choruaj30uw0detc2.jpg)


## with associate:
```rb
class Book < ApplicationRecord
    belongs_to :author
end
```

![](https://ws3.sinaimg.cn/large/0069RVTdgy1fua2ai8ezmj30tq08y76h.jpg)


