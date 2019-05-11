# Python: swapping rows and columns in a matrix
##### [Click here for the readme](README.md)

## Methods

There are multiple ways to do this, but the ones I think are most convenient/informative and the methods I will cover include:

* The zip() function
* A class in the numpy module
* List comprehensions

### Using the zip() function

In python, the zip() function takes any number of arguments. All arguments must be iterable, like lists for example. With any given lists, the zip function will return a list of tuples of each item at a specific index in each list. So, for example, zipping lists containing 1,2,3 and 4,5,6 returns tuples 1,4 and 2,5 and 3,6. With a list of lists, zip can be used to transpose each row and column. 

Let's say this is our matrix:
```python
>>> [[1,2,3],[4,5,6],[7,8,9]]
```
We can visualize this array like this:

 | column 1 | column 2 | column 3
--- |:---:| ---:
row 1 | 1 | 2 | 3
row 2 | 4 | 5 | 6
row 3 | 7 | 8 | 9
