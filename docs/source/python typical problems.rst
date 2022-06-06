Typical Problems
============

**Check if list
ontains
integer x**

.. code-block:: python

    l = [3, 3, 4, 5, 2, 111, 5]
    print(111 in l) # True

**Find duplicate
number in
integer list**

.. code-block:: python

    def find_duplicates(elements):
        duplicates, seen = set(), set()
        for element in elements:
            if element in seen:
                duplicates.add(element)
            seen.add(element)
        return list(duplicates)

**Check if two
strings are
anagrams**

.. code-block:: python

    def is_anagram(s1, s2):
        return set(s1) == set(s2)
    print(is_anagram("elvis", "lives")) # True

**Remove all
duplicates from
list**

.. code-block:: python

    lst = list(range(10)) + list(range(10))
    lst = list(set(lst))
    print(lst)
    # [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]

**Find pairs of
integers in list
so that their
sum is equal to
integer x**

.. code-block:: python

    def find_pairs(l, x):
        pairs = []
        for (i, el_1) in enumerate(l):
            for (j, el_2) in enumerate(l[i+1:]):
                if el_1 + el_2 == x:
                    pairs.append((el_1, el_2))
        return pairs

**Check if a
string is a
palindrome**

.. code-block:: python

    def is_palindrome(phrase):
        return phrase == phrase[::-1]
    print(is_palindrome("anna")) # True

**Use list as
stack, array,
and queue**

.. code-block:: python

    # as a list ...
    l = [3, 4]
    l += [5, 6] # l = [3, 4, 5, 6]
    # ... as a stack ...
    l.append(10) # l = [4, 5, 6, 10]
    l.pop() # l = [4, 5, 6]
    # ... and as a queue
    l.insert(0, 5) # l = [5, 4, 5, 6]
    l.pop() # l = [5, 4, 5]

