# 怪物固定攻击意图伤害
让怪物固定伤害显示，不会被改变
![示例1](https://github.com/QianRuawa/ArchiveLibrary-Optimization-Guide/blob/main/images/BFFEF6806D989603B69310E7032C2F2B.webp)
![示例1](https://github.com/QianRuawa/ArchiveLibrary-Optimization-Guide/blob/main/images/B93A11CA7C86383EECD782747E2B782F.webp)

这里没有改变

记得在伤害代码里添加 ValueProp.Unpowered 不被能力影响

修改标题看这个[怪物攻击意图标题介绍修改](https://github.com/QianRuawa/ArchiveLibrary-Optimization-Guide/blob/main/%E4%B8%AD%E6%96%87%E5%88%B6%E4%BD%9C%E6%95%99%E7%A8%8B/07%20-%20%E6%80%AA%E7%89%A9%E6%94%BB%E5%87%BB%E6%84%8F%E5%9B%BE%E6%A0%87%E9%A2%98%E4%BB%8B%E7%BB%8D%E4%BF%AE%E6%94%B9/README.md)

我这里使用马库库的意图代码部分
```csharp
protected override MonsterMoveStateMachine GenerateMoveStateMachine()
{
    ....
    var kingdomPilgrim = new MoveState("KINGDOM_PILGRIM", KingdomPilgrimMove, new FixedMultiAttackIntent(2, () => PilgrimHitCount) { CustomLocPrefix = "KINGDOM_PILGRIM" });
    ....
}
```
### new FixedMultiAttackIntent(int damage, int repeat)
**固定伤害多段攻击，不受能力影响**
- damage 伤害显示
- repeat 攻击次数
### new FixedSingleAttackIntent(int damage)
**固定伤害单段攻击，不受能力影响**
- damage 伤害显示
