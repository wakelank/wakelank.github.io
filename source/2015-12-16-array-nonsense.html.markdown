---
title: Array Nonsense
date: 2015-12-16 12:29 UTC
tags: code, Ruby
---

I was working on a Tic-Tac-Toe game recently in Ruby. The one thing anyone can see about a Tic-Tac-Toe game in Ruby is that making an 3 x 3 array might just be a good place to start. Once could do this: 

~~~ruby
arr_boxy = [
      [ nil, nil, nil ],
      [ nil, nil, nil ],
      [ nil, nil, nil ]
      ]
~~~

Then you could access the top left space with `arr[0][0]`, and the bottom right one with `arr[2][2]`. All well and good, but it doesn't seem very Ruby. 
This:

~~~ruby
arr_one_liner = Array.new(3,Array.new(3))
~~~

should get the same thing right? Sure look like they do:

~~~ruby
:> arr_boxy.to_s
"[[nil, nil, nil], [nil, nil, nil], [nil, nil, nil]]"

:> arr_one_liner.to_s
"[[nil, nil, nil], [nil, nil, nil], [nil, nil, nil]]"
~~~

But check this out:

~~~ruby
:> arr_boxy[0][1] = "X"
:> arr_boxy.to_s
"[[nil, nil, nil], [\"X\", nil, nil], [nil, nil, nil]]"

:> arr_one_liner[0][1] = "X"
:> arr_one_liner.to_s

"[[nil, \"X\", nil], [nil, \"X\", nil], [nil, \"X\", nil]]"
~~~

This is an example of a concept that I often run across in the first few chapters of coding books, but I used to skim through until I get to the code examples. But, as we can see here, it's an important concept. First a little breakdown of how that `arr_one_liner` declaration works.

1. `arr = Array.new` gives you an empty array.

2. `arr = Array.new(2)` gives you an array of two elements, each one is `nil`.

3. `arr = Array.new(2, "thing")` gives you an array of two elements, the value of each one is "thing".

So
4. `arr = Array.new(2(Array.new(3))` give you an array of two elements, the value of each one is the same is example 2 up there.

The deal is that the example four makes only one array object of three elements in computer memory. Then it puts two pointers to this object in the outer array. The two arrays of three elements are acutally one array of three objects. Like if you write the address to someone's house two times. You have two addresses, but they point to the same house. If you paint the house indicated by the first address, the house indicated by the second address gets painted too, because they are the same house. 

Each row in `arr_boxy` is a unique object. Each row in `array_one_liner` is a pointer to the same array, change one and you change all of them. That's what happened with:

~~~ruby
:> arr_one_liner[0][1] = "X"
:> arr_one_liner.to_s

"[[nil, \"X\", nil], [nil, \"X\", nil], [nil, \"X\", nil]]"
~~~

Here's what I did:

~~~ruby
:> arr_the_way = []
:> 3.times { arr_the_way << Array.new(3) }

:> arr_the_way.to_s
"[[nil, nil, nil], [nil, nil, nil], [nil, nil, nil]]"
:> arr_the_way[1][0] = "X"

:> array_the_way.to_s
"[[nil, nil, nil], [\"X\", nil, nil], [nil, nil, nil]]"
~~~

Because it goes through the loop three times, each `Array.new(3)` is created as a unique object, not a pointer to the same object.

