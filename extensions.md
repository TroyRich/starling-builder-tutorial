# 如何构建自定义主题、自定义组件SWF文件

一、创建ActionScript项目。

![](https://raw.githubusercontent.com/yuhengh/starling-builder-tutorial/cn/images/extensions/01.png)

下载代码，如果有Git客户端从Git上copy项目代码
git clone https://github.com/mindjolt/starling-builder-extensions --recursive
否则下载扩展项目源代码，由于项目使用git子模块(submodule)管理依赖，直接下载zip文件会获取不到子模块， 所以要另外下载编辑器和引擎的源代码，扩展项目中有引用到，
小编推荐使用Git客户端copy

Git客户端下载地址：https://www.sourcetreeapp.com/

扩展项目源代码：https://github.com/mindjolt/starling-builder-extensions 

编辑器源代码：https://github.com/mindjolt/starling-builder-editor

引擎源代码：https://github.com/mindjolt/starling-builder-engine

复制扩展项目到新建的库根目录下，项目结构如图：

![](https://raw.githubusercontent.com/yuhengh/starling-builder-tutorial/cn/images/extensions/02.png)
 
二、配置

   1. 修改主源文件夹，项目下有个tests目录里面的代码可以测试我们修改的主题，很方便，在这里将tests/src作为主源文件，除此之外还要添加主题文件夹、组件文件夹、编辑器文件夹、引擎文件夹，如图

![](https://raw.githubusercontent.com/yuhengh/starling-builder-tutorial/cn/images/extensions/03.png)

   2. 添加库，即项目的libs文件夹

![](https://raw.githubusercontent.com/yuhengh/starling-builder-tutorial/cn/images/extensions/04.png)

三、修改代码，测试

以上配置就完成了，接下来就是修改主题或者组件的代码和ui。
修改完后，可以运行tests下的Main.as程序测试效果。
（调试小技巧：修改TestApp.as的createDisplayObject方法，比如小编想测试Button，
就可以修改成_object = new Button();

![](https://raw.githubusercontent.com/yuhengh/starling-builder-tutorial/cn/images/extensions/05.png)

![](https://raw.githubusercontent.com/yuhengh/starling-builder-tutorial/cn/images/extensions/06.png)

四、构建swf

测试没问题之后就可以使用ant命令在buildscript目录下编译swf，在此之前需要修改下配置文件，修改自己AIRSDK所在的路径，比如小编的AIRSDK就放在D盘根目录下。
重点：使用ant构建的时候一定要记得关掉Flash Builder

![](https://raw.githubusercontent.com/yuhengh/starling-builder-tutorial/cn/images/extensions/07.png)

![](https://raw.githubusercontent.com/yuhengh/starling-builder-tutorial/cn/images/extensions/08.png)

![](https://raw.githubusercontent.com/yuhengh/starling-builder-tutorial/cn/images/extensions/09.png)

构建成功后将在deliverable目录下生成swf文件，然后直接替换掉工作区下的libs文件夹里面swf文件，之后重启Starling Builder就可以了
(注意: 如过是修改组件，要先删除工作区根目录settings文件中的editor_template.json文件)

![](https://raw.githubusercontent.com/yuhengh/starling-builder-tutorial/cn/images/extensions/10.png)

![](https://raw.githubusercontent.com/yuhengh/starling-builder-tutorial/cn/images/extensions/11.png)
