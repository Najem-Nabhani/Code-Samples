
```cpp

void SelectionSort(int arr[], int len, int Cur = 0, int i=1, int Min = -1) {
	//cout << Cur << endl;
	//base-case:
	if (Cur == len - 1)
		return;
	//base-case2:
		if (i == len) {
			// swap:
			int temp = arr[Cur];
			arr[Cur] = arr[Min];
			arr[Min] = temp;

			SelectionSort(arr, len, Cur + 1, Cur+2);
		}
	
	//general-case:
		else {
			if (arr[i] < arr[Cur]) {

				if (Min == -1)
					Min = i;
				else
					if (arr[Min] > arr[i])
						Min = i;

			}

			SelectionSort(arr, len, Cur, i + 1, Min);
		}
			
}
int main() {
	int A[] = { 1,8,9,4,5,3,1,0,4,5,2};
	SelectionSort(A, 11);

	for(int a : A) {
		cout << a << " ";
	}
	cout << '\n';
	return 0;
}

```
