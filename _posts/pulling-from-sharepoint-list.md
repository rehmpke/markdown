---
layout: "post"
title: "Pulling from a SharePoint list"
date: "2018-08-19 08:58:00"
expire_date: 2018-08-07 13:00:00
image: /uploads/ie.jpg
news_image_alt: 'Photo of issue'
article_lead: >-
  IE issue search box . . .
video_content: false
video_link: ''
categories: terminal
---

# Converting a SharePoint list into individual YAML files with terminal and regex on my Mac

The goal of the project was to automate the conversion of a SharePoint list into individual YAML files. We are using Jekyll to build out our pages and needed to have the content extracted from our previous site list and changed so we could use them.

I came accross several tools which were new to me. npm's xml2json, regex and cSplit.

SharePoint list export excel
that will show a file with a link to an xml file.
I then copy the link. and paste it into the browser.
It then is an xml format.
I then save the page to get the xml.
    
    $ cd desktop/mkdir && cd desktop/outputFolder

## Install xml2json

install xml2json with npm

    $ npm install -g xml2json-command
    
convert sharepoint xml file to json

    $ xml2json < kccevents.xml > changed.json
    $ xml2json < kccannouncments.xml > changed.json

## Split JSON file
I first tried to add a line and '======'
    
    $ csplit -k -n 3 changed.json /=====/ {285}
    
I then just split at the '{'
    
    $ csplit -k -n 3 changed.json /{/ {285}
    
## split json file into multiple files
## add .md ending

## Strip commas at the end of a line

This is for stripping commas off the end of a line that was JSON

    (,+$)

## Strip out \\r\\n

find in project

    \\r\\n

## Strip out \" 

These were in place for all quotes in html as it was converted to JSON. I proceded to find them in the project.

    \\"

## Stripped out start to number of characters

[regex tutorial that includes the following solution](https://www.icewarp.com/support/online_help/203030104.htm)

    span.{30}
    
## Strip out content that has random characters in it

There were a number of divs tags of equal length but different classes as guid numbers. I removed the divs by using the following technique.
<br>ex. `<div class="sdfasdfksdfk2w238383">` and `<div class="sdfasdfksdsdfsfssdfs">`
    
      <div class=".................."?

csplit -k -n 3 products.txt '/^@@@/' {'999'}; for i in xx*; do sed -i '' 's/@@@/---/g' $i; done; for i in xx*; do mv $i `egrep -m1 -e 'title:.*' $i | sed -e s/[^\]\[A-Za-z0-9~.,_{}\(\)\'\-\+]/-/g -e s/title---//`.md; done

csplit -k -n 3 products.txt

csplit -f text -- input.txt '//' "{$(wc -l input.txt)}"
for x in text[0-9]*; do mv -- "$x" "$x.txt"; done

csplit -b '%d.txt' -f text -- products.txt '//' '{*}'
csplit products.txt /\n/ {*}
csplit products.txt /\n/ {258}

csplit products.txt /^\s*0/ {258}
csplit products.txt /=====/ {258}

## cSplit

Used csplit to separate the old json file into individual files. I added the flag -f to switch the preset naming from xx01 to newsevent01
 
    csplit -k -f newsevent -n 3 news_event_archive.json /=====/ {285}

csplit -k -n 3 products.txt '/=====/' {'999'}; for i in xx*; do sed -i '' 's/@@@/---/g' $i; done; for i in xx*; do mv $i `egrep -m1 -e 'title:.*' $i | sed -e s/[^\]\[A-Za-z0-9~.,_{}\(\)\'\-\+]/-/g -e s/title---//`.md; done

csplit -k -n 3 products.txt '/=====/' {'999'}; for i in xx*; do mv $i `egrep -m1 -e 'title:.*' $i | sed -e s/[^\]\[A-Za-z0-9~.,_{}\(\)\'\-\+]/-/g -e s/title---//`.md; done   |  
cd /desktop
cd ..
sed -i 's/\"/"/g' changed.json
sed -i 's/ \\"/"/g' changed.json
sed -i 's/ \\"/"/g' changed.json

## Reverse the csplit

Occassionally I screw up something after the split. A simple save could be by reversing the split by using 'Cat' to rejoin all of the files.
