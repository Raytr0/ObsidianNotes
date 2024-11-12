Sorting
	Rearranging a set of data items in either ascending or decending order
	based on a **key**(what data to be focused on)

Stability
	When a data set is needed to be sorted more than once
	If sorting the second time, the order is affected, it is unstable![[Pasted image 20231113144151.png]]

Sorting Algorithms
	Simple ones
		Bubble sort, Insertion sort, Selection sort(Unstable but can make stable), Shell sort
	Advanced ones
		Merge Sort, Quick sort(unstable), Radix sort/Bucket sort(unstable but can be stable), Heap sort(unstable)

Bubble Sort
	Worst case time O(n^2)
	Best case time O(n)
	Start from beginning and swap numbers if larger number is in front, continue pattern until its at the end and restart from the front

Insertion Sort
	Left to right, one by one, checks if smaller value and inserts it between the checked values
	Best case O(n), already sorted only need to compare and not move stuff
	Space complexity O(1)
	
Selection Sort