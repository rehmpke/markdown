# Bash, Vim & Regex

## CD
	CD

CD can instantly send you to the home no need to type ~ or cd ~

## LS

also `ls -1` can create a single entry per line list of items.

## mkdir 

can create multiple levels of itself just by adding -p. that makes it easy to do something like r/r/r/

## Commands to help reduce repetitive typing

{} expansion generates patterns where *
 look for files that exist
{\_,} for ex.mv beep.txt beep.txt_
Could have just done mv beep.txt{_,}

or like cat b{ee, oo}p.txt

or echo {a,b}{c,d}
ac ad bc bd

or mkdir img{0..100..10}
produces img0/ img10/ img20/ img30/ img40/ img50/ img60/ img70/ img80/ img90/ img100

## WC

is for word count doesn't have a lot of options simple

## More on paths

if you add > you can add things into a file. if you add >> you can append them to the end of the file.