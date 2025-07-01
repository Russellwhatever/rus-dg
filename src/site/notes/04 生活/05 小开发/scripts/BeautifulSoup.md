---
{"dg-publish":true,"permalink":"/04/05/scripts/beautiful-soup/","noteIcon":"","created":"2025-01-31T00:35","updated":"2025-07-01T20:58"}
---

#Code/spider #Code/爬虫 
https://cuiqingcai.com/1319.html
# 1. 基本介绍
## 1. 四种tag
```python
html = """ XXXXXXX"""
soup = BeautifulSoup(html)
```
![99 Attachment/Pasted image 20250120135442.png](/img/user/99%20Attachment/Pasted%20image%2020250120135442.png)
title, head, a, p
不过只能获得第一个
- 每个tag有属性，最重要的是name和attrs
name就是tag名，title、head、a、p
attrs就是所有内容，是个字典。
```python
print soup.p.attrs
#{'class': ['title'], 'name': 'dromouse'}

print soup.p['class']
#['title']

print soup.p.get('class')
#['title']
```
从而获取信息（如上）或者修改信息：
```python
soup.p['class'] = "newClass"
#删除
del soup.p['class']
```
## 2. NavigableString获取标签内部的文字
```python
print soup.p.string
```
## 3. BeautifulSoup
本身是一个文档的全部内容，可以视为一个特殊的tag对象
```python
print type(soup.name)
#<type 'unicode'>
print soup.name 
# [document]
print soup.attrs 
#{} 空字典
```
## 4. Comment一种特殊的NavigableString对象
![99 Attachment/Pasted image 20250120140415.png](/img/user/99%20Attachment/Pasted%20image%2020250120140415.png)
正常直接使用.string，会把注释内容（图里的<!-- Elsie -->）直接去掉注释符号，会导致意想不到的麻烦，所有不能直接使用string，可以使用Comment先判断一下
```python
if type(soup.a.string) == bs4.element.Comment:
    XXXXX
```
# 操作
## 1. 直接子节点
    .contents .children .descendants
```python
print soup.head.contents
```
将tag的子节点以列表形式输出
```python
for child in soup.body.children:
    print child
```
将tag的子节点以生成器对象形式输出
![99 Attachment/Pasted image 20250120141017.png](/img/user/99%20Attachment/Pasted%20image%2020250120141017.png)

## 2. 间接子节点 
```python
for child in soup.descendants:
    print child
```
同样是生成器，不过包含所有子孙节点。上面这段代码的结果如下：
```python
<html><head><title>The Dormouse's story</title></head>
<body>
<p class="title" name="dromouse"><b>The Dormouse's story</b></p>
<p class="story">Once upon a time there were three little sisters; and their names were
<a class="sister" href="http://example.com/elsie" id="link1"><!-- Elsie --></a>,
<a class="sister" href="http://example.com/lacie" id="link2">Lacie</a> and
<a class="sister" href="http://example.com/tillie" id="link3">Tillie</a>;
and they lived at the bottom of a well.</p>
<p class="story">...</p>
</body></html>
<head><title>The Dormouse's story</title></head>
<title>The Dormouse's story</title>
The Dormouse's story


<body>
<p class="title" name="dromouse"><b>The Dormouse's story</b></p>
<p class="story">Once upon a time there were three little sisters; and their names were
<a class="sister" href="http://example.com/elsie" id="link1"><!-- Elsie --></a>,
<a class="sister" href="http://example.com/lacie" id="link2">Lacie</a> and
<a class="sister" href="http://example.com/tillie" id="link3">Tillie</a>;
and they lived at the bottom of a well.</p>
<p class="story">...</p>
</body>


<p class="title" name="dromouse"><b>The Dormouse's story</b></p>
<b>The Dormouse's story</b>
The Dormouse's story


<p class="story">Once upon a time there were three little sisters; and their names were
<a class="sister" href="http://example.com/elsie" id="link1"><!-- Elsie --></a>,
<a class="sister" href="http://example.com/lacie" id="link2">Lacie</a> and
<a class="sister" href="http://example.com/tillie" id="link3">Tillie</a>;
and they lived at the bottom of a well.</p>
Once upon a time there were three little sisters; and their names were

<a class="sister" href="http://example.com/elsie" id="link1"><!-- Elsie --></a>
 Elsie 
,

<a class="sister" href="http://example.com/lacie" id="link2">Lacie</a>
Lacie
 and

<a class="sister" href="http://example.com/tillie" id="link3">Tillie</a>
Tillie
;
and they lived at the bottom of a well.


<p class="story">...</p>
...
```
## 3. 节点内容
    .string
