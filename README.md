"# Chatbot" 

libraries to be used: nltk, keras, tensorflow, pickle
pip install tensorflow, keras, pickle, nltk

Import and load the data file

The dataset we will be using is ‘intents.json’. This is a JSON file that contains the patterns we need to find and the responses we want to return to the user. What we are doing with the JSON file is creating a bunch of messages that the user is likely to type in and mapping them to a group of appropriate responses. The tag on each dictionary in the file indicates the group that each message belongs too. With this data we will train a neural network to take a sentence of words and classify it as one of the tags in our file. Then we can simply take a response from those groups and display that to the user. The more tags, responses, and patterns you provide to the chatbot the better and more complex it will be.

Extracting and Preprocessing data
When working with text data, we need to perform various preprocessing on the data before we make a machine learning or a deep learning model. Tokenizing is the most basic and first thing you can do on text data. Tokenizing is the process of breaking the whole text into small parts like words. For each pattern we will turn it into a list of words using nltk.word_tokenizer, rather than having them as strings. The next step is to lemmatize each word and remove duplicate words from the list. Lemmatizing is the process of converting a word into its lemma form and then creating a pickle file to store the Python objects which we will use while predicting.

Creating Training  Data
We will create the training data in which we will provide the input and the output. Our input will be the pattern and output will be the class our input pattern belongs to. But the computer doesn’t understand text so we will convert text into numbers. We need some way to represent our sentences with numbers and this is where a bag of words comes in. What we are going to do is represent each sentence with a list the length of the amount of words in our models vocabulary. Each position in the list will represent a word from our vocabulary. If the position in the list is a 1 then that will mean that the word exists in our sentence, if it is a 0 then the word is nor present. We call this a bag of words because the order in which the words appear in the sentence is lost, we only know the presence of words in our model's vocabulary.
As well as formatting our input we need to format our output to make sense to the neural network. Similarly to a bag of words we will create output lists which are the length of the amount of labels/tags we have in our dataset. Each position in the list will represent one distinct label/tag, a 1 in any of those positions will show which label/tag is represented.

Developing a Model
Now that we have preprocessed all of our data we are ready to start creating and training a model. For our purposes we will use a fairly standard feed-forward neural network with two hidden layers. The goal of our network will be to look at a bag of words and give a class that they belong to.We use the Keras sequential API for this.We used softmax activation whi will tell us the probability of each output class. After training the model for 200 epochs, we achieved 100% accuracy on our model.

Predict the Response

We will load the trained model and then use a graphical user interface that will predict the response from the bot. The model will only tell us the class it belongs to, so we will implement some functions which will identify the class and then retrieve us a random response from the list of responses. We need to remember that our model does not take string input, it takes a bag of words. We also need to realize that our model does not spit out sentences, it generates a list of probabilities for all of our classes. This makes the process to generate a response look like the following:
– Get some input from the user
– Convert it to a bag of words
– Get a prediction from the model
– Find the most probable class
– Pick a response from that class

To code a graphical user interface. For this, we use the Tkinter library which already comes in python. We will take the input message from the user and then use the helper functions we have created to get the response from the bot and display it on the GUI.
