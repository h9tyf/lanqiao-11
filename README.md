遇到的问题：

1

Latch Control函数中，忘记再次修改P2。

2

继电器的关闭：LatchControl(5, 0xff);

打开：LatchControl(5, 0);

3

刚开始使用ds1302设置和读取时间，在正确输入密码的情况下，一次正确显示，一次直接返回initial状态，交替出现。

然后使用TickBkp，TicBkp % 1000 == 0时加一，大于等于5则到时间，则没有使用ds1302时出现的问题。

tyh说这个方法不准确。

采用第三种方法，存time_init时的SysTick的值，差大于5000则到时间。刚开始似乎是无论输入正确还是错误都直接显示到时间了。然后进行了若干调试操作后，（应该）没有做任何操作，就好了。

4

for(i = 5; i >= 0;i--)

注意i的范围。