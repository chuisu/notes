\#Section
\##Core section
\=Result/conclusion
\*Term
`example code with # language specific comment`


##What is programming?
	Every program is a set of instructions, no matter how big
	Programming is specific, individual, self-contained instructions
	Sequence is important
	Computers do things exactly as you tell them, you better get them right
	*Statements are these specific, self-contained instructions
		Akin to sentences, express one thought
		Require specific syntax

	Programming languages are invented languages bridging the gap between machine language and our language
	*Assembly language is close to machine code
	Languages closest to machine code are the hardest to write
	*Low-level Languages are languages closest to machine code
	*High-level languages are languages farthest from machine code.
=programming can be defined as writing code to be interpreted into machine code that comprises small, individual, and self contained instructions that make up a goal.
#Writing Souce Code
	Source code is written in plain text
	Some languages are more alike than they are different (such as ALGOL 68, Python, Lua)
	Some languages need to know where they start and where they end (some don't)
	*Integrated Development Environments (IDE) are suites for professional environments
=source code should be written in plain text and can vary and differ in syntax amongst all languages
#Compliled and Interpreted Languages
	Source code needs to get converted to machine code so that it can run
	Two ways:
	*Compiling - creates seperate file that runs off machine code (executable); no source code is given
		Pros: ready to run, often faster (due to CPU optimization), source code is private
		Cons: not cross-platform, inflexible, takes an extra step
	*Interpreting - gives copy of source code to be interpreted
		Pros: cross-platform, simpler to test, eaasier to debug
		Cons: interpreter required, often slower, source code is public
	There is a model with a bit of both:
	Intermidiate/hybrid: Compile partway upfront to "Intermediate language" (takes it as far to machine code as possible while being cross-platform), Just-In-Time compilation allows it to execute on client computer
=it's somemtimes good to analyze what type of language you're writing for what sort of tasks you're trying to accomplish. Certain tasks are better with compiled code, and certain tasks are better interpereted. Even still, some are better with a hybrid model, like Python.
##Core Programming Syntax	
#Javascript
	*Javascript is a C-based interpreted case-sensitive language. It's relevant and beginner-friendly.
		Manipulates webpages, created for this reason
		Intentionally limited
		Refered to as a *scripting language, a language that's more limited and embedded inside another program, in this case, the web browser
	Interpreted, and doesn't need to be compiled
	Case sensitive
		`document.getElementById("example").style.display = "none";`
		`document.getElementByID("example").style.display = "none";`
		One will work, and one will NOT
	Use of curly braces and semicolons at ends of lines can mean that the language is influenced by C
=Javascript is a C-based, interpreted, case-sensitive langauge. You can tell something is C based by the semantic use of the language. It runs within the browser (not needing to be compiled), and its level of case-sensitivity (as with most languages), makes the difference between code that works and code that fails.
#Javascript program
	Most programs run many levels within a system
		Computer > OS > Web browser > Webpage > script
	Javascript needs to run within a webpage (html file that only points to the js)
	container.html:
		`<html>
			<head><title>Simple Page</title></head>
			<body>
				<script src="script.js"></script>
			</body>
		</html>`
	script.js:
		`alert("Hello world"); 
			// make a dialogue (alert) box saying "Hello world"`
=Javascript programs run on a singular level which is nested within several layers, most notably the web browser and the web page. In order for it to run, it needs to have a webpage (an HTML file) point to it. The program itself uses the function `alert()` to make a dialogue box appear on a webpage
#Input
	Programs are generally about input and output
	*Input could be something like a string, a mouse movement, or pressing a button
	*Output could be an alert box, a graphical output, vibrating a controller
	script.js:
		`var name = prompt("What is your name?");
			// assign the variable 'name' to the product of the function prompt(), which accepts input from the user after displaying the output 'What is your name?'
		alert("Hello, " + name);
			// display an alert box first with the string 'Hello, ', and then the contents of the variable 'name'`
=Programs center around input and output, and each programming language has the ability to accept input, and make an output, and have the ability to make output from the input.
##Variables and Data types
#Intro
	Variable names are simple and should represent the data we want it to hold
	Used as one word with no spaces
	creating a variable is carving out an area of memory to hold a value
	When calling a variable, it is *undefined until a value is assigned to it	
	In js, calling a variable:
		`var year;
		year = 2017;
		// create the variable 'year', and assign the value 2017 to it`
		`var year = 2017;
		// create the variable 'year', and assign the value 2017 to it`
		`year = 2017;
		// find the variable 'year', and assign the value 2017 to it. If variable 'year' doesn't exist, make it`
		`var year, month, day;
		// create the variables 'year', 'month', and 'day'`
#Strong, weak, and duck-typed languages
	*Strong-typed languages don't allow variables to hold data of differing types
	*Weakly-typed languages allow generic variables which can hold any type of value
=Strong and weakly typed languages both have benefits as to their uses, either being very specific about data types, or lax.
#Numbers
	Javascript is lax with numbers, and doesn't care what kind of number it is
	*Numeric literals are numbers which represent a fixed value, like the number 5 (as opposed to '5')
=Sometimes numbers can be different types, such as integers, floating points, etc. Some languages care about calling a number by its type, but Javascript, for the purposes of this example, does not.
#Strings
	Words contained in sets of quotes are *Strings
	*String literals are fixed strings set in quotes
	Can't mix single and double quotes
	Most languages restrict to double quotes
	escaping quotes looks like this:
		`myVar = "He said, \"Don't mix your quotes,\" and he left."`
=Strings are word values, denoted by sets of quotes. You cannot end a called string with a single quote if you started calling it with a double quote. If you must mix quotes since your string includes quotes in them, they can be escaped using the \. Escape characters are started with \, and are IGNORED by the string, picked up immediately after the escaped character.
#Operators
	*Assignment: assigns a variable a value
		Evaluates whatever is on the RIGHT side of the assignment operator, even if it includes the variable being assigned
			`score = score + 10;`
		`score += 10;
		// store the sum of variable 'score' and 10 back in score`
			The above also works with -=, *=, and /=
		`a++
		//add 1, incrementally to a`
		++ is called increment operator
		-- is called decrememnt operator
	*Arithmetic: addition, subtraction, multiplication, and division, modulo?
		*Operator prescedence is order of operations for the program:
			`result = 5 + 5 * 10;
			// first multiply 10 and 5, then add 5`
			`result = (5 + 5) * 10;
			// first add 5 and 5, then multiply by 10`
=Operators are what change or assign values using the symbols above. There are certain shorthands for common operations, such as adding a variable to itself, then storing itself again. Increments make up another common shorthand, being ++.
#Whitespace
	*Whitespace is the space between statements, could be tabs, could be linebreaks between
	Some languages care about whitespace, some don't
		Javascript does not care about whitespace
		Python does care about whitespace
	Whitespace is used to make things clear
	Use whitespace in between contiguous things in the language
=Whitespace is used mainly for human readability, even when the language cares about when whitespace is used, such as Python. It can be used in between the elements, but it cannot separate an element from itself.
#Comments
	*Comments are snippets not read by the program when run, but make the code more readable by humans
=Comments add human readability to code, since code is not often intuitive to human eyes at first glance
==Code makes great use of data and values in the format of numbers, strings, booleans, and more. In addition to storing them, programs can also manipulate them in a number of ways. Data and values provide the elements upon which programs will work.
##Conditional Code
#If statement
	*If statements let something happen if a prescribed condition becomes emergent
	general format:
	`if ( ) {
		//conditional code goes here
	}`
	In parentheses are the conditional statement, something to be solved as TRUE or FALSE.
		For example: a > 50 //is variable a greater than 50?
			     b == 20 //is variable b equal to 20?
			     c != 100 //is variable c not equal to 100?
	the == sign is a comparison operator, the = is an assignment operator
	
	No semi colon after if statement curly braces	
	`if ( a == b) {
		alert("Yes, a is equal to b");
	}`
=Conditional statements, represented within the parentheses following the "if", evaluate to true or false. If the statement runs as true, at least for the above examples, they allow the code within the curly braces to run.
#Else
	`var balance = 5000;
	
	if ( balance > 0 ) {
		alert("The balance is positive");
	} else {
		alert("The balance is negative");
	}
	//set the variable balance to 5000, then check to see if the variable balance is greater than 0. If it is, output the alert with the string "The balance is positive", and if it is not, output the alert with the string "The balance is negative"`
	Were this the case, WHAT IF BALANCE WERE ZERO?
		the program would output "The balance is negative" erroneously. Really, the conditional should be `if ( balance >= 0 ) ...... `
#Comparison operators
	*Comparison operators evaluate to true or false for use in conditionals
		== != > >= < <= === !==
		=== is the strict equality operator
			eg:
			`var a = 123
			var b = "123"`
			a == b evaluates to true
			a === b evaluates to false
		
