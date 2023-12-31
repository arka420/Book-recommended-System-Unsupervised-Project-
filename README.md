# Book Recommendation System

<p align="center">
  <img src="https://i.pinimg.com/originals/24/9a/74/249a74f48f753ecc5a746784bd5c6594.jpg" alt="System Image" width="800" height="450">
</p>

## Description:
<p>A Book Recommendation System which recommends the users a selection of books based on their interests.</p>


###  Data Cleaning and Pre-Processing
The dataset consists of three tables; Books, Users, and Ratings. Data from all three tables are cleaned and preprocessed separately as defined below briefly:<br><br>
For Books Table:
* Drop all three Image URL features.
* Check for the number of null values in each column. There comes only 3 null values in the table. Replace these three empty cells with ‘Other’.
* Check for the unique years of publications. Two values in the year column are publishers. Also, for three tuples name of the author of the book was merged with the title of the book. Manually set the values for these three above obtained tuples for each of their features using the ISBN of the book.
* Convert the type of the years of publications feature to the integer.


For Users Table:
* Check for null values in the table. The Age column has more than 1 lakh null values.
* Check for unique values present in the Age column. There are many invalid ages present like 0 or 244.
* By keeping the valid age range of readers as 5 to 100 replace null values and invalid ages in the Age column with the mean of valid ages.
* The location column has 3 values city, state, and country. These are split into 3 different columns named; City, State, and Country respectively. In the case of null value, ‘other’ has been assigned as the entity value.
* Removal of duplicate entries from the table.

For Ratings Table:
* Check for null values in the table.
* Check for Rating column and User-ID column to be an integer.
* Removal of duplicate entries from the table.

###  Algorithms Implemented:
#### 1 Popularity Based Recommendation :

* ##### Popular in the Whole Collection <br>
We have sorted the dataset according to the total ratings each of the books have received in non-increasing order and then recommended top n books.

* ##### Popular at a Given Place <br>
The dataset was filtered according to a given place (city, state, or country) and then sorted according to total ratings they have received by the users in decreasing order of that place and recommended top n books.

* ##### Books By the Same Author, Publisher of Given Book Name <br>
For this model, we have sorted the books by rating for the same author and same publisher of the given book and recommended top n books.

#### Recommendation using Average Weighted Rating
We have calculated the weighted score using the below formula for all the books and recommended the books with the highest score.
<p align="center">score= t/(t+m)∗a + m/(m+t)∗c </p>
where, <br>
t represents the total number of ratings received by the book <br>
m represents the minimum number of total ratings considered to be included <br>
a represents the average rating of the book and, <br>
c represents the mean rating of all the books. 

#### 2 User-Item Collaborative Filtering Recommendation
Collaborative Filtering Recommendation System works by considering user ratings and finds cosine similarities in ratings by several users to recommend books. To implement this, we took only those books' data that have at least 50 ratings in all.

#### 3 Correlation Based Recommendation
For this model, we have created the correlation matrix considering only those books which have total ratings of more than 50. Then a user-book rating matrix is created. For the input book using the correlation matrix, top books are recommended.

#### 4 Nearest Neighbour Based Recommendation
To train the Nearest Neighbours model, we have created a compressed sparse row matrix taking ratings of each Book by each User individually. This matrix is used to train the Nearest Neighbours model and then to find n nearest neighbors using the cosine similarity metric.

#### 5 Content Based Recommendation
This system recommends books by calculating similarities in Book Titles. For this, TF-IDF feature vectors were created for unigrams and bigrams of Book-Titles; only those books' data has been considered which are having at least 80 ratings.


###  Libraries Used:
* sklearn - Machine learning library
* seaborn, matplotlib,plotly - Visualization libraries
* numpy, scipy- number python library
* pandas - data handling library

