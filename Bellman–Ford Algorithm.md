## Bellman–Ford
### Single source shortest path for positive and negative weights.
#### Time complexity: O(|v-1|.|e|), number of relaxations (# of nodes -1) times the number of edges then *O(n.|e|)*
#### Worst-case time complexity is when the graph is complete, hense |e| = n.(n-1)/n = O(n^2) then *O(n^3)*
#### Problem: negative weight cycles prevent the answer from being found.

```cpp
#include <iostream>
#include <vector>
#include <climits>
using namespace std;

int main() {
	
	int n = 6;
	int distance[7] = {};
	vector<vector<pair<int,int>>> graph = { 
		{}, 
		{{2, 10},{5, 4}}, 
		{{1, 7},{5, -20},{3, 100}}, 
		{{4, -1}}, 
		{{5, -10}, {6, 10}},
		{},
		{{4, 2}}
	};
    
	int relaxationCount = n - 1;
	
	for(int i=1; i <= n; ++i) {
		distance[i] = INT_MAX;
	}
	
	distance[1] = 0;

	while (relaxationCount--) {
		int nodeNo = 0;
		for (auto adjList : graph) {
			for (auto edge : adjList) {
				int nextNode = edge.first;
				int weightToNode = edge.second;
				
				if (distance[nextNode] > distance[nodeNo] + weightToNode) {
					distance[nextNode] = distance[nodeNo] + weightToNode;
				}
			}
			
			nodeNo += 1;
		}
	}
	
  // NOTE: on the n-th relaxation, the graph distances should not change, if it did, there is a negative weight cycle.
  
	for (int i=1; i <= n; ++i) {
		cout << i << ": " << distance[i] << "\n";
	}
	
	return 0;
}
```
