---
title: You can do more than just console.log
date: 2021-05-21T18:32:53.414Z
description: console.log is the favorite line of code for 1000s of JavaScript
  developers. While it definitely helps a lot during debugging and logging,
  console.table makes the information we print to the console easy to read.
---


> Writing a message, an object or any array to the console is definetly one of the things we do in everyday development. Often times when building real-world applications, you are required to log complex information to the console during development.

In this blog, we'll see how we can log complex objects to the console using the `console.table` function.

Let us say, we have an array of todo items.

```
const todoList = [
  {
    id: 1,
    title: "delectus aut autem",
    completed: false,
  },
  {
    id: 2,
    title: "quis ut nam facilis et officia qui",
    completed: false,
  },
  {
    id: 3,
    title: "fugiat veniam minus",
    completed: false,
  },
  {
    id: 4,
    title: "et porro tempora",
    completed: true,
  },
];
```

Now, let us pretend we're doing some debugging and want to see what is the 1st element in the array. So, let us use our favorite `console.log` function to log the element.

`console.log(todoList[0]);`

When the program executes, the output on the console will be something like this:

`{ id: 1, title: 'delectus aut autem', completed: false }`

Now, let us see how the output will be when we use `console.table` function with the same element.

```
┌───────────┬──────────────────────┐
│  (index)  │        Values        │
├───────────┼──────────────────────┤
│    id     │          1           │
│   title   │ 'delectus aut autem' │
│ completed │        false         │
└───────────┴──────────────────────┘
```

This is a better representation than a simple line as we have seen with `console.log`.

Let us say if we want to log the entire array, will that make a difference? Let us check -

- First, let us try with our good old friend `console.log`. If we execute `console.log(todoList)`, the output will be something like this

```
[
  { id: 1, title: 'delectus aut autem', completed: false },
  {
    id: 2,
    title: 'quis ut nam facilis et officia qui',
    completed: false
  },
  { id: 3, title: 'fugiat veniam minus', completed: false },
  { id: 4, title: 'et porro tempora', completed: true }
]
```

- Let us see if `console.table` can make it any better. So, if we execute `console.table(todoList)`, the output will be like this

```
┌─────────┬────┬──────────────────────────────────────┬───────────┐
│ (index) │ id │                title                 │ completed │
├─────────┼────┼──────────────────────────────────────┼───────────┤
│    0    │ 1  │         'delectus aut autem'         │   false   │
│    1    │ 2  │ 'quis ut nam facilis et officia qui' │   false   │
│    2    │ 3  │        'fugiat veniam minus'         │   false   │
│    3    │ 4  │          'et porro tempora'          │   true    │
└─────────┴────┴──────────────────────────────────────┴───────────┘
```

Isn't it nice and clean? This way of representation looks elegant and makes the information more readable.
