# Final-Project

The source for pytesseract `.exe` file is https://drive.google.com/drive/folders/1teiBNEoSiSJHn83OxJayb-gJ-7Lqhfzb?usp=sharing

The dataset can be accessed here https://drive.google.com/file/d/1Dvfv8VW8CEhTcidQPbJiA5bh_ICbBwfE/view?usp=sharing

This is the manual for the code that is added into this gitHub repository. This repository contains the project that is titled as `Judging a book by its cover`. This is a Deep Learning project that uses Long Short Term Memory (LSTM) model to classify the text taken from the cover page of a book, into a respective genre. This genre is used for various purposes. 

The `model.ipynb` script analyzes the text extracted from book covers to predict the genre of the book and conduct a sentiment analysis of the extracted text. It uses various Python libraries including pytesseract, Pillow, textblob, pandas, numpy, keras, and sklearn.

The script starts by importing the necessary libraries. It then defines a function, extract_text(), which takes an image file path as an argument and uses pytesseract to extract the text from the image. The function returns the extracted text.

The script then creates a list of original genres present in the `book-covers` directory and initializes two empty lists, genre_class and image_text. It then iterates through each genre, extracts text from each image in the genre, and appends the genre class and the extracted text to the respective lists. It uses the tqdm library to display a progress bar for the iteration.

The script creates a pandas DataFrame, extracted_data, and populates it with the image_text and genre_class lists. It then cleans the text data in the `Image_Text` column of the DataFrame by converting it to lowercase, removing extra whitespace, and removing punctuation marks. The cleaned data is stored in a new list, clean_text, which is then used to update the `Image_Text` column.

The cleaned data is then saved to a CSV file named `Extracted_data.csv`, which is read back into the script using pandas. The script then selects the first 24000 rows from the DataFrame and removes any rows containing null values. It then converts the `Genre` column to one-hot encoded categorical data.

The script creates a Keras tokenizer object and fits it to the `Image_Text` data. It then uses the tokenizer to convert the text data into sequences and pads the sequences to a fixed length. It also one-hot encodes the `Genre` data. The script then saves the tokenizer object to a file named `tokenizer.pkl`.

The script creates a sequential Keras model and adds an embedding layer, LSTM layer, and dense output layer to it. It compiles the model using categorical cross-entropy loss and the Adam optimizer. It trains the model using the padded text data and the one-hot encoded genre data for 20 epochs with a batch size of 64.

The script then predicts the genre for each row in the `Image_Text` column of the DataFrame. It also conducts sentiment analysis on the `Image_Text` data using TextBlob and adds the results to a new column named `sentiment`. The predicted genres and sentiment data are used to create a table that displays the percentage of positive, neutral, and negative sentiments for each genre and the percentage of predicted genres for each genre.

Finally, the script creates a bar chart that displays the percentage of positive, neutral, and negative sentiments for each genre.





