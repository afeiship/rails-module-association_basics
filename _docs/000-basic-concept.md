# Basic concept
~~~
belongs_to and has_one or has_many are a pair [强调成对出现]
belongs_to needs to add a column to store its owner's id [强调需要有 supplier_id,或者叫：references]
has_one or has_many don’t need a column to it, and Rails use the column added from belongs_to to look up.
through is like a "short-cut" to get something which cannot directly be queried from itself, sometimes source would be used together.
as is a keyword for polymorphic associations
~~~