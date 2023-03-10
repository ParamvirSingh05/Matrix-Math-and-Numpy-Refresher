# Matrix Math and Numpy Refresher

## 1.Introduction

Deep Learning involves a lot of matrix math, and it's important for you to understand the bascis before diving into building your own neural networks. This repository provides some guidance for using the Numpy library to work efficiently with matrices in Python.

## 2.Data Dimensions

Neural Networks do a lot of math with a lot of data. But before we start designing those networks with ourselves, and making sure that all that math is setup correctly, we first need to understand how we represent that data. Specifically, we need to think about the shapes data can have. For example, we might have a single number, representing a person's height in centimeters, or a list of numbers representing various features of that person like height, weight and age. Or maybe we have an image of that person and represent it as a grid, with rows and columns of individual pixels. And one possible way to represent a single pixel in that image might use three numbers, one for each red, blue, and green color channels.
We describe these different shapes of data in terms of their number of dimensions.

### Scalars
Smallest simple shape representing single value like 1, 9.7, -0.8. Scalars have zero dimensions. From the example before, a person's height would be a scalar.

### Vectors
Vectors list of values. There a two types of vectors:

#### 1. Row Vectors
#### 2. Column Vectors

Vectors have one dimensions which we also call length. From the example before, a person's height, weight and age, could be stored as a vector.

![Row and Column Vectors](/assests/images/Vectors.png)

### Matrices
A matrix is a two-dimensional grid of values. We describe the shape of a matrix in terms of it's number of rows and columns. If you had a single number for each pixel of an image, then you could store those pixel values in a matrix.

![Refering elements in a Matrix](/assests/images/Indices.png)

### Tensors
The term tensor can be refered to as any n-dimensional collections of values. So a scalar is a zero-dimensional tensor; a vector is a one-dimensional tensor; a matrix is two dimensional tensor; and anything larger than two-dimensions, we just call it a tensor.

We will also need to refer to individual elements inside of matrix. We do that using index, which is its row and then column.

## 3.Data in Numpy

Python is convenient, but it can also be slow. However, it does allow you to access libraries that execute faster code written in languages like C. NumPy is one such library: it provides fast alternatives to math operations in Python and is designed to work efficiently with groups of numbers - like matrices.

