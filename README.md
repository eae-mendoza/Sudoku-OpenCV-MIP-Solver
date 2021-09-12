### Sudoku-OpenCV-MIP-Solver

Tie up of using OpenCV to encode Sudoku Puzzle images into acceptable array formats for a Mixed Integer Programming Sudoku Solver

Break down of Jupyter notebooks and Py files:

1. Digit Data Generator.ipynb

Contains code used to generate non-handwritten digit data since most Sudoku puzzle images are type-faced. Using only
hand-written MNIST data lead to very inaccurate results.

Noise was added to the generated images since the font styles were fairly limited. One thing to improve on here is to
generate digits from more font-types.

2. LeNet MNist Training.ipynb

CNN model based on LeNet. Architecture source can be any of the LeNet variants, as most perform similarly well. The 
performance of the model is more dependent on the quality of the data being fed. Architecture used: LeNet-5 CNN - 99.48% from Kaggle (Chennai, Tamil Nadu).

Since I wanted to train this CNN for Sudoku reading purposes, I augmented the data by randomly adding borders to the images. To account
for the cropping problems that may arise when reading data from Sudoku Puzzle images.

The model that had the highest validation accuracy was saved.

The model weights are stored in: 'weights-improvement-07-0.99.hdf5'

3. SudokuImageReader.ipynb

Uses the usual pre-processing methods to prepare the data. Blurring, thresholding, and color inversion as LeNet was trained on
color-inverted data.

Contouring was used to locate the puzzle on the image, then the array is then sub-divided into 9 x 9 blocks containing
each digit.

Each digit/block is then fed into the model.predict() function.

Classes are extracted, and output as a txt file.

4. Sudoku_Solver.ipynb

Just a noteboook version of SudokuSolver.py.

The output of SudokuImageReader.ipynb is directly acceptable by these.

5. Sample Sudoku pictures

My CNN cannot properly identify Sudoku1.jpg, but does fine with the rest. This is probably due to the thick borders messing up with the data.
