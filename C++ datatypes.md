*and other stuff as well*

functions allllll have a return type, even void
EXCEPT for constructor functions

classics are:
	`int`; `double`; `std::string`; `char`, etc

`void`:
	returns no value, used for functions that do not need to return anything

`const`:
	we should be using const whenever possible
	this is actually just a keyword, it can be used:
	to tell the compiler not to change a variable after initialization
	to tell the compiler not to change a pointer after initialization
	note: there is a difference between:
		`const int* p;` and `int* const p `
	`const` member functions in a class mean that the member function will not modify any non-static data members of the object on which it's called
		this is essentially a promise that calling this function won't change the state of the object

`auto`:
	is a fantastic datatype because it automatically declares the correct datatype when working with something like a member function whose returned data you don't necessarily know