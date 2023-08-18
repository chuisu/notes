# #vectors
use `std::vector<type> name;`
eg: `std::vector<int> thisIsAVectorOfInts;`
can create and initialize in the same line: `std::vector<int> thisIsAVectorOfInts = {1,2,3};`
note: #arrays have a fixed size, its length must be known at compile time; #vectors are mutable and flexible
can use push_back() to add another element
can use pop_back() to delete last element - no return value
# #maps
are great because they can map a datatype to another datatype, which is great when you need to do something like map a string to a number. Like in the #magic8ball example, mapping each phrase to an int, and then calling a random phrase by calling a random int as in `std::cout << phrases[phrase];` is a valuable tool.

my code looked like this:
	`#include <iostream>
	`#include <map>`
	`#include <cstdlib>`
	
	`int main() {`
	`  srand(time(NULL));`
	`  int phrase = std::rand() % 21; `
	`  std::cout << "MAGIC 8-BALL: \n";`
	`  std::map<int, std::string> phrases;`
	`  phrases[0] = "It is certain.";`
	`  phrases[1] = "It is decidedly so.";`
	`  phrases[2] = "Without a doubt.";`
	`  phrases[3] = "Yes - definitely.";`
	`  phrases[4] = "You may rely on it.";`
	`  phrases[5] = "As I see it, yes.";`
	`  phrases[6] = "Most likely.";`
	`  phrases[7] = "Outlook good.";`
	`  phrases[8] = "Yes.";`
	`  phrases[9] = "Signs point to yes.";`
	`  phrases[10] = "Reply hazy, try again.";`
	`  phrases[11] = "Ask again later.";`
	`  phrases[12] = "Better not tell you now.";`
	`  phrases[13] = "Cannot predict now.";`
	`  phrases[14] = "Concentrate and ask again.";`
	`  phrases[15] = "Don't count on it.";`
	`  phrases[16] = "My reply is no.";`
	`  phrases[17] = "My sources say no.";`
	`  phrases[18] = "Outlook not so good.";`
	`  phrases[19] = "Very doubtful.";`
	`  phrases[20] = "Ah shit, this is bad!";`
	
	`std::cout << phrases[phrase];`
	`return 0;`
	
	`}`

But you can definitely improve on this with #classes
The code would look like this:
`	#include <iostream>`
`#include <map>`
`#include <cstdlib>`
`#include <ctime>`

`class Magic8Ball {`
`private:`
`    std::map<int, std::string> phrases;`

`public:
`    Magic8Ball() {`
`        phrases[0] = "It is certain.";`
`        phrases[1] = "It is decidedly so.";`
`        // ... fill in the rest of the phrases`
`        phrases[19] = "Very doubtful.";`
`        phrases[20] = "Ah shit, this is bad!";`
`    }``

    std::string getRandomPhrase() {
        int phraseIndex = std::rand() % phrases.size(); 
        return phrases[phraseIndex];
    }

    void printResponse() {
        std::cout << "MAGIC 8-BALL: \n";
        std::cout << getRandomPhrase() << '\n';
    }
`};`

`int main() {`
`    std::srand(std::time(NULL));`
`    Magic8Ball magic8Ball;`
`    magic8Ball.printResponse();`
`    return 0;`
`}`

#Classes can have [[public]] and [[private]] access
Best practice includes limiting public access,
private members are used for things like internal data, internal state
public members are used for altering the data in the class from elsewhere, or "getter" and "setter" methods, also validation, logging, additional logic
you can use [[protected]] to limit what members are public and allow certain inheriting classes to access members that should not be public

The **Principle of Least Privilege** states that you should start with most restrictive access. Make members all private by default, then adjust as needed.

A great example is the account class
its private members would be things like balance, to be used only within the code
a public member would be something like `adjustBalance`, where you can call it outside of the class in order to adjust the balance.

The void datatype is used to create functions that don't need to return value
other datatypes will of course return that datatype.
`Int` is used for error handling: `return 0` is used for a successful execution

an `&` is a pass by reference. This means that the function will have direct access to the variable, not just a copy

a pointer is a variable that stores memory to the address of another variable. It stores the memory address of a value that can be accessed later.

`int x = 42; // Declare an integer variable `
`int* p = &x; // Declare a pointer and initialize it with the address of x, by reference`
`std::cout << \*p; // Output the value pointed to by p (42)`

angle brackets, <> in C++ are used for template specialization. Templates can take any data type while being type safe. For example:
`std::vector<int> thisIsAnIntVector; 
`std::vector<std::string> thisIsAStringVector;`

What is a template? 
What is a vector?
what is a pointer and what are best practices for using pointers? How are they relevant in my JUCE project?
what is a constructor?

there are many [[C++ datatypes]], but what is a const?

# constructors 
are a special member function in a class
they can be identified in that they use `:` 
they also *must have the same name as the class* as in the #magic8ball example

# Class inheritance
Classes can inherit from other classes (subclassing) by using the colon `:`. The colon implies inheritance. An example looks like this:
`class Animal {`
	`public:`
		`void eat() {std::cout << "eating\n"};`
`}`
`class Dog : public Animal {
	`//code here...`
In the above example, the class `Dog` would inherit `eat()` from `Animal`
When listing multiple base classes to inherit from, you separate the list via a comma
`class Dog : public Animal, public Mammal {
	`public:
		`method()`
	`}
