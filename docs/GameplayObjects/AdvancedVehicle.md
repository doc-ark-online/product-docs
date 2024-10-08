# 高级轮式载具
::: tip **阅读本文预计 15 分钟**
**本文概述了如何在编辑器中，高级轮式载具逻辑对象的使用方法。**
:::

## 什么是高级轮式载具
> 高级轮式载具是编辑器提供的逻辑对象功能，用于快速实现一个具有模拟物理特性的地面轮式载具，并可以通过模型或特效搭建载具外观。

## 如何使用高级轮式载具
- **step.1** **通过本地资源库创建高级轮式载具**
在本地资源库搜索[高级轮式载具]，找到功能对象将其拖拽到场景中，完成创建。
| 中文示例   | 英文示例 |
| ------ | ---------------------------- |
|<video controls src="https://cdn.233xyx.com/athena/online/eae605aa0e724b9bbf30fdb84459c4f5.mp4"></video>|<video controls src="https://cdn.233xyx.com/athena/online/18e5ee6ef94e497eb6599933671e51b3.mp4"></video>|

- **step.2** **搭建载具外观**
可以使用任意模型或特效拼装你的高级轮式载具，模型会自动成为载具碰撞的一部分。
::: tip **注意车质量**
**拼装车身时，会将模型对象的质量计入载具整体质量中，拼装质量过大的模型时，需要考虑载具重心是否会影响平衡性，否则会出现翻车的情况。。**
:::
| 中文示例   | 英文示例 |
| ------ | ---------------------------- |
|<video controls src="https://cdn.233xyx.com/athena/online/2f7db14f06154995b74fca9737146668.mp4"></video>|<video controls src="https://cdn.233xyx.com/athena/online/0a1d4a09b51b4b279db71fb5a76f505e.mp4"></video>|

- **step.3** **绑定载具轮胎**
高级轮式载具可以指定某个模型做为载具的轮胎，绑定后模型会具有轮胎转动的动画效果。高级轮式载具的轮胎碰撞需要通过属性中的轮胎半径进行设置，被绑定的模型没有碰撞效果。
高级轮式载具可以绑定0~4个车轮，也可以调整车轮的位置，但要考虑车轮位置对车身整体的平衡性影响。

| 中文示例   | 英文示例 |
| ------ | ---------------------------- |
|<video controls src="https://cdn.233xyx.com/athena/online/340db8b9b8ad4d009cf2b55621815d17.mp4"></video>|<video controls src="https://cdn.233xyx.com/athena/online/c3af134ba038432a8d86d4c2324e6d3e.mp4"></video>|


