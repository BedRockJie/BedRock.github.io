
Linux 子进程共享父进程的什么资源
- 进程组ID 和 会话ID
- 所有的环境变量
- 当前工作路径，除非是用chdir修改
- 打开的文件
- 信号响应函数
- 整个内存空间，包括堆、栈、数据段、代码段、标准IO缓冲区等

子进程不会共享父进程的什么资源
- 进程号，PID是身份号码，每个都不一样
- 记录锁，对文件加的锁子进程不会继承这个锁
pid = fork();
if(pid < 0){
    error
}
else if(pid > 0){
    //父进程
}
else {
    //子进程
}

# 拓扑排序


```C++
#include<iostream>
#include <list>
#include <queue>
using namespace std;

/************************类声明************************/
class Graph
{
    int V;             // 顶点个数
    list<int> *adj;    // 邻接表
    queue<int> q;      // 维护一个入度为0的顶点的集合
    int* indegree;     // 记录每个顶点的入度
public:
    Graph(int V);                   // 构造函数
    ~Graph();                       // 析构函数
    void addEdge(int v, int w);     // 添加边
    bool topological_sort();        // 拓扑排序
};

/************************类定义************************/
Graph::Graph(int V)
{
    this->V = V;
    adj = new list<int>[V];

    indegree = new int[V];  // 入度全部初始化为0
    for(int i=0; i<V; ++i)
        indegree[i] = 0;
}

Graph::~Graph()
{
    delete [] adj;
    delete [] indegree;
}

void Graph::addEdge(int v, int w)
{
    adj[v].push_back(w); 
    ++indegree[w];
}

bool Graph::topological_sort()
{
    for(int i=0; i<V; ++i)
        if(indegree[i] == 0)
            q.push(i);         // 将所有入度为0的顶点入队

    int count = 0;             // 计数，记录当前已经输出的顶点数 
    while(!q.empty())
    {
        int v = q.front();      // 从队列中取出一个顶点
        q.pop();

        cout << v << " ";      // 输出该顶点
        ++count;
        // 将所有v指向的顶点的入度减1，并将入度减为0的顶点入栈
        list<int>::iterator beg = adj[v].begin();
        for( ; beg!=adj[v].end(); ++beg)
            if(!(--indegree[*beg]))
                q.push(*beg);   // 若入度为0，则入栈
    }

    if(count < V)
        return false;           // 没有输出全部顶点，有向图中有回路
    else
        return true;            // 拓扑排序成功
}

```