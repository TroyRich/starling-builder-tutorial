# Starling Builder教程扩展篇（二、扩展主题）

一、编写主题

作者已经给大家好了一个现成的主题，代码—修改BaseTestGameMobileTheme类，UI—修改assets目录下的资源

![](https://raw.githubusercontent.com/yuhengh/starling-builder-tutorial/cn/images/theme/01.png)

二、测试主题

看代码可以发现，作者已经在测试项目中默认使用了测试主题，只需要运行项目即可，
正式项目中还应该删掉原来的主题，删除new MetalWorksDesktopTheme2(this);即可

![](https://raw.githubusercontent.com/yuhengh/starling-builder-tutorial/cn/images/theme/02.png)

三、构建主题的swf

Swf文件主要给编辑器使用，作者已经给大家好构建的用到的build文件，只需要在buildscript目录下执行ant命令即可在deliverable目录下获得swf。使用ant命令前记得先修改AIRSDK的路径，就是build.properties文件，作者放地方的可跟小编不一样。

![](https://raw.githubusercontent.com/yuhengh/starling-builder-tutorial/cn/images/theme/03.png)
![](https://raw.githubusercontent.com/yuhengh/starling-builder-tutorial/cn/images/theme/04.png)

![](https://raw.githubusercontent.com/yuhengh/starling-builder-tutorial/cn/images/theme/05.png)

![](https://raw.githubusercontent.com/yuhengh/starling-builder-tutorial/cn/images/theme/06.png)

四、编辑器中的使用

只需要将获得EmbeddedTheme.swf文件复制到编辑器workspace目录下的lib文件夹内，在重启编辑器即可。

![](https://raw.githubusercontent.com/yuhengh/starling-builder-tutorial/cn/images/theme/07.png)

五、在游戏项目中的使用

在游戏项目的src目录下创建starlingbuilder.extensions.themes目录，然后将扩展项目中的themes代码复制进来，还有ui资源也复制进来，具体结构如下图。

![](https://raw.githubusercontent.com/yuhengh/starling-builder-tutorial/cn/images/theme/08.png)

修改代码
单单复制代码和资源还不行的，还需要做些小改动

1、修改BaseTestGameMobileTheme.as将 BaseTestGameMobileTheme extends UIEditorTheme
改成：BaseTestGameMobileTheme extends StyleNameFunctionTheme。去掉构造函数的themeMediator参数

改之前

![](https://raw.githubusercontent.com/yuhengh/starling-builder-tutorial/cn/images/theme/09.png)

![](https://raw.githubusercontent.com/yuhengh/starling-builder-tutorial/cn/images/theme/10.png)

改之后

![](https://raw.githubusercontent.com/yuhengh/starling-builder-tutorial/cn/images/theme/11.png)

![](https://raw.githubusercontent.com/yuhengh/starling-builder-tutorial/cn/images/theme/12.png)

2、修改TestGameMobileTheme.as，因为继承关系所以同样要去掉构造函数的themeMediator参数，图片参照上面的

3、在项目初始化代码中添加扩展主题，只需一行代码

```
new TestGameMobileTheme(false);
```

如图：

![](https://raw.githubusercontent.com/yuhengh/starling-builder-tutorial/cn/images/theme/13.png)


