---
layout: post
title: "求解某整数区间的素数个数"
subtitle: "\"the number of primes in a range\" Template in C++"
date: 2018-11-01 00:00:00
author: "Lester Tan"
tags: 
    - 算法模板
    - C++
---

## C++代码

```c++
#include <cstdio>
#include <iomanip>
#include <iostream>
#include <algorithm>
#include <cmath>
#include <cstring>
#include <queue>
#include <vector>
#include <functional>
#include <utility>
#include <map>
#include <set>

using namespace std;

typedef long long LL;

LL solve(LL r, LL n)//求[1,r]区间与n互素的个数
{
	vector<LL>p;
	p.clear();
	for (int i = 2; i*i <= n; ++i)//找n的质因数
	{
		if (n % i == 0)
		{
			p.push_back(i);
			while (n % i == 0) n /= i;
		}
	}
	if (n > 1) p.push_back(n); //可能n也是素数
	LL sum = 0;
	for (int msk = 1; msk < (1 << p.size()); ++msk)
	{
		LL mult = 1, bits = 0;//mult是选择的素数因子的乘积，bits是个数
		for (int i = 0; i < p.size(); ++i) 
		{
			if (msk & (1 << i)) //选择了第i个素数因子 
			{ 
				bits++;
				mult *= p[i];
			}
		}
		LL cur = r / mult;//[1,r]范围中mult的倍数的个数即为r/mult
		if (bits & 1) sum += cur;//利用容斥原理求得所有n的质因数的倍数，即非互质的数个数
		else sum -= cur;
	}
	return r - sum;
}

int main()
{
	LL m, k;
	while (scanf("%lld %lld", &m, &k) == 2)
	{
		LL l = 1, r = 0x0fffffffffffffff;
		while (l < r)
		{
			LL mid = l + (r - l) / 2;
			if (solve(mid, m) >= k)r = mid;
			else l = mid + 1;
		}
		printf("%lld\n", r);
	}


	return 0;
}
```

