Basic and Complex Data Types
==========

Integer, Float
---------

An **integer** is a positive or negative number
without floating point (e.g. 3). 

A **float** is a
positive or negative number with floating point
precision (e.g. 3.14159265359).

The ‘//’ operator performs integer division.
The result is an integer value that is rounded
toward the smaller integer number
(e.g. 3 // 2 == 1).

.. code-block:: python
    x, y = 3, 2
    print(x + y) # = 5
    print(x - y) # = 1
    print(x * y) # = 6
    print(x / y) # = 1.5
    print(x // y) # = 1
    print(x % y) # = 1s
    print(-x) # = -3
    print(abs(-x)) # = 3
    print(int(3.9)) # = 3
    print(float(3)) # = 3.0
    print(x ** y) # = 9


String
-------

Python Strings are sequences of characters.
The four main ways to create strings are the
following.

1. Single quotes

``'Yes'``

2. Double quotes

``"Yes"``

3. Triple quotes (multi-line)

``"""Yes
We Can"""``

4. String method

``str(5) == '5' # True``

5. Concatenation

``"Ma" + "hatma" # 'Mahatma'``

These are whitespace characters in strings.

- Newline ``\n``
- Space ``\s``
- Tab ``\t``

.. code-block:: python

    # 4. Indexing and Slicing
    s = "The youngest pope was 11 years old"
    print(s[0]) # 'T'
    print(s[1:3]) # 'he'
    print(s[-3:-1]) # 'ol'
    print(s[-3:]) # 'old'
    x = s.split() # creates string array of words
    print(x[-3] + " " + x[-1] + " " + x[2] + "s")
    # '11 old popes'

    ## 5. Most Important String Methods
    y = " This is lazy\t\n "
    print(y.strip()) # Remove Whitespace: 'This is lazy'
    print("DrDre".lower()) # Lowercase: 'drdre'
    print("attention".upper()) # Uppercase: 'ATTENTION'
    print("smartphone".startswith("smart")) # True
    print("smartphone".endswith("phone")) # True
    print("another".find("other")) # Match index: 2
    print("cheat".replace("ch", "m")) # 'meat'
    print(','.join(["F", "B", "I"])) # 'F,B,I'
    print(len("Rumpelstiltskin")) # String length: 15
    print("ear" in "earth") # Contains: True


List 
------

A container data type that stores a
sequence of elements. Unlike strings, lists
are mutable: modification possible.

.. code-block:: python

    l = [1, 2, 2]
    print(len(l)) # 3

**Adding elements**

Add elements to a list with (i) append, (ii)
insert, or (iii) list concatenation.
The append operation is very fast.

.. code-block:: python

    [1, 2, 2].append(4) # [1, 2, 2, 4]
    [1, 2, 4].insert(2,2) # [1, 2, 2, 4]
    [1, 2, 2] + [4] # [1, 2, 2, 4]

**Removal**

Removing an element can be slower.

.. code-block:: python

    [1, 2, 2, 4].remove(1) # [2, 2, 4]

**Reversing**

This reverses the order of list elements.

.. code-block:: python

    [1, 2, 3].reverse() # [3, 2, 1]

**Sorting**

Sorts a list. The computational complexity
of sorting is linear in the no. list elements.

.. code-block:: python

    [2, 4, 2].sort() # [2, 2, 4]

**Indexing**

Finds the first occurence of an element in
the list & returns its index. Can be slow as
the whole list is traversed.

.. code-block:: python

    [2, 2, 4].index(2) # index of element 4 is "0"
    [2, 2, 4].index(2,1) # index of element 2 after pos 1 is "1"


Stack
-------

Python lists can be used intuitively as
stacks via the two list operations append()
and pop().

.. code-block:: python

    stack = [3]
    stack.append(42) # [3, 42]
    stack.pop() # 42 (stack: [3])
    stack.pop() # 3 (stack: [])


Set 
-----

A set is an unordered collection of unique
elements (“at-most-once”).

.. code-block:: python

    basket = {'apple', 'eggs', 'banana', 'orange'}
    same = set(['apple', 'eggs', 'banana', 'orange'])


Dictionary
--------

The dictionary is a useful data structure for
storing (key, value) pairs.

.. code-block:: python

    calories = {'apple' : 52, 'banana' : 89, 'choco' : 546}

**Reading and writing elements**

Read and write elements by specifying the
key within the brackets. Use the keys() and
values() functions to access all keys and
values of the dictionary.

.. code-block:: python

    print(calories['apple'] < calories['choco']) # True
    calories['cappu'] = 74
    print(calories['banana'] < calories['cappu']) # False
    print('apple' in calories.keys()) # True
    print(52 in calories.values()) # True

**Dictionary Looping**

You can access the (key, value) pairs of a
dictionary with the items() method.

.. code-block:: python

    for k, v in calories.items():
        rint(k) if v > 500 else None # 'chocolate'


Membership operator
-------

Check with the ‘in’ keyword whether the
set, list, or dictionary contains an element.
Set containment is faster than list
containment.

.. code-block:: python

    basket = {'apple', 'eggs', 'banana', 'orange'}
    print('eggs' in basket) # True
    print('mushroom' in basket) # False

List and Set Comprehension
-------

List comprehension is the concise Python
way to create lists. Use brackets plus an
expression, followed by a for clause. Close
with zero or more for or if clauses.
Set comprehension is similar to list
comprehension.

.. code-block:: python

    #List comprehension
    l = [('Hi ' + x) for x in ['Alice', 'Bob', 'Pete']]
    print(l) # ['Hi Alice', 'Hi Bob', 'Hi Pete']
    l2 = [x * y for x in range(3) for y in range(3) if x>y]
    print(l2) # [0, 0, 2]
    # Set comprehension
    squares = { x**2 for x in [0,2,4] if x < 4 } # {0, 4}

