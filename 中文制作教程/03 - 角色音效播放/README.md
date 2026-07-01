# 角色音效播放
主要是目前前置，没有制作普通音频播放效果

所以我自己制作了一下

代码部分

- 我直接演示美游mod了

在RitsuLib设置随便一个Fmod音效路径

```csharp
....
  var audio = new CharacterAudioAssetSet(
    CharacterSelectSfx: "event:/sfx/miyu_character_select",
    CharacterTransitionSfx: null,
    AttackSfx: null,
    CastSfx: null,
    DeathSfx: "event:/sfx/miyu_character_death"
  );
....
static MiyuCharacter()
{
  CharacterAnimationRegistry.Register(
    "KASUMIZAWA_MIYU_CHARACTER_MIYU_CHARACTER",
    ....
    new Dictionary<string, (string Path, float VolumeOffset)>
    {
      ["event:/sfx/miyu_character_select"] = ("res://sound/Miyu_character_select_1.ogg", -7f),
      ["event:/sfx/miyu_character_death"] = ("res://sound/Miyu_character_death.ogg", -5f),
      ["event:/sfx/characters/miyu_character/miyu_character_attack"] = (null, 0f),
      ["event:/sfx/characters/miyu_character/miyu_character_cast"] = (null, 0f),
    }
  );
}
```
- CharacterSelectSfx: "event:/sfx/miyu_character_select",
- ["event:/sfx/miyu_character_select"] = ("res://sound/Miyu_character_select_1.ogg", -7f),

简单来说只要在[输入自定义的Fmod]然后拦截，播放你本地的音效 

(1.路径, 2.音效分贝)

![示例1](https://github.com/QianRuawa/ArchiveLibrary-Optimization-Guide/blob/main/images/408BE871C536B1AB765C12C4ED0D38EA.webp)
