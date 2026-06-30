# 动画播放
在这里看场景配置[3D场景配置](https://github.com/QianRuawa/ArchiveLibrary-Optimization-Guide/blob/main/%E4%B8%AD%E6%96%87%E5%88%B6%E4%BD%9C%E6%95%99%E7%A8%8B/3D%E5%9C%BA%E6%99%AF%E9%85%8D%E7%BD%AE/README.md)
## 角色部分
![示例](https://github.com/QianRuawa/ArchiveLibrary-Optimization-Guide/blob/main/images/C19AF43373B2B5490550802FE7FF0C50.webp)
![示例](https://github.com/QianRuawa/ArchiveLibrary-Optimization-Guide/blob/main/images/4DAE80288DFEF3BFB29E332DB004F1FA.webp)

角色代码

这个部分有讲[3D场景配置](https://github.com/QianRuawa/ArchiveLibrary-Optimization-Guide/blob/main/%E4%B8%AD%E6%96%87%E5%88%B6%E4%BD%9C%E6%95%99%E7%A8%8B/3D%E5%9C%BA%E6%99%AF%E9%85%8D%E7%BD%AE/README.md)
```csharp
	["Normal"] = new("CH0145_Normal_Idle", "CH0145_Normal_Attack_End",
					"CH0145_Normal_Reload", "CH0145_Vital_Dying_Ing",
					"CH0145_Vital_Death"),
	["Swimsuit"] = new("CH0218_Normal_Idle", "CH0218_Normal_Attack_End",
					"CH0218_Normal_Reload", "CH0218_Cafe_my_event057_fishbox_01",
					"CH0218_Vital_Death")
```
## Boss部分
![示例](https://github.com/QianRuawa/ArchiveLibrary-Optimization-Guide/blob/main/images/88EF67F2E9CAB0B2AA3F1383C49C555C.webp)

Boss动画制作代码调用
```csharp
//琉花占卜
private async Task RuriDivinationMove(IReadOnlyList<Creature> targets)
{
	BossAnimationHelper.PlayAttackAsync(Creature, ATTACk_EXS_1 ,IDLE_NORMAL,1.0f);
	// 如果不想等待动画播放完后执行的可以去掉await
	ExtraAnimationHelper.Play(Creature, "Ex_1", 1f);
	await Cmd.Wait(6.05f);
	// 自己添加await Cmd.Wait(6.05f);看看Boss动画在什么部分抬手	
	....
}
```
### BossAnimationHelper.PlayAttackAsync(Creature creature, string attackAnimName, string idleAnimName = "idle", float speedScale = 0.6f, float originalspeedScale = 0f)
- creature 是Boss本身
- attackAnimName 播放的攻击或者技能动画的名字
- idleAnimName 所有的动画结束后，代码会使用你设置的动画来播放，默认使用idle动画
- speedScale 本次播放动画的速度
- originalspeedScale 播放动画完后你可以设置待机动画速度

# 额外动画播放
在这里看场景配置[3D场景配置](https://github.com/QianRuawa/ArchiveLibrary-Optimization-Guide/blob/main/%E4%B8%AD%E6%96%87%E5%88%B6%E4%BD%9C%E6%95%99%E7%A8%8B/3D%E5%9C%BA%E6%99%AF%E9%85%8D%E7%BD%AE/README.md)

## 角色配置
默认对应原游戏里的5个动画名
![示例](https://github.com/QianRuawa/ArchiveLibrary-Optimization-Guide/blob/main/images/D040BE6E019E0179AFB2237220C08A97.webp)
## Boss配置
![示例](https://github.com/QianRuawa/ArchiveLibrary-Optimization-Guide/blob/main/images/9BA95B65BBB3DC44ED9031381E83BECD.webp)

**Boss额外动画配置比较特殊**

**制作者可以自定义，需要的动画**

代码部分调用
```csharp
//琉花占卜
private async Task RuriDivinationMove(IReadOnlyList<Creature> targets)
{
	BossAnimationHelper.PlayAttackAsync(Creature, ATTACk_EXS_1 ,IDLE_NORMAL,1.0f);
	ExtraAnimationHelper.Play(Creature, "Ex_1", 1f);
	await Cmd.Wait(6.05f);
	....
}
```
### ExtraAnimationHelper.Play(Creature creature, string animName, float speedScale = 1f)
- creature 是Boss本身
- animName 播放的额外动画的名字
- speedScale 本次动画播放速度，也按你自己喜欢来调整
