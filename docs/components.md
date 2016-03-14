# Starling Builder Extensions Tutorial (3. Create custom UI components)

As you run the test project, you already see it's used for testing UI component.
Writing custom UI components is similar to extending feathers theme.
In order to demonstrate how it works, I am making a gradient quad as an example.

1. Write the component code

Create a new class called GradientQuad inside starlingbuilder.extensions.uicomponents.

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

Modify custom_component_template.json as below, the JSON data tells the editor what is editable and what components are used to edit

![](https://raw.githubusercontent.com/yuhengh/starling-builder-tutorial/cn/images/components/02.png)

2. Test the component

Add a factory class in tests folder to test the component just created. Here we added a GradientQuadFactory class.
The factory class needs to implement IDisplayObjectFactory interface. For testing purpose, every component needs to corresponde to a factory.

![](https://raw.githubusercontent.com/yuhengh/starling-builder-tutorial/cn/images/components/03.png)

After writing the test class, you can assign it to SINGLE_COMPONENT to test it right away. You should also put it inside ALL_COMPONENTS array used by automated tests.
Launch the test app and you will see something as below:

![](https://raw.githubusercontent.com/yuhengh/starling-builder-tutorial/cn/images/components/04.png)

![](https://raw.githubusercontent.com/yuhengh/starling-builder-tutorial/cn/images/components/05.png)


3. Create EmbeddedComponents.swf.

It's similar to creating EmbeddedTheme.swf in the previous tutorial. Type ant to build.

4. Use it in the editor.

It's also similar to using EmbeddedTheme.swf in the previous tutorial.
Drop EmbeddedComponents to libs folder inside your workspace. 
The only difference is you need to DELETE WORKSPACE/settings/editor_template.json first, then reload the editor.
Now you see the newly created GradientQuad components inside the editor

![](https://raw.githubusercontent.com/yuhengh/starling-builder-tutorial/cn/images/components/06.png)

5. Use it in your game project


  1. Copy GradientQuad to your game project. Make sure the package name is the same as the one in the extension project

![](https://raw.githubusercontent.com/yuhengh/starling-builder-tutorial/cn/images/components/07.png)

![](https://raw.githubusercontent.com/yuhengh/starling-builder-tutorial/cn/images/components/08.png)

  2. You may need to link the class if there's no reference in your game project, otherwise the compiler won't linked it into the game. Something likes this should work, you can put it anywhere.

```actionscript
public static const linkers:Array = [ContainerButton, GradientQuad];
```

I wish you enjoy the tutorial and create more useful UI components.

End

