# Starling Builder Extensions Tutorial (2. Extend Feathers Theme)

##### 1. Write the Theme #####

There's already an existing working theme called TestGameMobileTheme.
You can modify it to your need.

![](https://raw.githubusercontent.com/yuhengh/starling-builder-tutorial/cn/images/theme/01.png)

##### 2. Test the Theme #####

You can see the test project is already using TestGameMobileTheme, you can just launch the test app to test it.

![](https://raw.githubusercontent.com/yuhengh/starling-builder-tutorial/cn/images/theme/02.png)

##### 3. Create EmbeddedTheme.swf #####

The swf file is created for editor's use. You can cd buildscript and type ant to build the swf under deliverable folder.
Before using ant remember change the path of AIRSDK to your SDK location.

![](https://raw.githubusercontent.com/yuhengh/starling-builder-tutorial/cn/images/theme/03.png)
![](https://raw.githubusercontent.com/yuhengh/starling-builder-tutorial/cn/images/theme/04.png)

![](https://raw.githubusercontent.com/yuhengh/starling-builder-tutorial/cn/images/theme/05.png)

![](https://raw.githubusercontent.com/yuhengh/starling-builder-tutorial/cn/images/theme/06.png)

##### 4. Use EmbeddedTheme.swf in the editor #####

You just need to drop the generated EmbeddedTheme.swf to libs folder inside editor's workspace, then reload the eidtor.

![](https://raw.githubusercontent.com/yuhengh/starling-builder-tutorial/cn/images/theme/07.png)

##### 5. Use the theme in the game project #####

Copy starlingbuilder.extensions.themes package to your game project, as well as the theme assets. Image as below:

![](https://raw.githubusercontent.com/yuhengh/starling-builder-tutorial/cn/images/theme/08.png)

You also need to slightly modify the code

1. Modify BaseTestGameMobileTheme.as, change BaseTestGameMobileTheme extends UIEditorTheme to
  BaseTestGameMobileTheme extends StyleNameFunctionTheme. Remove the themeMediator parameter from the constructor

  Before modify

  ![](https://raw.githubusercontent.com/yuhengh/starling-builder-tutorial/cn/images/theme/09.png)

  ![](https://raw.githubusercontent.com/yuhengh/starling-builder-tutorial/cn/images/theme/10.png)

  After modify

  ![](https://raw.githubusercontent.com/yuhengh/starling-builder-tutorial/cn/images/theme/11.png)

  ![](https://raw.githubusercontent.com/yuhengh/starling-builder-tutorial/cn/images/theme/12.png)

2. Modify TestGameMobileTheme.as, also remove the themeMediator parameter from the constructor
3. Add the following code to in your game project

```
new TestGameMobileTheme(false);
```

Image as below:

![](https://raw.githubusercontent.com/yuhengh/starling-builder-tutorial/cn/images/theme/13.png)


