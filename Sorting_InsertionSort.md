```cpp

void Insertion_Sort(int A[], int n) {
	for (int i = 1; i < n; ++i) {
		int cur_val = A[i];
		int j = i - 1;
		while (j >= 0 && A[j] > cur_val) {
			A[j+1] = A[j];
			j--;
		}
		A[j + 1] = cur_val;
	}
}


int Arr[] = { 6, 7, 1, 8, 3, 4, 9, 5, 10, 2 };

int main() {

	int size = sizeof(Arr) / sizeof(Arr[0]);
	cout << size << '\n';
	Insertion_Sort(Arr, size);

	for (int i = 0; i < size; ++i) {
		cout << Arr[i] << " ";
	}

	cout << '\n';
	return 0;
}
```
