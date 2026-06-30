# 单正负Power工具[双模式]
**Power 同时支持增益（正数）和减益（负数）两种模式，自动切换图标、标题、描述**

使用RitsuLib前置来制作优化了一下

继承 ModDynamicIconPower 类型

这里是我制作的buff，显示部分制作
```csharp
[RegisterPower]
public class AttackModifier : ModDynamicIconPower
{
    public override PowerType Type => PowerType.Buff;
    public override PowerStackType StackType => PowerStackType.Counter;

    public override string IconId => "ATK";
    public override PowerCategory Category => PowerCategory.Benefit;
    ....
}
```
### public virtual string PositiveIconPath => Category.GetIconPath(IconId);
**正数图标路径，默认从 Category + IconId 自动生成。可 override 自定义**
### public virtual string NegativeIconPath => PowerCategory.Adverse.GetIconPath(IconId);
**负数图标路径，默认使用 Adverse 分类 + IconId 自动生成。可 override 自定义**

- 自动检测更新描述
- 标题/描述自动切换
- Buff/Dubuff 描述框自动切换
- 正负共用.smartDescription，用 {Amount:cond:>0?...|...} 条件式区分

json内容
```
"ARCHIVE_LIBRARY_POWER_ATTACK_MODIFIER.title": "攻击力提升",
"ARCHIVE_LIBRARY_POWER_ATTACK_MODIFIER.title.negative": "攻击力降低",
"ARCHIVE_LIBRARY_POWER_ATTACK_MODIFIER.description": "提升单位的攻击力",
"ARCHIVE_LIBRARY_POWER_ATTACK_MODIFIER.description.negative": "降低单位的攻击力",
"ARCHIVE_LIBRARY_POWER_ATTACK_MODIFIER.smartDescription": "{Amount:cond:>0?增加|降低}单位的攻击力[blue]{Amount}[/blue]点伤害",
```
