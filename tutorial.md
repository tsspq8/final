# Python: swapping rows and columns in a matrix
##### [Click here for the readme](README.md)

## Methods

There are multiple ways to do this, but the ones I think are most convenient/informative and the methods I will cover include:

* The zip() function
* A class in the numpy module
* List comprehensions

### Using the zip() function

In python, the zip() function takes any number of arguments. All arguments must be iterable, like lists for example. With any given lists, the zip function will return zip object, which is a collection of tuples of each item at a specific index in each list. So, for example, zipping lists containing 1,2,3 and 4,5,6 returns tuples 1,4 and 2,5 and 3,6. With a list of lists, zip can be used to transpose each row and column. 

Let's say this is our matrix:
```python
>>> mainList = [[1,2,3],[4,5,6],[7,8,9]]
```
We can visualize this array like this:

. | column 1 | column 2 | column 3
--- |:---:|:---:|:---:
row 1 | 1 | 2 | 3
row 2 | 4 | 5 | 6
row 3 | 7 | 8 | 9

Our goal is to take each index of our mainList (which will each be a list), and take each index of that list, and assign the matching item of each unique index with other items of the same index. In python, you can consider addressing arrays as: 
```python
mainList[row][column]
```
The code evaluates the "row" in brackets first, and then the "column" of that specific list. 

Because we want to use zip(), we will also need to use an * before the name mainList. In python, this will unpack an iterable and pass in each individual list to the zip function. Running the code:
```python
zip(*mainList)
```
will return a zip object containing what we wanted, tuples 1,4,7 and 2,5,8 and 3,6,9. It's unintuitive to work with a zip object unless you have another goal in mind, so we will need to convert this to a list. You may also want lists instead of tuples, so that is what I will explain here. 

To get the zip object as a list, we must first run the code previously shown surrounded with brackets, as lists normally are. This will put a single zip object into a list. We can then add in an asterisk before zip so that each item within zip is put into the list.
```python
>>> [*zip(*mainList)]
[(1, 4, 7), (2, 5, 8), (3, 6, 9)]
```

The next step in understanding how to convert this list of tuples into a list of lists is to understand the map() function. This is the last step in getting a list of lists. map() takes two arguments, the first being a function, and the second being an iterable. For each item in the passed in iterable, map will perform the function specified. It returns a map object, so we can use the list() function surrounding the map function to get a list.

```python
>>> list(map(list, [*zip(*mainList)]))
[[1, 4, 7], [2, 5, 8], [3, 6, 9]]
```

This is what we wanted to do, and visualized is:

. | column 1 | column 2 | column 3
--- |:---:|:---:|:---:
row 1 | 1 | 4 | 7
row 2 | 2 | 5 | 8
row 3 | 3 | 6 | 9
