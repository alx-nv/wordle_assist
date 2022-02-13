# wordle_assist
A data science exercise in Jupyter which analyses the best position for each letter in a game of wordle.

***
DISCLAIMER:
This project is mainly a python/pandas/data science exercise and hence the mathematics and statistics in it do not pretend are quite basic. In case you have suggestions for improvement, please don't hasitate to contact me.

Background:
During a wordle game, I typed the word 'FLOAT' when the correct answer was ALOFT. This made me wonder what is the best position for each letter and I decided to use practise my data science skills to come up with a solution.

How it works:
  1. a rather large text file (copied the text of several books, including LotR, 'Three man in a boat' and a large word list I found on github) is supplied  - it serves as data to be analysed.
  2. all punctuation signs, digits and special characters* are removed and all letters are conerted to lowecase - what remains is a lowercase string of words, separated by spaces and new lines.
  3. the string is split and saved in a list(set(list())) variable so that repeating words are removed.
  4. with a for cycle all words that do not have exactly 5 letters are removed**.
  5. a letter frequency dict is created, linking each letter to a frequency score. This is done so that we can rate the likelyhood that a letter would appear in a word.
  (5.1) I was wondering whether the letter frequency in 5 letter words only would be different compared to the overall freqeuncy. The five-letter-word frequency is calculated in te notebook, but no further analysis has been done yet, comparing results with the two dicts.
  6. based on the letter frequency, a score is calculated*** for each word (score = sum of all letters indivudual frequencies). The higher scoring words aim to open as many letters as possible in the wordle game, giving the player information for the following attempts; words with repeating letters can be filtered; a 'vowel count' column is also present as vowels are less in number and hence easier to guess.
  7. next, for each letter is calculated the likelyhood that it will appear on a particular position in the word. For example, the letter Q is most likely to appear at the first position, while Y is most likely to be at the end of the word. The calculation is simply the appearances of the letter at each position as a percentage of total appearances. A heatmap plot is created for easier understanding, where appearance percentage below the average for each position (20%) are not shown.


Known issues:

  *1 I had some problems getting rid of non-ascii characters, such as single quotation marks and accented letters. Those are currently hard coded in the notebook and only work for the test file I am using. A general solution should be implemented.

  *2 The non-five-letter-words removal proces seems to be the slowest part of the code as it relies on a for loop going through every item in the list. 

  *3 The frequency score calculation is very basic and unstable. For example, a fake word such as 'eeeee' will score higher than any other word, assuming E is the most common letter. This is not a problem in the notebook, as I am only checking readily avaiable words, but the approach is prone to fake results. A solution I came up with was to check all words in a list with ome kind of dictionary online, making sure there are no fake words but this is currently not implemented.
