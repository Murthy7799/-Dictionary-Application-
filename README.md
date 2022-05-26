# -Dictionary-Application-

import json
from difflib import get_close_matches
data=json.load(open("C:\\Users\\murthy\\Downloads\\data.json"))
#print(data)
def keyword(word):

    if word in data:
       return data[word]
    elif len(get_close_matches(word, data.keys(),n=3,cutoff=0.8)) > 0:
           reenter=input("Did you mean %s instead? if yes enter Y,if no enter N :" % get_close_matches(word, data.keys(),n=3,cutoff=0.8)[0])
           if reenter == "Y":
               return data[get_close_matches(word, data.keys(),n=3,cutoff=0.8)[0]]
           elif reenter == "N":
               return "The entered key word is not in dictionary"
           else:
               return "We didn't recognize your entry"
    else:
        return "No such word in Dictionary"
word = input("enter the keyword:").lower()

output=keyword(word)

if type(output) == list:
    for item in output:
        print(item)
else:
    print(output)


