# JavaScript Data Types

## Learning Goals

- Define a data type
- Demonstrate basic type checking with the `typeof` operator
- Identify JavaScript's seven basic data types
- Describe interactions between data of various types in JavaScript

## Introduction

Did you ever hear this song from educational TV?

```text
One of these things is not like the others.
One of these things doesn't belong.
Can you tell which thing is not like the other by the time
I finish this song?
```

What this song is asking the young viewer to engage in is a pretty powerful
behavior: _abstraction_. It's looking at several _concrete_ examples and finding
some sort of "ideal" that the _concrete_ examples all have in common and using
that as a rule to find something that doesn't _quite_ fit.

Doing this is one of the most profound problems in philosophy and human
development. No less an authority than Aristotle wrote a [whole book][] on it
and how humans do it (one of the essential reasons why he [differs][] from his
teacher, Plato).

Who knew JavaScript would lead us to ancient Greece as well as "Sesame Street?"

In JavaScript, _concrete_ instances of data can be categorized into _abstract_
names called "data types" or, more simply, "types."

## What Is a Data Type?

**_Everything in JavaScript is data_** except:

1. **Operators**: `+`, `!`, `<=`, etc.
2. **Reserved words**: `function`, `for`, `debugger`, etc.

Every piece of data falls into one of JavaScript's seven data types: numbers,
strings, booleans, symbols, objects, `null`, and `undefined`.

## Basic Type Checking Using the `typeof` Operator

Throughout this lesson, we'll use the `typeof` operator to give us an idea of
what data types we're dealing with. `typeof` accepts one argument, the piece of
data that we'd like to know the _type of_.

> **NOTE** `typeof` is an operator, just like `+` or `!`. We get used to
> operators being only one character, but JavaScript (and many other languages)
> have operators with **_more than one_** character. Because it's an operator,
> **we don't need parentheses with `typeof`**. That said, JavaScript also
> supports `()` after `typeof`, but it's commonly not done.

## Identify JavaScript's Seven Basic Data Types

### Numbers

Some programming languages divide numbers up into integers, decimals, doubles,
floats, and so on. They do this so that they can have higher _precision_ in
their calculations. In a banking application or airplane wing engineering
application we want our interest rate or the curve of the wing to be **_as
accurate as possible_**. For good reason: we want to make sure we get paid or
have a safe plane! When JavaScript was created, this level of precision was not
thought to be a thing that would be needed, so JavaScript only has a single,
all-encompassing number type:

```js
typeof 42;
//=> "number"

typeof 3.141592653589793;
//=> "number"

typeof 5e-324;
//=> "number"

typeof -Infinity;
//=> "number"
```

> **Think About This:** As JavaScript has become a language for the back end as
> well as the front end, its imprecision around numbers keeps it from entering
> many banking or engineering applications where precision is vital.

### Strings

Strings are how we represent text in JavaScript. A string consists of a matching
pair of `'single quotes'`, `"double quotes"`, or `` `backticks` `` with zero or
more characters in between:

```js
typeof "I am a string.";
//=> "string"

typeof 'Me too!';
//=> "string"

typeof `Me three!`;
//=> "string"
```

Even empty strings are strings:

```js
typeof "";
//=> "string"
```

### Booleans

A boolean can only be one of two possible values: `true` or `false`. Booleans
play a big role in `if` statements and looping in JavaScript.

```js
typeof true;
//=> "boolean"

typeof false;
//=> "boolean"
```

### Objects

A JavaScript object, unlike the types we've looked at so far, is a _collection_
of data rather than a single value. An object consists of a list of properties,
wrapped in curly braces `{}` and separated by commas. Each property in the list
consists of a name — also known as a `key` — which points to a value:
`"name": "JavaScript"`. The example below has four properties, with the names
(or `key`s) "name", "createdBy", "firstReleased", and "isAwesome":

```js
const js = {
  name: "JavaScript",
  createdBy: {
    firstName: "Brendan",
    lastName: "Eich",
  },
  firstReleased: 1995,
  isAwesome: true,
};

typeof {};
//=> "object"
```

A dictionary is a good metaphor here: an object is a collection of terms (the
names or keys) and their definitions (the values). In fact, the programming
language Python has a similar data type which is called a dictionary.

Note that objects' properties can point to values of any data type. In the
example above, the properties have values of four different types: a string, a
number, a boolean, and another object!

### Arrays

An array is just a list of values enclosed in square brackets:
`["Byron", "Cubby", "Boo Radley", "Luca"]`. As with objects, the values can be
of any data type. In fact, from JavaScript's perspective, arrays are just
special cases of objects. We can see that if we check the data type of our
array:

```js
const dogs = ["Byron", "Cubby", "Boo Radley", "Luca", "Spinach"];
typeof dogs;
//=> "object"
```

This may seem strange at first, but will make more sense as we learn more about
objects and arrays in future lessons.

### `null`

The `null` data type represents an intentionally absent object. For example, if
a piece of code returns an object when it successfully executes, we could have
it return `null` in the event of an error. Confusingly, the `typeof` operator
returns `"object"` when called with `null`:

```js
typeof null;
//=> "object"
```

### `undefined`

The bane of many JS developers, `undefined` is a bit of a misnomer. Instead of
'not defined,' it actually means something more like 'not yet assigned a value.'

