---
layout: post
title: "基于优先队列的Prim算法"
subtitle: "Prim Algorithm(using priority queue) Template in C++"
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
#define MAX_V 120
typedef long long LL;

using namespace std;

struct Edge {
	int from, to;
	LL dist;
	Edge() {}
	Edge(int from, int to, LL dist) :from(from), to(to), dist(dist) {}
};

struct HeapNode {
	LL d;
	int u;
	HeapNode() {}
	HeapNode(LL d, int u) :d(d), u(u) {}
	bool operator<(const HeapNode rhs)const
	{
		return d > rhs.d;
	}
};

struct Prim {
	int n, m;
	vector<Edge> edges;
	vector<int> G[MAX_V];//从点i出发的边序号(edges数组中的)
	bool done[MAX_V];

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

	LL prim(int s)
	{
		priority_queue<HeapNode> Q;
		memset(done, 0, sizeof(done));
		done[s] = true;
		for (int i = 0; i < G[s].size(); i++)Q.push(HeapNode(edges[G[s][i]].dist, edges[G[s][i]].to)); 
		//将源点的出边加入优先队列
		LL sum = 0;//代价和
		int num_vis = 1;//已经访问点的个数，连通图中访问了n个点后最小生成树则已经建成
		while (!Q.empty())
		{
			if (num_vis == n)break;
			HeapNode x = Q.top(); Q.pop();
			int u = x.u;//出边终点
			if (done[u])continue;
			done[u] = true;
			sum += x.d;//点u没有访问过时，把点u加入最小生成树的点集并更新代价和
			for (int i = 0; i < G[u].size(); i++)
			{
				Edge& e = edges[G[u][i]];//点u的出边
				if (!done[e.to])
				{
					Q.push(HeapNode(e.dist, e.to));
				}
			}
		}
		return sum;
	}
};
```
