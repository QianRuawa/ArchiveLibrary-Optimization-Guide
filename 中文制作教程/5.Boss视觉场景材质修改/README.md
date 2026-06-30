# Boss视觉场景材质修改
- 你需要准备两个材质
- 我这里用我自己的设置的来

![示例1](https://github.com/QianRuawa/ArchiveLibrary-Optimization-Guide/blob/main/images/E599BF206EAA5F4CE8D62017E08D8FC3.webp)

- 选择修改模型节点名

![示例1](https://github.com/QianRuawa/ArchiveLibrary-Optimization-Guide/blob/main/images/B11D32AA34A23B82B9E15421CC9D3905.webp)
代码部分
```csharp
public partial class MyoukiKurokageCreatureVisuals : NCreatureVisuals, IDifficultyMaterialProvider
{
	public string GetMeshNodeName() => "EN0006_Body";
	string IDifficultyMaterialProvider.GetMaterialPathForDifficulty()
	{
		switch (MiyuModConfig.BossDifficulty)
		{
			case BossDifficulty.Extreme:
				return "res://monster/boss/myouki_kurokage/3D/EN0006_Ex.tres";
			default:
				return "res://monster/boss/myouki_kurokage/3D/EN0006_Insane.tres";
		}
	}
	public override void _Ready()
	{
		base._Ready();
		this.ApplyDifficultyMaterial(this);
	}
}
```
- GetMeshNodeName() => "EN0006_Body";我这里修改的模型节点是EN0006_Body
- IDifficultyMaterialProvider.GetMaterialPathForDifficulty() 返回材质路径
- 默认是修改0号位材质

**或者你想替换Boss场景下所有模型存在**
代码部分
```csharp
DifficultyMaterialHelper.ApplyMaterialToAllMeshInstances();
```
使用这个就可以
- 默认是替换全部可以替换的材质
