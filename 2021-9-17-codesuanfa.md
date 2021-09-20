
# Linux进程间通
- 信号
- 管道
- Socket
- 共享内存
- 消息队列
- 先入先出队列FIFO
进程创建：
```
fork
exec
exit
```
- 代码段
  - 文本段，存放指令，运行代码的一块内存空间
- 数据段
  - 初始化全局变量和 static 变量
- bss段
  - 未初始化的全局变量和未初始化的static变量，一般会默认存储0
- data段
  - 变量的值在程序运行的过程中修改
- 栈
  - 函数或者代码中的局部变量
- 堆
  - 动态内存分配的空间

# Linux 进程概念
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
  
```C
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
```
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



# 图床链接
路过图床，现在作为自己暂时所使用的图床，图片需求不大。
`https://imgtu.com/i/4KQdTU`


```
find 指令
    find [dir] -name  “查找相关文件”
```


## 升级工具链
```C
//d1-tina-open2\out\d1-nezha_min\compile_dir\target\libubox-2016-02-26\blobmsg.c 195:
	hdr->name[strlen((char*)hdr->name)] = '\0';
	strncpy((char *) hdr->name, (const char *)name, strlen((char*)hdr->name));
	//strcpy((char *) hdr->name, (const char *)name);
//d1-tina-open2\out\d1-nezha_min\compile_dir\target\procd-2016-02-08\service\validate.c
    vr->option[strlen((char*)vr->option)] = '\0';
    strncpy((char *) vr->option, (const char *)blobmsg_name(cur), strlen((char*)vr->option));
    //strcpy(vr->option, blobmsg_name(cur));
//替换动态库
    out/d1-nezha_min/compile_dir/target/memtester-4.3.0/
```
# IIC
IIC 在读的过程中，首先需知道需要读取的寄存器
- 发送起始位
- 发送slave 地址 姐 写入的数据
- 重新发送起始位 restart
- 重新发送 slave 地址 + read bit set
- 读取数据
- 时钟线高电平 数据线下降沿 启动信号
- 时钟线高电平 数据线上升沿 终止信号



