---
layout: educational
title: Codeforces 1051
date: 2018-09-21 00:35:24
tags:
---

## A

```C++
#include <bits/stdc++.h>

using namespace std;

int T;
string s;

void rps(int t1, int t2){
	t1--; t2--;
	for(int i = 0; i < s.size(); i++){
		char c = s[i];
		if(0 == t1 && c >= 'a' && c <= 'z'){
			s[i] = 1 == t2 ? 'A' : 2 == t2 ? '0' : s[i];
		}
		else if(1 == t1 && c >= 'A' && c <= 'Z'){
			s[i] = 0 == t2 ? 'a' : 2 == t2 ? '0' : s[i];
		}
		else if(2 == t1 && c >= '0' && c <= '9'){
			s[i] = 0 == t2 ? 'a' : 1 == t2 ? 'A' : s[i];
		}
		else{
			continue;
		}
		break;
	}
}

int main(){
	ios::sync_with_stdio(0);
	cin >> T;
	while(T--){
		int c1 = 0, c2 = 0, c3 = 0;
		cin >> s;
		int L = s.size();
		for(int i = 0; i < L; i++){
			if(s[i] >= 'a' && s[i] <= 'z'){
				c1++;
			}
			else if(s[i] >= 'A' && s[i] <= 'Z'){
				c2++;
			}
			else if(s[i] >= '0' && s[i] <= '9'){
				c3++;
			}
		}

		if(c1 && c2 && c3){
		}
		else if(c1 && c2){
			if(c2 >= c1) rps(2, 3); else rps(1, 3);
		}
		else if(c1 && c3){
			if(c3 >= c1) rps(3, 2); else rps(1, 2);
		}
		else if(c2 && c3){
			if(c2 >= c3) rps(2, 1); else rps(3, 1);
		}
		else if(c1){
			rps(1, 2); rps(1, 3);
		}
		else if(c2){
			rps(2, 1); rps(2, 3);
		}
		else if(c3){
			rps(3, 2); rps(3, 1);
		}
		cout << s << endl;
	}

	return 0;
}
```

## B

```C++
#include <bits/stdc++.h>

using namespace std;

long long l, r;

int main(){
	ios::sync_with_stdio(0);
	cin >> l >> r;
	cout << "YES\n";
	for(long long i = l; i <= r; i += 2){
		cout << i << " " << i+1 << endl;
	}

	return 0;
}
```

## C

```C++
#include <bits/stdc++.h>

using namespace std;

int n;
int s[105];
int stat[105];
bool nice[105];

int main(){
	ios::sync_with_stdio(0);
	cin >> n;
	for(int i = 0; i < n; i++){
		cin >> s[i];
		stat[s[i]]++;
		nice[s[i]] = stat[s[i]] == 1;
	}

	int nicecnt = 0;
	for(int i = 0; i <= 100; i++){
		if(nice[i]) nicecnt++;
	}

	int index_to_b = -1;

	if(nicecnt % 2 != 0){
		for(int i = 0; i < n; i++){
			if(!nice[s[i]] && stat[s[i]] > 2){
				index_to_b = i;
				break;
			}
		}

		if(index_to_b == -1){
			cout << "NO";
			return 0;
		}
	}

	cout << "YES" << endl;
	int index_nice = 0;
	for(int i = 0; i < n; i++){
		if(i == index_to_b){
			cout << 'B';
		}
		else if(!nice[s[i]]){
			cout << 'A';
		}
		else if(nice[s[i]]){
			if(index_nice < nicecnt/2){
				cout << 'B';
			}
			else{
				cout << 'A';
			}
			index_nice++;
		}
	}


	return 0;
}
```

## D

```C++
#include <bits/stdc++.h>

using namespace std;

int n, K;
long long dp[1005][2018][4];
long long mod = 998244353;

int main(){
	ios::sync_with_stdio(0);
	cin >> n >> K;

	dp[1][1][0] = 1; dp[1][1][1] = 1;
	dp[1][2][2] = 1; dp[1][2][3] = 1;
	for(int i = 2; i <= n; i++){
		for(int k = 1; k <= K && k <= 2*i; k++){
			dp[i][k][0] = dp[i-1][k][0] + dp[i-1][k-1][1] + dp[i-1][k-1][2] + dp[i-1][k-1][3];
			dp[i][k][1] = dp[i-1][k-1][0] + dp[i-1][k][1] + dp[i-1][k-1][2] + dp[i-1][k-1][3];
			dp[i][k][2] = dp[i-1][k-1][0] + dp[i-1][k-1][1] + dp[i-1][k][2];
			dp[i][k][3] = dp[i-1][k-1][0] + dp[i-1][k-1][1] + dp[i-1][k][3];
			if(k >= 2){
				dp[i][k][2] += dp[i-1][k-2][3];
				dp[i][k][3] += dp[i-1][k-2][2];
			}
			dp[i][k][0] %= mod; dp[i][k][1] %= mod;
			dp[i][k][2] %= mod; dp[i][k][3] %= mod;
		}
	}

	long long res = 0;
	for(int i = 0; i < 4; i++){
		res += dp[n][K][i];
	}
	res %= mod;

	cout << res;

	return 0;
}

```
