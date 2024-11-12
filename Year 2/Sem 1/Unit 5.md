Hashing determines an index or location for storage of an item in a data structure
Hash function receives the **hash-key** and returns the index of an array where it is stored

Collision
	Happens when more than one hash-key is in the same index

Good hash functions should
	minimize collisions
	distribute entries uniformly throughout the hash table
	computes fast

Generating hash codes
	any search key is converted to an integer value
	use Object's .hashCode() method
	Integer will return the value given
	Other primitive numerical types will need to be casted to int, Integer y = (int)3.25, hash code will then be 3
	using letters will return the ASCII code
	and without any casting we cannot guess the hashcode

HashCode in Java
	overwrite hashCode()
	if a class overwrites equals() then hashCode() also should be overridden
	if hashCode is invoked more than once on the same data on the **same execution**, it should return the same

Compress hash code
	has to fit index range of table
	hashcode *c* would be computed as c % n
	where n is a prime number (but also the size of the table)
	Index will then be between 0 and n-1

Why prime numbers?
	will have non-uniform distribution if not

Collision handling schemes
	how to resolve collision?
		Use another location in table
		Change structure
	Either
		Open addressing
			• Linear Probing 
			• Quadratic Probing 
			• Double Hashing
	Or
		Separate Chaining

Open addressing
	finding an unused, or open, location in the hash table is called open addressing
		Linear Probing:
			collision at hashTable\[k]
			start going down k+1, k+2... until free location is found(probe sequence)
			if it reaches the end it continues at the beginning of the table

Three types of locations
	Occupied
	Empty
		Contains null
	Available
		location's entry was removed, search will go past this location if expected entry is not found in any available location
		