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


/* OOP Implementation*/

class SegmentTree {
private:
	int n;
	vector<int>Tree;
public:
	SegmentTree(vector<int> arr) {
		n = arr.size();
		Tree.resize(2 * n);

		for (int i = 0; i < n; ++i)
			Tree[i + n] = arr[i];

		for (int i = n - 1; i >= 1; --i) {
			Tree[i] = min(Tree[2 * i], Tree[2 * i + 1]);
		}
	}

	void Update(int idx, int value) {
		idx += n;
		Tree[idx] = value;

		while (idx > 1) {
			idx /= 2;
			Tree[idx] = min(Tree[2 * idx], Tree[2 * idx + 1]);
		}
	}

	int Query(int l, int r) {
		l += n, r += n;
		int Mn = INT_MAX;

		while (l < r) {
			if (l % 2 != 0) 
				Mn = min(Mn, Tree[l++]);

			if(r % 2 != 0)
				Mn = min(Mn, Tree[--r]);

			l /= 2, r /= 2;
		}

		return Mn;
	}
};


```
