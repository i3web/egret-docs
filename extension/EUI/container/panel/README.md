面板 Panel 也是常用的容器，这种类型的组件在很多不同领域的 UI 库中都存在，也是开发者比较熟知的一种容器，它和 Group 的区别在于，可以给它附加一个皮肤，并设置一个标题栏和关闭按钮，实现类似下面的结构：

![][8-3-panel-A]

在皮肤中，标题栏的位置由开发者决定，如下图所示的：

![][8-3-panel-B]

下面是标准 Panel 的示例代码：
``` TypeScript
class PanelDemo extends eui.Group {
    constructor() {
        super();
    }
    protected createChildren() {
        super.createChildren();
        var theme = new eui.Theme(`resource/default.thm.json`, this.stage);
        var exml = `
        <e:Skin class="skins.PanelSkin" minHeight="230" minWidth="450" xmlns:e="http://ns.egret.com/eui"> <e:Image left="0" right="0" bottom="0"  top="0" source="resource/assets/Panel/border.png" scale9Grid="2,2,12,12" /> <e:Group id="moveArea" width="450" height="45" top="0"> <e:Image width="100%" height="100%" source="resource/assets/Panel/header.png"/> <e:Label id="titleDisplay" fontSize="20"  textColor="0x000000" horizontalCenter="0" verticalCenter = "0"/> </e:Group> <e:Button id="closeButton" label="touch to close" bottom="5" horizontalCenter="0"/> </e:Skin>        `
        var myPannel = new eui.Panel();
        myPannel.skinName = exml;
        myPannel.title = "titleHello";
        this.addChild(myPannel)
    }
}
```

显示效果：
![][8-3-panel-C]

Panel 中有3个默认的皮肤部件，就是上面代码中 exml 皮肤里对应的 ```id="xxx"```。
Panel 容器为他们提供了一些默认的功能，若皮肤中不存在这些id，对应的逻辑功能将无法使用。
```
moveArea
上面显示效果中的蓝色长条
点中这个区域可以拖拽整个面板
```
```
titleDisplay
上面显示效果中顶部的标题
可以通过 panel.text = "xxxx" 给它赋值
```
```
closeButton
上面显示效果中底部的按钮
点击它会把面板关闭
```

[8-3-panel-A]: http://sedn.egret.com/5604edaeea1f2.png
[8-3-panel-B]: http://sedn.egret.com/5604edb6b438b.png
[8-3-panel-C]: http://sedn.egret.com/5604edbb4b4bf.png
