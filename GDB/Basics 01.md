# This is the very basics of GDB Debugger 

In this Notes we will be debugging this simple code and get to know the commands used 

```c
#include<stdio.h>

int main(){

	int a = 0;
	int b = 1 ;
	int c = 2 ;
	int d = 3;
	printf("Value of a is %d\n",a);
	return 0;
}
```
Now Lets start first by Compiling the code to be able to use GDB with it 
Note that **-g** flag allow to use GDB debugger
```shell
┌─[micr0b0t@parrot]─[~/Desktop/GDB_Tutoiral]
└──╼ $gcc -g debug.c -o debug
```
## Now lets Start debugging 

To Load the Program with GDB -> Syntax is : gdb ProgramName
```shell
┌─[micr0b0t@parrot]─[~/Desktop/GDB_Tutoiral]
└──╼ $gdb debug
GNU gdb (Debian 7.12-6+b1) 7.12.0.20161007-git
Copyright (C) 2016 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.  Type "show copying"
and "show warranty" for details.
This GDB was configured as "x86_64-linux-gnu".
Type "show configuration" for configuration details.
For bug reporting instructions, please see:
<http://www.gnu.org/software/gdb/bugs/>.
Find the GDB manual and other documentation resources online at:
<http://www.gnu.org/software/gdb/documentation/>.
For help, type "help".
Type "apropos word" to search for commands related to "word"...
Reading symbols from debug...done.
```
Now we can run the code and see what it does 
```shell
(gdb) run
Starting program: /home/micr0b0t/Desktop/GDB_Tutoiral/debug 
Value of a is 0
[Inferior 1 (process 26239) exited normally]
```
Okay so the Program Prints the **Value of a is 0** and exit Normally
Next we can read the code of the loaded program by using the following command
```shell
(gdb) list
1	#include<stdio.h>
2	
3	int main(){
4	
5		int a = 0;
6		int b = 1 ;
7		int c = 2 ;
8		int d = 3;
9		printf("Value of a is %d\n",a);
10		return 0;
```
**Another Way** to use List is we can list certain amount of lines with in Range
```shell
(gdb) list 1,5
1	#include<stdio.h>
2	
3	int main(){
4	
5		int a = 0;
```
Now Lets Set Breakpoints -> Syntax break LineNumber or break FunctionName
```shell
(gdb) break 7
Breakpoint 1 at 0x555555554660: file debug.c, line 7.
```
