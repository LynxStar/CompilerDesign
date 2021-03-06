\pagebreak
>TODO : The next step of the compilation process is parsing.  Parsing takes input from the Lexical Analysis step and builds a parse tree, which will be used in future steps to develop the machine code.  In this unit, we will define parsing and identify its uses.  We will also discuss two parsing strategies, Top-Down Parsing and Bottom-Up Parsing, examining what it means to approach parsing from each standpoint and taking a look at an example of each.  By the end of the unit, you will understand parsing techniques with regards to compilers and be able to discuss each of the two main approaches.



<!---
DO NOT REMOVE THIS COMMENT OR TOPICS LISTED HERE.

This section should cover these topics.
It need not be in this order.

Indicate coverage of topics by copying topic lines verbatim into a comment adjacent to the relevant text.
Covered topics appear twice in a file: here and adjacent to the relevant text.
Uncovered topics appear only once in a file (in this comment).

This command checks whether topic lines appear only once in a file.

    ./check.sh uncovered

TOPICS:

3.1 Parsing Overview
3.1.1 Function
3.1.1.1 Input: Tokens from Lexical Analysis
3.1.1.2 Output: Program Parse Tree
3.1.2 Examples
3.1.2.1 Given an Arbitrary Function
3.1.2.2 Produce:
3.1.2.2.1 Parser Input
3.1.2.2.2 Parse Tree
3.1.3 Context-Free Grammar
3.2 Top-Down Parsing
3.2.1 Traversing a Parse Tree
3.2.1.1 Definition
3.2.1.2 Example
3.2.2 Backus-Naur Form Production Rules
3.2.3 LL Parser
3.2.4 Process 
3.2.4.1 Starts at Left-most Symbol Yielded from Production Rule
3.2.4.2 Continues to Next Production Rule for Each Non-Terminal Symbol
3.2.4.3 Proceeds "Down" the Parse Tree
3.3 Bottom-Up Parsing
3.3.1 Bottom-Up
3.3.1.1 Definition
3.3.1.2 Example
3.3.2 Process
3.3.2.1 Identify Terminal Symbols First
3.3.2.2 Combine Terminal Symbol to Produce Nonterminals
-->

Parsing
=======

### 3.1 Parsing Overview
Syntax Analysis also known as parsing is the process of analyzing tokens and
recombining them into a syntax tree. 

