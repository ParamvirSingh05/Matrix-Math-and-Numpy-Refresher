# Matrix Math and Numpy Refresher

Deep Learning involves a lot of matrix math, and it's important for you to understand the bascis before diving into building your own neural networks. This repository provides some guidance for using the Numpy library to work efficiently with matrices in Python.

## Data Dimensions

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