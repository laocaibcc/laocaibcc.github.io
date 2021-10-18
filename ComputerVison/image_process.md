## 图像


### 1. 数字图像

> 数字图像，是二维图像用有限数字数值（又称像素）的表示。 - [1]

常见的数字图像，根据其特性，可以分为两类：位图和矢量图。

> 位图（英语：Bitmap），又称栅格图（Raster graphics），是使用像素阵列(Pixel-array/Dot-matrix点阵)来表示的图像。 - [2]

> 矢量图形是计算机图形学中用点、直线或者多边形等基于数学方程的几何图元表示的图像。 - [3]

参考资料：
- [1] [Digital image](https://en.wikipedia.org/wiki/Digital_image)
- [2] [Raster graphics](https://en.wikipedia.org/wiki/Raster_graphics)
- [3] [Vector graphics](https://en.wikipedia.org/wiki/Vector_graphics)

#### 位图与矢量图的比较

图像特征\图像类型 | 矢量图 | 位图
--- | --- | ---
分辨率 |	scalable	| pixel, device dependent
文件大小 |	small	| large, depends on exported resolution
应用场景 | Fonts，Logos，Coin designs， laser engravings，T-shirts， Patches，Digital printing (e.g., business cards, billboards)， Lower thirds for video， 2D or 3D computer animation | Photography， Print Materials
文件类型 | EPS, SVG, AI | BMP, GIF, JPG, PNG, TIFF
软件 | Vector-based software (e.g., Adobe Illustrator) | Raster-based software (e.g., Adobe Photoshop), Digital cameras, Scanned images

参考资料：
- [1] [Raster vs Vector](http://vector-conversions.com/vectorizing/raster_vs_vector.html)
- [2] [VECTOR VS. RASTER IMAGES: CHOOSING THE RIGHT FORMAT](https://pavilion.dinfos.edu/Article/Article/2223089/vector-vs-raster-images-choosing-the-right-format/)

<br>

### 2. 数字图像（位图）分类


根据每个像素所代表信息的不同，可将图像分为
- **二值图像**：每个像素只有黑、白两种颜色的图像称为二值图像。在二值图像中，像素只有0和1两种取值，一般用0来表示黑色，用1表示白色。
- **灰度图像**：二值图像中进一步加入许多介于黑色与白色之间的颜色深度，就构成了灰度图像。这类图像通常显示为从最暗黑色到最亮的白色的灰度，每种灰度（颜色深度）称为一个灰度级。
- **RGB 图像**：自然界中几乎所有颜色都可以由红（Red, R）、绿（Green, G）、蓝（Blue, B）3种颜色组合而成，通常称它们为 RGB 三原色。计算机显示彩色图像时采用最多的就是 RGB 模型，对于每个像素，通过控制R、G、B三原色的合成比例决定该像素的最终显示颜色。
- **索引图像**：索引图像是一种把像素值直接作为RGB调色板下标的图像。索引图像可把像素值“直接映射”为调色板数值。索引图像像素点存放的是调色板中的下标，具有颜色不容易失真，存储文件小的优势。


参考资料：
- [1] [索引图像](https://linzhenyuyuchen.github.io/2020/01/21/%E7%B4%A2%E5%BC%95%E5%9B%BE%E5%83%8F/)
- [2] [Indexed color](https://en.wikipedia.org/wiki/Indexed_color)

<br>

### 3. 图像处理简介

> "图像处理，是对图像进行分析、加工、和处理，使其满足视觉、心理以及其他要求的技术。" - [1]

### 典型问题

- **图像增强**：图像增强的目的是为了提高图像的质量，如去除噪声，提高图像的清晰度等。
  - 图像平滑
  - 图像锐化
  - 边缘增强
- **图像变换**：包括放大、缩小、旋转等。
  - 傅立叶变换
  - 沃尔什变换
  - 离散余弦变换
  - 小波变换
- **颜色处理**：颜色空间的转化、亮度以及对比度的调节、颜色修正等。
- **图像分割**：图像分割是将图像中有意义的特征部分提取出来，这是进一步进行图像识别、分析和理解的基础。
  - 传统图像分割方法
  - 深度学习图像分割
- **图像编码压缩**：图像编码压缩技术可减少描述图像的数据量（即比特数），以便节省图像传输、处理时间和减少所占用的存储器容量。压缩可以在不失真的前提下获得，也可以在允许的失真条件下进行。
  - 图像编码
- **图像分类**（识别）：图像分类（识别）属于模式识别的范畴，其主要内容是图像经过某些预处理（增强、复原、压缩）后，进行图像分割和特征提取，从而进行判决分类。图像分类常采用经典的模式识别方法，有统计模式分类和句法（结构）模式分类，近年来新发展起来的模糊模式识别和人工神经网络模式分类在图像识别中也越来越受到重视。
- **图像融合**（image composite）：多个图像的加、减、组合、拼接。
- **图像配准**：比较或集成不同条件下获取的图像。
- **图像数字水印**：研究图像域的数据隐藏、加密、或认证。
- **图像编辑**：和计算机图形学有一定交叉。


参考资料：
- [1] [Digital image processing](https://en.wikipedia.org/wiki/Digital_image_processing)
