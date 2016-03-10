# 扩展组件的制作与使用

小编正学习怎么做扩展组件，作者推荐小编试试做个渐变的quad，看起来比较简单，拿它试试吧，以下是制做过程

一、编写代码
在项目中新建一个GradientQuad类, 代码很简单就是设置四个点的颜色，详细内容可以看我的项目代码

![](https://raw.githubusercontent.com/yuhengh/starling-builder-tutorial/cn/images/components/01.png)

二、修改custom_component_template.json文件, 添加我们新加的类，用于显示在编辑器上

![](https://raw.githubusercontent.com/yuhengh/starling-builder-tutorial/cn/images/components/02.png)

三、调试，只需要修改下TestApp的_object指向我们的新加的类，就可以调试了

![](https://raw.githubusercontent.com/yuhengh/starling-builder-tutorial/cn/images/components/03.png)

这是调试看到的效果，OK

![](https://raw.githubusercontent.com/yuhengh/starling-builder-tutorial/cn/images/components/04.png)


四、构建swf文件，只需要在buildscript目录下执行ant命令就可以在deliverable目录下生成EmbeddedComponents.swf。得到swf文件后，替换掉编辑器工作区libs目录下的EmbeddedComponents.swf，删掉settings目录下的editor_template.json，重启编辑器。
(使用ant命令记得修改配置文件中AIRSDK的路径，不明白请看上一篇扩展主题制作教程)

![](https://raw.githubusercontent.com/yuhengh/starling-builder-tutorial/cn/images/components/05.png)

![](https://raw.githubusercontent.com/yuhengh/starling-builder-tutorial/cn/images/components/06.png)
![](https://raw.githubusercontent.com/yuhengh/starling-builder-tutorial/cn/images/components/07.png)

![](https://raw.githubusercontent.com/yuhengh/starling-builder-tutorial/cn/images/components/08.png)

![](https://raw.githubusercontent.com/yuhengh/starling-builder-tutorial/cn/images/components/09.png)

五、	扩展组件在项目中的使用，这个比主题容易些只需两步
	
  1、将GradientQuad类复制到项目中，注意路径一定要json中的路径一致
    
![](https://raw.githubusercontent.com/yuhengh/starling-builder-tutorial/cn/images/components/10.png)

![](https://raw.githubusercontent.com/yuhengh/starling-builder-tutorial/cn/images/components/11.png)
    
   2、加上引用代码，因为我们只在编辑器上添加，项目中并没有引用到GradientQuad类，如果不引用这个类，编译的时候不会将GradientQuad嵌入到swf中，所以加上一行类似这样的代码，加载任何地方都行随你喜欢，静态是为了项目运行的时候第一时间执行到。
public static const linkers:Array = [ContainerButton, GradientQuad];