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

angle brackets, <> in C++ are used for template specialization. Templates can take any data type while being type safe. 

Basically, it allows you to use any datatype when you declare a function, like this:
`template <typename T>;` this makes `T` able to have any type, in a function, it looks like this:
`T myFunction(T x, T y) {return x + y}` This uses `T` to say `x` and `y` can be anything, and adds them together
That way, whether x and y are ints or floats or doubles, they can be added.
What happens when they are a `std::string`?

So what is a template?
Basically, a template is an argument where you use angle brackets to specify a datatype
It can be used in various ways, as in above, and also to specialize a datatype when you instantiate a class template, such as `std::lock_guard`, which you would follow up with `<std::mutex>` if you were creating a lock guard specifically for the type `std::mutex`. Pretty confusing, but I think this is to be thorough, and to be specific with datatypes for certain class templates. ADDENDUM, now that I understand a bit more of this: you HAVE to specify the datatype because it's a template class, and otherwise it wouldn't know what datatype to operate on.

So what is a class template, template class?
A class template or template class is the usage of the `template` and `typename` keywords like we used above. It's a class that can take any datatype because it was templated to do certain things agnostic of datatype. For example,
`template <typename T>;`
`class myClass {`
`private: T element;` this creates a variable called element that can be any type
`public:`
`    myClass(T element): element(element) {}`
`    T get() { return element; }`
`    void set(T newElement) { element = newElement; }`
`};`
and then you would use it via `myClass<int> myIntContainer(42);` or something like that to specify that we're using the int datatype for this class.
basically, there are a lot of classes in C++ that are built this way, and you have to use angle brackets to specify datatypes for certain classes.

What is a vector?
A vector is like an array, but it's variable in size. In C++, arrays have a fixed size.
For example:
`std::vector<int> thisIsAnIntVector;` here, we initialized a new vector called thisIsAnIntVector.
`std::vector<std::string> thisIsAStringVector;`

what is a pointer and what are best practices for using pointers? How are they relevant in my JUCE project?
what is a constructor?

there are many [[C++ datatypes]], but what is a const?

# constructors 
are a special member function in a class
they can be identified in that they use `:` 
they also *must have the same name as the class* as in the #magic8ball example
can have different types: 
-default (this just is a function with the same name)
-parameterized
	`class Class {
	`public:
		`int a;
		`Class(int ClassVariable) : a(ClassVariable) {}
	`};
The above basically says:
	let's create a class that uses one variable (a), and when we instantiate this class, we're going to call it like this: `Class class(4);`, and this '4' 
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
I also think it's worth mentioning that creating an instance of a class is a separate statement basically using the class as a keyword (almost). As the above, you would have
	`int main() {
		`Dog fido;
		`fido.eat();
		`}
I would like to know if this sort of statement has a name: it's actually called object declaration or object instantiation.
Object/class instantiation can happen directly after
	`class Class {} Class;`

Runtime polymorphism is when objects of different types are treated as objects of a common base type, like the class dog or cat being from the base class Animal
Virtual functions allow for runtime polymorphism because they allow the base class to, for a given function, have a default implementation for generic use cases (in case the function has not been overridden)
