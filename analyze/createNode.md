生成节点

首先导入的是 Minder 实例的 root 节点，以及 json 数据。

首先为 root 节点设定相应的 data 。遍历 children 字段，为其添加对应的数据。

遍历新建 Minder 节点，新建之后真正生成 svg 节点数据挂载DOM 于视图。此时节点并没有任何样式数据。


新建每个节点的 g 节点。
随后根据渲染器
```
TextRenderer
PriorityRenderer
OutlineRenderer
ExpanderRender
ShadowRenderer
WireFrameRender
```

遍历将每个节点的数据生成对应的渲染 svg path。

```
importNode -> createNode -> new MinderNode -> appendNode -> attachNode -> addShape (容器)
```

```
renderTree -> renderNodeBatch -> createRendererForNode  -> addShape (svg 路径)
```

第一轮布局进入具体的布局策略中，btree.js 。 负责节点的位置更新
第二轮布局进入到 minder.js 中。


节点最终绘制 applyMatrix
连线通过事件触发机制
连线的样式

在 theme.js 中 getNodeStyle('connect-color')

通过 node.js 根据节点的层级深度获得节点类型。
在 theme 中 匹配对应的样式，获得线条的颜色和宽度。

进入到 arc.js 圆弧连线

```
connection.setPathData()
```

在 kity.js 中
```
this.node.setAttribute('d', this.pathdata);
```

重点: matrix 数据是如何计算出来的？

