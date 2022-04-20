# Using Goodreads to get onto the New York Times Best Sellers list

### Abstract
How can a new publishing company break into the industry and get their books onto the New York Times Best Sellers list? [Goodreads](https://www.goodreads.com) is one of the largest social websites geared towards readers, and it allows its users to rate books, post reviews, as well as network with other users. Using information from Goodreads will provide insight to my client regarding strategies to pursue when publishing a new book.


### Design

I combined data from Goodreads that provided information on a book's ratings and a list of the books on the New York Times Best Sellers list from January 2010 through December 2019. The [Goodreads dataset](https://www.kaggle.com/datasets/bahramjannesarr/goodreads-book-datasets-10m) and the [New York Times Best Sellers dataset](https://www.kaggle.com/datasets/dhruvildave/new-york-times-best-sellers) were both found on Kaggle. After cleaning up the data, I obtained each book's subject(s) through [OpenLibrary's](https://openlibrary.org/) publicly available [Book API](https://openlibrary.org/dev/docs/api/books).

This information was used to determine the features that would help classify a book as a New York Times Best Seller.

### Data

The final dataset contains information on 22,412 books published between January 2010 and December 2019, with 22 features. This includes information such as the book's title, author, number of pages, date of publishing, overall user rating, rating distributions, the number of reviews, and ISBN. (An ISBN is a unique identifier for each book.) For this initial analysis, a subset of 13 features were used.

### Algorithms

*Feature Engineering*
All ratings distribution features were converted from strings into separate numerical features indicating the total number of ratings for each value (i.e., how many 5 star ratings, 4 star ratings, etc.).

*Models*
The baseline model was a Logistic Regression model. K-nearest neighbors and Random Forest classifier models were also used. After using cross-validation to find the model with the best overall F1 score, a Random Forest model was selected.

*Model Evaluation and Selection*
A split of 80/20 was used for training and holdout data. Random oversampling, undersampling, and SMOTE were used on the training data due to the large class imbalance. After cross-validation and refinement on the training data, the two final models were evaluated on the holdout data:

Complex model
Random forest with SMOTE:
Precision: 0.969
Recall: 0.820
F1: 0.889

Simplified model
Random forest with SMOTE
precision: 0.806
recall: 0.641
f1: 0.714

### Tools

I used the JSON library to obtain subject data from OpenLibrary, and pandas to clean and manipulate the data. I also used sklearn to build, test, and refine all models. Matplotlib was used for visualizations.

### Communication

See slides for presentation