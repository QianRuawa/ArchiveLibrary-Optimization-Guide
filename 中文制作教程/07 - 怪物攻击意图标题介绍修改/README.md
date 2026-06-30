# 怪物攻击意图标题介绍修改
![示例1](https://github.com/QianRuawa/ArchiveLibrary-Optimization-Guide/blob/main/images/BFFEF6806D989603B69310E7032C2F2B.webp)
![示例1](https://github.com/QianRuawa/ArchiveLibrary-Optimization-Guide/blob/main/images/ee08d8666077f261a868b8b4f6851149.webp)

可以随意修改意图名字

我这里使用马库库的意图代码部分
```csharp
protected override MonsterMoveStateMachine GenerateMoveStateMachine()
{
    ....
    var kingdomPilgrim = new MoveState("KINGDOM_PILGRIM", KingdomPilgrimMove, new FixedMultiAttackIntent(2, () => PilgrimHitCount) { CustomLocPrefix = "KINGDOM_PILGRIM" });
    ....
}
```
若藻的意图代码部分
```csharp
protected override MonsterMoveStateMachine GenerateMoveStateMachine()
{
    var ruriDivination = new MoveState("RURI_DIVINATION",RuriDivinationMove,new DynamicMultiAttackIntent(DivinationDamage, 6) { CustomLocPrefix = "RURI_DIVINATION" },new DebuffIntent());
    ....
}
```
**需要使用本前置**
### new FixedMultiAttackIntent(int damage, int repeat)
**固定伤害多段攻击，不受能力影响**
### new FixedSingleAttackIntent(int damage)
**固定伤害单段攻击，不受能力影响**
### new DynamicMultiAttackIntent(int damage, int repeat)
**动态伤害多段攻击**
### new DynamicSingleAttackIntent(int damage)
**动态伤害单段攻击**

在显示攻击意图后面添加
### CustomLocPrefix
- 没有设置的话，就默认使用原版的ATTACK

**要求创建**
```
res://
└── TestId(对应modid)
    └── localization
        ├── zhs
		│    └── ui_translation.json
        ├── eng
		│    └── ui_translation.json
		等等
```
*json内容*
```
{
    "KINGDOM_PILGRIM.title": "王国朝圣者" ,
    "KINGDOM_PILGRIM.description": "[red][jitter]「绝对存在」[/jitter][/red]\n这个敌人将要[gold]攻击[/gold]{IsMultiplayer:所有人|}造成[blue]2[/blue]点伤害{Repeat:choose(1):|[blue]{}[/blue]次}。" ,
    "RURI_DIVINATION.title": "琉花占卜" ,
    "RURI_DIVINATION.description": "这个敌人将要[gold]攻击[/gold]{IsMultiplayer:所有人|}造成[blue]{Damage}[/blue]点伤害{Repeat:choose(1):|[blue]{}[/blue]次}。"
}
```
**你可以选择直接复制后替换**
