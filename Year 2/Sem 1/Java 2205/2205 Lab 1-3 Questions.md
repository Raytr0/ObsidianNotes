1. In terms of data-processing time, what are your findings from labexercise 1?
	Recursive method takes longer time as the values get larger and larger, it also is more memory intensive
2. What are your findings on a recursive solution to any problem in terms
of processing time, and memory requirement?
	It can be fast if the recursive is small, but ultimately is very memory intensive 
3. When would you prefer iterative solutions over recursive ones?
	When the input size is large and efficiency is more important
4. True or False: The same code, executed in the same machine, always
results in the same execution time between two runs. What is the
rationale behind your answer to this question?
		False, the OS is constantly running different processes, there will always be variables thus affecting the processing speed each time.
5. True or False: Although factorial operation is only true for integertype data, depending on the datatype we choose to hold on to the result of factorial operation, we may encounter data-overflow. What is the rationale behind your answer to this question?
   factorials get large very quickly, data types have a limit on how many digits it can hold, for int, the limit is around 2 billion, so for any factorial that surpasses that number, it will result in data-overflow
6. If you need to find the max and min values from the data set where the available data items are between 18 and 65, what will be your choice in selecting the reference for min and max. What is the rationale behind your answer to this question?
   two variables min and max, both are initially empty or assigned the first value of the array, then have a for loop that compares each value to the next value of the array, depending on if its larger or smaller, replace the value and save it.
7. If we can handle any expected error related issue in our code without checking Exceptions, we should follow that path. What is the rationale for this comment?
	Allows code/program to keep running without breaking, can be used to easily get bug reports to developers from users
8. Exception handling separates error-handling code from normal programming tasks, thus making programs easier to read and to modify. However, what is the price we need to pay to enjoy this advantage.
9. What do we mean by ‘exception is thrown’?
   an unexpected error is caught during the execution of the program and displays information about the error.
10. What is the rationale behind declaring the Pair<> class as a generic one.
	Allows it to take any data type
11. What is the disadvantage of using arrays instead of linked list to realize a queue or a stack. Is there any advantage in using arrays to realize stack and queue?
Arrays are more simple to impliment and efficient in terms of memory, Linked lists
12. Is the implementation of stack and queue, with the help of arrays,
truly dynamic? What is the rationale behind your answer to this
question.
13. What do we mean by dynamic and static data structures?
14. How can you realize a stack using queue data structure?
15. Instead of declaring as a local reference-variable, what is the
rationale behind using the Scanner reference-variable as a field in the
driver class?
16. Explain with diagram how you implemented remvoveFromLastIndex()
method. Also, removeFromFirstIndex(), addAtFristIndex() and toString()
methods.
17. Explain how you can implement a new method public void
addAtFirstIndex(Pair p)in YourFirstNameArray class in lab 3?
18. Add the constructor with argument in your YourFirstNameArray class.
19. Explain the advantage of implementing the toString() method.
20. Explain whether an element can be added or removed from inside an
array.