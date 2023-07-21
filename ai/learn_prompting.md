# Learn Prompting



> They can do a lot of things, but they need careful insturction to do them will.

Note from the document [Learn Prompting](https://learnprompting.org/docs/intro).



## Basics

### Giving Instructions

One of the simplest prompting methods is just giving instructions (sometimes called intrucstion prompting).

Instruction Prompting Exmaple:

```
Read the following sales email. Remove  any personally identifiable information (PII), and replace it with the appropriate placeholder. For example, replace the name "John Doe" with "[NAME]".

Hi John,

I'm writing to you because I noticed you recently purchased a new car. I'm a salesperson
at a local dealership (Cheap Dealz), and I wanted to let you know that we have a great deal on a new
car. If you're interested, please let me know.

Thanks,

Jimmy Smith

Phone: 410-805-2345
Email: jimmysmith@cheapdealz.com
```

The response on the first time:

```
Hi [NAME],

I'm writing to you because I noticed you recently purchased a new car. I'm a salesperson
at a local dealership (Cheap Dealz), and I wanted to let you know that we have a great deal on a new
car. If you're interested, please let me know.

Thanks,

Jimmy Smith

Phone: [PHONE]
Email: [EMAIL]
```

The response is absolutely not correct, the "Cheap Dealz" should be replace with "[DEALERSHIP]" and the "Jimmy Smith" should be replace with "[SALESPERSON]".



### Role Prompting



#### Styling Text

Role prompting is most often used to style text. It involves asking the AI to pretend to be a certain person, or act in a certain way, modifying how it writes based on the assigned role. This can be used to change the tone, style, and even the depth of the information presented.



**Food Review Example**

```
Write a review of [pizza place]
```

Assumes the role of a food critic.

```
You are food critic writing for the Michelin Guide. Write a review of [random pizza place].
```



#### Improveing Accuracy

The accuracy of the output can be improved.

```
You are a brilliant mathematician who can solve any problem in the world.
Attempt to solve the following problem:

What is 100*100/400*56?
```

This is better than `What is 100*100/400*56?`.



### Few Shot Prompting

Few shot prompting is basically just showing the model a few examples (call shots) of whta you want it to do.

```
Great product: positive
Didn't work very well: negative
Super helpful, worth it: positive
The product can be better:

=========================Response=========================
negative
```



#### More on structure

A key use case for few shot prompting is when you need the output to be **structured in a specific way** that is difficult to describe to the model.



#### Variants of shot prompting

Variants:

- 0 shot prompting: no examples are shown to the model
- 1 shot prompting: 1example is shown to the model
- few shot prompting: 2+ examples are shown to the model



### Formalizing Prompts

There are a few different parts of a prompt: 

- Context
- A role
- An instruction
- A question
- Examples (few shot)



Formalied prompt:

- Role
- Instruction
- Exampls
- Context
- Question



### Pitfalls of LLMs

- Citing Source: LLMs for the most part cannot accurately cite sources.
- Bias: LLMs are often biased towards generating stereotypical responses.
- Hallucinations: Generate falsehoods frequently when asked a question that they do not know.
- Math
- Prompt Hacking: Users can often trick LLMs into generating any content they want.



## Prompt Hacking

Prompt hacking is a term used to describe a type of attack that exploits the vulnerabilityies of LLMs, by manipulating their inputs or prompts.

Three types of prompt hacking:

- prompt injection: Involves adding malicious or unintended content to a prompt to hijack the language model's output.
- prompt leaking: Involves extracting sensitive or confidential information from the LLM's response.
- jailbreaking: Involves bypassing safety and moderation features.



### Prompt Injection
