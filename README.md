# emmetp
## emmet as a template language

### How
Just use emmet

Now you can use tabs for nesting (not `^+>` ... they still work though!)

If you need a $ be sure to escape it `\$` ... emmet uses $ for item number (ex: item.num$*5)

If you want to inline some text like javascript use `&` at the end of the tag (ex: `script&`) and `-` on a line alone to close the block.

Example:

	!
		#app
			button.btn{Hello \$someVar or {{ \$handlebars }} }
			ul>li.item${or one line... this is item #$}*4
		#footer
		script[type="text/javascript"]&
			console.log("inline text with the new & operator")
			console.log("use - to end the block")
		-
			  
Put it all on one line if you want:

	!>#app>button.btn{hello \$someVar}+ul>li*4{item #$}^^#footer+script&
	console.log('hello world')
	-

emmet cheat sheat is available: [here](http://docs.emmet.io/cheat-sheet/)

#### Inline JS

Want babel or coffeescript (or stylus/sass/whatever)? Use & ex: `script&appname:` and close with a `-` on its own line. Example:

	#app
		button.btn1+button.btn2
	script[src=jquery.js]
	
	script&coffee:
		$ ->
			$('.btn1').click () -> console.log 'hello world'
			$('.btn2').click () -> console.log 'from coffeescript'
	-
	#footer

Note: You will have to create a whitelist file `~/.config/emmetp` and add your preprocessors to it, It should be a valid JSON object. example: 

	{
		"coffee": { "args": ["-b","-c","-s","-p"] },
		"babel": { "args": ["-p","--blacklist","strict"] }
	}

### Install

Requires nodejs

Via npm: `npm install emmetp -g`

**Manual:**

Put the script somewhere, and `chmod u+x emmetp`

Then install the deps: 

	npm install emmet minimist -g
	#note: use -g for global, but it didnt work on my install... it should though.

### Usage

usage: `emmetp [-ph] [files] [-o outputfile1[,outputfile2]]`

Any one will do:

	emmetp file1.tmpl file2.tmpl   # creates file1.html and file2.html
	emmetp file1.tmpl -o outputFile.html
	cat myTemplate.file | emmetp > outputFile.html
	cat myTemplate.file | emmetp -o outputFile.html 

If no output file is named emmetp will use the old file name and a new extension of '.html'.

Piping `cat file | emmetp` will cause emmetp to print the results.

`-h` for help and `-p` for print.

### Contribute
Feel free to send a pull request.

Todo list:

* [X] Make NPM installable
* [X] Should be able to write raw javascript somewhere in the template file

### License (MIT)
The MIT License (MIT)
Copyright (c) 2016 falafflepotatoe

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
