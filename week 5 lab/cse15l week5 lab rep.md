
**Week 5 lab report**

Alex Zhang

less command options:
```
less -N find-results.txt     
      1 technical/plos
      2 technical/plos/journal.pbio.0020001.txt
      3 technical/plos/journal.pbio.0020010.txt
      4 technical/plos/journal.pbio.0020012.txt
      5 technical/plos/journal.pbio.0020013.txt
      6 technical/plos/journal.pbio.0020019.txt
      7 technical/plos/journal.pbio.0020028.txt
      8 technical/plos/journal.pbio.0020035.txt
      9 technical/plos/journal.pbio.0020040.txt
     10 technical/plos/journal.pbio.0020042.txt
     11 technical/plos/journal.pbio.0020043.txt
     12 technical/plos/journal.pbio.0020046.txt
     13 technical/plos/journal.pbio.0020047.txt
     14 technical/plos/journal.pbio.0020052.txt
     15 technical/plos/journal.pbio.0020053.txt
     16 technical/plos/journal.pbio.0020054.txt
     17 technical/plos/journal.pbio.0020063.txt
     18 technical/plos/journal.pbio.0020064.txt
     19 technical/plos/journal.pbio.0020067.txt
     20 technical/plos/journal.pbio.0020068.txt
     21 technical/plos/journal.pbio.0020071.txt
     22 technical/plos/journal.pbio.0020073.txt
     23 technical/plos/journal.pbio.0020100.txt
     24 technical/plos/journal.pbio.0020101.txt
     25 technical/plos/journal.pbio.0020105.txt
     26 technical/plos/journal.pbio.0020112.txt
     27 technical/plos/journal.pbio.0020113.txt
     28 technical/plos/journal.pbio.0020116.txt
     29 technical/plos/journal.pbio.0020121.txt
     30 technical/plos/journal.pbio.0020125.txt
     31 technical/plos/journal.pbio.0020127.txt
     32 technical/plos/journal.pbio.0020133.txt
```
-N will give you the line numbers

this helps you see where you are when using arrow keys, and know how many files are there.

```
[cs15lfa22gc@ieng6-202]:docsearch:166$ less -X find-results.txt
technical/plos
technical/plos/journal.pbio.0020001.txt
technical/plos/journal.pbio.0020010.txt
technical/plos/journal.pbio.0020012.txt
technical/plos/journal.pbio.0020013.txt
technical/plos/journal.pbio.0020019.txt
technical/plos/journal.pbio.0020028.txt
technical/plos/journal.pbio.0020035.txt
technical/plos/journal.pbio.0020040.txt
technical/plos/journal.pbio.0020042.txt
technical/plos/journal.pbio.0020043.txt
technical/plos/journal.pbio.0020046.txt
technical/plos/journal.pbio.0020047.txt
technical/plos/journal.pbio.0020052.txt
technical/plos/journal.pbio.0020053.txt
technical/plos/journal.pbio.0020054.txt
technical/plos/journal.pbio.0020063.txt
technical/plos/journal.pbio.0020064.txt
technical/plos/journal.pbio.0020067.txt
technical/plos/journal.pbio.0020068.txt
...
```
keeps the outputs instead of clearing it.

this is helpful when you want to see the output while working on something else but don't want to keep going back to less to see the results. this keeps the outputs in your terminal.


```
[cs15lfa22gc@ieng6-202]:docsearch:179$ less -e find-results.txt
```
quit at the end of file after you read through, no need to press q to leave less.

this is helpful if you just want to read through the output, it will automatically quit after you are done and then you can continue to work on other things.