#### 3.1.1 Function
Syntax analysis will verify that the input`s syntax is valid. 

##### 3.1.1.1 Input: Tokens from Lexical Analysis
Lexical analysis splits input into tokens which the syntax analyzer then
recombines into a syntax tree.

##### 3.1.1.2 Output: Program Parse Tree
Recombining of a syntax parse tree during lexical analysis is done according  to
the syntax specification. The leaves of the parse tree are the tokens generated
during lexical analysis.

#### 3.1.2 Examples

##### 3.1.2.1  Given an Arbitrary Function

##### 3.1.2.2 Produce:

###### 3.1.2.2.1 Parser Input

###### 3.1.2.2.2 Parse  Tree

#### 3.1.3 Context-Free Grammar

### 3.2 Top-Down Parsing

#### 3.2.1 Traversing a Parse Tree

##### 3.2.1.1 Definition

##### 3.2.1.2 Example

#### 3.2.2 Backus-Naur Form Production Rules

#### 3.2.3 LL Parser

#### 3.2.4 Process

##### 3.2.4.1 Starts at Left-most Symbol Yielded from Production Rule

##### 3.2.4.2 Continues to Next Production Rule for Each Non-Terminal Symbol

##### 3.2.4.3 Proceeds "Down" the Parse Tree

### 3.3.1 Bottom-Up Parsing

##### 3.3.1.1 Definition

##### 3.3.1.2 Examplel

#### 3.3.2 Process

##### 3.3.2.1 Identify Terminal Symbols First

##### 3.3.2.2 Combine Terminal Symbol to Produce Nonterminals


### What is a context-free language?
A language generated by [context-free grammar](#what-is-a-context-free-grammar).

### What is a context-free grammar?
A context-free grammar is a [formal grammar](#what-is-a-grammar) in which:

- The left-hand side of every [production](#what-is-a-production) is a single [nonterminal](#what-is-a-nonterminal) symbol.
- The right-hand side of every production is a sequence of terminals and nonterminals.
If the sequence is empty, as in $A \to \epsilon$, the nonterminal [derives](#what-is-a-derivation) the empty string.

#### Examples
This grammar is [context-free](#what-is-a-context-free-grammar), but [improper](#what-is-an-improper-context-free-grammar), because it is impossible to derive B into just terminal symbols.
$B \to hB$

This grammar is [context-free](#what-is-a-context-free-grammar) and [regular](#what-is-a-regular-grammar) (it matches `h*`).
$B \to hB$
$B \to \epsilon$

This grammar is [context-free], but not [regular](#what-is-a-regular-grammar), since it has [left-recursion](#what-is-left-recursion) (it matches balanced parentheses).
$S \to S (S)$
$S \to \epsilon$

#### Follow-up questions

- [How can you tell if a language is context-free](#how-can-you-tell-if-a-language-is-context-free)?
- [Is English context-free](http://cs.haifa.ac.il/~shuly/teaching/08/nlp/complexity.pdf)?
- [When a language is context free, do terminals have only one meaning](#what-are-the-implications-of-chomskys-hierarchy)?
- [Is infinite recursion allowed in context-free grammars](#what-is-left-recursion)?

### How can you tell if a language is context-free?
A language is context-free if it follows context-free grammar. In context-free language, the left side is always single nonterminal producing rules of the form "'<A>' ::= a", such as '<expression>' ::= '<expression>'*<term>. The right side is sequence of terminal and non-terminal symbols. "*" is non-terminal symbol.

So, a context-free language should always form "'<A>' ::= a" where left side is always single non terminal symbol.

The authenticity of a context free language can be determined by a mathematical property known as the pumping lemma that all context free languages have.
A language L would be considered context free if an integer pumping length q >= 1 exists so that any string t in L with |t| >= q can be defined as

	t = jmacs

where t is split into the substrings j, m, a, c, and s under the following conditions.

	a.
|mac| <= q
	b.
|mc >= 1|
	      n  n
	c.
jm^ a^ cs is in the language L for every n

These proofs may be tested against any language in contempt of questionable context.
All conditions stated above must be met in order for a grammar to be considered context free.


A grammar is context-free if left-hand sides of all productions contain exactly one non-terminal symbol.

### What is left recursion?

Left recursion is defined as a grammer set where the nonterminal starting symbol will eventually derive itself back to its original form with the starting symbol as the the left-symbol.
For example:

	Z -> Zy|e

### What is the difference between a regular language and a context free language?

[Formal regular expressions](#what-is-a-regular-expression) define [regular languages](#what-is-a-regular-language),
and can be accepted by [deterministic and non-deterministic](#what-is-the-difference-between-deterministic-and-nondeterministic) [finite state machines](#what-is-a-finite-automaton).
Regular languages also do not accept arbitrary nesting, like [recursion](#what-is-recursion).
[Context-free grammars](#what-is-a-context-free-grammar) define context-free languages, and can be accepted by [pushdown automata](#what-is-a-pushdown-automaton) 

#### Example:

- The [language](#what-is-a-language) of balanced parentheses is context-free, but not regular.
Thus, it is impossible to construct a regular expression (but possible to construct a context-free grammar) that matches balanced parentheses.

### What is a derivation?

A derivation refers to the way the syntax of a grammar is broken down to create sentence structures based on the rules of the grammar.


Add examples


### What is a leftmost derivation?

The process of determining a leftmost derivation involves replacing the left hand non-terminal for each step of derivation until all nonterminals have been used.

	Grammar		Derivation

	J -> J M	J
	J -> M		J M
	M -> 5		J M M
	M -> 6		M M M
	M -> 7		6 M M
	M -> 8		6 7 M
	M -> 9		6 7 8

### What is a rightmost derivation?

The process of determining a rightmost derivation involves replacing the right hand non-terminal for each step of derivation until all nonterminals have been used.

	Grammar		Derivation
			
	J -> J M	J
	J -> M		J M
	M -> 5		J 5
	M -> 6		J M 5
	M -> 7		J 6 5
	M -> 8		M 6 5
	M -> 9		7 6 5

### What is an ambiguous grammar?

An ambiguous grammar exists if a string has multiple possible outcomes of its leftmost derivation. That is, the grammar would yield more than one parse tree when determining the outcome of the grammar's derivation. When it comes to compiler interpretation, it must be determined whether or not a string has been declared or not within the scope of the program. There isn't always a correct choice for a compiler to pick when it is processing a language with an ambiguous grammar structure.

Given the ambiguous grammar, two different means of derivation are shown.
    
    X -> X + X|x
      
    X -> X + X          X -> X + X
      -> x + X            -> X + X + X    
      -> x + X + X        -> x + X + X
      -> x + x + X        -> x + x + X
      -> x + x + x        -> x + x + x
    
If there exists a string which can be generated by the grammar in more than one way the grammar is said to be ambiguous. An example of this is
if the grammar has more than one leftmost derivation it is ambiguous.

### What is a LL(k) grammar?
 
A LL(k) grammar parses sentences from the top down in left to right order of input without returning backwards. The (k) refers to an incoming number of k token strings that the parser is able to take into consideration as it determines rules. Every step of derivation must be already be defined in the grammar's parse tree and k tokens for it to be LL(k) grammar.


### What is a LR(k) grammar?

A LL(k) grammar parses sentences from the bottom up in left to right order of input without returning backwards, and results in a reversed rightmost derivation. Like LL(k) grammars, the (k) refers to a number of k lookahead input as it parses symbols appearing earlier than k.

### What is Backus-Naur Form?
<!--3.2.3 LL Parser Kyle Cantrell-->

A BNF specification is a set of derivation rules, written as

 '<symbol> ::= __expression__'

where '<symbol>' is a nonterminal, and the '__expression__' consists of one or more sequences of symbols; more sequences are separated by the vertical bar, '|', indicating a choice, the whole being a possible substitution for the symbol on the left.
Symbols that never appear on a left side are terminals.
On the other hand, symbols that appear on a left side are non-terminals and are always enclosed between the pair <>.

The '::=' means that the symbol on the left must be replaced with the expression on the right


### LL Parser
The LL Parser is a top-down parser that works on some context free grammars. 

The basic operation needs three things:
	* An input buffer to hold the code to be parsed
	* A stack structure to store the terminal and non terminal symbols (See above for explanation of terminal and non terminal symbols)
	* A parsing table which might contain rules such as identifier syntax and reserved words to interpret the next token on the stack

As an aside, LL parsers become LL(k) parsers for k amount of lookahead tokens.

Example: Consider an LL(1) Parser (The first L tells us that this parser is starting at the Leftmost point, the second L tells us that it does Leftmost derivation and the (1) tells us we are using two tokens of lookahead)

Let the following grammar below represent a context free grammar:
	S => a | aS | bS
	
	or
	
	1. S => a
	2. S => aS
	3. S => bS
	
	Example Strings:
	a;
	aa;
	aabaa;
	aaaaba;
	baaaaa;
	bababa;
	For our purposes, let us demonstrate an LL(1) Parser on the string "bababa".
	
	Now an LL(1) Parser table for this string would look like this:
	-------------------------------
	Non-terminal | a | aS | bS | $
	-------------------------------
	       S     | 1 |  2 |  3 | -
	-------------------------------
	
	Note that the special symbol $ denotes the end of the input.
	
	What the table says is simply that for our non terminal symbol "S" we have three terminal symbols and the special terminator symbol $. The numbers in each of the columns correspond to the production rules stated above.
	
	The stack sequence for our string "bababa" is as follows:
	[b,a,b,a,b,a,$]
	
	The first step for the parser is to look at the input symbol "b" and the stack-top symbol S. Since "b" is the input symbol, the parser compares that to the stack-top symbol S,
	and since the rule for "b" is to replace "b" with "bS", the stack now becomes:
	[b,S,a,b,a,b,a,$]
	
	
	Since the input symbol "b" did not match the stack-top symbol S, the "b" is put as the stack-top symbol and not processed further in the first step. Had it been a match, we would further
	process the terminal symbol as defined by the production rules (for example if the first symbol was S, we could have applied any of the three rules producing a stack
	of [a,a,b,a,b,a,$] or [a,s,a,b,a,b,a,$]).
	
	This yields a Nonterminal stack of:
	[b,S,S,$]
	
	The second step now process the "b" and since the second token is now "S" (the stack-top symbol), the b is removed because the stack-top symbol is "b"
	and the S is removed because the third rule states that "S" can produce "bS" which is the current top of the stack, leaving the stack to look like:
	[a,b,a,b,a,$]
	and the output stream writes rule #3:
	[3]
	with the Non terminal stack becoming:
	[S,$]
	
	
	The third iteration continues on and processes the input character "a". Now since we have two production rules with "a" listed, the parser has a choice. Also, our parser 
	only has a lookahead of 1. We will assume the parser is lazy and takes the rules sequentially, so our production rule on the input symbol "a" will be refactored by rule 1 which is
	simply "a". Again the input symbol and stack-top symbol do not match so the "a" is not removed yet but is refactored as so by rule 1 and the stack-top symbol becomes "a":
	[a,b,a,b,a,$]
	with the Nonterminal stack:
	[a,S,$]
	
	Now because "a" is the current stack-top symbol, the parser removes it leaving the stack as:
	[b,a,b,a,$]
	The nonterminal stack:
	[S,$]
	and writing rule #1 to the output stream:
	[3,1]
	
	
	Again our input symbol is "b" so we process as we did in the first and second iteration. For brevity's sake I will keep it shorthand:
	
	current stack:
	[b,a,b,a,$]
	
	"b" does not match current stack-symbol S, so we push "b" onto the stack and refactor:
	[b,S,a,b,a,$]
	Non terminal stack:
	[b,S,S,$]
	
	We process again and since the next two symbols match, the third rule is written to the output stream and the stack becomes:
	[a,b,a,$]
	Non terminal stack:
	[S,$]
	With the output stream becoming:
	[3,1,3]
	
	And again we encounter "a" as our terminal input symbol and process as we did in the third and fourth iteration:
	
	current stack:
	[a,b,a,$]
	current non-terminal stack:
	[S,$]
	
	"a" does not match "S" so the parser pushes "a" onto the Non-terminal stack:
	[a,S,$]
	
	After the Non-terminal stack is resituated, we re-evaluate, and because the Non-terminal stack and input stack match, we remove the "a", write output rule #1 and process the current stack:
	[b,a,$]
	[3,1,3,1]
	
	As you can see where this is going, I'll sum up the next two. 
	[b,a,$] => [3,1,3,1,3]
	[a,$]	=> [3,1,3,1,3,1]
	
	Once our parser reaches the special terminator character, it knows it has done it's job and is done. 
	It's important to note that had we instead chosen rule #2 to replace A, it would have produced the same output. In fact, it would be a good excercise to prove this result
	yourself.
	Excercises
	1. Given the same grammar and production rules, what would be the output stream produced by an LL(1) parser for the string "aabaa"?
	2. If we added a production rule S => acS, what would the parse table and output stream be for the string "aaacaca"?
	
	
	
	
	
	
	
	

### What is a pushdown automaton?
A pushdown automaton (PDA) is a finite state machine with [stack](#what-is-a-stack) memory.

It manipulates a stack by choosing an indexing variable within the stack, a current state, and a symbol at the top of the stack.


> TODO: It'd be nice to have a picture of a pushdown automaton, in a vector format such as SVG.

### What is a deterministic pushdown automaton?

Deterministic pushdown automaton is a linear pushdown automaton where all future operations and stack combinations are known as soon as parsing has begun. Operarations are only performed on the head of the stack, as the order of the stack is "pushed down" in its determined order as it is processed and parsed. Grammars accepted by deterministic pushdown automatons must not be ambiguous, since DPDA's only have one possible action at all times, and not all context free languages can be used unless they are simplified.

### What is a nondeterministic pushdown automaton?

A nondeterministic pushdown automaton will always have a variety of possible outcome for any instance of its input on a stack. NPDAs are capable of handling any context-free grammar and will create multiple branches to test all output possibilities. Some specific instances may even yield multiple outcomes. To handle instances like this, the automaton makes use of backtracking for the most efficient results. Nondeterministic pushdown automatons are slower than deterministic pushdown automatons, because they are capable of handling more complex inputs.

### What is a parser?
A parser:
- Checks for [syntax errors](#what-is-a-syntax-error)
- Constructs a [parse tree](#what-is-a-parse-tree) or an [abstract syntax tree](#what-is-an-abstract-syntax-tree).

Typically, a [scanner](#what-is-a-scanner) first [tokenizes](#what-is-tokenization) the source code into a [token](#what-is-a-token) [sequence](#what-is-a-sequence) that the parser reads as input.
However, scanner-less parsers work directly with source code as input.

Parsers do not [produce assembly or object code](#what-is-code-generation).

Follow ups:
- [How do parsers work](#how-do-parsers-work)?

### What is a syntax error?

Syntax of a language is the rule that determines what is allowed in that language. It specifies how a program can be written using statements, loops and functions etc. This rule also applies to how different types of such loops, statements and functions are constructed. Basically, syntax of a programming language is a vocabulary of that language. A syntatically correct program can be sucessfully compiled and interpreted to a machine language. Therefore, a syntatically incorrect program cannot be compiled and they are supposed to have syntax errors. Syntax errors are errors in the structure of the language. When writing a program, if syntax of the language is not followed, the program will have syntax error.

For e.g, in java programming language, semicolon(;) is required at the end of every statement. If semicolon is not typed after every statement in java, you will get a syntax error while trying to compile your program. Let's see this in the real statement in java. Let's say, a programmer wants to display "Hello World!" in his monitor using java programming language.

    System.out.println("Hello Word!");

This statement displays "Hello Word!" in the monitor without quotations when executed even though programmer meant to type "Hello World!". This is syntatically correct statement and will compile without any error.

    System.out.println("Hello World!")

In the second example, the program will get syntax error even though "Hello World!" is typed correctly. As we can see, the programmer forgot to type semicolon at the end of the statement. In java, semicolon at the end of the statement is part of its syntax. Hence, a program that doesn't follow the syntax of the language will get a compilation error as the program contains syntax error/s. So, A programmer has to have a detail knowledge of the syntax of the language to be expert in that programming language.

A parser first tokenizes the source code depending on its syntax.
It takes the structure of the code and uses said tokens to convert it to object code.
After evaluation it will convert it to ASM code if there are no syntax errors.

### What is a parse tree?

A parse tree for a grammar G is a tree where

- The root is the start symbol for G
- The interior nodes are the nonterminals of G
- The leaf nodes are the terminal symbols of G.
- The children of a node T (from left to right) correspond to the symbols on the right hand side of some production for T in G.


Every terminal string generated by a grammar has a corresponding parse tree; every valid parse tree represents a string generated by the grammar (called the yield of the parse tree). 

### How do parsers work?
