# 切换战斗时的背景
**场景配置**

**注意一下**
- 代码查找的是自己自定义节点SubViewportContainer名下的AnimationPlayer节点，记得看一下节点名字是否对上了
- 特效自己可以添加一点

油桶蟹代码部分调用
![示例](https://github.com/QianRuawa/ArchiveLibrary-Optimization-Guide/blob/main/images/4031338A63C36DEA8C0F6FABC53A49F9.webp)
```csharp
// 背景节点名称常量
private const string STREET_BG = "SubViewportContainer";
//发怒
private async Task AngerAction(IReadOnlyList<Creature> targets)
{
    ....
    if(MiyuModConfig.IsHighDifficulty)SwitchBackgroundWithAnimation(STREET_BG, "ins_op_2");
    else SwitchBackgroundWithAnimation(STREET_BG, "op_2");
    ....
}
```
**SwitchBackgroundWithAnimation(STREET_BG, "ins_op_2")**
- 优先播放小动画
  
**SwitchBackgroundWithAnimation(STREET_BG, "op_2")**
- 切换场景，调用场景动画里名为op_2动画

猫鬼·黑影代码部分调用
![示例](https://github.com/QianRuawa/ArchiveLibrary-Optimization-Guide/blob/main/images/02F8D1B209F44D1622034DC530156C66.webp)
```csharp
// 背景节点名称常量
private const string STREET_BG = "SubViewportContainer_1";
private const string DOMAIN_BG = "SubViewportContainer_2";
// 转场
//二阶段
private async Task EnterPhase2()
{
  ....
  SwitchBackgroundWithAnimation(STREET_BG);
  ....
}
//三阶段
private async Task EnterPhase3()
{
  ....
  SwitchBackgroundWithAnimation(DOMAIN_BG);
  ....
}
```
**未指定播放动画名称**
- 默认播放名为play

附带
![示例](https://github.com/QianRuawa/ArchiveLibrary-Optimization-Guide/blob/main/images/E45A1FF57949CE8AAED3FFD700A85E7D.webp)
![示例](https://github.com/QianRuawa/ArchiveLibrary-Optimization-Guide/blob/main/images/55002D407995239BD52DAD68DA6997D0.webp)
![示例](https://github.com/QianRuawa/ArchiveLibrary-Optimization-Guide/blob/main/images/AD70954734056FB989054DDF10A3DACC.webp)
![示例](https://github.com/QianRuawa/ArchiveLibrary-Optimization-Guide/blob/main/images/7ABC727A150401D02B804E3D20F2147C.webp)
