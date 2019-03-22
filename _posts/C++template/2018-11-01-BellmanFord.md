---
layout: post
title: "Bellman-Ford算法"
subtitle: "Bellman-Ford Algorithm Template in C++"
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
#define MAX_V 10000

using namespace std;

struct Edge { 
	int from, to;
	int dist;
	Edge(){}
	Edge(int from, int to, int dist) :from(from), to(to), dist(dist) {}
};

struct BellmanFord {
	int n, m;
	vector<Edge> edges;
	vector<int> G[MAX_V];
	bool inq[MAX_V];//是否在队列中
	int d[MAX_V];//源点S到各点的距离
	int p[MAX_V];//最短路上一条弧
	int cnt[MAX_V];//进队次数

	void init(int n)
	{
		this->n = n;
		for (int i = 0; i < n; i++)G[i].clear();
		edges.clear();
	}

	void AddEdge(int from, int to, int dist)
	{
		edges.push_back(Edge(from, to, dist));
		m = edges.size();
		G[from].push_back(m - 1);
	}

	bool negativeCycle()
	{
		queue<int> Q;
		memset(inq, 0, sizeof(inq));
		memset(cnt, 0, sizeof(cnt));
		for (int i = 0; i < n; i++)
		{
			d[i] = 0;
			inq[0] = true;
			Q.push(i);
		}
		while (!Q.empty())
		{
			int u = Q.front(); Q.pop();
			inq[u] = false;
			for (int i = 0; i < G[u].size(); i++)
			{
				Edge& e = edges[G[u][i]];
				if (d[e.to] > d[u] + e.dist)
				{
					d[e.to] = d[u] + e.dist;
					p[e.to] = G[u][i];
					if (!inq[e.to])
					{
						Q.push(e.to);
						inq[e.to] = true;
						if (++cnt[e.to] > n)return true;
					}
				}
			}
		}
		return false;
	}
};
```

