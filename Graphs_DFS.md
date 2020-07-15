# Depth First Search

Example Graph
```cpp
vector<vector<int>> graph = { {}, {2,5}, {1,5,3}, {2,4}, {3,5,6}, {1,2,4}, {4} };
vector<bool> isVisited(7);
```
Recursive Algorithm
```cpp

void DFS(int curNode) {
	isVisited[curNode] = true;
	cout << curNode << " ";
	for (int i = 0; i < graph[curNode].size(); ++i) {
		auto thisChild = graph[curNode][i];
		if (!isVisited[thisChild])
		DFS(thisChild);
	}
}
```

Stack Implementation
```cpp
stack<int> stk;
void DFS(int startingNode) {

	stk.push(startingNode);

	while (!stk.empty()) {
		int curNode = stk.top();
		stk.pop();

		if (!isVisited[curNode]) {
			cout << curNode << " ";
			isVisited[curNode] = true;

		}

		for (int i = 0; i < graph[curNode].size(); ++i) {
			auto thisChild = graph[curNode][i];
			if (!isVisited[thisChild]) {
				stk.push(thisChild);
			}
		}
	}

}
```


Driver Method
```cpp
int main() {
	DFS(1);
	return 0;
}

```
