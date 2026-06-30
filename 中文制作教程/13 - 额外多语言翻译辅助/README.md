# 额外多语言翻译辅助
- 添加额外翻译
- 自动识别调用方
- 多个 Mod 各管各的翻译文件，key 重复不会冲突

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
在你的文件入口

```csharp
[ModInitializer(nameof(Init))]
public class TestEntiyId
{
	// 注册翻译实例（自动识别调用方 Mod 用）
	UIHelper.Register(Assembly.GetExecutingAssembly(), $"res://{ModId}/localization/");
	// 或者直接填写
	UIHelper.Register(Assembly.GetExecutingAssembly(), $"res://KasumizawaMiyu/localization/");
}
```
*json随便内容*
```
{
    "MY_KEY": "显示文本",
    "HELLO": "你好",
    "COST_REDUCTION_SPECIFIC": "指定卡牌[gold]{0}[/gold]费用减少[blue]{1}[/blue]点"
}
```
### string text = UIHelper.Get("HELLO");
**简单获取翻译内容**
### string msg = UIHelper.Get("COST_REDUCTION_SPECIFIC", cardTitle, amount);
**获取带参数的翻译内容**
### UIHelper.Default?.Get("MY_KEY");
**指定默认实例 翻译内容**
