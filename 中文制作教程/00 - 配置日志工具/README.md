# 配置日志工具
在你的文件入口

```csharp
[ModInitializer(nameof(Init))]
public class TestEntiyId
{
		// 设置日志中文前缀
		LibraryLogger.SetPrefix("XXXX");
}
```
### 调用LibraryLogger.Info(string message, [CallerFilePath] string filePath = "", [CallerLineNumber] int lineNumber = 0)

**Log.Info($"{GetPrefix()}{{信息}}: {message} 路径：{GetShortPath(filePath)}:{lineNumber}");**

- message 输出日志的文本

**输出日志格式**
- 》》》[霞沢美游 mod]信息：XXXXXXXXX 路径:xxxx.cs
