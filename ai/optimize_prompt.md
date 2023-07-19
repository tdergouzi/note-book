## Optimize Your Prompt



### Principles of Prompting

- Principle 1: Write clear and specific instructions, clear != short
- Principle 2: Give the model time to think



### Principle 1

#### Tractic 1: Use delimiters 

```
Triple quotes: """

Triple backticks: ```

Triple dashes: ---

Angle brackets: < >

XML tags: <tag> </tag>
```



#### Tractic 2: Ask for structured output

HTML, JSON

```python
prompt = f"""
Generate a list of three make-up book titles along \
with their author and genres.
Provided them in JSON format with the following keys:
book_id, title, author, genre.
"""
```



#### Tractic 3: Check whether conditions are satisfied 

Check assumptions required to do the task.

```python
text = "..."

prompt: f"""
You will be provided with text delimited by triple quotes.
If it contains a sequence of instractions, \
re-write those instructions in the following format:

Step 1 - ...
Step 2 - ...
...
Step N - ...

If the text does not contain a sequence of instructions, \
then simply write \"No steps provided.\"

\"\"\"{text}\"\"\"
"""
```



#### Tractic 4:   Few-shot prompting

Give successful examples of completing task. Then ask model to perform the task.

```python
prompt = f"""
Your task is to answer in a consistent style.

<child>: Teach me about patience.

<grandparent>: .....

<child>: Teach me about resilience.
"""
```



### Principle 2

#### Tractic 1:  Specify the steps to complete a task

Step 1: ...

Step 2: ...

 ...

Step N: ...

```python
text: "...."

prompt: f"""
Your task is to perform the following actions:
1 - Summarize the following text delimited by <> with 1 sentence.
2 - Translate the summary into Franch.
3 - List each name in the French summary.
4 - Output a json object that contains the following keys: french_summary, num_names.

Use the following format:
Text: <text to summarize>
Summary: <summary>
Translation: <summray translation>
Names: <list of names in Italian summary>
Output JSON: <json with summary and num_names>

Text: <text>
"""
```



#### Tractic 2: Instruct the model to work out its own solution before rushing to a conclusion

````python
prompt = f"""
Your task is determine if the student's solution is correct or not.
To solve the problem do the following:
- First, work out your own solution to the problem.
- Then compare your solution to the student's solution and evaluate \
if the student 's solution is correct or not. Don't decide if the student's \
solution is correct until you have done the problem yourself.

Use the following format:
...

Question:
```
question content
```

Student's solution:
```
Student's solution content.
```
"""
````



### Model limitations

#### Hallucination

Makes statements that sound plausible but are not true.

Reducing hallucination:

Fist find the relevant information, then answer the question based on the relevant information.