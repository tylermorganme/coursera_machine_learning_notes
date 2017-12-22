# General machine learning ideas
- m - number of training samples
- x's - input variable/features
- y's - output variables/target variable
- training set > learning algorithm > h(x) = hypothesis
# Supervized Learning
- Supervised learning is the most common type of machine learning.
- Classification Problems have discrete outputs
- Supervised Learning is given correct answers
- Regression predicts continuous valued output
# Unsupervised Learning
- Clustering algorithms for classifying things into groups.
- We can derive structure from data where we don't necessarily know the effect of the variables.
#Gradient Descent
- alpha is the learning rate. Controls the - aggressiveness of the descent.
- NOTE: be sure to simultaneously update all variables. Not piecemeal.
- gradient descent with a constant alpha will still then to converge because as the derivative gets closer to zero the steps are smaller.
- normal equations method is an alternative method for solving a linear equation set without iteration, but it doesn't scale well to large data sets.
- batch gradient descent looks at every sample in the set for each iteration.
- Works well when n is large.
# Matrixes & Vectors
- Aij refers to the element in the ith row and jth column of matrix A.
- A vector with 'n' rows is referred to as an 'n'-dimensional vector.
- vi refers to the element in the ith row of the vector.
- In general, all our vectors and matrices will be 1-indexed. Note that for some programming languages, the arrays are 0-indexed.
- Matrices are usually denoted by uppercase names while vectors are lowercase.
- "Scalar" means that an object is a single value, not a vector or matrix.
- ℝ refers to the set of scalar real numbers.
- ℝ𝕟 refers to the set of n-dimensional vectors of real numbers.
## Matrix Addition
- You can only add or subtract matrixes of the same dimensions.
- Each element is added or subtracted to/from the counterpart at the same location in the other matrix.
- The resulting matrix has the same dimensions as the two original matrices.
- NOTE: Some programs will let you add/subtract a matrix with a scalar.
## Matrix Multipication with a Scalar
- Each element in the matrix is multiplied by the scalar factor.
- The resulting matrix will have the same dimensions as the original matrix.
## Matrix Multiplication with a Vector
- The number of columns of the matrix must equal the number of rows of the vector.
- A matrix is multiplied by a vector by summing the product of each subsequent element across a row in the first matrix with each subsequent element down the column in the second matrix.
  m1 = [1,2;3,4;5,6] * [3;2] = [1 * 3 + 2 * 2;3 * 3 + 4 * 2;5 * 3 + 6 * 2] = [7;17;27]
- The resulting matrix will be a vector with the same number of rows as the first matrix.
### Using Matrix/Vector Multiplication for Predicting Linear Regression
- For Linear Regression, predictions can be made by creating a data matrix and multiplying it by the parameters.
- A data matrix is formed by creating a matrix with column 1 containing the integer 1 and column 2 containing the input values.
- The parameter matrix should be formatted as the constant in position 1 and the multiplicative factor in position 2.
- It is more efficient to do this than to use loops.

## Matrix Multiplication with a Matrix
- The first matrix must have the same number of columns as the second matrix has rows.
- The resulting matrix will have the same number of rows as the first matrix and the same number of columns as the second matrix.
- Each subsequent column of the resulting matrix is the product of the first matrix with with the corresponding column of the second matrix, which happens to be a vector.
### Using Matrix/Matrix Multiplication for Predicting Linear Regression
- Can be used to test multiple hypotheses at once.
- This works the same way as Matrix/Vector multiplication except the second matrix is formed of columns, where each column is a vector containing the constant in position 1 and the multiplicative factor in position 2.
### Properties of Matrix Multiplication
- Matrix multiplication is not commutative (i.e AxB != BxA)
- Matrix multiplication is associative (i.g AxBxC = Ax(BxC) = (AxB)xC)
#### Identity Matrix
- Is denoted *I* or for the sake of these notes I
- Has the value 1 along the diagonal from top left to bottom right and zero for all others values e.g.[1,0,0,0;0,1,0,0;0,0,1,0;0,0,0,1]
- For any Matrix A: AxI = IxA = A
## Matrix Inverses
- Not all matrices have an inverse.
- Only matrixes that are mxm (square matrix) can have an inverse.
- If a matrix does have an inverse A^-1 x A = I where A^-1 is the inverse.
- Matrices that don't have an inverse are called "singular" or "degenerate" matrices.
## Matrix Transposition
- Row i of the matrix becomes column i in the transposed matrix.
- B_ij = B_ji

# Multivariate Linear Regression
- n is the number of features
- m is the number of training examples
- x^i is the set of training features for a single training example.
_ x_j^i is the value of feature j in the ith training example.
- There is always an implied x_0 feature with the value 1. This is the multiplier of the constant factor.
  - That means that the feature set (a vector with all of the parameter values) is length n + 1.
  - hθ(x)=θ0+θ1x1+θ2x2+θ3x...+θnxn
  - The purpose of this is the allow matrix operations where the the number of theta and x values are equal.
# Gradient Descent Optimization
- If features are within similar scales gradient descent will converge more quickly.
  - Ideally each feature is between approximately -1 and 1.
  - This can be accomplished by normalizing the data, this is known as *feature scaling*.
  - It also helps to have value centered around zero which can be accomplished by comparing to the average. This is known as *mean normalization*.
  - e.g. room sizes in square feet and range is 0 to 2000 and the average is 1000 you could normalize by using (x - 1000)/2000 where x is room size.
  - Instead of range, standard deviation is another good method or normalizing.
  - A good way to debug gradient descent is to plot the cost function as it's running.
  - It's very hard to tell in advance how fast gradient descent will converge.
  - A typical test for convergence is to check if the cost function J(theta) has decreased by less than 10^-3.
  - If you look at a plot of the cost function and it's increasing it's a sign that you alpha value is likely too large.
  - If the alpha value is sufficiently small it should decrease on every iteration, but if the alpha is too small it can take a long time to converge.
## Computing Parameters Analytically (Normal Equation)
- The optimal value theta can be found where theta = (X^T*X)^-1*X^T*y where X^T is the transpose of X. This is known as the "normal equation". You don't have to worry about feature scaling when you use the normal method.
- Is slow when the number of training samples is very large. This is typically an issue if your sample set gets over 10,000 samples.
### Non-invertible Matrices
- Features are redundant (e.g. site in feet^2 and size in feet)
- Too many features e.g. m <= n. The work around for this is to delete features or use regularization.
# Matlab Notes
- A `.` preceding an operations such as `*` tend to represent an element-wise operation e.g. each element of one array is multiplied by the corresponding element in another array.
- `'` is the symbol to transpose an array.
- When plotting the `hold on;` command will force the plot to draw a new plot overlaid over the existing plot.
- You can pull up multiple plots by using the `figure` command
- `imagesc` creates a color map of data. You can do it in grayscale by using `imagesc, colorbar, colormap gray`
- You can chain command on the same line by following each command with `;`
