# Starling Builder教程扩展篇（三、扩展组件）

细心的朋友可能发现了，扩展主题的过程中已经看到组件的影子，没错扩展组件的过程很主题很类似。为了示范，小编个可渐变的Quad组件

一、编写代码

在扩展项目中的ui组件目录即ui-components目录中新建一个GradientQuad类, 结构如图：
类里面的代码可以看项目，此组件已经合并到作者Git上的扩展项目中，为方便阅读这里给出完整代码

```java
package starlingbuilder.extensions.uicomponents
{
    import starling.display.Quad;
    /**
     *颜色渐变的quad
     *author WG
     *2016-3-7
     */
    public class GradientQuad extends Quad
    {
        private var _topLeftColor:uint;
        private var _topRightColor:uint;
        private var _bottomLeftColor:uint;
        private var _bottomRightColor:uint;
        public function GradientQuad(width:Number, height:Number, color:uint=0xffffff, premultipliedAlpha:Boolean=true ):void
        {
            super(width, height, color, premultipliedAlpha);

            _topLeftColor = _topRightColor = _bottomLeftColor = _bottomRightColor = 0xffffff;
        }
        public function set topLeftColor(value:uint):void
        {
            _topLeftColor = value;
            setVertexColor(0, value);
        }
        public function set topRightColor(value:uint):void
        {
            _topRightColor = value;
            setVertexColor(1, value);
        }
        public function set bottomLeftColor(value:uint):void
        {
            _bottomLeftColor = value;
            setVertexColor(2, value);
        }
        public function set bottomRightColor(value:uint):void
        {
            _bottomRightColor = value;
            setVertexColor(3, value);
        }
        public function get topLeftColor():uint
        {
            return _topLeftColor;
        }
        public function get topRightColor():uint
        {
            return _topRightColor;
        }
        public function get bottomLeftColor():uint
        {
            return _bottomLeftColor;
        }
        public function get bottomRightColor():uint
        {
            return _bottomRightColor;
        }
    }
}
```

![](https://raw.githubusercontent.com/yuhengh/starling-builder-tutorial/cn/images/components/01.png)

修改custom_component_template.json文件, 添加新加的组件类，这样在编辑器上才能看到新加的组件


![](https://raw.githubusercontent.com/yuhengh/starling-builder-tutorial/cn/images/components/02.png)

二、测试

在测试目录即test目录下添加测试该组件的工厂，小编这里添加个GradientQuadFactory类，
测试工厂类的创建需要继承IDisplayObjectFactory接口，添加注释，每一个组件需要对应一个测试类以方便测试。具体代码看项目

![](https://raw.githubusercontent.com/yuhengh/starling-builder-tutorial/cn/images/components/03.png)

写好该组件的测试工厂类后，在TestApp.as中赋值给SINGLE_COMPONENT，并在ALL_COMPONENTS数组中，如图。 最后运行项目

![](https://raw.githubusercontent.com/yuhengh/starling-builder-tutorial/cn/images/components/04.png)

![](https://raw.githubusercontent.com/yuhengh/starling-builder-tutorial/cn/images/components/05.png)

三、构建组件的swf。此过程跟扩展主题一样，使用ant命令构建。

四、编辑器中的使用。此过程在扩展主题基础上，先删掉settings目录下的editor_template.json，重启编辑器可以发现多了一个

![](https://raw.githubusercontent.com/yuhengh/starling-builder-tutorial/cn/images/components/06.png)

五、扩展组件在游戏项目中的使用
这个比主题容易些只需两步

1、将GradientQuad类复制到项目中，注意GradientQuad的路径一定要和扩展项目中的json中写的路径一致，如图

![](https://raw.githubusercontent.com/yuhengh/starling-builder-tutorial/cn/images/components/07.png)

![](https://raw.githubusercontent.com/yuhengh/starling-builder-tutorial/cn/images/components/08.png)

2、加上引用代码，因为我们只在编辑器上添加，项目中并没有引用到GradientQuad类，如果不引用这个类，编译的时候不会将GradientQuad嵌入到swf中，所以加上一行类似这样的代码，加载任何地方都行随你喜欢，静态是为了项目运行的时候第一时间执行到。

```actionscript
public static const linkers:Array = [ContainerButton, GradientQuad];
```

希望大家可以多开发些好用的组件

完

