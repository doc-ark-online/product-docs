# 初生点
::: info
**阅读本文预计 5 分钟**

在项目中使用【初生点】来确定玩家角色生成位置和朝向。一般游戏中使用初生点来控制玩家刷新的位置，例如出现在第一关的场景起点，或者分布于地图的各处。
:::
# 初生点

【初生点】是在项目中决定玩家角色初次生成或重新生成位置与朝向的对象。每个项目创建时都会自带一个【初生点】：BP_PlayerStart。此外你也可以在【游戏功能对象】栏目中找到【初生点对象】，并将它拖入场景中。当场景中存在多个【初生点对象】时，玩家角色会在其中随机选择一个作为生成或者刷新的位置。

| 中文示例    | 英文示例                                                         |
| ----------- | ------------------------------------------------------------ |
|![img](https://qn-cdn.233leyuan.com/athena/online/ba34a5acab9148728b8bd432dcddce7d_357739615.webp)![img](https://qn-cdn.233leyuan.com/athena/online/80756e17295e4e6dbb686c7515626b35_357739616.webp)|![img](https://qn-cdn.233leyuan.com/athena/online/7120733cc5f34445801750cef99be247_357739625.webp)![img](https://qn-cdn.233leyuan.com/athena/online/6b4f2790d4f842b0aaebe98ed4dedc7f_357739626.webp)|

# 创建初生点

## 通过放置资源创建：

【初生点对象】本身作为一个游戏对象可以存在于游戏场景中。你可以从【本地资源库】中找到【游戏功能对象】栏，在游戏功能对象分类中，找到【初生点对象】并拖入【场景】或者【对象管理器】后，会自动生成一个新的初生点。选中初生点可以修改它的位置和旋转（仅z轴）。

1. 在【本地资源库】中找到【初生点对象】

| 中文示例    | 英文示例                                                         |
| ----------- | ------------------------------------------------------------ |
|![img](https://qn-cdn.233leyuan.com/athena/online/d4b98332929c4505b769b8bd6fad2739_357739617.webp)|![img](https://qn-cdn.233leyuan.com/athena/online/9e4643a0ee4648838600d42081718855_357739627.webp)|

2. 将对象拖入到场景中或者【对象管理器】下

| 中文示例    | 英文示例                                                         |
| ----------- | ------------------------------------------------------------ |
|![img](https://qn-cdn.233leyuan.com/athena/online/349906bd1cd744b99272adab13721733_357739618.webp)|![img](https://qn-cdn.233leyuan.com/athena/online/767097400de14e7eb8eca6d1d729338e_357739628.webp)|

3. 在右侧【对象管理器】中【对象】栏找到对应的【初生点对象】并自定义位置和旋转。

| 中文示例    | 英文示例                                                         |
| ----------- | ------------------------------------------------------------ |
|![img](https://qn-cdn.233leyuan.com/athena/online/24ce5bc5e54e4978ae91b9ada871a9d9_357739619.webp)![img](https://qn-cdn.233leyuan.com/athena/online/27c6b396b00046e5bfe5f7f401dfc2a8_357739620.webp)|![img](https://qn-cdn.233leyuan.com/athena/online/a31330df60cd4475a7a489fddc1f10c8_357739629.webp)![img](https://qn-cdn.233leyuan.com/athena/online/8f0fa7e89ef94e6b9a26b31963b47377_357739630.webp)|

::: tip
【初生点】是一个仅存在于服务端的游戏对象。
:::
# 自定义初生点对象

【初生点对象】的属性将决定玩家角色刷新时的位置和朝向：

玩家角色的位置：Position

玩家角色的朝向：Rotation（z轴）

在【对象管理器】中【对象】栏找到对应的【初生点】，选中后我们可以查看它的属性面板，通过属性面板我们可以修改【初生点对象】的坐标和旋转（仅z轴）。一般来说【初生点对象】不需要在脚本中操作，当游戏运行时玩家角色会随机在场景中选择一个初生点作为刷新的位置。

| 中文示例    | 英文示例                                                         |
| ----------- | ------------------------------------------------------------ |
|![img](https://qn-cdn.233leyuan.com/athena/online/3a437e37724f4b63a1b549f6cdd29bd1_357739621.webp)|![img](https://qn-cdn.233leyuan.com/athena/online/ca75ec8f2e7a43ac95fe3008b09070d6_357739631.webp)|

## 初生点位置

玩家生成的位置是由【初生点对象】的位置决定的，你可以直接在【对象管理器】中【对象】栏选中【初生点对象】，在【属性面板】中找到【变换】，改变初生点的【位置】属性，就能改变玩家生成的位置。

| 中文示例    | 英文示例                                                         |
| ----------- | ------------------------------------------------------------ |
|![img](https://qn-cdn.233leyuan.com/athena/online/25cfa912ae7e475fb77d0886d350a099_357739622.webp)|![img](https://qn-cdn.233leyuan.com/athena/online/b6d7351a499841a688714e2eff84644a_357739632.webp)|

## 初生点旋转

玩家生成的朝向是直接由初生点的朝向决定的，你可以【对象管理器】中【对象】栏选中【初生点对象】，在【属性面板】中找到【变换】，改变初生点的【旋转】属性，就能改变玩家生成的位置。同时【初生点对象】的朝向在场景中会通过一个蓝色小箭头进行提示：

| 中文示例    | 英文示例                                                         |
| ----------- | ------------------------------------------------------------ |
|![img](https://qn-cdn.233leyuan.com/athena/online/ad709e3410e4413a858e00d59121b4fb_357739623.webp)|![img](https://qn-cdn.233leyuan.com/athena/online/5fbe54c4a583491a819eb398a64aee8b_357739633.webp)|

::: tip

【初生点对象】其实并没有自己的私有属性，它的位置属性和旋转属性都是是继承自父类`GameObject`。【初生点对象】的【旋转】属性中X、Y的值和【初生点对象】的【缩放】属性也可修改，但无效。

:::

# 使用初生点对象

## 获取初生点对象

### 【对象管理器】中【对象】栏下的【初生点对象】：

**使用`asyncFindGameObjectById`接口通过【初生点对象】的gameObjectId去获取：**

1. 选中【初生点对象】后右键点击【复制对象ID】获取它的gameObjectId。注意区分对象ID与资源ID的区别。

| 中文示例    | 英文示例                                                         |
| ----------- | ------------------------------------------------------------ |
|![img](https://qn-cdn.233leyuan.com/athena/online/6c2a1910c4c4450b83d30da6605d56ec_357739624.webp)|![img](https://qn-cdn.233leyuan.com/athena/online/87a8f404ca6449459d467f319eb9ff5e_357739634.webp)|

1. 在脚本的`onStart`方法中添加下列代码：代码将异步查找ID对应的对象并以【初生点对象】进行接收。

```TypeScript
if(SystemUtil.isServer()) {
    let spawnPoint = await GameObject.asyncFindGameObjectById("06D5DBFC") as PlayerStart;
    console.log("spawnPoint 的gameObjectId是 " + spawnPoint.gameObjectId);
}
```

**使用脚本挂载的方式进行获取：**

1. 在脚本的onStart方法中添加下列代码：代码获取脚本挂载的对象。

```TypeScript
if(SystemUtil.isServer()) {
    let spawnPoint = this.gameObject as GameObject;
}
```

