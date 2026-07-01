# 自定义新层级
**可以让你方便的创建新的层级**
- 自动注册，无需补丁
- 自动在怪物图鉴注册
- 如果没有添加[篝火/宝箱]等背景，默认帮你添加
- 默认拦截达弗，可以自己设置
- 允许在A10，可以自己设置是否存在第2个Boss

但是制作比较复杂
![示例1](https://github.com/QianRuawa/ArchiveLibrary-Optimization-Guide/blob/main/images/654bb2a65282eac3549e6c6876069ac3.webp)

创建新文件

继承 ModActTemplate 创建新章节

```csharp
public class ExtraAct : ModActTemplate
{
    // act 4
    public override int Index => 4;
    // 地图颜色
    public override Color MapTraveledColor => new Color("");
    public override Color MapUntraveledColor => new Color("");
    public override Color MapBgColor => new Color("");
    // 地图内容
    public override IEnumerable<EventModel> AllEvents => ...;
    public override IEnumerable<EncounterModel> GenerateAllEncounters() => ...;
    public override IEnumerable<AncientEventModel> AllAncients => ...;
    // 地图背景
    public override string? CustomMapTopBgPath => "";
    public override string? CustomMapMidBgPath => "";
    public override string? CustomMapBotBgPath => "";
    // 层级音乐
    public override string[] BgMusicOptions => ...;
    public override string[] MusicBankPaths =>...;
    public override string AmbientSfx => ...;
    public override string ChestOpenSfx => ...;
    public override string ChestSpineSkinNameNormal => ...;
    public override string ChestSpineSkinNameStroke => ...;
    public override string ChestSpineResourcePath => ...;
    // 房间类型分布
    public override MapPointTypeCounts GetCustomMapPointTypes(Rng mapRng)
    {
        var counts = base.GetCustomMapPointTypes(mapRng);
        SetPrivateField(counts, "NumOfElites", 1);
        SetPrivateField(counts, "NumOfShops", 1);
        SetPrivateField(counts, "NumOfUnknowns", 2);
        SetPrivateField(counts, "NumOfRests", 3);
        return counts;
    }
    private static void SetPrivateField(object obj, string fieldName, object value)
    {
        var field = typeof(MapPointTypeCounts).GetField($"<{fieldName}>k__BackingField",
            BindingFlags.NonPublic | BindingFlags.Instance);
        field?.SetValue(obj, value);
    }
}
```

```
```
json内容
```csharp
{
  "STEEL_CONTINENT.title": "钢铁大陆"
}
```
### Index
**你要制作的层级**
### MapTraveledColor / MapUntraveledColor / MapBgColor
**地图的颜色，按你自己喜欢来**
- MapTraveledColor 走过的路径颜色
- MapUntraveledColor 未探索路径颜色
- MapBgColor 背景颜色
### CustomMapTopBgPath / CustomMapMidBgPath / CustomMapBotBgPath
**你可以自定义背景路径**

本前置已经优化过了
- CustomMapTopBgPath 地图顶部背景
- CustomMapMidBgPath 地图中间背景
- CustomMapBotBgPath 地图低部背景
### 层级音乐
**你可以自己复用原游戏的**
