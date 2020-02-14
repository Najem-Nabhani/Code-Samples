```cpp

const int SIZE = 7;
int Storage[SIZE];

int Hash(int key, int HashTableSize, int i=0) {
	if (i == 0)
		key %= HashTableSize;
	int index = (key + i*i) % HashTableSize;  // Quadratic Proping
	if (Storage[index] != 0) // collision ?
		Hash(key, HashTableSize, i + 1);
	else
		return index;
}
int main() {
	int elements[] = { 12,15,21,36,84,96  }; //6,1,10,36,8,12
	int len = 7;
	
	for (int i = 0; i < len; ++i) {
		int pos = Hash(elements[i], len);
		Storage[pos] = elements[i];
	}

	for (int i = 0; i < SIZE; ++i)
		cout << Storage[i] << " ";
	cout << '\n';

	return 0;
}

```
