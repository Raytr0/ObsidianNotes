### Generic Types
Errors are detected at compile time rather than runtime
Can avoid casting (Change of data type)
Makes programs easy to read
The class can be shared regardless of the type (OrderedPair\<String> and OrderedPair\<Name> both work)

### Generic Method
Has own type parameters
Static and non-static are both allowed but static generic method calls need to be formatted such that it is: Classname.\<Type>Methodname()

### Enhanced for-loop
for (dataType variableName : arrayName){
}
example:
int\[] myArray = {1,2,3,4,5};
for(int x: myArray){
}
this loops through all elements of the array of type int

### Generic Restrictions
Restriction 1: Cannot Create an Instance of a Generic Type (i.e., new T()).
Restriction 2: Generic Array Creation (i.e., new T\[100]) is Not Allowed. 
Restriction 3: A Generic Type Parameter of a Class Is Not Allowed in a Static Context.
![[Pasted image 20231017201749.png]]
Restriction 4: Exception Classes cannot be generic

### ArrayList(java.util.ArrayList)
Allows for object type storage not primitive-type storage
Automatically adjusts size when items are added and removed
You have to import it
![[Pasted image 20231017205424.png]]
You can use a for loop to print out each individual element in the array, or instead, use toString() which gives an output like \[thing1, thing2, thing3]

### Generic Interface
is an abstract class
![[Pasted image 20231017210333.png]]
![[Pasted image 20231017210341.png]]
![[Pasted image 20231017210405.png]]
