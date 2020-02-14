```cpp

#include <iostream>

void BubbleSort(int A[], int n);

int Arr[] = {4, 5, 7, 2, 0, 1, 8, 9, 6, 3};
int main() {

	int n = sizeof(Arr) / sizeof(Arr[0]);
	BubbleSort(Arr, n);

	for (auto a : Arr)
		std::cout << a << ' ';
	std::cout << std::endl;
}

void BubbleSort(int A[], int n) {
	for (int i = 0; i < n; ++i) {
		for (int j = 0; j < n - i - 1; ++j) {
			if (A[j] > A[j + 1])
				std::swap(A[j], A[j + 1]);
		}
	}
}

```
