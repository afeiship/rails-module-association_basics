# book_author

## generator model:
```shell
# rails g model book author_id:integer published_at:datetime (代替语法是下面这种，会建立好索引和一些对应关系 belongs_to)
rails g model book author:references published_at:datetime
rails g model author name:string
rake db:migrate
```

## 上面的 author:references:
```rb
class CreateBooks < ActiveRecord::Migration[5.2]
  def change
    create_table :books do |t|
      t.references :author, foreign_key: true # 重点是这一句
      t.datetime :published_at

      t.timestamps
    end
  end
end

```

## 在官网上的版本：
```rb
class CreateBooks < ActiveRecord::Migration[5.0]
  def change
    create_table :authors do |t|
      t.string :name
      t.timestamps
    end
 
    create_table :books do |t|
      t.belongs_to :author, index: true #重点是这一句
      t.datetime :published_at
      t.timestamps
    end
  end
end
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


