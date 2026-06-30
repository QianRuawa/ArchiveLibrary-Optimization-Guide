# 先古遗物图鉴分类注册
**只要使用RitsuLib前置**

通过 [RegisterActAncient] 特性注册的先古

```csharp
[RegisterActAncient(typeof(SteelContinent))]
public class Transporter : ModAncientEventTemplate
{
    public override EventAssetProfile AssetProfile => new(
        InitialPortraitPath: "res://images/ancients/transporter.png"
    );
}
```
框架自动扫描程序集中的 ModAncientEventTemplate 子类

自动注册到遗物图鉴先古分类里
