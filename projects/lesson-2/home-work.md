# 如下
智能合约编写完成后，每次添加一个员工，每个员工薪水都是2ETH
每次调用calculateRunway()所花gas如下：

|调用次数|gas|
|-|-|
|1|1720|
|2|2483|
|3|3264|
|4|4045|
|5|4826|
|6|5607|
|7|6388|
|8|7169|
|9|7950|
|10|8731|

可见每次调用，所花gas都会增加。原因如下：
每增加一个员工，计算totalSalary时会多循环一次，所以所需gas将增加。从表中可看出每次循环所需gas为781

### calculateRunway()优化
设置一个内部变量totalSalary,在每次新增、修改、删除员工时对内部变量totalSalary进行相应修改。每次调用calculateRunway()时，无需通过循环，直接使用内部变量totalSalry即可计算。
