# 住户用例模型

##用例图
![UseCase_user_graph](UseCase_user_graph.png)
## 用例说明
1.开机
| 用例编号             |User_01   |
| -------------------- | --- |
| 用例名称             |开机    |
| 范围                 |分布式温控系统    |
| 级别                 |用例   |
| 主要参与者           |住户，客户端     |
| 项目相关人员及其兴趣 |     |
| 前置条件             |主控端开启，住户已经注册房间     |
| 后置条件             |开机成功，从控机和主控机建立连接并用来收发送风请求，将信息（当前温度，目标温度等）显示在客户端控制面板上； |
| 主要成功场景         | 1. 用户点击开机按钮 |
|                      | 2. 开机成功，从控机和主控机建立连接，显示当前温度到客户端控制面板上 |
| 扩展（或替代流程)    |     |
|                      |     |
| 特殊需求             |     |
| 发生频率             |     |


2.关机
| 用例编号             |User_02   |
| -------------------- | --- |
| 用例名称             |关机    |
| 范围                 |分布式温控系统    |
| 级别                 |用例   |
| 主要参与者           |住户，客户端     |
| 项目相关人员及其兴趣 |     |
| 前置条件             |主控端开启    |
| 后置条件             |从控机关闭|
| 主要成功场景         | 1. 用户点击关机按钮 |
|                      | 2. 从控机断开与主控机联系，不在收发送风请求 |
| 扩展（或替代流程)    |     |
|                      |     |
| 特殊需求             |     |
| 发生频率             |     |


3.更改目标温度
| 用例编号             |User_03   |
| -------------------- | --- |
| 用例名称             |更改目标温度    |
| 范围                 |分布式温控系统    |
| 级别                 |用例   |
| 主要参与者           |住户，客户端     |
| 项目相关人员及其兴趣 |     |
| 前置条件             |主控机开启，从控机开启，主控机和从控机建立连接   |
| 后置条件             |用户输入目标温度成功，客户端将这一温度（送风）请求发送给主控机|
| 主要成功场景         | 1. 用户输入温度 |
|                      | 2. 从控机接收到目标温度，并发送给主控机温度请求 |
| 扩展（或替代流程)    | 1a.用户输入的目标温度间隔小于一定间隔，从控机只响应最近一次温度   |
|                      |     |
| 特殊需求             |     |
| 发生频率             |     |


4.更改风速
| 用例编号             |User_04   |
| -------------------- | --- |
| 用例名称             |更改风速   |
| 范围                 |分布式温控系统    |
| 级别                 |用例   |
| 主要参与者           |住户，客户端     |
| 项目相关人员及其兴趣 |     |
| 前置条件             |主控机开启，从控机开启，主控机和从控机建立连接   |
| 后置条件             |用户输入目标风速成功，客户端将这一风速（送风）请求发送给主控机|
| 主要成功场景         | 1. 用户输入风速 |
|                      | 2. 从控机接收并保存风速信息，发送给主控机送风请求 |
| 扩展（或替代流程)    | 1a.用户输入的目标风速间隔小于一定间隔，只响应一秒内最近的一次。   |
|                      |     |
| 特殊需求             |     |
| 发生频率             |     |



5.显示控制面板
| 用例编号             |User_05   |
| -------------------- | --- |
| 用例名称             |显示控制面板   |
| 范围                 |分布式温控系统    |
| 级别                 |用例   |
| 主要参与者           |住户，客户端     |
| 项目相关人员及其兴趣 |     |
| 前置条件             |主控机开启，用户已经注册房间   |
| 后置条件             |控制面板成功显示|
| 主要成功场景         | 1. 客户端显示控制面板|
|                      |                |
| 扩展（或替代流程)    |                          |
|                      |     |
| 特殊需求             |     |
| 发生频率             |     |


## 系统顺序图
住户用例1系统顺序图：开机
![Order-on](Order-on.png)

住户用例2系统顺序图：关机
![Order-off](Order-off.png)

住户用例3系统顺序图：更改温度
![Order-temperature](Order-temperature.png)

住户用例4系统顺序图：更改风速
![Order-speed](Order-speed.png)

住户用例5系统顺序图：显示控制面板
![Order-control_panel](Order-control_panel.png)


## 操作契约

| 系统事件 | Power on    |
| -------- | --- |
| 交叉引用 | 开机  |
| 前置条件 | 主控机开启    |
| 后置条件 | 从控机开启    |



| 系统事件 | Connect request    |
| -------- | --- |
| 交叉引用 | 开机  |
| 前置条件 | 从控机开启    |
| 后置条件 | 从控机和主控机建立联系，收发送风请求    |


| 系统事件 | Initial Info transmit    |
| -------- | --- |
| 交叉引用 | 开机  |
| 前置条件 | 从控机和主控建立联系    |
| 后置条件 | 主控机将从控机的初始配置信息（风速，温度）发送给从控机    |


| 系统事件 | Initial Info show    |
| -------- | --- |
| 交叉引用 | 开机  |
| 前置条件 | 主控机将从控机的初始配置信息（风速，温度）发送给从控机    |
| 后置条件 | 控制面板显示从控机初始配置信息    |




| 系统事件 | Power off    |
| -------- | --- |
| 交叉引用 | 关机  |
| 前置条件 | 用户按下关机按钮    |
| 后置条件 | 从控机响应用户的关机请求    |




| 系统事件 |Connect break  |
| -------- | --- |
| 交叉引用 | 关机  |
| 前置条件 | 从控机响应用户的关机请求    |
| 后置条件 | 从控机和主控机断开连接    |




| 系统事件 |Temperature change request  |
| -------- | --- |
| 交叉引用 | 更改目标温度  |
| 前置条件 | 从控机开启    |
| 后置条件 | 从控机接收温度更改请求，并要求用户输入目标温度    |






| 系统事件 |Please input temperature  |
| -------- | --- |
| 交叉引用 | 更改目标温度  |
| 前置条件 | 从控机要求用户输入目标温度    |
| 后置条件 | 用户输入目标温度    |





| 系统事件 |Input temperature  |
| -------- | --- |
| 交叉引用 | 更改目标温度  |
| 前置条件 | 用户输入目标温度    |
| 后置条件 | 从控机记录新的目标温度，并发送给主控机新的送风请求    |





| 系统事件 |Speed change request  |
| -------- | --- |
| 交叉引用 | 更改风速  |
| 前置条件 | 从控机开启    |
| 后置条件 | 从控机接收风速更改请求，并要求用户输入新的目标风速    |





| 系统事件 |Please input speed  |
| -------- | --- |
| 交叉引用 | 更改风速  |
| 前置条件 | 从控机要求用户输入目标风速    |
| 后置条件 | 用户输入目标风速    |




| 系统事件 |Input speed  |
| -------- | --- |
| 交叉引用 | 更改目标温度  |
| 前置条件 | 用户输入目标风速    |
| 后置条件 | 从控机记录新的目标风速，并发送给主控机新的送风请求    |




| 系统事件 |control panel show |
| -------- | --- |
| 交叉引用 | 显示控制面板  |
| 前置条件 | 从控机已经开机    |
| 后置条件 | 客户端将当前温度，目标温度和目标风速显示在屏幕上，并提供用户修改温度和风速的按钮    |



