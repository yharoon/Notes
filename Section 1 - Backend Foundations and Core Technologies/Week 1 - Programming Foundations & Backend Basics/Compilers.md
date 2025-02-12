# Overview
- Generally a compiler will translate a file from the programming languages source code to machine code dedicated to that specific machine.
- In doing this, there will be several steps taken by most compilers to do this translation but also optimize and show the developer any errors in the source code, most of the time this is focused on syntax related errors
# Compilation Stages
- There are generally 6/7 stages to compilation;
	1. Lexical Analysis - Tokenizing the Source Code
	2. Syntax Analysis - Checking for grammatical correctness
	3. Semantic Analysis - Ensuring logical correctness
	4. Intermediate Code Generation - Converting Source Code into an Intermediate Representation (IR)
	5. Optimization - Improving the IR for efficiency
	6. Code Generation - Translating IR into Machine Code
	7. Linking - Resolving external dependencies and creating an executable
- Languages may not necessarily do all the steps of compilation of they may have more steps
	- Some language compilers may do direct compilation without an Intermediate Representation
	- Some language compilers may do additional optimizations
# Lexical Analysis
- Lexical Analysis can also sometimes be called the tokenization stage
- It will break down the stream of characters of the source code and split it into individual fragments called lexemes
	- A lexeme is an abstract unit of a specific languages lexical system
	- For example, the code snippet will turn into 5 lexemes;
```java
		String name = "Haroon";
```
- For the above example, the 5 lexemes would be;
	- String
	- name
	- =
	- "Haroon"
	- ;
- After splitting code into lexemes, a sequence of tokens is created, and this sequence of tokens is the final product of lexical analysis
- A lexeme can also be known as an actual string of chars that matches with a pattern and generates a token
- A token is an object that describes a lexeme, usually by assigning each lexeme to a token type such as; Keyword, Identifier, Operator, Delimiters
- Token Types;
	- Most lexers will divide tokens types into 3 categories;
		- Terminal Symbol: Keywords and Operators
		- Literals: Values like numbers and strings
		- Identifiers: Names defined by the user
- A Token can also be described as a "meaningful unit of code"
# Implementation of Lexical Analysis in the C Compiler
- ![[lexical_analysis.jpg]]
- The above diagram is a overview of how a lexical analyser or scanner works
- The scanner will read source code by char and convert it into a token stream, the compiler will then use this token stream for further processing
- Tokens in this case are basically a mapping:
	- **{{Lexeme} -> {Token Type}}** - This is a Token
- The scanner will then also remove whitespaces, comments and detects simple syntax errors like invalid characters
- Implementation wise, the scanner will basically be a finite automata or use regular expressions to define patterns for recognising tokens, outputting recognised tokens in the form of a token stream
# Syntax Analysis
- During this stage, the token stream is used to generate an abstract syntax tree (AST) which represents the logical structure of the program
- In this phase, the compiler is checking for the grammatical and syntactical correctness of the source code, any errors will result in compilation errors
- In general, syntax analysis is responsible for:
	- Checking source code for syntax errors
	- Generating an abstract syntax tree for the next stage to use
# Abstract Syntax Trees
- An Abstract Syntax Tree is a tree that represents the abstract syntactical structure of the source code written in a given programming language
- Each node will denote a construct occurring in the source code
- Often an AST is used as an intermediate representation of the program as it continues the steps of compilation
- For example the syntax tree for (id + id * id) would be;
	- ![[1-200x163.png]] and its abstract syntax tree would follow to be;
	- ![[2-300x164.png]]
# Formalisms of Syntax Analysis
- There are various formalisms to help understand and verify the structure of the source code; for this we need certain key concepts
	- Context Free Grammars
		- CFGs define the syntax rules of a language, they consist of production rules that describe how valid strings (sequences of tokens) are formed
		- CFGs are used to specify the grammar of the language, ensuring that the source code adheres to language syntax