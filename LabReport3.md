# Lab Report 3
## Grep Command
The grep command by itself searches a file or files for a particular pattern such as a string in a text file. It then displays all lines that match that pattern. For the following examples, I will be using the ./technical directory.
## grep -c
By putting -c after grep, the command instead outputs the number of lines that match the pattern. If it searches through multiple files, it displays the file name and the number of lined within each file that match the pattern. 

Example 1: Using grep -c to search for all the instances of the letters "and". This includes whenever "and" is used alone or when the letters "and" are included within a larger word. The use of this is pretty straightforward as it can be used mainly as a word counter for a text file.
```
$ grep -c "and" 911report/chapter-1.txt
243
```
Example 2: Using grep -c on all files within 911report which displays both the file names and the number of lines that match the pattern for each file. This can be used to compare the use of a certain word or letter amongst multiple files. 
```
$ grep -c "and" 911report/*.txt
911report/chapter-1.txt:243
911report/chapter-10.txt:163
911report/chapter-11.txt:211
911report/chapter-12.txt:553
911report/chapter-13.1.txt:377
911report/chapter-13.2.txt:295
911report/chapter-13.3.txt:351
911report/chapter-13.4.txt:650
911report/chapter-13.5.txt:762
911report/chapter-2.txt:289
911report/chapter-3.txt:926
911report/chapter-5.txt:383
911report/chapter-6.txt:484
911report/chapter-7.txt:471
911report/chapter-8.txt:225
911report/chapter-9.txt:569
911report/preface.txt:54
```
## grep -i
By putting -i after grep, it runs the grep command normally except it isn't case sensitive. For example, if you're searching for "and", grep -i will display lines that have "and", "AND", "aNd", etc. 

Example 1: Using grep -i "inside" on the file chapter-1.txt displays a line that includes INSIDE, which is all capitals. There are far more outputs that would take up too much space but this command allows the user to find lines where the desired word is at the beginning of a sentence and therefore includes a capital letter. 
```
$ grep -i "inside" 911report/chapter-1.txt
INSIDE THE FOUR FLIGHTS
...
...
```
Example 2: Using grep -i "preface" on all text files in 911report displays the different files and the lines that correspond. Here, you can see that preface is lowercase and uppercase in multiple files which can be useful if you are just looking for any instance of the word over multiple files. 
```
$ grep -i "preface" 911report/*.txt
911report/chapter-13.3.txt:                For its preface, the Plan quoted a memo Tenet had sent to the CIA's senior
911report/chapter-3.txt:                prefaced the directions with a message:"From the American President down to the
911report/preface.txt:            PREFACE
```

-i Displays all lines, doesn't care about being case sensitive
-l Displays file where pattern is located
-n Displays what line matches and line number
