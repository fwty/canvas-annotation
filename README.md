# annotation
canvas做的在线标注库，适用于自动驾驶标注，目前支持图像的指定位置缩放，拖动，绘制矩形、多边形、线等，库会持续维护。

#### [Online example](https://codepen.io/componentty/pen/VwGgVar)

#### 快速使用

```typescript
    import Canvas from 'canvas-annotation'
    interface canvasProps = {
        el: string | HTMLCanvasElement,
        width?: number,
        height?: number,
        imgUrl: string
    }
    let props: canvasProps = {
        el: '#app' // 你的canvas标签的id
    }
    let c = new Canvas(props)
```

#### 目前库支持的形状类型
type: 'rect' | 'polygon' | 'line'

#### 绘制规则

- 矩形（rect）绘制， 鼠标按下确认第一个点，鼠标移动，矩形绘制，鼠标二次点击确认结束点，绘制结束。

- 多边形（polygon）绘制， 鼠标单击、移动依次选择点，鼠标双击结束绘制多边形。

- 线(line)绘制， 同多边形。

#### 选中图形

如果您希望通过鼠标点击选中图形， 你需要先将selectTool设置为'select',此时工具变成了选择工具，这时候就可以选中图形，并对图形进行操作了。


#### 属性
|  属性名   |  类型  |  描述  |
| :--------| :------| :------- |
|   el     |   string\|HTMLCanvasElement  |  用于绑定你的canvas标签，可以传id、class或者canvas元素 |
| width    |   number |  画布宽度 |
| height   |   number |  画布高度 |
| imgUrl   |   string |  要标注的素材图片地址 |
| selectTool | 'rect'\|'polygon'\|'line' | 形状 |
| minScale |  number |   最小缩放倍数 |
| maxScale | number |  最大缩放倍数 |
| activeIndex | number | 当前激活的下标, 如果想设置不激活，请把此属性设置为-1 |
| focusMode | boolean | 专注模式，默认false |


#### 方法
| 方法名 |  参数   | 描述 |
|:------ | :------- | :-----|
| setImage | 图片地址 | 设置标注图像 |
| fitInWindow | 无 | 使图像自动适配当前视口
| addShape | shape图形 | 画布中添加一个图形
| resetCanvas | 无 | 重置画布 |
| update |  无   |  更新画布
| clear  |  无   |  清空画布
| getCurrentActiveShape | 无 | 获取当前激活的图形
| setMouseCursor | pointer\|auto\|css样式的cursor | 设置鼠标的样式
| setData | 数组[shape, shape] | 初始化素材时，需要显示的图形数据
| getResultData | 无 | 获取标注结果数据 |
| deleteByIndex | 图形下标 |  删除对应的图形
| destory | 无 | 清空事件监听器，请先调用此函数，在将你的标注实例赋值为null

#### 事件
| 事件名 | 描述 |
|:------ | :------- |
| created | 初始化canvas完成，事件绑定完成，素材以及图形绘制完成 |
| hoveredShape | 鼠标移动到图形内触发，有一个回调参数是当前图形
| selectedShape | 鼠标在图形中按下，激活的图形作为此函调函数的参数。
