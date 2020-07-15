# Longest Common Subsequence

Includes & Globals
```cpp
#include<iostream>
#include<string>
using namespace std;

string s1, s2;
const int Size = 3e3 + 5;
int DP[Size][Size];
```

Top Down Approach 
```cpp
int lcs(int i, int j){
	// base case:
  if(i >= s1.size() || j >= s2.size())
    return 0;
	
  if(DP[i][j] != -1)
    return DP[i][j];

  if(s1[i] == s2[j]) // remove one character from both strings and increase the answer by one.
		return DP[i][j] = lcs(i+1, j+1) + 1;
    
  return DP[i][j] = max(
    lcs(i+1, j),
    lcs(i, j+1)
  );
}
```



Driver Function
```cpp
int main() {

  memset(DP, -1, sizeof(DP));
  cin >> s1 >> s2;
  
  // The length of the LCS
  cout << lcs(0, 0) << '\n'; 
  
  // The LCS itself
  string lcsString = "";
  
  int i = 0, j = 0;
	while(i < s1.size() && j < s2.size()){

		if(s1[i] == s2[j]){

			lcsString += s1[i];
			i++; j++;

		} else if(DP[i+1][j] > DP[i][j+1])
			i++;
		else
		 j++;
		 
	}

	cout << lcsString << '\n';

  return 0;
}


```
