# 在 belongs_to 和 has_one 之间选择
~~~
如果想建立两个模型之间的一对一关系，
要在一个模型中添加 belongs_to，
在另一模型中添加 has_one。但是怎么知道在哪个模型中添加哪个呢？

二者之间的区别是在哪里放置外键（外键在 belongs_to 关联所在模型对应的表中），
不过也要考虑数据的语义。has_one 的意思是某样东西属于我，即哪个东西指向你。
例如，说供应商有一个账户，比账户拥有供应商更合理，所以正确的关联应该这么声明：
~~~

![](https://ws4.sinaimg.cn/large/0069RVTdgy1fua7jc89v0j31060zwq7m.jpg)

## 画重点：
~~~
t.integer :supplier_id 更明确地表明了外键的名称。
在目前的 Rails 版本中，可以抽象实现的细节，使用 t.references :supplier 代替。
~~~