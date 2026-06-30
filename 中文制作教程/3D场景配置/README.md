# 3D场景配置制作教程
**节点要求**
```
其他和原版一样
SubViewportContainer (用于显示 SubViewport 内容的容器)
├──SubViewport( 游戏世界的界面，不会创建窗口，也不会直接绘制到屏幕上)
├──Camera3D (3D场景的摄像头)
├──Node3D (你的3D模型会自动生成) (建议用obj来制作)
│   ├──你的3D模型
│   └──3D模型的AnimationPlayer (这个是模型里的动画)
├──WorldEnvironment (其实不怎么需要)
├──随便制作AnimationPlayer (这个是光环动画)
└──PlayerExtraAnimation (额外动画)
```
![示例1](https://github.com/QianRuawa/ArchiveLibrary-Optimization-Guide/blob/main/images/AFE8999EFB421D45763A8CC8163F60B3.webp)
![示例1](https://github.com/QianRuawa/ArchiveLibrary-Optimization-Guide/blob/main/images/B7EDAB888EAB6AE1290A5236D7259CE2.webp)
**注意Boss和角色创建是一样的**
### 特别注意一下
**创建SubViewport节点时**
当你准备发布mod时，请你检查是否开启了这个，不然使用3D制作的场景都会出现模型冲突！
![示例1](https://github.com/QianRuawa/ArchiveLibrary-Optimization-Guide/blob/main/images/7ca610281875ebaa3241189451e509a7.webp)
## 代码部分
我是使用RitsuLib前置来制作的🐇
## 美游角色制作的部分
```csharp
[RegisterCharacter]
public class MiyuCharacter : ModCharacterTemplate<MiyuCardPool, MiyuRelicPool, MiyuPotionPool>
{
  ....
	static MiyuCharacter()
	{
		CharacterAnimationRegistry.Register(
			"KASUMIZAWA_MIYU_CHARACTER_MIYU_CHARACTER", // 在先古那里可以到你角色ID部分 -> "NEOW.talk.KASUMIZAWA_MIYU_CHARACTER_MIYU_CHARACTER.1-0r.ancient": "[sine]小兔子...可能...你...需要...再来一次...[/sine]",
			new SkinAnimationProvider(
				nodePath: "miyu_character",// 这个是角色场景节点名
				extraNodePath: "PlayerExtraAnimation",// 额外动画节点名（可选添加）
				skins: new Dictionary<string, AnimSet>
				{
					["Normal"] = new("CH0145_Normal_Idle", "CH0145_Normal_Attack_End",// 当前皮肤名分类
									"CH0145_Normal_Reload", "CH0145_Vital_Dying_Ing",
									"CH0145_Vital_Death"),
					["Swimsuit"] = new("CH0218_Normal_Idle", "CH0218_Normal_Attack_End",// 当前皮肤名分类
									"CH0218_Normal_Reload", "CH0218_Cafe_my_event057_fishbox_01",
									"CH0218_Vital_Death")
				},
				getCurrentSkin: () => MiyuModConfig.SelectedSkin ?? "Normal"// 返回的皮肤
			),
      ....
		);
	}
  ....
}
```
## 默认角色制作
```csharp
[RegisterCharacter]
public class TestCharacterID : ModCharacterTemplate<TestCardPool, TestRelicPool, TestPotionPool>
{
  ....
	static TestCharacterID()
	{
    CharacterAnimationRegistry.Register(
        "CHARACTER_ID", // 角色 ID，用于本地化先古对话 key
        new SkinAnimationProvider(
            nodePath: "test_character",// 角色场景节点名
            skins: new Dictionary<string, AnimSet>
            {
                ["Normal"] = new("待机", "攻击", "技能", "受伤", "死亡")
            },
				getCurrentSkin: () => "Normal"// 固定返回一个皮肤随便填写，需要["Normal"] = new 一样
			),
    ....
		);
	}
  ....
}
```
