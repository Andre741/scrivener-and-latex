# scrivener-and-latex
A repository for a integrated bibtex, pandoc and latex solution for Scrivener


#Instructions

Set up the project with the exported format and use the following script

### Script
The script I use is this find after a # the information what this line is doing
```
filename=$(basename -- $1)
extension="${filename##*.}"
filename="${filename%.*}"
pandoc $1 -s \
--citeproc \
--standalone  \
--csl apa.csl \ # this selects the citation format, download and use a different .csl file for a different format
--bibliography [YOUR BIBTEX].bib \
--template=capstone_template.tex  \ # selects the tex template
-o "$filename"_capstone.pdf  \
--shift-heading-level-by=-1 \
--pdf-engine=/Library/TeX/texbin/pdflatex

echo "capstone" $(ps2ascii "$filename"_article_apa.pdf | wc -w) | terminal-notifier #prints out the total document word count in the terminal

pandoc $1 -s \ # this creates the docx
--citeproc \
--standalone  \
--csl apa.csl \
--bibliography /Users/andre/Documents/bibtex/all/library.bib \
-o "$filename"_capstone.docx  \
--shift-heading-level-by=-1 \
```

## Requirements 
`ps2ascii` & `terminal-notifier` for having an output of the wordcount of the final document 
