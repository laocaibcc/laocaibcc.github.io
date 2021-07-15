
## Linux 打包压缩

UPDATE: Apr.21 2019<br>
Author: laocai

### 1. Linux下常见打包压缩工具

Linux下压缩工具挺多，但有些工具只能对一个文件进行压缩，对一大堆文件进行压缩并不方便。因此，在Linux下常用tar对文件进行打包的同时压缩。

Linux下常用的压缩工具有：
- zip/unzip
- gzip/gunzip
- bzip2/bunzip2
- xz/unxz
- compress/uncompress
- lzma/unlzma
- 7z


更多信息可以参考：
- [An Introduction to File Compression Tools on Linux Servers](https://www.digitalocean.com/community/tutorials/an-introduction-to-file-compression-tools-on-linux-servers)
- [compressing files](https://www.cyberciti.biz/howto/question/general/compress-file-unix-linux-cheat-sheet.php)
- [Linux下压缩工具详解](https://blog.51cto.com/ucode/1842572)


#### tar命令

```sh
# 第一选项（默认小写，大写会注明）
-c ：创建归档文件
-x ：解包归档文件
-t ：列出归档文件的内容列表
-r ：向归档文件中添加（替换）文件（只对未压缩的归档文件有效）
-u ：更新归档文件中的内容（只对未压缩的归档文件有效

# 压缩选项（指定压缩方法，当前的版本一般能够识别压缩算法，可以不添加，但建议添加）：
-z，-j，-J，-a，分别对应于 gzip，bzip2，xz，lzma 四种压缩命令。

# 通用选项：
-v ：开启更详细的输出信息
-w ：交互模式
-f ：指定归档文件的位置（在f之后要立即接打包文件名！不要再加参数！）

# tar 格式
tar -cvf Archive.tar DirName  # 压缩
tar -xvf Archive.tar  # 解压

# tar.gz 或 tgz 格式
tar -czvf FileName.tar.gz DirName  # 压缩
tar -xzvf FileName.tar.gz  # 解压

# tar.bz 或 tar.bz2 格式（其余压缩格式类似）
tar -cjvf FileName.tar.bz DirName # 压缩
tar -xjvf FileName.tar.bz # 解压
```
注：
- 在上面的参数中， 第一选项仅能存在一个，不可同时存在。
- f指定打包的文件名，切记，这个参数是最后一个参数（不能再接其它参数），后面只能接打包文件名。
- 参数可以合并在一起，也可以单独分开。

##### 对应压缩算法与工具

tar压缩选项 | 压缩文件后缀 | 压缩工具
--- | --- | ---
z | .gz | gzip
j | .bz 或 .bz2 | bzip2
Z | .Z | compress
J | .xz | xz
a | .lzma | lzma

tar命令的详细参数可以参考：
- [tar命令](http://man.linuxde.net/tar)
- [Linux 打包 压缩 解压 命令详解](https://rollingstarky.github.io/2018/03/11/use-tar-to-package-and-compress-files/)
- [Linux文件打包和压缩命令总结](https://www.kawabangga.com/posts/2144)
- [Linux压缩打包tar命令总结](http://www.cnblogs.com/kerrycode/p/9827742.html)



#### zip & unzip

zip可以对多个文件打包并压缩，自带打包归档功能，是Linux/Mac/Windows比较通用的一个工具。
```sh
# 压缩文件
zip myzip.zip file1 file2 file3

# 解压文件
unzip myzip.zip
```

zip与unzip的详细参数，可以使用man，也可以参考
- [zip命令](http://man.linuxde.net/zip)
- [unzip命令](http://man.linuxde.net/unzip)

#### 7-Zip

7-Zip也是当前最普及的开源压缩程序，Linux版本为p7zip。 - [7-Zip](https://zh.wikipedia.org/wiki/7-Zip)

7z, 7za与7zr的区别
> - 7z uses plugins to handle archives.
> - 7za is a stand-alone executable that handles fewer archive formats than 7z.
> - 7zr is a stand-alone executable. It is a "light-version" of 7za that only handles 7z archives. In contrast to 7za, it cannot handle encrypted archives. - [p7zip](https://wiki.archlinux.org/index.php/p7zip)

```sh
# 第一选项
a  添加
d  删除
e  解压
x  带路径解压
l  列表查看
t  测试
u  更新

# 压缩文件
7z a myfile.7z file1  # 7za同
# 解压文件
7z e myfile.7z
```

7z/7za详细的参数解释可以参考：
- [7zip命令行使用简略手册
](http://www.freeoa.net/scheme/manual/7zip-cmd-brief-man_2137.html)

<br>

### 2. 常见压缩算法的比较与选择

有文章对Linux下各种压缩算法进行了简单的实验和对比：
- [Linux下的文件打包和压缩](https://www.jianshu.com/p/38b32107bc3e)

初步结果如下（原数据为4G大小的文件，配置和资源等）：
命令 | 发布时间 | 压缩算法 | 压缩用时 | 解压用时 | 压缩后的大小
--- | --- | --- | --- | --- | ---
zip | 1990 | DEFLATE | 2m43s | 2m15s | 796MB
gzip | 1993 | DEFLATE | 2m34s | 32s | 796MB
bzip2 | 1996 | Burrows-Wheeler | 9m20s | 2m1s | 660MB
xz | 2009 | LZMA,LZMA2 | 28m31s | 1m3s | 474MB
7za | 1999 | LZMA,LZMA2 | 1m51s | 52s | 487MB

下文对几种压缩工具进行了详细的对比，更多可以参考：
- [Quick Benchmark: Gzip vs Bzip2 vs LZMA vs XZ vs LZ4 vs LZO](https://catchchallenger.first-world.info/wiki/Quick_Benchmark:_Gzip_vs_Bzip2_vs_LZMA_vs_XZ_vs_LZ4_vs_LZO)


#### 初步小结

- 日常使用中，临时性的压缩尽量选择压缩与解压时间较快的压缩格式。比如: ```.gz```
- 归档存储的可以选择压缩率比较大的压缩格式。比如：```.7z```