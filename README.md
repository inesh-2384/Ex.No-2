# Ex-2-GENERATION OF LEXICAL TOKENS LEX FLEX TOOL
# AIM
## To write a lex program to implement lexical analyzer to recognize a few patterns.
# ALGORITHM

1.	Start the program.

2.	Lex program consists of three parts.

     a.	Declaration %%

     b.	Translation rules %%

     c.	Auxilary procedure.

3.	The declaration section includes declaration of variables, maintest, constants and regular definitions.
4.	Translation rule of lex program are statements of the form

    a.	P1 {action}

    b.	P2 {action}

    c.	…

    d.	…

    e.	Pn {action}

5.	Write a program in the vi editor and save it with .l extension.

6.	Compile the lex program with lex compiler to produce output file as lex.yy.c. eg $ lex filename.l $ cc lex.yy.c
7.	Compile that file with C compiler and verify the output.
# Program

%{
#include <stdio.h>
#include <stdlib.h>
%}

// Declarations
%option noyywrap

// Regular Definitions
ID      [a-zA-Z][a-zA-Z0-9]*
NUM     [0-9]+
KEYWORD if|else|while|for
OPERATOR [+\-*/=<>]

%%

// Translation rules
{KEYWORD}   { printf("Keyword: %s\n", yytext); }
{ID}        { printf("Identifier: %s\n", yytext); }
{NUM}       { printf("Number: %s\n", yytext); }
{OPERATOR}  { printf("Operator: %s\n", yytext); }
[ \t\n]+    { /* ignore whitespace */ }
.           { printf("Unknown character: %s\n", yytext); }

%%

// Auxiliary procedure
int main() {
    yylex();  // Call the lexer
    return 0;
}

int yywrap() {
    return 1;  // End of input
}

# INPUT

if a < 10
for i = 0

# OUTPUT

Keyword: if
Identifier: a
Operator: <
Number: 10
Keyword: for
Identifier: i
Operator: =
Number: 0


# RESULT
## The lexical analyzer is implemented using lex and the output is verified.
