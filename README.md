# DICTIONARY

A dictionary is a book or electronic resource that lists the words of a language (typically in alphabetical order) and gives their meaning, or gives the equivalent words in a different language, often also providing information about pronunciation, origin, and usage.

This mini-project aim to create a dictionary in Python which can retrieve definitions for user and ask 'did you mean this instead?' if user made a typo while entering the word, and if the word has more than one definition then retrieve them all.

## CODE:
'''python
import json
from difflib import get_close_matches

data = json.load(open("data.json"))

def translate(word):
    word = word.lower()
    if word in data:
        return data[word]
    elif word.title() in data:
        return data[word.title()]
    elif word.upper() in data:
        return data[word.upper()]
    elif len(get_close_matches(word , data.keys())) > 0 :
        print("Did you mean '%s' instead?" %get_close_matches(word, data.keys())[0])
        decide = input("Press y for yes or n for no ")
        if decide == "y":
            return data[get_close_matches(word , data.keys())[0]]
        elif decide == "n":
            return("Wrong Input. Try again. ")
        else:
            return("You have entered wrong input please enter just y or n ")
    else:
        print("Wrong keys")

word = input("Enter the word you want to search: ")
output = translate(word)
if type(output) == list:
    for item in output:
        print(item)
else:
    print(output)
'''
