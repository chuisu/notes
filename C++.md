Classes can have [[public]] and [[private]] access
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
