# 切换战斗时的背景
**场景配置**

![示例](https://github.com/QianRuawa/ArchiveLibrary-Optimization-Guide/blob/main/images/02F8D1B209F44D1622034DC530156C66.webp)

油桶蟹代码部分调用
![示例](https://github.com/QianRuawa/ArchiveLibrary-Optimization-Guide/blob/main/images/4031338A63C36DEA8C0F6FABC53A49F9.webp)
```csharp
private const string STREET_BG = "SubViewportContainer";
  //发怒
  private async Task AngerAction(IReadOnlyList<Creature> targets)
  {
      _phaseTwoTriggered = true;
      FmodMusicHelper.UpdateLoopSegment(3.96, 129.69);
      BossAnimationHelper.PlayAttackAsync(Creature, PHASECHANGE,null,1f);
      ExtraAnimationHelper.Play(Creature, "PhaseChange_01", 1f);
      await Cmd.Wait(3.2f);
      TitleAnimationHelper.Play();
      await Cmd.Wait(1f);
      SwitchModelToPhase2();
      await Cmd.Wait(0.1f);
      if(MiyuModConfig.IsHighDifficulty)SwitchBackgroundWithAnimation(STREET_BG, "ins_op_2");
      else SwitchBackgroundWithAnimation(STREET_BG, "op_2");
  var barrel = ModelDb.Monster<BarrelMonster>().ToMutable();
  if (barrel is BarrelMonster guidanceDevice)
  {
    string slotName = "barrel";
    await CreatureCmd.Add(guidanceDevice, CombatState, CombatSide.Enemy, slotName);
          LibraryLogger.Info("已召唤油桶怪到 barrel 槽位");
  }
      // 清除所有能力
      var allPowers = Creature.Powers.ToList();
      foreach (var power in allPowers)
      {
          if (power is SpecialPower) continue;
          await PowerCmd.Remove(power);
      }
      await SetScaledMaxHp(Phase2LowLevelHP, Phase2HighLevelHp);
      await PowerCmd.Apply<DamagedHullPower>(new BlockingPlayerChoiceContext(), Creature, 1, Creature, null);
      await Cmd.Wait(0.2f); 
      NCombatRoom.Instance?.GetCreatureNode(Creature)?.RefreshIntents();
  }
```
