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

\&lt;program\&gt;                 ::=   **program** id \&lt;block\&gt; **endprogram**

\&lt;block\&gt;                 ::=  \&lt;declarations\&gt;  \&lt;subprograms\&gt;  \&lt;statements\&gt;

\&lt;declarations\&gt;                ::=  ( **declare**  \&lt;varlist\&gt; ; )\*

\&lt;varlist\&gt;                 ::=  ε | id ( , id )\*

\&lt;subprograms\&gt;         ::=  ( \&lt;subprogram\&gt; ) \*

\&lt;subprogram\&gt;                ::=   **function**  id  \&lt;funcbody\&gt;   **endfunction**

\&lt;funcbody\&gt;                ::=  \&lt;formalpars\&gt;  \&lt;block\&gt;

\&lt;formalpars\&gt;                 ::=  **(** \&lt;formalparlist\&gt;**)**

\&lt;formalparlist\&gt;         ::=  \&lt;formalparitem\&gt;  ( , \&lt;formalparitem\&gt; )\* | ε

\&lt;formalparitem\&gt;         ::=   **in** id | **inout** id | **inandout** id

\&lt;statements\&gt;         :        :=  \&lt;statement\&gt;  ( ; \&lt;statement\&gt; )\*

\&lt;statement\&gt;                 ::=  ε |

\&lt;assignment-stat\&gt; |

\&lt;if-stat\&gt; |

\&lt;while-stat\&gt; |

\&lt;do-while-stat\&gt; |

\&lt;loop-stat\&gt; |

\&lt;exit-stat\&gt; |

\&lt;forcase-stat\&gt; |

\&lt;incase-stat\&gt; |

\&lt;return-stat\&gt; |

\&lt;input-stat\&gt; |

\&lt;print-stat\&gt;

\&lt;assignment-stat\&gt;         ::=  id **:=** \&lt;expression\&gt;

\&lt;if-stat\&gt;                 ::=   **if**   **(**\&lt;condition\&gt;**)**   **then**  \&lt;statements\&gt;  \&lt;elsepart\&gt;   **endif**

\&lt;elsepart\&gt;                 ::=  ε | **else** \&lt;statements\&gt;

\&lt;while-stat\&gt;                 ::=   **while**  **(**\&lt;condition\&gt; **)**  \&lt;statements\&gt;   **endwhile**

\&lt;do-while-stat\&gt;        ::=   **dowhile**  \&lt;statements\&gt;   **enddowhile**  **(** \&lt;condition\&gt; **)**

\&lt;loop-stat\&gt;                ::=   **loop**  \&lt;statements\&gt; **endloop**

\&lt;exit-stat\&gt;                 ::=   **exit**

\&lt;forcase-stat\&gt;                ::=   **forcase**

( **when**  **(** \&lt;condition\&gt; **)**  : \&lt;statements\&gt; )\*

**default** : \&lt;statements\&gt; **enddefault**

        **endforcase**

\&lt;incase-stat\&gt;                ::=   **incase**

                                ( **when**  **(** \&lt;condition\&gt; **)**  :  \&lt;statements )\*

                              **endincase**

\&lt;return-stat\&gt;                 ::=   **return** \&lt;expression\&gt;

\&lt;print-stat\&gt;                 ::=   **print** \&lt;expression\&gt;

\&lt;input-stat\&gt;                 ::=   **input** id

\&lt;actualpars\&gt;                 ::=  **(**\&lt;actualparlist\&gt; **)**

\&lt;actualparlist\&gt;         ::=  \&lt;actualparitem\&gt; ( , \&lt;actualparitem\&gt; )\* | ε

\&lt;actualparitem\&gt;         ::=   **in** \&lt;expression\&gt; | **inout** id | **inandout** id

\&lt;condition\&gt;                 ::=  \&lt;boolterm\&gt;  ( **or**  \&lt;boolterm\&gt; )\*

\&lt;boolterm\&gt;                 ::=  \&lt;boolfactor\&gt;  ( **and**  \&lt;boolfactor\&gt; )\*

\&lt;boolfactor\&gt;                 ::=   **not**  **[**\&lt;condition\&gt; **]**  |  **[**\&lt;condition\&gt; **]**|

\&lt;expression\&gt;   \&lt;relational-oper\&gt;   \&lt;expression\&gt;

\&lt;expression\&gt;                 ::=  \&lt;optional-sign\&gt;  \&lt;term\&gt;  ( \&lt;add-oper\&gt;  \&lt;term\&gt;)\*

\&lt;term\&gt;                 ::=  \&lt;factor\&gt;  ( \&lt;mul-oper\&gt;  \&lt;factor\&gt; )\*

\&lt;factor\&gt;                 ::=  constant  |   **(**\&lt;expression\&gt; **)**   |   id  \&lt;idtail\&gt;

\&lt;idtail\&gt;                 ::=  ε  |  \&lt;actualpars\&gt;

\&lt;relational-oper\&gt;         ::=   **=**  | **\&lt;=** | **\&gt;=** | **\&gt;** | **\&lt;** | **\&lt;\&gt;**

\&lt;add-oper\&gt;                 ::=   **+**  |   **-**

\&lt;mul-oper\&gt;                ::=   **\***  |   **/**

\&lt;optional-sign\&gt;        ::=  ε  | \&lt;add-oper\&gt;
# Tests

There are some test used during the assignment to make sure everything was working fine. From the parser generator ,
syntax analyzer and final assembly code.
