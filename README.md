## Data ETL Pipeline Using Python

This code demonstrates how to load the Fashion MNIST dataset using TensorFlow's Keras API, preprocess the data, and store it in a SQLite database. The Fashion MNIST dataset consists of grayscale images of clothing items with corresponding labels.

### Loading and Preprocessing the Data

- The code begins by importing the necessary libraries, including TensorFlow Keras and SQLite.
- The Fashion MNIST dataset is loaded using `keras.datasets.fashion_mnist.load_data()`, and it is split into training and test sets.
- The code then prints the shapes of the loaded data to verify the dimensions.
- Next, the pixel values of the images are normalized by dividing by 255 to scale them between 0 and 1.
- The `xtrain` and `xtest` arrays are reshaped to include a channel dimension for compatibility with convolutional neural networks.

### Storing the Data in SQLite Database

- A connection is established with an SQLite database file named `fashion_mnist.db`.
- The code creates a table named `images` in the database if it doesn't exist already.
- A loop iterates over the training set, inserting each image and its corresponding label into the `images` table using binary data conversion.
- The connection is committed to save the changes.
- Another loop iterates over the test set, inserting the images and labels into the `images` table.
- The connection is committed again to finalize the changes.
- Finally, the connection to the database is closed.

### Retrieving Data from SQLite Database

- The code re-establishes a connection with the `fashion_mnist.db` file.
- A cursor is created to execute SQL queries.
- The cursor selects all rows from the `images` table.
- The selected rows are fetched and stored in the `rows` variable.
- Additionally, the `pandas` library is used to read the entire `images` table into a DataFrame named `data`.

### Usage

To use this code, follow these steps:

1. Make sure you have TensorFlow and SQLite installed.
2. Download or clone the code from this GitHub repository.
3. Run the code in a Python environment.
4. After execution, you will find a file named `fashion_mnist.db` containing the dataset stored in an SQLite database.

Acknowledgments

This code is adapted from the Fashion MNIST example provided in the TensorFlow documentation.

References

- [Fashion MNIST Dataset](https://github.com/zalandoresearch/fashion-mnist)
- [TensorFlow Keras](https://www.tensorflow.org/api_docs/python/tf/keras)
- [SQLite](https://www.sqlite.org/)
