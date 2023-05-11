# Lab Report 3
## grep Command
The grep command by itself searches a file or files for a particular pattern such as a string in a text file. It then displays all lines that match that pattern. For the following examples, I will be using the ./technical directory. For all the commands I'm describing below, I found the commands at [this link](https://www.geeksforgeeks.org/grep-command-in-unixlinux/).
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
## grep -l
By putting -l (lowercase L, NOT one or capital I) after grep, it displays only the file names that contain a matching pattern anywhere within the file that is being searched.

Example 1: Looking for a string within a single text file can determine whther or not the file contains the string. This can be a simple way to determine if you are looking in the correct file for a certain pattern. 
```
$ grep -l "September" 911report/chapter-1.txt
911report/chapter-1.txt
```
Example 2: When looking through a large directory such as biomed, using grep -l can help to significantly lower the amount of files you have to search through. Using grep by itself in a similar situation could result in an output that gives too many lines and is confusing to look through. 
```
$ grep -l "History" biomed/*.txt
biomed/1471-2334-2-29.txt
biomed/1471-2431-3-3.txt
biomed/1471-2466-2-3.txt
biomed/1472-6947-1-6.txt
```
## grep -n
grep -n displays what line matches the pattern and also gives the line number of where that pattern is within the file(s). 

Example 1: Similar to the previous example except with -n allows me to find the lines where "History" is located. This makes it far easier for me to locate the source of the text within the .txt files. 

```
$ grep -n "History" biomed/*.txt
biomed/1471-2334-2-29.txt:124:          disease. History of schistosomiasis was obtained by
biomed/1471-2431-3-3.txt:115:          Menarcheal History
biomed/1471-2466-2-3.txt:152:          We used the Cognitive Lifetime Drinking History (CLDH)
biomed/1471-2466-2-3.txt:182:          questionnaires (FFQ), the Health Habits and History
biomed/1472-6947-1-6.txt:83:          Examination", and "Medical History Taking", linked by OR
```
Example 2: Using grep -n over a large text file makes it a lot easier to locate the text that I'm looking for. Otherwise, I would have to look through potentially thousands of lines of text. 
```
$ grep -n "year" 911report/chapter-1.txt
70:    At the same time or shortly thereafter, Atta-the only terrorist on board trained to fly a jet-would have moved to the cockpit from his business-class seat, possibly accompanied by Omari. As this was happening, passenger Daniel Lewin, who was seated in the row just behind Atta and Omari, was stabbed by one of the hijackers-probably Satam al Suqami, who was seated directly behind Lewin. Lewin had served four years as an officer in the Israeli military. He may have made an attempt to stop the hijackers in front of him, not realizing that another was sitting behind him.
156:    No one at the FAA or the airlines that day had ever dealt with multiple hijackings. Such a plot had not been carried out anywhere in the world in more than 30 years, and never in the United States. As news of the hijackings filtered through the FAA and the airlines, it does not seem to have occurred to their leadership that they needed to alert other aircraft in the air that they too might be at risk.
214:    On 9/11, the defense of U.S. airspace depended on close interaction between two federal agencies: the FAA and the North American Aerospace Defense Command (NORAD). The most recent hijacking that involved U.S. air traffic controllers, FAA management, and military coordination had occurred in 1993.90 In order to understand how the two agencies interacted eight years later, we will review their missions, command and control structures, and working relationship on the morning of 9/11.
728:    He was, and is, right. But the conflict did not begin on 9/11. It had been publicly declared years earlier, most notably in a declaration faxed early in 1998 to an Arabic-language newspaper in London. Few Americans had noticed it. The fax had been sent from thousands of miles away by the followers of a Saudi exile gathered in one of the most remote and impoverished countries on earth.
```