NumPy is a large library and we are only going to scratch the surface of it here. If you plan on doing much math with Python, you should definitely spend some time exploring its [documentation](https://numpy.org/doc/stable/reference/) to learn more.

### Importing NumPy
When importing the NumPy library, the convention you'll see used most often ??? including here ??? is to name it np, like so:

> import numpy as np

Now you can use the library by prefixing the names of functions and types with np., which you'll see in the following examples.

### Data Types and Shapes
The most common way to work with numbers in NumPy is through ndarray objects. They are similar to Python lists, but can have any number of dimensions. Also, ndarray supports fast math operations, which is just what we want.

Since it can store any number of dimensions, you can use ndarrays to represent any of the data types we covered before: scalars, vectors, matrices, or tensors.

### Scalars
Scalars in NumPy are a bit more involved than in Python. Instead of Python???s basic types like int, float, etc., NumPy lets you specify signed and unsigned types, as well as different sizes. So instead of Python???s int, you have access to types like uint8, int8, uint16, int16, and so on.

These types are important because every object you make (vectors, matrices, tensors) eventually stores scalars. And when you create a NumPy array, you can specify the type - but every item in the array must have the same type. In this regard, NumPy arrays are more like C arrays than Python lists.

If you want to create a NumPy array that holds a scalar, you do so by passing the value to NumPy's array function, like so:

> s = np.array(5)

You can still perform math between ndarrays, NumPy scalars, and normal Python scalars, though, as you'll see in the element-wise math lesson.

You can see the shape of your arrays by checking their shape attribute. So if you executed this code:

> s.shape

it would print out the result, an empty pair of parenthesis, (). This indicates that it has zero dimensions.

Even though scalars are inside arrays, you still use them like a normal scalar. So you could type:

> x = s + 3

and x would now equal 8. If you were to check the type of x, you'd find it is probably numpy.int64, because its working with NumPy types, not Python types.

By the way, even scalar types support most of the array functions. so you can call x.shape and it would return () because it has zero dimensions, even though it is not an array. If you tried that with a normal Python scalar, you'd get an error.

### Vectors
To create a vector, you'd pass a Python list to the array function, like this:

> v = np.array([1,2,3])

If you check a vector's shape attribute, it will return a single number representing the vector's one-dimensional length. In the above example, v.shape would return (3,)

Now that there is a number, you can see that the shape is a tuple with the sizes of each of the ndarray's dimensions. For scalars it was just an empty tuple, but vectors have one dimension, so the tuple includes a number and a comma. (Python doesn???t understand (3) as a tuple with one item, so it requires the comma. You can read more about tuples [here](https://docs.python.org/3/tutorial/datastructures.html#tuples-and-sequences))

You can access an element within the vector using indices, like this:

> x = v[1]

Now x equals 2.

NumPy also supports advanced indexing techniques. For example, to access the items from the second element onward, you would say:

> v[1:]

and it would return an array of [2, 3]. NumPy slicing is quite powerful, allowing you to access any combination of items in an ndarray. But it can also be a bit complicated, so you should read up on it in the documentation.

### Matrices
You create matrices using NumPy's array function, just you did for vectors. However, instead of just passing in a list, you need to supply a list of lists, where each list represents a row. So to create a 3x3 matrix containing the numbers one through nine, you could do this:

> m = np.array([[1,2,3], [4,5,6], [7,8,9]])

Checking its shape attribute would return the tuple (3, 3) to indicate it has two dimensions, each length 3.

You can access elements of matrices just like vectors, but using additional index values. So to find the number 6 in the above matrix, you'd access m[1][2].

### Tensors
Tensors are just like vectors and matrices, but they can have more dimensions. For example, to create a 3x3x2x1 tensor, you could do the following:

> t = np.array([[[[1],[2]],[[3],[4]],[[5],[6]]],[[[7],[8]],[[9],[10]],[[11],[12]]],[[[13],[14]],[[15],[16]],[[17],[17]]]])

And t.shape would return (3, 3, 2, 1).

You can access items just like with matrices, but with more indices. So t[2][1][1][0] will return 16.

### Changing Shapes
Sometimes you'll need to change the shape of your data without actually changing its contents. For example, you may have a vector, which is one-dimensional, but need a matrix, which is two-dimensional. There are two ways you can do that.

Let's say you have the following vector:

> v = np.array([1,2,3,4])

Calling v.shape would return (4,). But what if you want a 1x4 matrix? You can accomplish that with the reshape function, like so:

> x = v.reshape(1,4)

Calling x.shape would return (1,4). If you wanted a 4x1 matrix, you could do this:

> x = v.reshape(4,1)

The reshape function works for more than just adding a dimension of size 1. Check out its [documentation](https://numpy.org/doc/stable/reference/generated/numpy.reshape.html) for more examples.

One more thing about reshaping NumPy arrays: if you see code from experienced NumPy users, you will often see them use a special slicing syntax instead of calling reshape. Using this syntax, the previous two examples would look like this:

> x = v[None, :]

or

> x = v[:, None]

Those lines create a slice that looks at all of the items of v but asks NumPy to add a new dimension of size 1 for the associated axis. It may look strange to you now, but it's a common technique so it's good to be aware of it.

## 4.Element-wise Matrix Operations

I am sure you are already familiar with the scalar math. It's the normal addition, multiplication and so on.

![Scalar Math](/assests/images/Scalar%20Math.png)

But sometimes with neural networks you might need to perform those sort of operations on a lot of numbers, maybe hundreds, thousands, even millions of them. Maybe you need to double them, square them, or divide them all by the same number. If you were writing a program, you might decide to make a loop where you iterate over every value and perform the same operation on each one over and over, but matrices offer a better alternative.

![Addition of Scalar and Matrix](/assests/images/Adding%20Scalar%20and%20Matrix.png)

If you have all those numbers stored in a matrix, you can perform element-wise operations on them. You can also do element-wise math between all the elements within two different matrices. For this to work, the matrices have to be the same shape. 

![Addition of two matrices](/assests/images/Adding%20two%20matrices.png)

## 5.Element-wise Operations in Numpy

### The Python way
Suppose you had a list of numbers, and you wanted to add 5 to every item in the list. Without NumPy, you might do something like this:

```
values = [1,2,3,4,5]
for i in range(len(values)):
    values[i] += 5
# now values holds [6,7,8,9,10]
```

That makes sense, but it's a lot of code to write and it runs slowly because it's pure Python.

### The NumPy way
In NumPy, we could do the following:

```
values = [1,2,3,4,5]
values = np.array(values) + 5
# now values is an ndarray that holds [6,7,8,9,10]
```

Creating that array may seem odd, but normally you'll be storing your data in ndarrays anyway. So if you already had an ndarray named values, you could have just done:

```
values += 5
```

We should point out, NumPy actually has functions for things like adding, multiplying, etc. But it also supports using the standard math operators. So the following two lines are equivalent:

```
x = np.multiply(some_array, 5)
x = some_array * 5
```

We will usually use the operators instead of the functions because they are more convenient to type and easier to read, but it's really just personal preference.

One more example of operating with scalars and ndarrays. Let's say you have a matrix m and you want to reuse it, but first you need to set all its values to zero. Easy, just multiply by zero and assign the result back to the matrix, like this:

```
m *= 0
# now every element in m is zero, no matter how many dimensions it has
```

### Element-wise Matrix Operations
The same functions and operators that work with scalars and matrices also work with other dimensions. You just need to make sure that the items you perform the operation on have compatible shapes.

Let's say you want to get the squared values of a matrix. That's simply x = m * m (or if you want to assign the value back to m, it's just m *= m

This works because it's an element-wise multiplication between two identically-shaped matrices. (In this case, they are shaped the same because they are actually the same object.)

```
a = np.array([[1,3],[5,7]])
a
# displays the following result:
# array([[1, 3],
#        [5, 7]])

b = np.array([[2,4],[6,8]])
b
# displays the following result:
# array([[2, 4],
#        [6, 8]])

a + b
# displays the following result
#      array([[ 3,  7],
#             [11, 15]])
```

And if you try working with incompatible shapes, like the other example from the video, you'd get an error:

```
a = np.array([[1,3],[5,7]])
a
# displays the following result:
# array([[1, 3],
#        [5, 7]])
c = np.array([[2,3,6],[4,5,9],[1,8,7]])
c
# displays the following result:
# array([[2, 3, 6],
#        [4, 5, 9],
#        [1, 8, 7]])

a.shape
# displays the following result:
#  (2, 2)

c.shape
# displays the following result:
#  (3, 3)

a + c
# displays the following error:
# ValueError: operands could not be broadcast together with shapes (2,2) (3,3) 
```

You'll learn more about what that "could not be broadcast together" means in a later lesson, but for now, just notice that the two shapes are different so we can't perform the element-wise operation.