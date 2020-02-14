```cpp

vector<vector<int>> graph = { {}, {2,5}, {1,5,3}, {2,4}, {3,5,6}, {1,2,4}, {4} };
vector<bool> isVisited(7);
queue<int> q;
void BFS(int startingNode) {

	q.push(startingNode);

	while(!q.empty()){
		int curNode = q.front();

		if (!isVisited[curNode]) {
			isVisited[curNode] = true;
			cout << curNode << " ";
		}

		for (int i = 0; i < graph[curNode].size(); ++i) {
			auto thisChild = graph[curNode][i];
			if (!isVisited[thisChild]) {
				q.push(thisChild);
			}
		}

		q.pop();
	}

}

//Driver Method
int main() {
	
	BFS(1);
	
	return 0;
}

```
