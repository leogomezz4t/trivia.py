# trivia.py

An easy to use python api wrapper for [Open Trivia DB](https://opentdb.com/api_config.php) with autocaching


**Note:**
There is an request limit of 1 category per request and a max of 50 questions per request


# Installing

Python 3.6 or higher is required

```
pip install trivia.py
```




# Usage

```python
question(parameters)
```

**Parameters:**
- amount (*int*):
    The amount of questions you wish to request, defaults to 10

- category (*int*):
    The category you wish to request from (refer to table below for which number correlates to which category), defaults to `None` returning all categories.

| Int | Category                              |
| --- |:------------------------------------- |
| 0   | All categories                        |
| 1   | General Knowledge                     |
| 2   | Entertainment: Books                  |
| 3   | Entertainment: Film                   |
| 4   | Entertainment: Music                  |
| 5   | Entertainment: Musicals & Theatres    |
| 6   | Entertainment: Television             |
| 7   | Entertainment: Video Games            |
| 8   | Entertainment: Board Games            |
| 9   | Science & Nature                      |
| 10  | Science: Computers                    |
| 11  | Science: Mathematics                  |
| 12  | Mythology                             |
| 13  | Sports                                |
| 14  | Geography                             |
| 15  | History                               |
| 16  | Politics                              |
| 17  | Art                                   |
| 18  | Celebrities                           |
| 19  | Animals                               |
| 20  | Vehicles                              |
| 21  | Entertainment: Comics                 |
| 22  | Science: Gadgets                      |
| 23  | Entertainment: Japanese Anime & Manga |
| 24  | Entertainment: Cartoon & Animations   |

- difficulty (*str*):
    The difficulty of the questions, can be `easy`, `medium`, or `hard`. Defaults to `None` returning all difficulties. 

- quizType (*str*):
    The type of questions, can be `multiple` (multiple choice questions), or `boolean` (true/false questions). Defaults to `None` returning all questions types. 


**Return:**

Return a list of dicts which contains the keys below
- category (*str*):
    The category the question comes from.

- type (*str*):
    The type of question (multiple, or boolean).

- difficulty (*str*):
    The difficulty of the question.

- question (*str*):
    The text of the question.

- correct_answer (*str*):
    The correct answer.

- incorrect_answer (*list*):
    List of strings of all the incorrect answers.




# Examples

**Basic code example**
```python
from trivia import trivia
import asyncio

#To use outside of an async function
loop = asyncio.get_event_loop()
questions = loop.run_until_complete(trivia.question(amount=1, category=2, difficulty='easy', quizType='multiple'))

#To use within an aysnc function
async def main():
    questions = await trivia.question(amount=1, category=2, difficulty='easy', quizType='multiple')
```


**An example of the return**
```python
[{
    'category': 'Entertainment: Books', 
    'type': 'multiple', 
    'difficulty': 'easy', 
    'question': 'What is the title of the first Sherlock Holmes book by Arthur Conan Doyle?',
     'correct_answer': 'A Study in Scarlet', 
     'incorrect_answers': ['The Sign of the Four', 'A Case of Identity', 'The Doings of Raffles Haw']
}]
```
