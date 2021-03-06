0 超链接
=========
Markdown 支持两种形式的链接语法： 行内式和参考式两种形式，行内式一般使用较多。
#### 行内式
超链接的行内式的基础格式：
```
[链接文字](链接地址 "链接标题")  
```
[]里写链接文字，()里写链接地址, ()中的""中可以为链接指定title属性，title属性可加可不加。title属性的效果是鼠标悬停在链接上会出现指定的 title文字。链接地址与链接标题前有一个空格。
#### 参考式
参考式超链接一般用在学术论文上面，或者另一种情况，如果某一个链接在文章中多处使用，那么使用引用 的方式创建链接将非常好，它可以让你对链接进行统一的管理。
语法说明：  
参考式链接分为两部分：

文中的写法` [链接文字][链接标记]`  

在参考文献位置(文本的任意位置)添加` [链接标记]:链接地址 "链接标题" `  **链接地址与链接标题前有一个空格**。

如果链接文字本身可以做为链接标记，文中写成 [链接文字][]
参考文献位置写成： [链接文字]：链接地址

#### 自动链接

语法说明： 
Markdown 支持以比较简短的自动链接形式来处理网址和电子邮件信箱，只要是用<>包起来， Markdown 就会自动把它转成链接。

1 插图
==============
插图的格式类似于超链接，区别在于开头多了一个！，也分行内式和参考式。 

插图最基础的"行内式"格式就是：
`![Alt text](图片链接 "optional title")`

Alt text：图片的Alt标签，用来描述图片的关键词，可以不写。最初的本意是当图片因为某种原因不能被显示时而出现的替代文字，后来又被用于SEO，可以方便搜索引擎根据Alt text里面的关键词搜索到图片。  
图片链接：可以是图片的本地地址或者是网址。"optional title"：鼠标悬置于图片上会出现的标题文字，可以不写。

- 插入本地图片
只需要在基础语法的括号中填入图片的位置路径即可，支持绝对路径和相对路径。
例如：
```
![avatar](/home/picture/1.png)
```
不灵活不好分享，本地图片的路径更改或丢失都会造成markdown文件调不出图。

- 插入网络图片
只需要在基础语法的括号中填入图片的网络链接即可，现在已经有很多免费/收费图床和方便传图的小工具可选。
例如：
`![avatar](http://baidu.com/pic/doge.png)`
将图片存在网络服务器上，非常依赖网络。

- 把图片存入markdown文件
用base64转码工具把图片转成一段字符串，然后把字符串填到基础格式中链接的那个位置。

基础的“行内式”用法：
`![avatar](data:image/png;base64,iVBORw0......)  `
这个时候会发现插入的这一长串字符串会把整个文章分割开，非常影响编写文章时的体验。  
可以采用"参考式"的语法,比如：  
```
![avatar][base64str]
[base64str]:data:image/png;base64,iVBORw0......
```

最后，base64的图片编码如何得来？

使用python将图片转化为base64字符串
```
import base64
f=open('723.png','rb') #二进制方式打开图文件
ls_f=base64.b64encode(f.read()) #读取文件内容，转换为base64编码
f.close()
print(ls_f)
base64字符串转化为图片
import base64
bs='iVBORw0KGgoAAAANSUhEUg....' # 太长了省略
imgdata=base64.b64decode(bs)
file=open('2.jpg','wb')
file.write(imgdata)
file.close()
```
2 公式
=========
由于GitHub 的 markdown 渲染是不支持公式的，推荐使用外链的方式。  
使用 [codecogs](https://editor.codecogs.com/)  

只需要写
`![](http://latex.codecogs.com/svg.latex?公式代码)`
有几个注意事项

1. 不要有多余的空格&回车（注意是多余）
2. \\ 要打2遍，因为转义

codecogs网站已更新，可以像word里的公式编辑器一样编写公式，输出选择svg，外链格式选Url Encodec 
例如：

代码  
```![](http://latex.codecogs.com/svg.latex?P(B%7CA)%20=%20%5Cfrac%7BP(AB)%7D%7BP(A)%7D) ```

svg效果图  
![](http://latex.codecogs.com/svg.latex?P(B%7CA)%20=%20%5Cfrac%7BP(AB)%7D%7BP(A)%7D) 

