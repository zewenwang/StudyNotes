## JavaScript 学习记录

Date:  20151204

#### 1. Code Tips








#### 2. Tips




#### 3. 正则表达式
```JavaScript
var str = "Visit w3cschool!";
var n = str.search("w3cschool"); // n为6
var res = str.replace(/microsoft/i, "w3cschool"); // res为 "Visit Microsoft"
```
修饰符 | 描述（修饰符不区分大小写）
:|:
i | 执行对大小写不敏感的匹配。
g | 执行全局匹配（查找所有匹配而非在找到第一个匹配后停止）。
m | 执行多行匹配。

- 正则表达式方法
    - test() 检测一个字符串是否匹配某个模式，如果字符串中含有匹配的文本，则返回 true，否则返回 false。
    - exec() 方法用于检索字符串中的正则表达式的匹配。  **??**
    该函数返回一个数组，其中存放匹配的结果。如果未找到匹配，则返回值为 null。

[完整参考手册](http://www.runoob.com/jsref/jsref-obj-regexp.html)

#### 4. 
