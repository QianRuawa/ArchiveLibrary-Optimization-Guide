# 使用代码生成标题动画
```csharp
TitleAnimationHelper.Play();// 默认生成黑幕

TitleAnimationHelper.Play("res://monster/scene/title/title_Wakamo.tscn");// 指定路径生成
```
## 场景配置
**黑幕场景**
![示例](https://github.com/QianRuawa/ArchiveLibrary-Optimization-Guide/blob/main/images/379FF0C5C5CB349EDCE34C1C6196DCD8.webp)
**若藻标题场景**
![示例](https://github.com/QianRuawa/ArchiveLibrary-Optimization-Guide/blob/main/images/9C715952A71C7000C3262103ED9A691F.webp)
### 注意事项
![示例](https://github.com/QianRuawa/ArchiveLibrary-Optimization-Guide/blob/main/images/515711850D68DE3BE48253130ACEB1FB.webp)
- 在Anim节点动画设置里，启用默认 (就是动画那里出现三角形里面有个A)
- 在动画结尾添加，方法调用轨道，选择该场景的根节点，添加queue_free()方法调用，在动画结尾移除该节点
- 其他可以自己制作喜欢的🐇
