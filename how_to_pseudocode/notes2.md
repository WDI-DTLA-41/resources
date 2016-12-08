# Programming is Articulated Problem Solving
 ![Flow Chart](https://media2.wnyc.org/i/620/951/c/80/1/FlowchartReal_1.jpg)
 

#### What is Programming? 
**Programming is writing instructions for a machine to follow.** It is a langugage-based discipline that involves translating your ideas into "machine-readable" form. In this course you'll use several high-level languages that are very similar to English. Good programmers write code that is easy to read by humans as well as machines.

**Programmers take a well-defined idea and turn it into code.** This course will teach you how to build full-stack applications, so that means you'll learn how to write code to build applications that connect clients, servers, and databases. But before building anything, you have to develop a well-defined idea of what it is that you want to build. 

**Programming is problem solving.** An algorithm is a set of steps that solves a problem. Think "recipe". Every program you write is an algorithm for a computer to follow. Solve problems away from the computer. Spend as little time programming as possible. You'll write your programs faster if you know exactly what you want to do before you try to do it. Use pencils, pens, paper, and talking to form sketches of your soultions.

#### What is Pseudocode? 
Psuedocode is : "an informal high-level description of the operating principle of a computer program or other algorithm. It uses the structural conventions of a programming language, but is intended for human reading rather than machine reading." -wikipedia https://en.wikipedia.org/wiki/Pseudocode 

Activity 

#### Write Instructions for Common Procedures
 - Mailing a letter 
 - Calculate an average of five test grades
 - Making a hot dog

<!-- You may have left out some details like "how does a letter go from the mail box to my door?" 
Those details are "abstracted" from us 

#### What is abstraction?

1. Removed from the concrete. The generic idea. Platonic forms.
2. Information-hiding. The more commonly used definition in computer science.
 -->
 
#### What is the Problem Solving Process?

1. **Understand the Problem**
    -What are you trying to do? 
    -What are your problem constraints?
    
2. **Pick a Problem Solving Method/Tool**
    -How will you break your solution into manaegable chunks?
    -How will you model your solution?
    -How will you "order" the steps of your solution? 
    
3. **Solve the Problem**
    -Write the algorithm. Remember: This is a set of instructions. Order matters. Ambiguity is bad. Verbosity is confusing. Communication is key.
    -"Run" the algorithm
    
4. **Test your Solution**
    -Does your solution/code work?
    -If it worked, what would you expect to happen?
    -How do you know it works? Did you write well-defined tests? 
    -Repeat previous steps if needed. Re-evaluate your understanding of the problem. 
    
5. **Optimize Your Solution**
    -Can you cut out unnecessary steps/"work"?
    -Can you say the same thing, but better?
    -Could feedback improve your results?
 

#### Programming Instructions (Control Structures)
What types of instructions can you give a machine?

#### Imperative Statement (assignment, artithmetic, console.log, etc.)
"Do this." 

#### Conditional Statement (if statements, switch statments, decisions)
"Do this *sometimes*."

#### Repetition Statement (loops, while statements, for statements)
"Do this *many* times."

#### Subtask (Function/Method/Module)
"Do this *collection of statements*."

# Applying PseudoCode to a problem 


### Steps to create Pseudocode
- Write out the problem or scenario
- Identify nouns, verbs and actions that repeat
- Breakdown logic into a single loop or decision
- Write actions sequentially 
- Any actions showing a dependency are to be indented

Example:

```
Count how many times a given letter appears in a word. 
```

```
set a counter to 0
set a word to "Log Lady"
set a chosen letter to "L"
    
for each letter in the word 
    if the letter is the chosen letter
        increment the counter 

print the counter 
```


```js
// set a counter to 1
var counter = 0;
var chosenLetter = "L"
// pick a word 
var word = "Log Lady"
// for each letter in the word 
word.forEach(function(letter){
// if the letter is L 
   if ( letter === chosenLetter ) {
// increment the counter 
        counter++;
   }
});
// print the counter
console.log( counter );
```


## Let's try it
Write a Folding Your Laundry algorithm using all 4 types of programming control structures


