# Text Preprocessing in Natural Language Processing
> **Author: Mason Swanson**

## What is tokenization
When reading natural language into a computer program, it immediately becomes necessary to identify the boundaries between words. The simple text—"the boy kicked the ball"—can be split into into "the" "boy" "kicked" "the" "ball" by choosing to use space as a delimiter.
```python
>>> "the boy kicked the ball".split(" ")
['the', 'boy', 'kicked', 'the', 'ball']
```

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