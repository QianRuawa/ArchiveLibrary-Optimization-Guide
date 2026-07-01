# 自定义新层级房间生成
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
```
