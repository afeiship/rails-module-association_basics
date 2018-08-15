# has_one
> belongs_to 关联创建两个模型之间一对一的关系，声明所在的模型实例属于另一个模型的实例。例如，如果应用中有作者和图书两个模型，而且每本书只能指定给一位作者，就要这么声明图书模型：


> has_one 关联也建立两个模型之间的一对一关系，但语义和结果有点不一样。这种关联表示模型的实例包含或拥有另一个模型的实例。例如，应用中每个供应商只有一个账户，可以这么定义供应商模型

> blongs_to声明应该出现在包含外键定义的表model中

## create model:
```shell
rails g model supplier name:string
rails g model account supplier:references account_number:string
rake db:migrate
```

## rails console
```rb
s1 = Supplier.new
s1.name = "FEI";
s1.save

a1 = Account.new
a1.supplier = s1;
a1.account_number = '001'
a1.save

## console get account OR supplier
s1.account
a1.supplier
```