```
[cs15lfa22gc@ieng6-202]:docsearch:180$ less -?

                   SUMMARY OF LESS COMMANDS

      Commands marked with * may be preceded by a number, N.
      Notes in parentheses indicate the behavior if N is given.
      A key preceded by a caret indicates the Ctrl key; thus ^K is ctrl-K.

  h  H                 Display this help.
  q  :q  Q  :Q  ZZ     Exit.
 ---------------------------------------------------------------------------

                           MOVING

  e  ^E  j  ^N  CR  *  Forward  one line   (or N lines).
  y  ^Y  k  ^K  ^P  *  Backward one line   (or N lines).
  f  ^F  ^V  SPACE  *  Forward  one window (or N lines).
  b  ^B  ESC-v      *  Backward one window (or N lines).
  z                 *  Forward  one window (and set window to N).
  w                 *  Backward one window (and set window to N).
  ESC-SPACE         *  Forward  one window, but don't stop at end-of-file.
  d  ^D             *  Forward  one half-window (and set half-window to N).
  u  ^U             *  Backward one half-window (and set half-window to N).
  ESC-)  RightArrow *  Left  one half screen width (or N positions).
  ESC-(  LeftArrow  *  Right one half screen width (or N positions).
  F                    Forward forever; like "tail -f".
  r  ^R  ^L            Repaint screen.
  R                    Repaint screen, discarding buffered 
  ...
```
-? will display the help information for less.

this will help you get an ideas on how to use different commands for less.

find options:

```
[cs15lfa22gc@ieng6-202]:docsearch:183$ find -help
Usage: find [-H] [-L] [-P] [-Olevel] [-D help|tree|search|stat|rates|opt|exec] [path...] [expression]

default path is the current directory; default expression is -print
expression may consist of: operators, options, tests, and actions:

operators (decreasing precedence; -and is implicit where no others are given):
      ( EXPR )   ! EXPR   -not EXPR   EXPR1 -a EXPR2   EXPR1 -and EXPR2
      EXPR1 -o EXPR2   EXPR1 -or EXPR2   EXPR1 , EXPR2

positional options (always true): -daystart -follow -regextype

normal options (always true, specified before other expressions):
      -depth --help -maxdepth LEVELS -mindepth LEVELS -mount -noleaf
      --version -xautofs -xdev -ignore_readdir_race -noignore_readdir_race

tests (N can be +N or -N or N): -amin N -anewer FILE -atime N -cmin N
      -cnewer FILE -ctime N -empty -false -fstype TYPE -gid N -group NAME
      -ilname PATTERN -iname PATTERN -inum N -iwholename PATTERN -iregex PATTERN
      -links N -lname PATTERN -mmin N -mtime N -name PATTERN -newer FILE
      -nouser -nogroup -path PATTERN -perm [-/]MODE -regex PATTERN
      -readable -writable -executable
      -wholename PATTERN -size N[bcwkMG] -true -type [bcdpflsD] -uid N
      -used N -user NAME -xtype [bcdpfls]
      -context CONTEXT


actions: -delete -print0 -printf FORMAT -fprintf FILE FORMAT -print
      -fprint0 FILE -fprint FILE -ls -fls FILE -prune -quit
      -exec COMMAND ; -exec COMMAND {} + -ok COMMAND ;
      -execdir COMMAND ; -execdir COMMAND {} + -okdir COMMAND ;

Report (and track progress on fixing) bugs via the findutils bug-reporting
page at http://savannah.gnu.org/ or, if you have no web access, by sending
email to <bug-findutils@gnu.org>.
```
-help finds the help page for find.

```
find -type f
./technical/plos/pmed.0020235.txt
./technical/plos/pmed.0020236.txt
./technical/plos/pmed.0020237.txt
./technical/plos/pmed.0020238.txt
./technical/plos/pmed.0020239.txt
./technical/plos/pmed.0020242.txt
./technical/plos/pmed.0020246.txt
./technical/plos/pmed.0020247.txt
./technical/plos/pmed.0020249.txt
./technical/plos/pmed.0020257.txt
./technical/plos/pmed.0020258.txt
./technical/plos/pmed.0020268.txt
./technical/plos/pmed.0020272.txt
./technical/plos/pmed.0020273.txt
./technical/plos/pmed.0020274.txt
./technical/plos/pmed.0020275.txt
./technical/plos/pmed.0020278.txt
./technical/plos/pmed.0020281.txt
...
```
will find everything of this type, in this case f is for file.
this is helpful in filtering the type to find. in this case we won't see other types other than file.

