# centerMiddle

* 实例演示recttransform中的center-middle 居中模式。效果图如下：<br>
![center](images\UI.png)

## UI

* 在新建场景中创建一个UIImage作为CenterMiddle1，设置节点的大小为资源图片的原始大小，并设置居中对齐模式，操作步骤如下图：<br>
![](images\middle.gif)
* 创建脚本UI.js，负责动态状态一个UIImage作为LeftBottom2，并设置其为居中对齐模式。脚本挂在根节点下。<br>
代码如下：<br>

```javascript
/**
 * Anchored the Node to Left-Bottom
 */ 
var UI = qc.defineBehaviour('qc.engine.UI', qc.Behaviour, function() {
}, {
    // fields need to serialize
});

UI.prototype.awake = function() {
	// Download the texture and then create UIImage
    var self = this;
    self.game.assets.load('texture2', 'Assets/texture/texture2.bin', function(t) {
        // create UIImage
        var node = self.game.add.image(self.gameObject);
        node.name = 'LeftBottom2';
        node.texture = t;
        
        // set minAnchor and maxAnchor
        // 0: left/top
        // 1: right/bottom
        node.setAnchor(new qc.Point(0.5, 0.5), new qc.Point(0.5, 0.5));
        
        // The Node's center is Center-Middle
        node.pivotX = 0.5;
        node.pivotY = 0.5;
        
        // set the position
        node.anchoredX = 100;
        node.anchoredY = 100;
        
        // set size
        node.resetNativeSize();
    });
};
```