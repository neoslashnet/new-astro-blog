---
title: "I Created a Magic 8 Ball in Python"
pubDate: 2024-01-31
intro: Magic 8 ball app in Python.
author: dg
tag: Python
image: ../../assets/python.jpg
---

I am doing a Python course that requires hands-on projects vs. watching training videos. Below is a "Magic 8 Ball" app I made based on a project that required elif statements.

I added the answers to a list and reworked it a little bit. Below is the code. Check it out!

```python
import random

answers = [
    "Yes, definitely",
    "It is decidedly so",
    "Without a doubt", 
    "Reply hazy, try again",
    "Ask again later",
    "Better not tell you now", 
    "My sources say no",
    "Outlook not so good",
    "Very doubtful"
]

name = input("What's your name: ")

question = input("Ask your question: ")

random_index = random.randint(0, len(answers) - 1)
random_answer = answers[random_index]

print(name + " asks: " + question) 
print("Magic 8 Ball's answer: " + random_answer)
```
