# Text Preprocessing in Natural Language Processing
> **Author: Mason Swanson**

## What is tokenization
When reading natural language into a computer program, it immediately becomes necessary to identify the boundaries between words. The simple text—"the boy kicked the ball"—can be split into into "the" "boy" "kicked" "the" "ball" by choosing to use space as a delimiter.
```python
>>> alep = "the boy kicked the ball".split(" ")
>>> alep
['the', 'boy', 'kicked', 'the', 'ball']
```
This is effective for cases where all of your text is separated by spaces, with no other punctuation, and where capitalization matters. We can see the frequency of each word using some form of counter:
```python
>>> from collections import Counter
>>> Counter(alep)
Counter({'the': 2, 'boy': 1, 'kicked': 1, 'ball': 1})
```
Unfortunately, this simple approach does not work in more complicated examples
```python
>>> bet = """Yes or no isn’t null; yes it is; no, I don't know    
Yes or no? Isn't it a silly question? Ask it anyway, 'cause""".split(" ")
>>> bet
['Yes', 'or', 'no', 'isn’t', 'null;', 'yes', 'it', 'is;', 'no,', 'I', "don't", 
 'know\nYes', 'or', 'no?', "Isn't", 'it', 'a', 'silly', 'question?', 'Ask',
 'it', 'anyway,', "'cause"]
>>> Counter(bet)
Counter({'it': 3, 'or': 2, 'Yes': 1, 'no': 1, 'isn’t': 1, 'null;': 1, 'yes': 1,
         'is;': 1, 'no,': 1, 'I': 1, "don't": 1, 'know\nYes': 1, 'no?': 1, 
         "Isn't": 1, 'a': 1, 'silly': 1, 'question?': 1, 'Ask': 1, 
         'anyway,': 1, "'cause": 1})
```
The counter is differentiating between `Yes` and `yes`, and it's not separating `know` and `yes` in `know\nYes`. It's also creating different counts for `no`, `no,` and `no?`.

We can force the text to be all uppercase or lowercase, and we could add more separators, but this quickly becomes complicated. 

> ### How?
> Typically, an apostrophe character is used in computer text as either a single quote or an apostrophe. Take this example sentence:
>
>  > He said 'don't don that t-shirt' to Don-who was doing dishes.
> 1. If we normalized capitalization, we would be unable to differentiate between don (to put on) and Don (nickname for Donovan).
>    - This can sometimes be ignored, but it can be a problem in languages like Turkish where the capital form of i is İ, and the lowercase form of I is ı. Kir means "dirt" but Kır means "countryside".
> 2. If we added punctuation to the list of separators, we wouldn't have to worry about the single quotes merging into the words `don't` or `t-shirt` or the hypen merging `Don-who`, but we'd end up splitting `don't` into `don` and `t`, and `t-shirt` into `t` and `shirt`.

Thankfully, computational linguists have created tools for assisting with these problems. 


## What is Stemming?
> *My \*knowing\* of the Art as humans \*know\* it is limited. But I \*know\* enough. I will teach you its ways.*
>
> -- Planescape Torment

The words argue, argued, argues

## What is Lemmatization?
Let's take a large step back from the world of programming and think about language. Grab a dictionary, and you'll find that there's usually one entry that unites all of the forms of a word

> ![image](/images/dictionary.png)
>
> *This dictionary has an entry for the word **muscle**, but no separate entries for **muscle<ins>s</ins>**, **muscle<ins>d</ins>**, or **muscl<ins>ing</ins>**.*

The group of words that an entry unites is called a **lexeme**, and the word chosen for that entry is called the **lemma**. In the above dictionary entry, *muscle* is the lemma for the lexeme which includes the forms muscles, muscled, muscling.

If you're familiar with the English language, you'll know that not all