```
[cs15lfa22gc@ieng6-202]:docsearch:187$ find -user cs15lfa22gc
./technical/biomed/1471-2369-3-6.txt
./technical/biomed/1471-2369-3-9.txt
./technical/biomed/1471-2369-4-1.txt
./technical/biomed/1471-2369-4-5.txt
./technical/biomed/1471-2377-1-2.txt
./technical/biomed/1471-2377-2-4.txt
./technical/biomed/1471-2377-2-6.txt
./technical/biomed/1471-2377-3-4.txt
./technical/biomed/1471-2407-1-13.txt
./technical/biomed/1471-2407-1-15.txt
./technical/biomed/1471-2407-1-19.txt
./technical/biomed/1471-2407-1-6.txt
./technical/biomed/1471-2407-2-11.txt
./technical/biomed/1471-2407-2-12.txt
./technical/biomed/1471-2407-2-15.txt
./technical/biomed/1471-2407-2-16.txt
./technical/biomed/1471-2407-2-17.txt
./technical/biomed/1471-2407-2-18.txt
./technical/biomed/1471-2407-2-19.txt
...
```
this will find everything under this user name.

this is helpful in cases where you have diferernt users. you will filter out other user's outputs.


```
[cs15lfa22gc@ieng6-202]:docsearch:188$ grep -i ".TXt" find-results.txt
technical/plos/journal.pbio.0020001.txt
technical/plos/journal.pbio.0020010.txt
technical/plos/journal.pbio.0020012.txt
technical/plos/journal.pbio.0020013.txt
technical/plos/journal.pbio.0020019.txt
technical/plos/journal.pbio.0020028.txt
technical/plos/journal.pbio.0020035.txt
technical/plos/journal.pbio.0020040.txt
technical/plos/journal.pbio.0020042.txt
technical/plos/journal.pbio.0020043.txt
technical/plos/journal.pbio.0020046.txt
technical/plos/journal.pbio.0020047.txt
technical/plos/journal.pbio.0020052.txt
technical/plos/journal.pbio.0020053.txt
technical/plos/journal.pbio.0020054.txt
technical/plos/journal.pbio.0020063.txt
technical/plos/journal.pbio.0020064.txt
technical/plos/journal.pbio.0020067.txt
...

[cs15lfa22gc@ieng6-202]:docsearch:189$ grep ".TXt" find-results.txt
[cs15lfa22gc@ieng6-202]:docsearch:190$ 
```
ignores case, when we don't have -i, we don't see any results.

this is helpful when you do not want to find case sensitve things or typo(upper/lower case) in names and searches. 


```
[cs15lfa22gc@ieng6-202]:docsearch:190$ grep -c ".txt" find-results.txt
252
```
counts the matching lines instead.

this is helpful when you want to see how many outputs you get without having to count and read all of the output.

```
[cs15lfa22gc@ieng6-202]:docsearch:191$ grep -n ".txt" find-results.txt
2:technical/plos/journal.pbio.0020001.txt
3:technical/plos/journal.pbio.0020010.txt
4:technical/plos/journal.pbio.0020012.txt
5:technical/plos/journal.pbio.0020013.txt
6:technical/plos/journal.pbio.0020019.txt
7:technical/plos/journal.pbio.0020028.txt
8:technical/plos/journal.pbio.0020035.txt
9:technical/plos/journal.pbio.0020040.txt
10:technical/plos/journal.pbio.0020042.txt
11:technical/plos/journal.pbio.0020043.txt
12:technical/plos/journal.pbio.0020046.txt
13:technical/plos/journal.pbio.0020047.txt
14:technical/plos/journal.pbio.0020052.txt
15:technical/plos/journal.pbio.0020053.txt
16:technical/plos/journal.pbio.0020054.txt
17:technical/plos/journal.pbio.0020063.txt
18:technical/plos/journal.pbio.0020064.txt
19:technical/plos/journal.pbio.0020067.txt
20:technical/plos/journal.pbio.0020068.txt
21:technical/plos/journal.pbio.0020071.txt
22:technical/plos/journal.pbio.0020073.txt
23:technical/plos/journal.pbio.0020100.txt
24:technical/plos/journal.pbio.0020101.txt
...
```
match the outputs with a line number.

this is helpful when you want to see how many files are there and easier to communicate with other people by refering to line numbers.