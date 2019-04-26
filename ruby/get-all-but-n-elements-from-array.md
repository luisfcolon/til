# Getting elements from an array sans mutation

When working with arrays most of the methods I use also mutate the array.

Getting all but the first element?

```ruby
numbers = [1, 2, 3, 4, 5]

numbers.shift
=> 1

numbers
=> [2, 3, 4, 5]
```

Ruby has an array method [drop](https://ruby-doc.org/core-2.6/Array.html#method-i-drop) that can do the same without mutating the original array

```ruby
numbers = [1, 2, 3, 4, 5]

numbers.drop(1)
=> [2, 3, 4, 5]

numbers
=> [1, 2, 3, 4, 5]

numbers.drop(3)
=> [4, 5]

numbers
=> [1, 2, 3, 4, 5]
```

I prefer to code without mutating variables whenever possible.
