# 如何在项目中使用扩展主题

扩展主题的修改以及在编辑器中的使用已经在上一篇教程说过，可是如何在项目中使用自己的主题呢？小编体验了下，感觉还是有点小麻烦的，跟发家分享下其中的经验。

一、复制主题代码和资源到项目下

![](https://raw.githubusercontent.com/yuhengh/starling-builder-tutorial/cn/images/theme/01.png)

二、修改代码
单单复制代码和资源还不行的，还需要做些小改动

1、修改BaseTestGameMobileTheme.as
将 BaseTestGameMobileTheme extends UIEditorTheme
改成：
BaseTestGameMobileTheme extends StyleNameFunctionTheme
去掉构造函数的themeMediator参数
改之前

![](https://raw.githubusercontent.com/yuhengh/starling-builder-tutorial/cn/images/theme/02.png)

![](https://raw.githubusercontent.com/yuhengh/starling-builder-tutorial/cn/images/theme/03.png)

改之后

![](https://raw.githubusercontent.com/yuhengh/starling-builder-tutorial/cn/images/theme/04.png)

![](https://raw.githubusercontent.com/yuhengh/starling-builder-tutorial/cn/images/theme/05.png)

2、修改TestGameMobileTheme.as，因为继承关系所以同样要去掉构造函数的themeMediator参数，图片参照上面的


三、使用主题
在项目初始化代码中添加我们的扩展主题，只需一行代码
new TestGameMobileTheme(false);
如图：

![](https://raw.githubusercontent.com/yuhengh/starling-builder-tutorial/cn/images/theme/06.png)

以上就是主题使用的所有步骤了（小提示：小编的项目中都有一个文件夹，里面是用git客户端从github上面copy的相关源代码，这样作者提交代码后我们只需要在本地更新就好了）