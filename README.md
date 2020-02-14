# Introduction

This is a project assignment for the undergraduate course Compilers of the Department of Computer Science and
Engineering at the University of Ioannina.
Python3 was used to develop the compiler. For the assembly files MIPS was used.
The programming language that compiles is called Scarlet.

# Scarlet

Scarlet contains.

## • Letters «Α»,...,«Ζ» and «a»,...,«z»

## • Numbers «0»,...,«9»

## • Operators «+», «-», «*», «/»

## • Comparators «<», «>», «=», «<=», «>=», «<>»

## • Assignment «:=»,

## • Separators («;», «,», «:»)

## • Brackets «(»,«)»,«[»,«]»

## • Comments ( /* , */ , // )

![alt text](https://github.com/Peter-Sav/Scarlet-Compiler/blob/master/automaton/automaton1.png)
![alt text](https://github.com/Peter-Sav/Scarlet-Compiler/blob/master/automaton/automaton2.png)
# Reserved words
program, endprogram
declare
if , then , else , endif
while , endwhile , dowhile , enddowhile
loop , endloop , exit
forcase , endforcase , incase , endincase , when , default , enddefault
function , endfunction , return , in , inout , inandout
and , or , not
input , print

# Grammar
![alt text](https://github.com/Peter-Sav/Scarlet-Compiler/blob/master/grammar/grammar1.PNG)
![alt text](https://github.com/Peter-Sav/Scarlet-Compiler/blob/master/grammar/grammar2.PNG)
# Tests

There are some test used during the assignment to make sure everything was working fine. From the parser generator ,
syntax analyzer and final assembly code.
