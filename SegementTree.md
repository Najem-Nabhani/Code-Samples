```cpp

#include<iostream>
#include<vector>

std::vector<int> t; // the segment tree list. space complexity: O(n*n)

// CONSTRUCTION  time complexity: O(n)
void build(int ar[], int n) {
	t.resize(2 * n);
	for (int i = n; i < 2 * n; ++i) 
		t[i] = ar[i];
	
	for (int i = n - 1; i > 0; --i)
		t[i] = t[i * 2] + t[i * 2 + 1];
}

// QUERY time complexity: O(nlogn)
ll get(int l, int r) {
	l += n, r += n;
	ll sum = 0;
	while (l < r) {
		if (l & 1) sum += t[l++];
		if (r & 1) sum += t[--r];
		l /= 2;
		r /= 2;
	}

	return sum;
}

// MODIFICATION time complexity: O(nlogn)
void update(int idx, int value) {
	idx += n;
	t[idx] = value;
	while (idx > 1) {
		idx /= 2;
		t[idx] = t[idx * 2] + t[idx * 2 + 1];
	}
}

```
