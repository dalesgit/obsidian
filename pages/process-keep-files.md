## Ultimately to get this to work I had to

### fix the filenames

### have pandoc convert the html files

find . -name "*.ht*" | while read i; do pandoc -f html -t markdown "$i" -o "${i%.*}.md"; done

### [ozum/concat-md: CLI and API to concatenate markdown files and modify as necessary.](https://github.com/ozum/concat-md)

concat-md --toc --decrease-title-levels --file-name-as-title --dir-name-as-title /mnt/chromeos/MyFiles/Downloads/google-keep-takeout-12-26/takeout-20221226T142744Z-001/Takeout-12-26-22/Keep-12-26-22/security2/security2-md >concat-md-output.md

concat-md --toc --decrease-title-levels --file-name-as-title --dir-name-as-title /mnt/chromeos/MyFiles/Downloads/google-keep-takeout-12-26/takeout-20221226T142744Z-001/Takeout-12-26-22/Keep-12-26-22/security-3/markdown >concat-md-output.md

### convert resulting markdown to html for ease of use

pandoc concat-md-output.md -f markdown -t html -o concat-md-output.html