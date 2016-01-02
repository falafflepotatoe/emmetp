# emmetp
## emmet as a template language

### How
Just use emmet

Now you can use tabs for nesting (not `^+>` ... they still work though!)

If you need a $ be sure to escape it `\$` ... emmet uses $ for item number (ex: item.num$*5)

Example:

    !
         #app
              button.btn{Hello \$someVar or {{ \$handlebars }} }
              ul>li.item${or one line... this is item #$}*4
         #footer
              
Put it all on one line if you want:

    !>#app>button.btn{hello \$someVar}+ul>li*4{item #$}^^#footer

emmet cheat sheat is available: [here](http://docs.emmet.io/cheat-sheet/)

### Install

Requires nodejs

Put the script somewhere, and `chmod u+x emmetp`

Then install the deps: 

    npm install emmet minimist -g
    #note: use -g for global, but it didnt work on my install... it should though.

### Usage

Any one will do

    cat myTemplate.file | emmetp > outputFile.html
    cat myTemplate.file | emmetp -o outputFile.html 
    emmetp file1.tmpl -o outputFile.html
    emmetp file1.tmpl file2.tmpl   # creates file1.html and file2.html

If no output file is named emmetp will use the old file name and a new extension of '.html'.

Piping `cat file | emmetp` will cause emmetp to print the results.

### Contribute
Feel free to send a pull request.

Todo list:

* [ ] Make NPM installable
* [ ] Should be able to write raw javascript somewhere in the template file

### License (MIT)
The MIT License (MIT)
Copyright (c) 2016 falafflepotatoe

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

