
 ### Common text file related tools 


|Command|Use|
|--|--|
|less|Opens file in a pager|
|cat| dumps text file on screen|
|head|view top of file|
|tail|view bottom of file |  
|cut| filter columns or characters from file|
|sort| what do you think|
|wc|counts lines, words and characters|

### less
- main points in text
  - less can be used to view files 
  - use `page up` and `page down` keys to move respectively 
  - `q` is used to quit
  - searching
    - `/` forward search 
    - `?` backward search 
    - `n` repeat last search
  - uses same navigation and similar keys as `vim` and `man`:w    
- random 
  -  use `less -X *some-file*` to keep output of file on screen
- tips 
 - `-n` print number line  


### cat 
<img src="https://static.wikia.nocookie.net/garfield/images/c/c3/1980-09-24.gif/revision/latest/scale-to-width-down/1000?cb=20180817085808" width="200" height="100">     

- main points from text 
  - use `cat` for short files   
  - use `tac` for to inverse display   					 


### head and tails ![not heads or tails because we have to know both](https://d138zd1ktt9iqe.cloudfront.net/media/seo_landing_files/himanshi-tossing-a-coin-01-1608189912.png)

- `head` shows the first 10 lines by default 
- `tail` shows the last 10 lines be default
- `-n` or `-5`  use this option to show n number of lines 
- `-f` follow output 
- combine head and tail to print single  line  

### cut
- `cut -d : f 1 *filename*`
  - `-d` sets the delimiter which in this case is `:`
  - `f 1` this would be used to select the first field
  -`filename` and of course this would be the file that the command is filtered   

### sort 
- the command sorts by byte order by default,  
- need to review this did a lot of research but cant locate notes/finding

### wc 
- used to count lines words and characters. it uses three columns to display the counts, respectively 
### regular expressions 
[regex game](https://mekagem.itch.io/regxkcd)
![the game](https://itch.io/jam/xkcdgamejam)
![Tech Fantasy](https://imgs.xkcd.com/comics/regular_expressions.png)



#### line anchors
- `^` - look for matches at the start of the line (meta character is placed at beginning) 
- `$` -  look for matches at end of line  (meta character is placed at end)
- use single quotes to escape and as best practice use them all the time
#### wildcards and multipliers
- `.`  wild card for any single character  
  - r.t would match rat, rot, rut, rit, ret
- `[ ]` range of characters 
  - r[aot] would math the first 3 results from the previous example but not the last 2
-  
  - some useless use case and notes
    - download copy of Moby Dick
      - curl -O https://www.gutenberg.org/cache/epub/2701/pg2701.txt
    - search for lines matching deck or Dick 
      -  grep -i  d[ei]ck pg2701.txt
        -  this would work but you end up dropping half the book to STDOUT
        - `i` is important to make case insensitive as Dick is only used as a pro
    - when trying to match rot i keep getting any sequence of "rot" like 
        -`bro`ther-in-law, and a spare Bible for the steward—after all this, the
w`rot`e the first account of our Levi/athan? Who but mighty Job! And who
he find the torn limbs of his b`rot`her?
from the leviathanic `bro`therhood any sea creature hitherto identified
less `rot`und and jolly girth; indeed, he is of quite a neat and
It was during the more pleasant weather, that in due `rot`ation with the
whaler are p`rot`ected from the inclement weather of the frozen seas. In
perhaps, at mid-day, in the fairest weather, with one half-th`rot`tled
warfare; such men p`rot`esting that although other leviathans might be
with new-fallen snow? Or, to the unread, unsophisticated P`rot`estant of
being facetious than Moses, when he w`rot`e the history of the plagues of
Belisarius general. As many know, he w`rot`e the history of his own
background (for few men’s courage is proof against p`rot`racted
of course have been most anxious to p`rot`ect himself. That p`rot`ection
tooth evilly p`rot`ruding from its steel-like lips. A rumpled Chinese
much right-down hearty good-will and brotherly love about it at all. As
reserved for the scientific Frederick Cuvier, b`rot`her to the famous
c`rot`ch, and with what little strength may remain, he essays to pitch it   
    - it seem very important to use quotes when try to use ber\{2\}y
to match berry in the fruit file `ber\{2\}y` didnt work but `"ber\{2\}y"` did 
   - try to find some use cases for `?` and `+`, the extended regular expressions

#### types of regular expressions
 - base regex
 - extended regex 

#### most significant regular expressions


|regular expression | use| 
|-----|-------|
|^text|              Matches line that starts with specified text.|
|text$|              Matches line that ends with specified text.| 
|.|                  Wildcard. (Matches any single character.)|
[abc]|              Matches a, b, or c.| 
|?|                  Extended regular expression that matches zero or one of the
preceding character.|
|+|                  Extended regular expression that matches one or more of the
preceding character.|
|*|                  Matches zero to an infinite number of the previous character.
|\{2\}|              Matches exactly two of the previous character.|
|\{1,3\}|            Matches a minimum of one and a maximum of three of the previous|
character.|
|colou?r|            Matches zero or one of the previous character. This makes the
previous character optional, which in this example would match both
color and colour.|
|(…)|                Used to group multiple characters so that the regular expression can
be applied to the group|

### grep 

#### grep options 

|Option |Use|
|---|---|
|-i| Matches upper- and lowercase letters (i.e., not case sensitive).|
|-v| Shows only lines that do not contain the regular expression.|
|-r| Searches files in the current directory and all subdirectories.|
|-e| Searches for lines matching more than one regular expression. Use
-e before each regular expression you want to use.|
|-E| Interprets the search pattern as an extended regular expression.|
|-A| <number> Shows <number> of lines after the matching regular expression.|
-B| <number> Shows <number> of lines before the matching regular expression.|

### awk and sed 
|command|explanation|
|---|---| 
|`awk -F : '{ print $4 }'` /etc/passwd | shows the fourth field from /etc/passwd|
|`awk -F : '/user/ { print $4 }' /etc/passwd` | This command searches the /etc/passwd file for the text user and will print the
|fourth field of any matching line.|
|`sed -n 5p /etc/passwd` | print the fifth line from the /etc/passwd file|
|`sed -i s/old-text/new-text/g ~/myfile` | search for the text old-text in ~/myfile and replace all occurrences with the text new-text.|
|`sed -i -e '2d' ~/myfile` | delete a line based on a specific line number|


