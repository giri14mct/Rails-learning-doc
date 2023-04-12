

## How to reverse a string (I’m hilarious, ain’t I?) avoiding .reverse method?

`Using Map`

```
str = "abcdef"
reversed_array = []
str.chars.map {|x| reversed_array.unshift(x)}.flatten.uniq.join
```
`Using Reduce`

```
str = "abcdef"
str.chars.reduce{|s,c| c + s }
```

## What will happen when we define same class variable in both parent and child class

```
So child class also in same scope as his superclass just rewrites the value.
```

## Can a private method be called outside the class
`In ruby it's Yes, via send method`

```
Example: 

class_instance_name.send(:private_method_name)
```

## Consider the following code: array.map(&:capitalize) Constructions like this can often be seen in Ruby projects. Can you explain how it works?

```
array.map { |x| x.method_name } When a param is passed with & in front of it Ruby will take it as a block, that calls the method with the same name on each element of the array.
So, &:capitalize is equivalent to {|item| item.capitalize }
```

## what is the difference between super and super() in Ruby

```
So, the main difference between super and super() is in the arguments that are passed to the superclass method. If you want to pass the same arguments that were passed to the current method, you can use super without parentheses. If you want to pass no arguments to the superclass method, you can use super() with empty parentheses.
```

## Ruby is a dynamically typed language, please, specify the pros and cons.

```
Pros — allows less typing which leads to a more elegant code style and flexibility.

Cons — this aspect forces Ruby to interpret lines on the fly, which takes more time to process, and, as an interpreted language, makes the process even slower
```

## Ruby has few ways to call a method


```
obj = Obj.new
puts obj.object_id
puts obj.send(:object_id)
puts obj.method(:object_id).call
puts obj::object_id
```

## What is an object freezing in Ruby and why would you do that?

```
Freezing an object just means preventing it from changing .freeze will do the trick
```

## Can you explain Ruby method lookup?

```
The Ruby interpreter will start looking in the object class and if the called method is not found, it will continue to look up to the ancestor’s chain.
```


# How to use .nil? .empty? .blank? .present? in Rails


| | nil? | empty? | blank? | present?
|--- | --- | --- | --- | --- |
nil | true | NoMethodError | true | false
false | false | NoMethodError | true | false 
true | false | NoMethodError| false| true
"" | false | true | true | false
" "| false | false | true | false
[] | false | true | true | true
{} | false | true | true | false
"String" | false | false | false| true
25 | false | NoMethodError | false | true

# .nil?
 ` nil is also its own class. Checking for .nil? will only return true if the object itself is nil`

 ```
 nil.class
=> NilClass

nil.nil? 
=> true 

"".nil? 
=> false

false.nil? 
=> false

[].nil? 
=> false

 ```

 # .empty?

 `.empty means that the length object you are trying to evaluate == 0. It’s primarily used for hashes, strings, and array`

 ```
 nil.empty? 
=> NoMethodError: undefined method `empty?' for nil:NilClass

false.empty? 
=> NoMethodError: undefined method `empty?' for false:FalseClass

"".empty? 
=> true

" ".empty? 
=> false

[].empty? 
=> true

[ ].empty? 
=> true
 ```

 # .blank?

 `This is an ActiveRecord method that exists for any Rails object and will return true for nil, false, empty, or a whitespace string.`

 ```
 nil.blank?
 =>  true 

 false.blank?
 => true

 "".blank?
 => true

 "  ".blank?
 => true

 [].blank?
 => true

 {}.blank?
 => true
 ```

 # .present?
  Also a Rails method (meaning it won’t work in your irb console), .present? is just the opposite of .blank?

# .exists?

.exists? has been deprecated since Rails 3, so don’t use .exists.
