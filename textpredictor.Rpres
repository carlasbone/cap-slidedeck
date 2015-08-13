Next Word Text Predictor
========================================================
author: Carla Bone
date: 10/8/2015
font-family: 'Timesroman'

This is the capstone requirement for the Data Scientist Specialisation

To utilise all skills learnt throughout the course to explore, 
clean, and process datasets in order to build a Shiny app that 
predicts the next word, given some typed in text. Then to create
a presentation to showcase the process and algorithms that
were employed.  Three datasets from twitter, news and blogs were
provided to base project on.

Cleaning Datasets
========================================================  
transition:rotate
The three datasets were read in and cleaned. Unicodes, and other non-English
characters were found and removed, along with hashtags, URLS, certain 
swear words, numbers, and other punctuation.  Any strings with less 
than 30 chars were removed, as the short sentences were unlikely to 
positively influence the end dataset. 

The cleaned datasets were then sampled into 3 sets of training, testing
and validation ( 25%, 37.5%, 37.5% respectively ) 


Processing and Creating the ngrams
========================================================
transition:rotate
Each of the training datasets was then pasted together to 
form one document each. The result being 3 training documents of twitter,
news, and blogs. A corpus of these 3 documents was then created, allowing
for much faster processing of ngrams and weightings.  The same process was 
applied to the testing and validation sets when required.

The ngrams were created using Quanteda's tokenize function, and dfms created.
Sparse features were removed. Ngrams of sizes 2, 3, and 4 were created with 
log of term frequency times inverse document frequency weights applied. The 
resulting dataframes were first saved as data tables using the data.tables 
package, and then saved as .Rdata files for faster search and retrieval. 
These tables are used in the Shiny app to search against.

The Text Predictor App
========================================================
transition:rotate 
The user is prompted to type text in a box and click Predict button.  The input 
string is checked for contractions and adjusted eg ("I'd live" becomes 
"(id|i'd|I would) live"), and first word stemmed.  Depending on number of words, 
first 4-gram table is searched,  if result, then saves last word of each to predict
table and extra weight applied to higher matches. If a smaller string is entered, 
then the trigram or bigram tables are searched first.  Any duplicates are aggregated 
and frequencies summed. Program will then search 3-gram table and then 2-gram table 
in the same manner, each time aggregating duplicates and merging to predict table. 
If still no matches, next w-1 word is taken and searched against trigram table, so 
missing out last word in search.

The top 5 predictions, with profanities are removed, or none found message, 
are then shown to user.

App Usage
========================================================
transition:rotate
Type your words in to box.
Click the Predict button.
The top five predicted words will then be shown.

![screen shot](textpredictor-figure/ss1.jpg)
