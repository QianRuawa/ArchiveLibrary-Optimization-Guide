# Bgm音乐播放
**这个比较麻烦**
- 有简单播放
- 有比较难的需要你自己调整循环时间
- 比较难可以制作设置两段循环点

*文件路径:*

![示例1](https://github.com/QianRuawa/ArchiveLibrary-Optimization-Guide/blob/main/images/408BE871C536B1AB765C12C4ED0D38EA.webp)

**代码部分**

我这里使用自己猫鬼部分
```csharp
public override async Task AfterAddedToRoom()
{
  await base.AfterAddedToRoom();
  ....
    FmodMusicHelper.PlayWithLoop(
        "res://sound/audio/Dark_Shadows.mp3", 
        loopStart: 23.65,
        loopEnd: 56.35,
        fadeInDuration: 1.0f, 
        volumeDb: -14
    );
  ....
}
//二阶段
private async Task EnterPhase2()
{
  ....
  FmodMusicHelper.UpdateLoopSegment(23.11, 110.58);
  ....
}
```
若藻部分
```csharp
public override async Task AfterAddedToRoom()
{
  await base.AfterAddedToRoom();
  ....
  FmodMusicHelper.Play("res://sound/audio/Na_Na_Natsu!.ogg", fadeInDuration: 1.0f,-18);
  ....
}
```

介绍一下调用部分

### FmodMusicHelper.Play(string musicPath, float fadeInDuration = 1.5f, float volumeDb = 0f)
**使用这个比较简单**

- musicPath 路径
- fadeInDuration 淡入音乐时长
- volumeDb 音乐分贝

### FmodMusicHelper.PlayWithLoop(string musicPath, double loopStart, double loopEnd = 0.0, float fadeInDuration = 1.5f, float volumeDb = 0f)
**这个是设置音乐循环**

- musicPath 路径
- loopStart 循环开始播放时间段
- loopEnd 播放到循环结束段
- fadeInDuration 淡入音乐时长
- volumeDb 音乐分贝

### FmodMusicHelper.UpdateLoopSegment(double newLoopStart, double newLoopEnd)
**更新音乐循环点**

- newLoopStart 新循环开始时间段
- newLoopEnd 新循环结束时间段
