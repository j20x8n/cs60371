java c
Systems and   Networks
COMPSCI 4043
December 2022
1.          (a)             Express the following   in   16-bit two’s   complement   representation,   giving   your   answers   in   hexadecimal.   Show your working.
i.                      1000                    ii.                     -2000                          [4]
(b)          Recall that   a   sign-and-magnitude   code   represents   integer values   by   using   the   most   significant   bit   to   indicate the sign, and the   remaining   bits to   hold the   magnitude   (or   size)   of the   number. Thus         $8002   is -2, while $0002   is +2,   and   soon.
Write a commented Sigma16   program to   convert a   variable, x,   containing   a   16-bit   integer value   in   sign-and-magnitude form,   into to a two’s complement value stored   in   another variable   y. Thus $8001   (sign and   magnitude code for -1) should turn   into   $FFFF   (two’s   complement   code   for   -1)   and soon. Assume that x will   never contain the anomalous   sign-and-magnitude   code   for “negative zero”   ($1000) so you do   not   need to   check for   this.      [5]
(c)             Write a Sigma16   program to   read a   16-bit variable x,   swap the   most   significant   and   least
significant   bytes and store the   result   in another variable y. Thus,   if x   contains   $1234   initially,   y   should   be $3412   etc.      [4]
(d)          Write a   commented   Sigma16   program to   process   an   array,   X,   of   n   16-bit   signed   numbers   in   memory.   If a   number   is   positive,   double   it;   if it   is   negative, square   it   (multiply   it   by   itself).       [7]
For   reference,   here   is a summary of the   instruction set of   the   Sigma16   CPU.
Mnemonic                                       Syntax                                                                   Action
lea
Rd, x[Ra]
Rd:= x   +Ra
   
load
Rd, x[Ra]
Rd:=   mem[x +Ra]
store
Rd, x[Ra]
mem[x +Ra]:=Rd
add
Rd,Ra,Rb
Rd:=   Ra+Rb
sub
Rd,Ra,Rb
Rd:=   Ra-Rb
mul
Rd,Ra,Rb
Rd:=   Ra*Rb
div
Rd,Ra,Rb
Rd:=   Ra/Rb,    R15:=Ra   mod   Rb
and
Rd,Ra,Rb
Rd:=   Ra AND   Rb
inv
Rd,Ra,Rb
Rd:=   NOT   Ra
or
Rd,Ra,Rb
Rd:=   Ra   OR   Rb
xor
Rd,Ra,Rb
Rd:=   Ra XOR   Rb
cmplt
Rd,Ra,Rb
Rd:=   Racmpeq
Rd,Ra,Rb
Rd:=   Ra=Rb
cmpgt
Rd,Ra,Rb
Rd:=   Ra>Rb
shiftl
Rd,Ra,Rb
Rd:=Ra   logic shifted   left   Rb   places
shiftr
Rd,Ra,Rb
Rd:=Ra   logic shifted   right   Rb   places
jumpf
Rd, x[Ra]
If   Rd=0 then   PC:=x+Ra
jumpt
Rd, x[Ra]
If   Rd<>0 then   PC:=x+Ra
jal
Rd, x[Ra]
Rd:=   pc,   pc: =x   +Ra
trap
Rd,Ra,Rb
PC:=   interrupt   handler
jump
x[Ra]
PC:= x   +Ra
2                (a)             Taking   the   Sigma16   instruction   STORE   R4,   100[R1]   as   an   example,   describe   how   this   would   appear   as
machine code   in   memory and   outline the steps   involved   in fetching   and代 写COMPSCI 4043 Systems and Networks 2022Processing
代做程序编程语言   executing   it.          [6]
(b)             The following Sigma16 code   is   intended to take   a   10-element   array   of two’scomplement   numbers   (only   the first   DATA element   is shown),   replace   every odd   element   with   1   and   every   even   element   with   0.
However, although the code will assemble,   it   contains   several   logical   errors   (as   opposed   to   syntax   errors   or   inefficiencies, which you   may   ignore).
i.                   Draw   up a   register   use   table   for   the   program   (suitable   for   inclusion   as   comment).
ii.                   Identify the   errors   and   explain   how you   would   correct them.
iii.                   Write   out the   corrected   program.
LEA R1,1[R0] ;Set R1 to constant 1
LOAD R2,0[R0] ;i:=0
ADD R5,R1,R1 ;R5:=2
LOAD R3,n[R0] ;Set R3 to n
FOR CMPEQ R14,R3,R2 ;Is i=n?
JUMPF R14,OUT[R0] ;if yes, exit
LOAD R4,X[R2] ;load X[i]
DIV R6,R4,R5 ;R6= X[i] mod 2
ADD R2,R2,R1 ;i:=i+1
STORE R6,X[R2] ;X[i]=X[i] mod 2
JUMP FOR[R0] ;loop
OUT TRAP R0,R0,R0 ; Data Area
n DATA 10
X DATA -8
DATA ...                                                                                                                                                                   [6]
(c)                Estimate   how   many   memory cycles the corrected   program would take to   run.   [4]
(d)             In the corrected   program   estimate the   advantage   a   system   with   a   cache   memory   would   gain   if   a   primary   memory cycle took   10ns and a   cache   cycle   1ns.       [4]
3.                            (a)                               Processors that support   multitasking operating systems   (unlike   Sigma16)   will   generally   have
privileged   instructions   in their   instruction sets.   Explain why the   notion of “privilege”   is   necessary   and give two   examples of what such   instructions   might   do.          [5]
(b)                            Explain   why   analogue   transmission   of   data   is   more   vulnerable   to   noise   than   digital.   If   bit   errors   do   occur   in digital transmission,   briefly   describe one way these   might   be detected.       [5]
(c)                               UDP   is often   used to transmit   real-time   audio   (e.g.   in VoIP   applications).   Explain why   UDP   might   be   considered   more suitable than TCP for this   purpose.           [5]
(d)                            Suppose a TCP   sender   is   transmitting   at   1.5Gbytes/sec   (1.5   x   109      bytes/sec)      with TCP   segments   that
are   approximately   1500   bytes   long.   Each segment   has a   32-bit   (unsigned) sequence   number   in   its      header that   is   incremented   by   1 at the sender each time   a   new   segment   is   transmitted.   If the   first   segment sent   has   number 0,   how   long   before the   numbers   run out?   Discuss   briefly what would happen then?           [5]

         
加QQ：99515681  WX：codinghelp  Email: 99515681@qq.com
