
|寄存器	|  ABI | 名字	| 描述 |	Saver|
| ---- | ----- | ------|  --  | ------  |
|x0 | 	zero | 	硬件连线0	| - |
|x1	|ra	|返回地址|	|Caller|
|x2	|sp	|栈指针|	Callee|
|x3|	gp|	全局指针|	-|
|x4	|tp	|线程指针|	-|
|x5-x7|	t0-t2	|临时寄存器|	Caller|
|x8	|s0/fp|	保存的寄存器/帧指针|	Callee|
|x9	|s1|	保存寄存器保存原进程中的关键数据，避免在函数调用过程中被破坏|	Callee|
|x10-x11|	a0-a1|	函数参数/返回值|	Caller|
|x12-x17|	a2-a7	|函数参数	|Caller|
|x18-x27	|s2-s11|	保存寄存器|	Callee|
|x28-x31|	t3-t6	|临时寄存器	|Caller|