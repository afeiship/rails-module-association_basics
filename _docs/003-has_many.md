# has_many
~~~
has_many 关联建立两个模型之间的一对多关系。
在 belongs_to 关联的另一端经常会使用这个关联。
has_many 关联表示模型的实例有零个或多个另一模型的实例。
例如，对应用中的作者和图书模型来说，作者模型可以这样声明：
~~~

```rb
class Author < ApplicationRecord
  has_many :books
end
```


## rails console:
```rb
# create two authors:
a1 = Author.create(:name=>'FEI');
a2 = Author.create(:name=>'Jay');

# books:
b1 = Book.new
b2 = Book.new
b1.author = a1;
b2.author = a1;
b1.published_at = '2018';
b2.published_at = '2019';

b1.save
b2.save


```

## 这里希望直接删除b1:
```rb
a1 = Author.first
a1.destroy
```
~~~
ActiveRecord::InvalidForeignKey: SQLite3::ConstraintException: FOREIGN KEY constraint failed

解决方案：【hasMany/hasOne的地方加这个： dependent: :destroy】
class Author < ApplicationRecord
    has_many :books, dependent: :destroy
end
~~~

## 加了这个：dependent: :destroy 实际上是执行了以下几步：
```rb
a1.books.each do|item|
    item.destroy
end
a1.destroy;
```