```js
typeof undefined;
//=> "undefined"

let unassignedVariable;
typeof unassignedVariable;
//=> "undefined"

unassignedVariable = "";
typeof unassignedVariable;
//=> "string"
```

Any variable declared but not defined will be `undefined` until a value is assigned.

> **_Top Tip_**: When writing JavaScript code, it's good practice to **_never_**
> set a variable equal to `undefined`. Variables will be `undefined` until we
> explicitly assign a value, so encountering an `undefined` variable is a strong
> signal that the variable was declared but not assigned prior to the reference.
> That's valuable information that we can use while debugging, and it comes at
> no additional cost to us.

### Symbols

Symbols are a relatively new data type (introduced in ES2015) that's primarily
used as an alternative way to add properties to objects. Don't worry about
symbols for now.

### Primitive Types

Six of the seven JavaScript data types — everything except object — are
**primitive**. All this means is that they represent _single_ values, such as
`7` or `"hello"` or `false`, instead of a collection of values.

## How Different JavaScript Data Types Interact

Every programming language has its own rules governing the ways in which we can
operate on data of a given type. For example, it's rather uncontroversial that
numbers can be subtracted from other numbers...

```js
3 - 2;
//=> 1
```

...and that strings can be added to other strings:

```js
"Hello" + ", " + `world!`;
//=> "Hello, world!"
```

But what happens if you mix them?

Some programming languages, such as Python, are strict about how data of
different types can interact, and they will refuse to compile a program that
blends types. Well, that's rather strict.

Other languages, such as Ruby, will attempt to handle the interaction by
converting one of the data types so all data is of the same type. For example,
instead of throwing an error when an integer (`3`) is added to a floating-point
number (`0.14159`), Ruby will simply convert the integer into a floating-point
number and correctly calculate the sum:

```ruby
3 + 0.14159
#=> 3.14159
```

Ruby throws errors when some stranger cases come up:

```ruby
"THX-" + 1138
#=> TypeError: no implicit conversion of Fixnum into String
```

That seems pretty reasonable: Ruby won't make the `Integer`, `1138`, into a
`String` without being directly told that you want it to be a `String` (same as
Python's rule).

That seems like a good baseline. JavaScript, on the other hand, is a little
_too_ nice when handling conflicting data types. **No matter what weird
combination of types you give it, JavaScript won't throw an error and will
return _something_ (though that _something_ might make no sense at all).**

Sometimes it makes _some_ sense:

```js
"High " + 5 + "!";
//=> "High 5!"
```

...and sometimes it's downright [comical][wat]:

```js
null ** 2; // null to the power of 2
//=> 0

undefined ** null; // undefined to the power of null
//=> 1

{}+{}; // empty object plus empty object
//=> "[object Object][object Object]" <-- That's a string!
```

Why JavaScript returns a string when we ask it to add two empty objects is
anyone's guess, but its heart is in the right place. The language always tries
to bend over backwards for us, returning actionable data instead of throwing
errors. However, JavaScript's eagerness occasionally results in data type issues
that surprise novice and expert programmers alike.

Try to follow along with what's happening here:

```js
1 + 2 + 3 + 4 + 5;
//=> 15

"1" + 2 + 3 + 4 + 5;
//=> "12345"

1 + "2" + 3 + 4 + 5;
//=> "12345"

1 + 2 + "3" + 4 + 5;
//=> "3345"

1 + 2 + 3 + "4" + 5;
//=> "645"

1 + 2 + 3 + 4 + "5";
//=> "105"
```

As long as we are only adding numbers to other numbers, JavaScript performs the
expected addition. However, as soon as we throw a string in the mix, we stop
adding and start concatenating everything together into a string. Let's take a
look at an example to see how this works:

```js
1 + 2 + "3" + 4 + 5;
//=> "3345"
```

First, we add the numbers `1`and `2` together to get `3` (a number). We then ask
JavaScript to add `3` (a number) to `"3"` (a string). JavaScript can't perform
addition with a string, so it decides to concatenate the two operands instead,
resulting in `"33"` (a string). The next operation, `"33" + 4`, is also between
a string and a number, and JavaScript once again concatenates, giving us the
result of `"334"` (a string). In the final operation, we're adding `"334"` with
`5` (a number). Again, JavaScript concatenates, giving the final result of
`"3345"`.

You'll encounter a lot of these weird data type behaviors throughout your
JavaScript programming, but fear not: they'll trip you up less and less often as
you gain experience.

## Conclusion

In this lesson we've learned about data types, which are abstractions used to
categorize pieces of information, or data. JavaScript defines seven different
types: numbers, strings, booleans, symbols, objects, `null`, and `undefined`.

## Resources

- [MDN — JavaScript data types and data structures](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Data_structures)
- [Destroy All Software — Types](https://www.destroyallsoftware.com/compendium/types?share_key=baf6b67369843fa2) – A cross-language examination of type in various languages
- [Destroy All Software — Wat][wat] – A beloved **_and hilarious_** talk in which JavaScript's friendliness when mixing types is discussed at a feverish pace – with awesome slides

[wat]: https://www.destroyallsoftware.com/talks/wat
[whole book]: https://plato.stanford.edu/entries/aristotle-categories/
[differs]: https://www.diffen.com/difference/Aristotle_vs_Plato
