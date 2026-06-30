# 判断存在遗物相关
代码部分

```csharp
  await RelicHelper.IfHasRelic<TestRelicId>(creature, async () =>
  {
    // 你自己的逻辑
  });
```
