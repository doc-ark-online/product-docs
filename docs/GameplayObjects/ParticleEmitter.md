![20240723151207_rec_](https://github.com/user-attachments/assets/e352cc63-c40a-4ef7-9401-9c6c1f53f3fa)# 粒子发射器
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

效果演示：

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

效果演示：

![20240723143028_rec_](https://github.com/user-attachments/assets/16e4ccb5-01fd-493c-a11d-c40874ddff26)

#### 3.2.3 亮度：控制粒子的亮度。默认值1。
![image](https://github.com/user-attachments/assets/262abbc1-965f-4b04-bd67-c18a984cd76f)

效果演示：

![20240723144533_rec_](https://github.com/user-attachments/assets/d2141b45-9abd-4394-92b8-d640601b074c)

#### 3.2.4 光照影响：控制粒子收到环境光照影响的程度，0到1代表完全不受影响到完全受影响。默认值0。
![image](https://github.com/user-attachments/assets/43e6009a-1946-46aa-be89-796be3a44740)

效果演示：

![20240723144927_rec_](https://github.com/user-attachments/assets/cd3bc116-cf84-4d5a-abad-c7d9270423ad)

#### 3.2.5 透明度：控制粒子的透明度，支持“关键帧插值”，默认值1。
![image](https://github.com/user-attachments/assets/762163d1-02f3-4ea6-a4d6-73637110d0e7)

效果演示：

![20240723145734_rec_](https://github.com/user-attachments/assets/ea26894c-3f41-4033-8893-ddcfb415511f)

#### 3.2.6 贴图：单个粒子的贴图，目前仅适配场景贴图。
![image](https://github.com/user-attachments/assets/a2bed62a-e02e-4cf8-bbe5-ce74a24335a6)

效果演示：

![20240723150305_rec_](https://github.com/user-attachments/assets/2ceef36f-1288-43aa-a0e7-b2d9cd23b708)

#### 3.2.7 大小：控制粒子的大小，支持“关键帧插值”，默认值1。
![image](https://github.com/user-attachments/assets/4127a32f-e6c0-463f-ad2e-ac28a742cf5f)

效果演示：

![20240723150846_rec_](https://github.com/user-attachments/assets/dc37ec86-0566-4307-8277-2936f9ca1ec3)

#### 3.2.8 宽高比：控制粒子的宽高比，默认值0。
![image](https://github.com/user-attachments/assets/445bf523-02b6-4016-a9f0-c5fdaa2587a0)

效果演示：

![20240723151207_rec_](https://github.com/user-attachments/assets/7fcf801b-ad0e-4309-8be5-eb62311db77d)

### 3.3 释放属性
#### 3.3.1 生命周期：控制粒子从诞生到销毁的时间，X和Y代表区间，当相同时，生命周期恒定，当不同时，生命周期会在二者中间随机，默认值(10,10)。
![image](https://github.com/user-attachments/assets/3b9ad859-4045-4e30-afce-9e7d5304a394)

效果演示：

![20240723151740_rec_](https://github.com/user-attachments/assets/83d5d69a-937c-4dc7-8159-f41bb5140652)

#### 3.3.1 发射频率：控制粒子的发射频率，单位“个/秒”，范围0-100，默认值20。

::: tip
如果单个粒子发射器的仍未被销毁的粒子达到了1000个，那么就会自动减缓粒子的发射频率，以保证数量维持在1000以内。
如果您需要大片粒子的效果，不妨将多个粒子整合为单张图片以减缓渲染压力。
如果效果仍不理想，可以试试堆叠多个粒子发射器。
:::

效果演示：

![20240723152446_rec_](https://github.com/user-attachments/assets/640485f9-d183-4dd2-ba49-e93a97ec1b9c)

#### 3.3.1 速度：控制粒子的速度，单位“厘米/秒”。










