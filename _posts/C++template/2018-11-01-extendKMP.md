---
layout: post
title: "扩展KMP算法"
subtitle: "Extend-KMP Algorithm Template in C++"
date: 2018-11-01 00:00:00
author: "Lester Tan"
tags: 
    - 算法模板
    - C++
---

## C++代码

```c++
#include <cstdio>
#include <cmath>
#include <cctype>
#include <cstring>
#include <cstdlib>

#include <iostream>
#include <iomanip>
#include <algorithm>
#include <utility>
#include <functional>
#include <string>
#include <vector>
#include <queue>
#include <stack>
#include <list>
#include <map>
#include <set>

using namespace std;

int nex[100010];
int extend[200020];

//令p为之前匹配过程中成功的最远位置,p0为取这个最大值时的起点，则p = p0 + extend[p0] - 1
//已知nex[0,1,2,....k]时要求解nex[k+1]，利用的是S[p0,p]已经匹配过所以情况确定的这个条件
//显然有S[p0,p] = T[0,p-p0],则有S[k+1,p] = T[k+1-p0,p-p0]
//现在我们需要知道的是S[k+1,p]与T[0,p-k]的关系
//于是我们利用len = nex[k+1-p0]，len即为T[0,m-1]与T[k+1-p0,m-1]的最大公共前缀长度
//从而得到T[0,p-k-1]与S[k+1,p] = T[k+1-p0,p-p0]的关系(被包含)
//当k+len<p时，我们注意到区间[p0,p]上的所有情况都是已经确定的，所以说明在k+len+1位置一定失配，马上得出extend[k+1] = len
//当k+len>=p时，说明情况确定的S[k+1,p]与T[0,p-k-1]完全匹配，此时需要从S[p+1]与T[p-k]开始一一匹配，直到失配，并更新p0

void Extend_GetNext(char T[])
{
	int p0;
	int len = strlen(T);
	memset(nex, 0, sizeof(nex));
	nex[0] = len;

	//算出nex[1]
	int tmp = 0;
	while (T[tmp] == T[tmp + 1] && tmp + 1 < len)tmp++;
	nex[1] = tmp;

	p0 = 1;
	for (int i = 2; i < len; i++)//i即为证明中的k+1
	{
		//即k + nex[k+1-p0] < nex[p0] + p0 - 1 = p
		//事实上当k+1大于p时，推论无法继续，本应直接从头开始暴力，但是因为此时可以保证i-1=k >= p=nex[p0]+p0-1
		//即i >= nex[p0] + p0,也即i + nex[i - p0] >= nex[p0] + p0
		//所以一定会进入else，此时在else中加上一个判断，即可将两类情况归于一种情况---即需要从头开始匹配
		if (i + nex[i - p0] < nex[p0] + p0)nex[i] = nex[i - p0];
		else
		{
			int j = nex[p0] + p0 - i;//T的前j位即前p - (k+1)位已经匹配，现在要从第j位开始，j = p - k
			if (j < 0)j = 0;//如果i>p0+next[p0](即k+1不在p0与p之间时),则要从头开始匹配
			while (i + j < len&&T[j] == T[j + i])j++;
			nex[i] = j;
			p0 = i;
		}
	}
}


void Extend_KMP(char S[], char T[])
{
	Extend_GetNext(T);
	memset(extend, 0, sizeof(extend));
	int p0;
	int len = strlen(S);
	int tlen = strlen(T);
	int i = 0;
	while (S[i] == T[i] && i < tlen&&i < len)i++;
	extend[0] = i;

	p0 = 0;
	for (int i = 1; i < len; i++)
	{
		if (i + nex[i - p0] < extend[p0] + p0)extend[i] = nex[i - p0];
		else
		{
			int j = extend[p0] + p0 - i;
			if (j < 0)j = 0;
			while (i + j < len&&T[j] == S[j + i])j++;
			extend[i] = j;
			p0 = i;
		}
	}
}
```

