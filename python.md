print "Hello World"
	# returns Hello World
exit()
	# Exits python interpreter
def main():
	print "hello world!"
	# defines function called main, which prints hello world!
	# python needs these to be indented specifically; uses indentation of level to indicate where the code belongs

def main():
	print "hello world"
print "me too"
# only prints me too because "hello world" is being defined as main, but "me too" is not.

if __name__ == "__main__":
	main()
	# if this module was invoked specifically (if it was the main module), run the function.

f = 0;
print f
# returns 0

f = "abc"
print f
# redeclaring variable changes it; returns abc

print "string type " + 123
# returns error, cannot add integer and string. "Strongly typed language"

print "string type " + str(123)
# returns string type 123 (converts 123 to string)

f = 0;
print f
def someFunction():
	f = "def"
	print f
someFunction()
print f
#returns:
	#0
	#def
	#0
#variable f inside function is its own variable (local variable). f outside is global

f = 0;
print f
def someFunction():
	global f
	f = "def"
	print f
someFunction()
print f
# line 49 "global f" says that the variable is no longer local.
#returns:
	#0	
	#def
	#def

f = 0;
print f
del f
print f
#returns:
	#0
	#error

def func1():
	print "I am a function"
# defines func1, which, when called, will print "I am a function"
func1()
# returns I am a function
print func1()
# returns I am a function
# also returns None (tries to return the product of func1, which was what gets returned after printing "I am a function")
print func1
# prints without invoking the function
# returns None
# <function func1 at (some hex)>

def func2(arg1, arg2):
	print arg1, " ", arg2
# defines func2, which takes two arguments labeled arg1 and arg2 and prints them with a space in the middle
func2(10,20)
print func2(10,20)
#returns 10 20
	    #10 20
	    #none (because no return value)

def cube(x):
	return x*x*x

print cube(3)
# returns 27 (because there is a value returned, unlike lines 73 and 85

def power(num, x=1):
	result = 1;
	for i in range(x):
		result = result * num
	return result
# num to the power of x
# multiplies num by itself x number of times.
print power(2)
print power(2,3)
print power(x=3, num=2)
# reversing order, but specifying name. Returns 2^3.

def multi_add(*args):
	result = 0;
	for x in args:
		result = result + x
	return result
# defined function can add each respective member of args (which can have any number of members) to each other in order.
print multi_add(4,5,10,4)
# returns 23

# CONDITIONAL EXAMPLE
def main():
	x, y = 10, 100

	if (x < y):
		st= "x is less than y"
	elif (x == y):
		st= "x is the same as y"
	else:
		st= "x is greater than y"
	print st
if __name__ == "__main__"
	main()


# conditional statements let you use "a if C else b"
	st = "x is less than y" if (x < y) else "x is greater than or equal to y"
	#returns

# LOOPS
# WHILE LOOP
while (x < 5):
	print x
	x = x +1

# FOR LOOP
for x in range(5,10):
	print x
days = ["mon", "tues", "etc"]
for d in days:
	print d

# BREAK AND CONTINUE
for x in range(5,10):
	if (x == 7): break #stop if x gets to 7
	if (x % 2 == 0): continue #continue if it's divisible by 2
	print x

# ENUMERATE
days = ["mon","tues","etc"]
for i, d in enumerate(days):
	print i, d
# returns index AND data

# CLASSES
# these encapsulate
class myClass():
	def method1(self): #self argument refers to method itself
		print "myClass method1"
	
	def method2(self, soemString):
		print "myClass method2: " + someString
	
c = myClass()
c.method1() # take class "c", and perform its method "method1"
c.method2("This is a string") # take class "c", and perform its method "method2" with argument ""This is a string""
#returns:
#myClass method1
#myClass method2: This is a string

class anotherClass(myClass): #inherit anotherClass from myClass
	def method2(self): #override method2
		print "anotherClass method3"
	
	def method1(self):
		myClass.method1(self); #call parent class's method1"
		print "anotherClass method1" #calls own method1"

#import
from datetime import date #import date class from datetime library
#use imported
today = date.today() # today() method exists in date.class, making today variable out of it
print today.day, today.month, today.year
#uses information 
from datetime import datetime
t = datetime.time(datetime.now())
print "the current time is ", t
#uses a combination of functions from datetime to tell the current time
print timedelta(days=365, hours=5, minutes=1)
#represents a span of time lasting 365 days, etc
print "one year from now it will be: " + str(datetime.now() + timedelta(days=365))
#print following string, add to it another string. Within the second string, add the span of time for 365 days to the exact time now.
