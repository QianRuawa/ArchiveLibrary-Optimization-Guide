# 生物位移能力
类似沙虫的效果，我自己优化了一下

**在你的怪物代码里添加**
```csharp
public abstract class TestBossId : MonsterModel, IMovementEffect

public async Task Knockback(Creature target, float distance = 120f)
{
    MovementHelper.Knockback(target, distance);
}
public async Task MoveRight(Creature target, float distance = 120f)
{
    MovementHelper.MoveRight(target, distance);
}
```
可调用代码

### Knockback(Creature target, float distance = 120f)
**将目标向左击退**
- target 目标
- distance 限制，我这里默认向左最大120像素距离，你自己调整

### MoveRight(Creature target, float distance = 120f)
**将目标向右击退**
- target 目标
- distance 限制，我这里默认向右最大120像素距离，你自己调整

我自己使用猫鬼代码部分
```csharp
//疾奔的猫鬼夜行
private async Task CatNightMarchMove(IReadOnlyList<Creature> targets)
{
  ....
    foreach (var player in players)
    {
      ....
      if(!maximumParameter)Knockback(player, totalKnockback / 3);
    }
  ....
}
// 蔓延的街谈巷说
private async Task StreetRumorsMove(IReadOnlyList<Creature> targets)
{
  ....
  for (int i = 0; i < totalHits; i++)
  {
    foreach (var player in players)
    {
      ....
      MoveRight(player, totalPullToBoss / totalHits);
    }
    ....
  }
  foreach (var player in players)
  {
    await MovementHelper.Knockback(player, finalKnockback);
  }
  ....
}
```
