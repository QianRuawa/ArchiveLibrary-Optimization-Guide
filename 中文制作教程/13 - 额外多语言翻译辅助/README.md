# 额外多语言翻译辅助
添加额外翻译

**要求创建**
```
res://
└── TestId(对应modid)
    └── localization
        └── zhs
            └── ui_translation.json
```
		// 注册翻译实例（自动识别调用方 Mod 用）
		UIHelper.Register(Assembly.GetExecutingAssembly(), $"res://KasumizawaMiyu/localization/");
