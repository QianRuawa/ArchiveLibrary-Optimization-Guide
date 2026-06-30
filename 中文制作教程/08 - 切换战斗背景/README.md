# 切换战斗时的背景
**场景配置**

**注意一下**
- 代码查找的是你自己自定义查找节点的名字"SubViewportContainer"递归查找节点下的"AnimationPlayer"节点，记得看一下节点名字是否对上了
- 特效自己可以添加一点

**在你的怪物代码里添加**
```csharp
public void SwitchBackgroundImmediate(string backgroundPartName)
{
    var bg = BackgroundHelper.GetCombatBackground();
    if (bg != null)
        BackgroundHelper.SwitchImmediate(bg, backgroundPartName);
}
public async Task SwitchBackgroundWithAnimation(string backgroundPartName,string AnimName = "play")
{
    var bg = BackgroundHelper.GetCombatBackground();
    if (bg != null)
        await BackgroundHelper.PlaySwitchAnimation(bg, backgroundPartName,AnimName);
}
```
可调用代码


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
### SwitchBackgroundWithAnimation(string backgroundPartName,string AnimName = "play")
- backgroundPartName 背景节点名称
- AnimName 播放的动画名字
- 未指定播放动画名称，默认播放名为play

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

附带
![示例](https://github.com/QianRuawa/ArchiveLibrary-Optimization-Guide/blob/main/images/E45A1FF57949CE8AAED3FFD700A85E7D.webp)
![示例](https://github.com/QianRuawa/ArchiveLibrary-Optimization-Guide/blob/main/images/55002D407995239BD52DAD68DA6997D0.webp)
![示例](https://github.com/QianRuawa/ArchiveLibrary-Optimization-Guide/blob/main/images/AD70954734056FB989054DDF10A3DACC.webp)
![示例](https://github.com/QianRuawa/ArchiveLibrary-Optimization-Guide/blob/main/images/7ABC727A150401D02B804E3D20F2147C.webp)
