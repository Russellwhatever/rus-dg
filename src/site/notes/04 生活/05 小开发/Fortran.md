---
{"dg-publish":true,"permalink":"/04/05/fortran/","noteIcon":"","created":"2025-01-31T00:35","updated":"2025-07-01T20:58"}
---

基础知识
- 数组：与其他语言不同，从1开始（而不是0），矩阵列优先（而不是行）
- 跨行符号&![99 Attachment/Pasted image 20240828103413.png](/img/user/99%20Attachment/Pasted%20image%2020240828103413.png)
即使是在字符串中间也可以这样，不过需要行末与行尾都加上&
![99 Attachment/Pasted image 20240828103504.png](/img/user/99%20Attachment/Pasted%20image%2020240828103504.png)
- 注释：用！
- 循环：用do和enddo表示
![99 Attachment/Pasted image 20240828103731.png](/img/user/99%20Attachment/Pasted%20image%2020240828103731.png)
注意循环结束之后n仍然存在，所以尽量同一脚本的不同循环用不同变量
也可以加上限制变量
```
do while(n>0)
```
- 条件语句
    分句
    if (条件) then
     ...........
    else
     .........
    endif

    一句话
    if (条件) (执行)
- 子程序
```
subroutine subr1
 implicit none
  real a, b
  integer i
  .......

end subroutine subr1
```
或者初始化变量
```
subroutine subr2(x,m,y,n)
 implicit none
 real x,y,a,b,z(10)
 integer m,n,i,k
 ......
end subroutine subr2
```
调用子程序
```
call subr2(10.0, 100, z, m*5+1)
```
需要注意两点：
1. 子程序在.f90文件中与主程序的代码片段是并列关系，可以处于主程序代码的前方，也可以处于后方
2. 调用时不会相互干扰，所有可以重复调用
3. 可以使用`if`和`return`判断，退出子程序返回主程序

- [x] 子程序的值返回  [completion:: 2025-02-03]
![99 Attachment/Pasted image 20240829142434.png](/img/user/99%20Attachment/Pasted%20image%2020240829142434.png)
fortran中会将参数变量全部返回给主程序，可以认为是地址引用
- 函数
函数只能返回一个结果，而子程序可以返回多个，二者相较，要根据使用场景选取
![99 Attachment/Pasted image 20240829143636.png](/img/user/99%20Attachment/Pasted%20image%2020240829143636.png)
*我现在的感想是：在fortran中，return、function好像都回到了字面意义，更好理解了。应该让大学生的计算基础课程都从fortran开始才是啊！*
- 全局变量
必须用module单独定义。主程序或子程序在使用时，需要在implicit none上一行用use <module名>来声明引用
![99 Attachment/Pasted image 20240829143944.png](/img/user/99%20Attachment/Pasted%20image%2020240829143944.png)
也可以这样选择性引入变量：
```
use <module name>, only : x, y, ...
```
