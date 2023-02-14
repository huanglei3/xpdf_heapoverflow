XPDF v4.04


pdftotext poc

Syntax Warning: PDF file is damaged - attempting to reconstruct xref table...
Syntax Error (2711): Dictionary key must be a name object
Syntax Error (2715): Dictionary key must be a name object
Syntax Error (2720): Dictionary key must be a name object
Syntax Error: Dictionary key must be a name object
Syntax Error: End of file inside dictionary
Syntax Error (393): Illegal character <3d> in hex string
Syntax Error (398): Illegal character <80> in hex string
Syntax Error (399): Illegal character <67> in hex string
Syntax Error (400): Illegal character <74> in hex string
Syntax Error (401): Illegal character <68> in hex string
Syntax Error (409): Illegal character '>'
Syntax Error (172): Dictionary key must be a name object
Syntax Error (393): Illegal character <3d> in hex string
Syntax Error (398): Illegal character <80> in hex string
Syntax Error (399): Illegal character <67> in hex string
Syntax Error (400): Illegal character <74> in hex string
Syntax Error (401): Illegal character <68> in hex string
Syntax Error (409): Illegal character '>'
Syntax Error (887): Illegal character ')'
Syntax Error (1296): Illegal character ')'
Syntax Error (1781): Illegal character ')'
Syntax Error (2386): Dictionary key must be a name object
Syntax Error (2390): Dictionary key must be a name object
Syntax Error: Unterminated string
Syntax Error: End of file inside dictionary
Syntax Error: End of file inside array
Syntax Error: End of file inside dictionary

Program received signal SIGSEGV, Segmentation fault.


(gdb) bt


#0  0x00007ffff7a989df in _IO_new_file_seekoff (fp=0x555555b81c30, offset=1446, dir=0, mode=<optimized out>) at fileops.c:976
#1  0x00007ffff7a967cd in __fseeko (fp=0x555555b81c30, offset=offset@entry=1446, whence=whence@entry=0) at fseeko.c:40
#2  0x0000555555848c19 in gfseek (f=<optimized out>, offset=offset@entry=1446, whence=whence@entry=0) at /home/fuzz/fuzzing_xpdf/xpdf-4.04/goo/gfile.cc:733
#3  0x00005555557ec8c1 in SharedFile::readBlock (this=0x555555b81fd0, buf=buf@entry=0x555555b832b8 "6 0 objnt 3 0 R\r\n/Resources <<\r\n/Font <<\r\n/F1 9 0 R \r\n>>\r\n/ProcSet 8 0 R\r\n>>\r\n/MediaBo\202 [0 0 612.0000 792.0000]\r\n\r\n7 0 obj\r\n<< /Length 676 >> 00000 Name /ream\r\n2 J\r\nBT\r\n0\r\n57.3750 722.2800 Td\r\n( Simpl"..., pos=1446, size=256) at /home/fuzz/fuzzing_xpdf/xpdf-4.04/xpdf/Stream.cc:739
#4  0x00005555557ecfe8 in FileStream::fillBuf (this=this@entry=0x555555b83280) at /home/fuzz/fuzzing_xpdf/xpdf-4.04/xpdf/Stream.cc:842
#5  0x0000555555813d23 in FileStream::getChar (this=0x555555b83280) at /home/fuzz/fuzzing_xpdf/xpdf-4.04/xpdf/Stream.h:324
#6  0x00005555557b1153 in Object::streamGetChar (this=0x555555b833f0) at /home/fuzz/fuzzing_xpdf/xpdf-4.04/xpdf/Object.h:300
#7  Lexer::getChar (this=this@entry=0x555555b833e0) at /home/fuzz/fuzzing_xpdf/xpdf-4.04/xpdf/Lexer.cc:93
#8  0x00005555557b13fa in Lexer::getObj (this=0x555555b833e0, obj=obj@entry=0x555555b838e8) at /home/fuzz/fuzzing_xpdf/xpdf-4.04/xpdf/Lexer.cc:125
#9  0x00005555557d078d in Parser::Parser (this=0x555555b838d0, xrefA=<optimized out>, lexerA=<optimized out>, allowStreamsA=<optimized out>) at /home/fuzz/fuzzing_xpdf/xpdf-4.04/xpdf/Parser.cc:35
#10 0x000055555582c0e2 in XRef::fetch (this=0x555555b83990, num=6, gen=0, obj=0x7fffff7ff330, recursion=<optimized out>) at /home/fuzz/fuzzing_xpdf/xpdf-4.04/xpdf/XRef.cc:1231
#11 0x00005555556754a0 in Object::arrayGet (this=0x7fffff7ff320, recursion=0, obj=0x7fffff7ff330, i=1) at /home/fuzz/fuzzing_xpdf/xpdf-4.04/xpdf/Object.h:243
#12 Catalog::countPageTree (this=0x555555b5d4a0, pagesObj=<optimized out>) at /home/fuzz/fuzzing_xpdf/xpdf-4.04/xpdf/Catalog.cc:566

