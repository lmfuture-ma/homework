问题：
-------
有一个 100GB 的文件，里面内容是文本， 要求：
+ 假定：每行都是`,`分隔的字符串
+ 找出第一个不重复的词
+ 只允许扫一遍原文件
+ 尽量少的 IO
+ 内存限制 16G

思路：
--------
1. 把大文件切割成若干小文件， 保证每个小文件大小不超过内存限制
2. 读取字符串同时记录索引， 根据字符串哈希值取余选择一个文件，写入 "字符串|索引\n"
3. 依次读取文件，利用hashmap,key记录字符串，value保存出现的次数和索引，遍历map取出次数为1并且索引最小的字符串
   遍历所有文件完成之后，即选中第一个不重复的词

 使用
 -------
 ```shell script                            
  ## build 
  go build .   

  ## run 
  ./homework -file words.txt -count 10
 ```

