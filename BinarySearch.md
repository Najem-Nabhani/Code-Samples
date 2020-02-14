```cpp

#include<iostream>

// Recursion implementation
int BinarySearch(int arr[], int item, int from, int to) {
	int mid = (from + to) / 2;
	if (from > to)
		return -1;

	if (arr[mid] == item) 
		return mid;
	
	
	if (arr[mid] > item) 
		BinarySearch(arr, item, from, mid - 1);
	else 
		BinarySearch(arr, item, mid + 1, to);
	
}

// loop implementation
int binarySearch(int arr[], int item, int low, int hi) {

	int mid;
	while (low <= hi) {
		mid = (low + hi) / 2;

		if (arr[mid] == item)
			return mid;
		
		if (arr[mid] > item)
			hi = mid - 1;
		else
			low = mid + 1;
	}

	return -1;
}

int main() {
	int arr[] = { 0 ,2 ,4, 6, 8, 10, 12, 14, 16, 18, 20, 22, 24, 26, 28 };

	int found = BinarySearch(arr, 24, 0, 14);
	if (found != -1)
		std::cout << "Element found at:\t" << found << '\n';
	else
		std::cout << "Element NOT found!\n";
	return 0;
}

```
