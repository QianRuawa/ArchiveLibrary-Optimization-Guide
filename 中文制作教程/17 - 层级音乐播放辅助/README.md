# 层级音乐播放辅助
**因为原版游戏是使用Fmod制作**

本人不会，所以优化了一下播放

在继承 ModActTemplate 里添加代码

```csharp
public class ExtraAct : ModActTemplate
{
  ....
  public override ActMusicProfile? CustomMusic => new("你自己音乐的路径", VolumeDb: 音乐大小);
  ....
}
```
```csharp
public record class ActMusicProfile(
    string MusicPath,
    float VolumeDb = -6f,
    float FadeIn = 1.5f,
    float FadeOut = 1.5f,
    double LoopStart = 0f,
    double LoopEnd = 0f
);
```
### ActMusicProfile(string MusicPath, float VolumeDb = -6f, float FadeIn = 1.5f, float FadeOut = 1.5f, double LoopStart = 0f, double LoopEnd = 0f);
- MusicPath 音乐的路径
- VolumeDb 音乐大小
- FadeIn 淡入秒数
- FadeOut 淡出秒数
- LoopStart 循环起点 0=从头
- LoopEnd 循环终点 0=播到尾循环

在这里看[自定义新层级](https://github.com/QianRuawa/ArchiveLibrary-Optimization-Guide/tree/main/%E4%B8%AD%E6%96%87%E5%88%B6%E4%BD%9C%E6%95%99%E7%A8%8B/16%20-%20%E8%87%AA%E5%AE%9A%E4%B9%89%E6%96%B0%E5%B1%82%E7%BA%A7)
