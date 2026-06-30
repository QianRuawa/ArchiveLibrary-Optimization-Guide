# 额外动画播放
在这里看场景配置[3D场景配置](https://github.com/QianRuawa/ArchiveLibrary-Optimization-Guide/blob/main/%E4%B8%AD%E6%96%87%E5%88%B6%E4%BD%9C%E6%95%99%E7%A8%8B/3D%E5%9C%BA%E6%99%AF%E9%85%8D%E7%BD%AE/README.md)

**该方法适应全部**
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
    ....
	}
	//占有之榴弹
	private async Task PossessionGrenadeMove(IReadOnlyList<Creature> targets)
	{
		BossAnimationHelper.PlayAttackAsync(Creature, ATTACk_EXS_2 ,IDLE_NORMAL,1.0f);
        ExtraAnimationHelper.PlayAsync(Creature, "Ex_2", 1f, "Idle");
		await Cmd.Wait(5.32f);
		for (int i = 0; i < 2; i++)
		{
			await DamageCmd
				.Attack(GrenadeDamage)
				.FromMonster(this)
				.Execute(null);
		}
		//获取格挡
		await CreatureCmd.GainBlock(Creature, GrenadeBlock, ValueProp.Move, null);
	}
	//思慕之霰弹
	private async Task YearningShotgunMove(IReadOnlyList<Creature> targets)
	{
		BossAnimationHelper.PlayAttackAsync(Creature, ATTACk_EXS_3 ,IDLE_NORMAL,1.0f);
		ExtraAnimationHelper.PlayAsync(Creature, "Ex_3", 1f, "Idle");
		await Cmd.Wait(5.30f);
		await DamageCmd
			.Attack(ShotgunDamage)
			.FromMonster(this)
			.Execute(null);
	}
```

