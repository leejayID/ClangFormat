#代码格式化插件教程与配置
## 前言
统一团队内部编程风格，提高程序的可读性以及团队的编码效率，避免团队在开发过程中因为编码风格的差异可能带来的混乱。所以说代码规范对于团队的好处想必大家应该都知道。

当然，不仅对团队很重要，个人也很重要，如果你现在去了一家新的公司，上个人留下的代码风格跟你的差异很大，你看着也很难受。

有了这个插件，你就可以定制自己的代码风格，一键格式化，再也不用担心看别人的代码觉得难受，大大节约了你的时间。

## 正文
ClangFormat-Xcode：是一款Xcode的代码格式化插件 (github[下载链接](https://github.com/travisjeffery/ClangFormat-Xcode))，非常方便好用，可以极大减少花费调整代码规范的时间，提高编码效率。用了之后，妈妈再也用不担心我的编码规范了。
下面教大家怎么去配置ClangFormat-Xcode，打造一个属于自己的团队的代码规范。
### 安装插件
* 1.手动安装                          
和其他的插件一样，先去github下载工程，运行程程序安装。
* 2.自动安装           
如果安装过Alcatraz的同学，可以去可视化窗口搜索ClangFormat，点击Install自动安装。
![](http://upload-images.jianshu.io/upload_images/1321491-0e7c3785b41f96a5.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)  

### 配置参数
安装完成之后重启Xcode，点击Load Bundle，选择Xcode ->Edit，看到ClangFormat的选项，说明安装成功了。
![](http://upload-images.jianshu.io/upload_images/1321491-4cc76d071be9e3f6.jpeg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![ClangFormat菜单](http://upload-images.jianshu.io/upload_images/1321491-d3c30dadd0d4f3e5.jpeg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

我们可以看到有LLVM，Google，Chromium，Mozilla，WebKit，File这几种格式化风格，File就是我们自定义的风格。
下面我来教大家怎么去自定义风格。
首先创建一个".clang-format"文件，创建这个文件有两种方式：
* 1.终端创建：这边以DemoTest项目为例，打开终端，cd到**工程目录**下（一定要工程目录哦），创建一个".clang-format"文件。

![](http://upload-images.jianshu.io/upload_images/1321491-815db48a6114af89.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
```objc
$  cd /Users/xxx/DemoTest
$  vim .clang-fomat
```
然后将下面这些配置参数粘贴进去，这些参数是我根据我们团队的代码规范整理出来的（仅供参考），可能并不适合你们的团队，所有参数的含义下面都有说明：

``` objc
# 基础样式
BasedOnStyle: LLVM

# 缩进宽度
IndentWidth: 4

# 花括号的换行方式(Attach，Stroustrup, Allman-所有大括号都另起一行)
BreakBeforeBraces: Allman

# 支持一行的if
AllowShortIfStatementsOnASingleLine: false

# 是否允许循环单行
AllowShortLoopsOnASingleLine: false

# switch的case缩进
IndentCaseLabels: true

# 针对OC的block的缩进宽度
ObjCBlockIndentWidth: 4

# 针对OC，属性名后加空格
ObjCSpaceAfterProperty: true

# 每行字符的宽度限制，0不限制
ColumnLimit: 0

# 注释对齐
AlignTrailingComments: true

# 括号后加空格
SpaceAfterCStyleCast: true

# 不在小括号里加空格
SpacesInParentheses: false

# 不在中括号里加空格
SpacesInSquareBrackets: false

# 指针对准
# DerivePointerAlignment: true

# @[]里面两边空格，默认true
SpacesInContainerLiterals: false

# 赋值前(=)的空格 默认true
#SpaceBeforeAssignmentOperators: true

# 指针的位置
PointerAlignment: Right

# 最大空的行数
MaxEmptyLinesToKeep: 1
```

*  2.手动拖入：如果你觉得上面太麻烦，你也可以用比较简单粗暴的方法，把配置好的.clang-format文件直接拖到**工程目录**下，这边附上配置好的[.clang-format](https://github.com/leejayID/ClangFormat.git)。

### 基本使用
前面的配置成功之后，后面的使用就更简单了，打开你刚刚配置的工程，然后点击Xcode ->Edit->ClangFormat->Format Select Files，格式化整个文件中的代码。
下面附上两张格式化前和格式化后的截图：
格式化前：

![](http://upload-images.jianshu.io/upload_images/1321491-d227c40febbcc946.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![](http://upload-images.jianshu.io/upload_images/1321491-0b8f91bf5464b27a.jpeg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

格式化后：

![](http://upload-images.jianshu.io/upload_images/1321491-9c7eb4f8894e0d8e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
!![](http://upload-images.jianshu.io/upload_images/1321491-9ef3648252354843.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

是不是感觉一下子从凤姐变成了AngelaBaby，代码是是我们程序员的脸面，大家理应重视。
### 快捷键
快捷键的使用：可以给常用的操作设置快捷键，我们一般常用的操作是Format Select Files和Format Select Text两个功能。
* 1.Format Select Files是格式化当前文件的代码。设置快捷键：点击下面的Enable Format on Save（当它是Disable Format on Save状态就不用点了），插件会自动帮我们生成（Command+S）快捷键。

![](http://upload-images.jianshu.io/upload_images/1321491-782d411cc8723a4e.jpeg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
* 2.Format Select Text是格式化选中的代码。这个快捷键需要手动设置。

> (PS:第二个快捷键可以不用设置的，因为Format Select Files格式化当前文件已经够用了，感兴趣的同学可以试试)，打开设置->键盘->快捷键->点击右侧应用快捷键->添加。

![](http://upload-images.jianshu.io/upload_images/1321491-ea68021e8b27f1ca.jpeg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![](http://upload-images.jianshu.io/upload_images/1321491-18cbc31a63907da5.jpeg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

ok，大功告成！

## 最后
文中如果有错误的地方，还请大神指正。

如果你觉得看完后对你有所帮助，还望点个star。赠人玫瑰，手有余香。

