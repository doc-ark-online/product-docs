# UI 控件-进度条

**阅读本文大概需要 10 分钟**

本文概述了 UI 控件—进度条的各项属性以及使用方法。

## 什么是进度条？

**进度条**是比较常用的动态滑动类型的交互控件；也可以作为不可交互控件，用于展示百分比的进度效果。

- 变换/对齐/通用/渲染属性请见 [UI 控件的基础属性](https://docs.ark.online/UI/UIWidget-BaseProperties.html)

## 进度条属性-滑动设置


### 填充类型

- Left To Right（从左到右）

  - 从左到右填充图片的效果。
- Right To Left（从右到左）

  - 从右到左填充图片的效果。
- Fill From Center（从中间向外填充）

  - 从中间向外填充图片的效果。
- Top To Bottom（从上到下）

  - 从上到下填充图片的效果。
- Bottom To Top（从下到上）

  - 从下到上填充图片的效果。
  - 示意图：

![](https://qn-cdn.233leyuan.com/online/mgp2mmOWwZn61724133629112.gif)

### 滑动最小值

- 设置滑动条可滑动到的最小值
- 举例说明：下载进度条从 0 到 100%，0 即为滑动最小值

### 滑动最大值

- 设置滑动条可滑动到的最大值
- 举例说明：下载进度条从 0 到 100%，100% 即为滑动最大值

### 当前值

- 规定滑动按钮的初始位置的值。
- 举例说明：下载进度条是从 0 开始的，所以当前值为 0。相反假设角色满体力是 100，那么角色运行游戏时体力应该是 100，也就是说当前值为 100。

### 当前百分比

- 规定滑动按钮的初始位置的百分比，该百分比是通过当前值进行换算的，也就是说两个值调整的是同一个参数。
- 举例说明：还以上面的下载进度条为例，当前值为 0 时，则当前百分比应该为 0%，如果当前值为 50 时，则当前百分比应该为 50%。

### 取整

- 限制滑动值是整数还是小数。
- 举例说明：商店的道具数量购买时的滑动条需要取整，因为道具数量没有小数。
  - 示意图：

![](https://qn-cdn.233leyuan.com/online/bjcPEUBXnbF71724133629581.gif)

### 条厚度

- 进度条控件允许分别设置渲染图形大小和可操作范围为不同大小：

  - 1.进度条的【条厚度】用于修改进度条滑动填充图片和滑动背景图片渲染图形的宽度
   ![](https://wstatic-a1.233leyuan.com/productdocs/static/boxcnhkpK45mqaE3EK8hPGSn3hJ.gif)
  - 2.进度条的【变换】-【大小】是控件实际可以操作范围的大小，也就是下方动图中的蓝框，这个范围内都允许玩家点击和拖动，滑动值均为点击/拖动点作垂线到进度条上的值；<br />修改【变换】-【大小】时，只会改变进度条滑动填充图片和滑动背景图片渲染图形的长度，并不会改变其宽度
   <br />![](https://wstatic-a1.233leyuan.com/productdocs/static/boxcnwtfzphqdjT9EY0SkdlBkkc.gif)
  - 3.修改滑动按钮图片大小应使用【滑动按钮图片】-【图片大小】
   ![](https://wstatic-a1.233leyuan.com/productdocs/static/boxcnKLl7D9Kdm2wUcEwe6kx5cd.gif)

- 举例说明：制作一个看起来很细，但是触发区域较大的滑动条。

  - 示意图：

![](https://wstatic-a1.233leyuan.com/productdocs/static/boxcnrVwwaRlMZnrIB2g61pfRX8.gif)

## 进度条属性-样式

### 滑动填充图片

- 修改的是进度条在填充时的填充效果。图片属性请见【UI 控件-图片】

### 滑动按钮图片

- 修改的是进度条填充位置的按钮效果。图片属性请见【UI 控件-图片】

  - 锚点类型：可以选择中心或者两侧，用于修改锚点在按钮图片的具体位置
    - 中心锚点在按钮图片正中心
![](https://wstatic-a1.233leyuan.com/productdocs/static/boxcn8Ip5e1uOVJ1NzpQvUWCi7f.jpg)
    - 两侧锚点在图片两侧，图片不会超出进度条范围
![](https://wstatic-a1.233leyuan.com/productdocs/static/boxcnrY2JQUtJuBA0fTh3dsGtod.jpg)

  - 偏移值：用于修改按钮相对锚点的位置
    - 锚点类型为中心时，偏移值为 X 像素即让按钮图片整体向右偏移 X 像素，偏移值为-X 像素即让按钮图片整体向左偏移 X 像素
    - 锚点类型为两侧时，偏移值为 X 像素即让按钮图片可滑动的最左位置和最右位置整体向外偏移 X 像素，偏移值为-X 像素即让按钮图片的最左位置和最右位置整体向内偏移 X 像素

### 滑动背景图片

- 修改的是进度条在未填充的背景效果。图片属性请见 [UI 控件-图片](https://docs.ark.online/UI/UIComponent-Image.html)


## 如何使用进度条？

- 举例说明：制作控制音量大小的滑动条，以及加载界面的进度条或者是角色的能量条。

### 示例一：制作调整音量大小的进度条

- 首先我们需要用 UI 编辑器制作一个面板，然后将进度条等 UI 控件放置在面板上，如图

![](https://qn-cdn.233leyuan.com/online/gnp84nCvoWUx1724133630031.png)

- 然后把对应的音效文件拖入优先加载内，并把与脚本进行绑定好的 UI 文件拖入对象列表中


- 脚本示例：

```ts
@UIBind('')
export default class DefaultUI extends UIScript {
	private character: Character;
	private anim1 = null;
	
	/** 仅在游戏时间对非模板实例调用一次 */
    protected  onStart() {
		 //找到进度条
		 const progressbar = this.uiWidgetBase.findChildByPath('Canvas/ProgressBar') as ProgressBar

		 AssetUtil.asyncDownloadAsset("4165").then((res : boolean) => {
			if (res) {
				//生成一个音效并播放
				let sound1 = GameObject.spawn("4165") as Sound
				sound1.isLoop = true
				sound1.play()
				//取到当前音效的音量并设置成进度条当前值
				let volume1=sound1.volume
				progressbar.currentValue=volume1
				//进度条移动后设置音量
				progressbar.onSliderValueChanged.add(() => {
					let volume1=progressbar.currentValue
					sound1.volume=volume1
				});
			}
		})
    }
}
```

- 示意视频：<video controls src="https://qn-cdn.233leyuan.com/online/OhyCHQ9Yd9FS1724133627151.mp4"></video>

