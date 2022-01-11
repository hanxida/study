[toc]



# Markdown语法

> ___
>
> ___
>
> 

## 基础语法

>- ```*[str]*```:	*字体倾斜*
>
>- ```_[str]_```:  _字体倾斜_
>
>- ```**[str]**```:  **字体加粗**
>
>- ```***[str]***```:   ***倾斜加粗***
>
>- ```~~[str]~~``` :   ~~下划线~~
>
> ___
>
>  

## 分级标题

> - ```# 一级标题```
>
> - ```### 二级标题```
>
> -  
>
> -  
>
> - ```###### 六级标题```
>
>   ___
>
>   

## 链接

>- ```![]()```	![图片描述]()
>
>- ```<自动链接>``` <2773070167@qq.com>
>
>- ```分割线{‘---’，‘***’，‘___’}```
>
> ___
>
>  

## 代码

> - ```代码块```
>
>   ```c
>   #include "stdio.h"
>   int main(void)
>   {
>       printf("Hello World");
>       return 0;
>   }
>   ```
>
> - ```行内式```
>       `printf("Hello World");`
>
>   ___
>
>   

## 表格

>|---|---|---|
>
>| ---  | ---  | ---  |
>| ---- | ---- | ---- |
>|      |      |      |
>
>___
>
>

## 字体颜色与字号

> ```html
> <font face="黑体">黑体</font>
> <font face="黑体" color="red">黑体红色</font>
> <font face="黑体" color=“red” size=4>黑体4号红色</font>
> ```
>
> <font face="黑体" color="red">黑体红色</font>
>
> <font face="黑体" color="red" size=4>黑体4号红色</font>
>
> ___
>
> 

## 链接的高级操作

> - 内容目录：`[toc]`:在段落中填写 [TOC] 以显示全文内容的目录结构
>
> - 锚点：锚点其实就是页内超链接。比如我这里写下一个锚点，点击回到目录，就能跳转到目录。 在目录中点击这一节，就能跳过来。
>
>   ```markdown
>   目录{#index}
>   [目录](#index)
>   ```
>
>   目录{#index}
>
>   [目录](#index)
>
> - 在需要添加注脚的文字后加上脚注名字[^注脚名字]
>
> ___
>
> 

## 背景色

> ```html
> Markdown本身不支持背景色设置，需要采用内置html的方式实现：借助 table, tr, td 等表格标签的 bgcolor 属性来实现背景色的功能。举例如下：
> <table><tr><td bgcolor=orange>背景色是：orange</td></tr></table>
> ```
>
> <table><tr><td bgcolor=red>背景色是：red</td></tr></table>
>
> ___
>
> 

## -Toda列表

>```html
>- [ ] 事情1
>- [ ] 事情2
>- [ ] 事情3
>- [ ] 事情3
>```
>
>- [ ] 事情1
>- [x] 事情2
>- [ ] 事情3
>- [x] 事情3
>
>___
>
>

___

___

#### 语法补充

```html
<!--基于html语法的图片插入(带图注)-->
<center>
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
    src="在这里插入图片地址" width = "70%" alt=""/>
    <br>
    <div style="color:orange; border-bottom: 1px solid #d9d9d9;
    display: inline-block;
    color: #999;
    padding: 2px;">
      在这里插入图片注释
  	</div>
</center>
```





[^注脚名字]:称为加注。 然后在文本的任意位置(一般在最后)添加脚注，脚注前必须有对应的脚注名字。

___



