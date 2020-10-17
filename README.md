# HideCode
Hide code from dnSpy and other C# spying tools

Compile with https://github.com/mobdk/compilecs (using csc.exe)
Execution: Use rundll32 in same folder as BetaBeta.log. rundll32 BetaBeta.log,exec or with ordinal number. rundll32 BetaBeta.log,#1
BetaBeta.log is the compiled .dll it execute MimiKatz (64 bit)

Strings in C# has the format, lets say the string is "Hello", H.e.l.l.o if one use an hex editor, it contains a "dot" for every character, if this syntax 
break, dnSpy and other tools cannot read it, it simply disappears from the debugger.

The source code has the function Dummy() it contains a string data that is used as buffer for Mimikatz, after compiling BetaBeta.cs Mimikatz shellcode is
copied to the buffer in the format 232000000000000089073137200072129193 every byte is three chars long. Then compile one more time, edit the file in an hex editor
and find the offset, use the offset in the function FindCode() and change: int idx = offset, save and recompile.
'''
public static void Dummy()
{
   string data = "0000000000000000000000000000000000000000000000 (cut)";
}        
'''

