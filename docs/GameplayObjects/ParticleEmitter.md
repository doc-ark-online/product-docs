# 粒子发射器
::: info
**阅读本文预计 15 分钟**

本文概述了 游戏功能对象——粒子发射器的使用方法。
:::

## 1. 什么是粒子发射器？
- 粒子发射器是能发射粒子的特效单元，可以修改各种属性实现丰富的特效表现。
- 粒子发射器属于自定义特效，可以修改多种属性，甚至是贴图。非自定义特效是定制化的UE特效，可修改参数少，但是完成度高。实际项目中可以根据需要选择特效类型。

## 2. 如何创建粒子发射器？
- 将发射器从功能组件中拖出到场景或对象管理器中，选中粒子发射器后可以在面板中更改属性。
![image](https://github.com/user-attachments/assets/dfb44484-e942-4e1a-99d0-4867847dae6c)

## 3. 粒子发射器有哪些属性和接口？
### 3.1 变换
![image](https://github.com/user-attachments/assets/7bebf453-a626-4840-b743-1522ed4ef2aa)
#### 3.1.1 相对位置：粒子发射器在世界中的位置。
#### 3.1.2 相对旋转：粒子发射器在世界中的旋转。
#### 3.1.3 相对缩放：固定为(1,1,1)，无法更改。

演示效果：

![20240723133937_rec_](https://github.com/user-attachments/assets/66e34634-37b8-4ea3-8afe-340e9d454de1)

### 3.2 效果属性
#### 3.2.1 启用：打开时，粒子发射器会在游戏启动时发射粒子，反之则不会。暂停按钮可以让粒子发射器在编辑器中暂停发射。该属性仅可在编辑器中修改。

![image](https://github.com/user-attachments/assets/5ed98648-7e36-4721-b069-38e8a9f9c7ff)

::: tip
脚本中使用ParticleEmitter.play()开始发射粒子，使用ParticleEmitter.stop()停止发射粒子，使用ParticleEmitter.forceStop()停止发射并销毁所有已经发射的粒子。
:::

#### 3.2.2 颜色：控制粒子在生命周期中的颜色以及变化。

![image](https://github.com/user-attachments/assets/27bee8d5-0583-4758-8507-f366e2239e2f)

::: tip
如上这种数据形式为“关键帧插值”，在粒子发射器中被频繁使用，以实现丰富的效果。
使用方法：
1. 点击加号新增关键帧节点。
2. “时间点”属性为粒子从诞生到被销毁整个生命周期中的百分比。
3. “值”可以为颜色、透明度甚至加速度等，代表粒子会从上个“时间点”的该属性向当前值变化。
4. 脚本中实现关键帧插值请见如下代码示例。
:::

```TypeScript
// 在脚本中实现关键帧插值
let Effect = this.gameObject as ParticleEmitter;

// 创建粒子颜色的关键帧数组 效果为由蓝线性过度至红色
let ColorSequence = Array<mw.colorSequencePoint>();
// 生命周期0%时为蓝色
ColorSequence.push(new mw.colorSequencePoint(0, new LinearColor(1,0,0)));
// 生命周期100%时为红色
ColorSequence.push(new mw.colorSequencePoint(1, new LinearColor(0,0,1)));
Effect.color = ColorSequence;
```

演示效果：

![20240723143028_rec_](https://github.com/user-attachments/assets/16e4ccb5-01fd-493c-a11d-c40874ddff26)

#### 3.2.3 亮度：控制粒子的亮度。默认值1。
#### 3.2.4 光照影响：控制粒子收到环境光照影响的程度，0到1代表完全不受影响到完全受影响。默认值0。
#### 3.2.5 透明度：控制粒子的透明度，支持“关键帧插值”，默认值1。
