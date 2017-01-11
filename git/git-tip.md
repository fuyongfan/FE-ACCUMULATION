## git add . 时发生警告  LF will be replaced by CRLF               
```            
$ git add .          
warning: LF will be replaced by CRLF in 1.txt.
The file will have its original line endings in your working directory.
```       
1. 出现这个警告的原因和git安装时的配置有关                                                                              
```
安装git时的选项：              　　　
a. Checkout Windows-style,commit Unix-style line endings.

b.Checkout as-is,commit Unix-style line endings.

c.Checkout as-is,commit as-is line endings.
```      

```          
a.     
检出时，git 会把文本文件的换行符转化为 CRLF（只转化纯 LF 的文件）
提交时，把暂存区的内容（也就是我们对工作区做的改动）转化为 LF 然后放入版本库。
```         
2. 三种处理的含义                     
> CRLF->Windows-style            
> LF->Unix Style            
> CR->Mac Style                            
> CRLF表示句尾使用回车换行两个字符(即我们常在Windows编程时使用"\r\n"换行)             
> LF表示表示句尾，只使用换行.           
> CR表示只使用回车.                                                           

3. 更改此设置的方法（除了重装 git）                    
```            
$git config --global core.autocrlf true
```          
```           
配置含义 ：              　
1) true:             x -> LF -> CRLF
2) input:            x -> LF -> LF
3) false:            x -> x -> x
```                                        
4. 配置了core.autocrlf true （多人协作开发建议为 true）如何消除警告                              
> 添加到暂存区的文件只包含 CRLF（即用windows换行形成的文件） 警告自动消失             
