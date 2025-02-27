# Lexical Analysis (Lexing)

Lexical analysis is the first stage of compilation, where the source code is broken down into tokens.

## What I've Learned

* **Manual Tokenization:** I practiced manually breaking down code snippets into tokens.
* **Regular Expressions:** I used regex to define patterns for identifiers, numbers, and operators.
* **Simple Lexer Implementation:** I wrote a Python script to implement a basic lexer.

## Python Lexer Example

```python
import re

def lexer(code):
    tokens = []
    patterns = [
        ('IDENTIFIER', r'[a-zA-Z_][a-zA-Z0-9_]*'),
        ('INTEGER', r'\d+'),
        ('OPERATOR', r'[+\-=><()]'),
        ('STRING', r'"[^"]*"'),
        ('WHITESPACE', r'\s+'),
    ]
    combined_pattern = '|'.join('(?P<%s>%s)' % pair for pair in patterns)
    for match in re.finditer(combined_pattern, code):
        token_type = match.lastgroup
        token_value = match.group(token_type)
        if token_type != 'WHITESPACE':
            tokens.append((token_type, token_value))
    return tokens

code = "result = a + 10; if (count > 0) { print(\"Positive\"); }"
print(lexer(code))


**3. `parsing.md` (Syntactic Analysis)**

```markdown
# Syntactic Analysis (Parsing)

Parsing is the second stage, where tokens are organized according to grammar rules.

## What I've Learned

* **Parse Trees:** I drew parse trees to visualize the structure of expressions.
* **BNF Grammar:** I wrote BNF grammar rules for simple expressions.
* **Recursive Descent Parser:** I implemented a basic recursive descent parser in Python.

## Parse Tree Example

     S
    / \
   NP  VP
  / |   | \
Det N   V  NP
|   |   | / | \
The cat saw Det N
            |   |
           a   dog
		  
 "The cat saw a dog." 

## Recursive Descent Parser Snippet

(Include a snippet of your recursive descent parser code here)

## Next Steps

* Implement parsers for more complex grammar rules.
* Explore parser generators like Yacc.