如果tag包含了多个子节点，tag无法确定，输出结构就会是None
## 4. 多个内容
    .strings .stripped_strings
.strings获取多个内容，不须遍历获取；.stripped_strings去除多余的空格空行内容
## 5. 父节点
    .parent
```python
p = soup.p
print p.parent.name
#body
```
```python
content = soup.head.title.string
print content.parent.name
#title
```
    .parents
```python
content = soup.head.title.string
for parent in content.parents:
    print parent.name
#title
#head
#html
#[document]
```
## 6. 兄弟节点
    .next_sibling .previous_sibling
前者获取该节点的下一个兄弟节点，后者相反；如果节点不存在，返回None
**实际经常为空白**：因为空白或者换行也被视作一个节点
    .next_siblings .previous_siblings
全部兄弟节点
```python
for sibling in soup.a.next_siblings:
    print(repr(sibling))
```
## 7. 前后节点
    .next_element .previous_element
不分层次，只管前后顺序
![99 Attachment/Pasted image 20250120142432.png](/img/user/99%20Attachment/Pasted%20image%2020250120142432.png)
类似地，也有所有前后节点
    .next_elements .previous_elements
# 3. 搜索文档
## 1. find_all(name, attrs, recursive, text, **kwargs)
- 传字符串
```python
soup.find_all('a')
```
对**tag**带a的进行搜索
- 传正则表达式
![99 Attachment/Pasted image 20250120142853.png](/img/user/99%20Attachment/Pasted%20image%2020250120142853.png)
- 传列表，返回所有内容的匹配结果
- 传True，返回所有
- 传方法
![99 Attachment/Pasted image 20250120143007.png](/img/user/99%20Attachment/Pasted%20image%2020250120143007.png)
## keyword搜索，比如
![99 Attachment/Pasted image 20250120143245.png](/img/user/99%20Attachment/Pasted%20image%2020250120143245.png)
可以多keyword
如果keyword是class这样本身是关键词的，加个下划线：
```python
soup.find_all("a", class_="sister")
# [<a class="sister" href="http://example.com/elsie" id="link1">Elsie</a>,
#  <a class="sister" href="http://example.com/lacie" id="link2">Lacie</a>,
#  <a class="sister" href="http://example.com/tillie" id="link3">Tillie</a>]
```
- 具体来说，文档中内容用.text搜索
## limit限制搜索量
```python
soup.find_all("a", limit=2)
```
## recursive设置迭代与否
不想看子孙节点就设置成false![99 Attachment/Pasted image 20250120143615.png](/img/user/99%20Attachment/Pasted%20image%2020250120143615.png)
## 2. find(name, attrs, recursive, text, **kwargs)
find_all返回列表，find直接返回结果
## 3. find_parents() find_parent(), find_next_siblings() find next_sibling(), find_previous_siblings() find_previous_sibling(), find_all_next() find_next(), find_all_previous() find_previous()
# 4. CSS选择器：find_all平替
    soup.select()
返回list
```python
print soup.select('title') #返回title tag的
print soup.select('.sister') #通过类名：class="sister"
print soup.select('#link1') #通过id名查找
print soup.select('p #link1') #组合查找：中间用空格隔开就行
print soup.select('a[class="sister"]')
```
以上这些都返回list，可以用get_text()方法获取内容
```python
soup = BeautifulSoup(html, 'lxml')
print type(soup.select('title'))
print soup.select('title')[0].get_text()

for title in soup.select('title'):
    print title.get_text()
```