| **动力轮组属性** | **说明**                                | **类型** | **取值范围** |
| --------------- | ---------------------------------------- | ------- | ------------ | 
| 轮胎半径         | 设置物理轮胎的半径                        | number | 0 - 1000 |
| 转向角度         | 设置轮胎最大转向角度，建议使用区间(0 - 40） | number | 0 - 90 |
| 绑定车轮         | 指定一个物体做为载具的轮胎                 | GameObject | 模型或特效 |



- **step.4** **自动上车功能**
高级轮式载具的自动上车功能，通过创建时自带的触发器和交互物逻辑对象来完成这一功能，可以在编辑器运行时快速验证载具运行效果。

| **属性** | **说明**|
| ------------ | ------- |
| 自动上车| 启用后，角色进入载具默认触发器范围时，自动执行驾驶逻辑。上车后可以通过W/A/S/D键控制载具移动，空格键控制载具制动，F键控制角色下车。**使用自动上车功能时，无法执行高级轮式载具对象下的自定义脚本逻辑。**|
| 隐藏驾驶员| 角色执行上车逻辑后，会自动隐藏自身形象。|
| 下车位置偏移| 设置角色脱离载具时，与载具中心点的相对位置；|
| 载具触发器| 只有绑定高级轮式载具对象下的触发器后，才可以执行自动上车逻辑|
| 载具交互物| 只有绑定高级轮式载具对象下的交互物后，才可以执行自动上车逻辑|



- **step.5** **运行体验载具效果**
| 中文示例   | 英文示例 |
| ------ | ---------------------------- |
|<video controls src="https://cdn.233xyx.com/athena/online/8112fad534e6468e9978bd63a7aed379.mp4"></video>|<video controls src="https://cdn.233xyx.com/athena/online/26d49c2e059c4400bbea6c05a0bb4166.mp4"></video>|


| **基础属性**  | **说明**              | **类型** | **取值范围** |
| ----------| --------------------- | -------- | ------------ | 
| 载具模式  | 选择基础模式或高级模式，对载具属性进行设置。| enum| 基础模式| 
| 质量      | 载具基础质量，会影响行驶速度与稳定性。在添加额外的物体拼装载具外形时，会将物体的质量计入载具总质量中，并重新分配载具的物理重心。| number| 0.01 - 100000(KG)|
| 摩擦力    | 设置载具的轮胎摩擦力，摩擦力影响载具的运行效果，摩擦力为0时，轮胎与地面摩擦力失效，会导致载具无法移动。| number| 0 - 8|
| 发动机转速(RPM) | 设置每分钟发动机的最大转速，转速越大，载具可达到的最大速度更大。(注意，此处为载具发动机转速，并不代表实际运行时的KM/H速度)| number| 0 - 1000000|
| 加速系数  | 设置载具加速系数,加速效果基于物理模拟运算，直接修改加速系数并不会出现很大的效果差距，配合载具摩擦力、质量等其他参数可以进一步调整载具行驶速度| number| 0.1 - 100|
| 制动速度  | 设置主动刹车时的制动力。| number| 0 - 1000000|

 > 高级轮式载具可以指定某个模型做为载具的轮胎，绑定后模型会具备轮胎转动的动画效果。高级轮式载具的轮胎碰撞需要通过属性中的轮胎半径进行设置，被绑定的模型没有碰撞效果。

| **动力轮组属性** | **说明**                                | **类型** | **取值范围** |
| --------------- | ---------------------------------------- | ------- | ------------ | 
| 轮胎半径         | 设置物理轮胎的半径                        | number | 0 - 1000 |
| 转向角度         | 设置轮胎最大转向角度，建议使用区间(0 - 40） | number | 0 - 90 |
| 绑定车轮         | 指定一个物体做为载具的轮胎                 | GameObject | 模型或特效 |

> 选择高级模式后，可以通过自定义发动机参数，制作出不同动力的载具。发动机属性模拟现实中的物理特性，通过齿比值计算出对应的载具动力。

| **高级模式属性** | **说明**                                | **类型** | **取值范围** |
| --------------- | ---------------------------------------- | ------- | ------------ | 
| 下齿比   | 每个档位自动降档时的转速比值。| number | 0 - 1 |
| 上齿比   | 每个档位自动升档时的转速比值。| number | 0 - 1 |






## 如何通过脚本控制高级轮式载具

- **step.6**  **创建载具控制脚本

```TypeScript

@Component
export default class NewScript extends Script {

    vehicle: mw.AdvancedVehicle;
    interactiveObj: mw.Interactor;
    trigger: mw.Trigger;

    /** 当脚本被实例后，会在第一帧更新前调用此函数 */
    protected onStart(): void {

        this.vehicle = mw.GameObject.findGameObjectById("337D3F6F") as mw.AdvancedVehicle;  //获取到高级轮式载具逻辑对象
        this.interactiveObj = mw.GameObject.findGameObjectById("2093ED53") as mw.Interactor; //获取到交互物逻辑对象
        this.trigger = mw.GameObject.findGameObjectById("09523175") as mw.Trigger; //获取到触发器逻辑对象

        //通过触发器，激活上车事件
        if (SystemUtil.isClient()) {
            this.trigger.onEnter.add((chara: mw.Character) => {
                if (chara instanceof mw.Character) {
                    Event.dispatchToLocal("InVehicle");
                    Event.dispatchToServer("setPlayerCollision",false);
                }
            });
        }



        //客户端执行上车逻辑
        Event.addLocalListener("InVehicle", () => {
            let player = Player.localPlayer;
            player.character.setCollision(mw.PropertyStatus.Off) //关闭角色碰撞,避免角色与载具发生碰撞冲突
            Camera.currentCamera.springArm.collisionEnabled = false; //关闭摄像机碰撞，避免摄像机与载具发生碰撞冲突
            this.interactiveObj.enter(player.character, mw.HumanoidSlotType.Buttocks, "14015"); //激活交互物
            this.vehicle.owner = player;
            this.VehicleKeyEvents();
        });



        //客户端执行下车逻辑
        Event.addLocalListener("LeaveVehicle", () => {
            let player = Player.localPlayer;
            let endLoc = this.trigger.worldTransform.position; //获取当前触发器位置，做为下车位置
            this.interactiveObj.leave(endLoc.add(new mw.Vector(0, 200, 50))); //激活交互物,并设置一个下车位置
            this.vehicle.owner = null; //清除载具控制权
            player.character.setCollision(mw.PropertyStatus.On); //打开角色碰撞
        });

        
        //在服务端处理角色碰撞                
        Event.addClientListener("setPlayerCollision",(player,value:boolean)=>{
            if(value){
                player.character.setCollision(mw.PropertyStatus.On) //打开角色碰撞
            }else{
                player.character.setCollision(mw.PropertyStatus.Off) //关闭角色碰撞
            }

        });

    }


    /** 
     * 通过按钮控制载具移动
     */
    private VehicleKeyEvents() {

        //按下UP键，载具加油前进；
        InputUtil.onKeyDown(mw.Keys.Up, () => {
            this.vehicle.throttleInput = 1;
        });
        InputUtil.onKeyUp(mw.Keys.Up, () => {
            this.vehicle.throttleInput = 0;
        });

        //按下Down键，载具减速后退；
        InputUtil.onKeyDown(mw.Keys.Down, () => {
            this.vehicle.throttleInput = -1;
        });
        InputUtil.onKeyUp(mw.Keys.Down, () => {
            this.vehicle.throttleInput = 0;
        });

        //按下LEFT键，载具左键；
        InputUtil.onKeyDown(mw.Keys.Left, () => {
            this.vehicle.steeringInput = -1;
        });
        InputUtil.onKeyUp(mw.Keys.Left, () => {
            this.vehicle.steeringInput = 0;
        });

        //按下RIGHT键，载具右键；
        InputUtil.onKeyDown(mw.Keys.Right, () => {
            this.vehicle.steeringInput = 1;
        });
        InputUtil.onKeyUp(mw.Keys.Right, () => {
            this.vehicle.steeringInput = 0;
        });

        //按下SpaceBar键，载具刹车；
        InputUtil.onKeyDown(mw.Keys.SpaceBar, () => {
            this.vehicle.handbrakeInputEnable = true;
        });
        InputUtil.onKeyUp(mw.Keys.SpaceBar, () => {
            this.vehicle.handbrakeInputEnable = false;
        });

        //按下F键，下车；
        InputUtil.onKeyDown(mw.Keys.F, () => {
            Event.dispatchToLocal("LeaveVehicle");
            Event.dispatchToServer("setPlayerCollision",true);
        });
    }
}
```

