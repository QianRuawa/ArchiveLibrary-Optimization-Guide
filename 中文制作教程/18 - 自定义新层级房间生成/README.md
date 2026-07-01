# 自定义新层级房间生成
**优化创建自定义房间生成**
- 节点特效
- 背景美化
![示例1](https://github.com/QianRuawa/ArchiveLibrary-Optimization-Guide/blob/main/images/654bb2a65282eac3549e6c6876069ac3.webp)

创建新文件

继承 ModMapTemplate 创建章节的房间生成

```csharp
public class MyMap : ModMapTemplate
{
    public MyMap(RunState state) : base(state) { }
    // 布局：定网格、设起点终点、创建节点
    protected override int GridCols => 7;
    protected override int GridRows => 9;
    protected override void BuildMap()
    {
        _start = new MapPoint(3, 0) { PointType = MapPointType.Ancient };
        _boss  = new MapPoint(3, 8) { PointType = MapPointType.Boss };
        var a = CreatePoint(3, 1, MapPointType.Unknown);
        var b = CreatePoint(2, 2, MapPointType.Monster);
        _start.AddChildPoint(a);
        a.AddChildPoint(b);
        b.AddChildPoint(_boss);
    }
}
```
**如果需要房间节点下创建生成特效**

*可以看一下这里*
```csharp
public class MyMap : ModMapTemplate
{
....
    //  粒子特效
    protected override string? ParticleScenePath => ""; 
    protected override string? BossVfxScenePath => "";
    // 节点视觉
    protected override void SetupPointVisuals()
    {
        SetPointStyle(3, 1);
        SetPointStyle(2, 2);
        ....
        AddBossVfx(3, 8);
    }
....
}
```
### ParticleScenePath
**普通房间节点下的特效**
- 默认固定跳过先古和Boss
### BossVfxScenePath
**Boss房间节点下的特效**
