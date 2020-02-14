```cpp

#include <iostream>
#include <stack>

void Merge(int l, int m, int r);
void MergeSort(int l, int r);

int arr[] = { 9,0,4,5,6,7,1,8,2,3 };

int main() {

	int n = sizeof(arr)/sizeof(arr[0]);
	
	MergeSort(0, n - 1);

	for (auto elem : arr)
		std::cout << elem << ' ';
}


void Merge(int l, int m, int r) {

	std::stack<int> L_stk, R_stk;
	L_stk.push(INT_MAX), R_stk.push(INT_MAX);

	for (int i = r; i >= l; --i) {

		if (i <= m)
			L_stk.push(arr[i]);

		else
			R_stk.push(arr[i]);

	}

	for (int i = l; i <= r; ++i) {

		int L = L_stk.top(), R = R_stk.top();
		if (L <= R) {
			arr[i] = L;
			L_stk.pop();
		}
		else if (L > R) {
			arr[i] = R;
			R_stk.pop();
		}
	}
}

void MergeSort(int l, int r) {

	if (l >= r)
		return;

	int mid = (l + r) / 2;

	MergeSort(l, mid);

	MergeSort(mid + 1, r);

	Merge(l, mid, r);

}

```
