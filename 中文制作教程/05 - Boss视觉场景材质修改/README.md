# Boss视觉场景材质修改
- 你需要准备两个材质
- 我这里用我自己的设置的来

![示例1](https://github.com/QianRuawa/ArchiveLibrary-Optimization-Guide/blob/main/images/E599BF206EAA5F4CE8D62017E08D8FC3.webp)

- 选择修改模型节点名

![示例1](https://github.com/QianRuawa/ArchiveLibrary-Optimization-Guide/blob/main/images/B11D32AA34A23B82B9E15421CC9D3905.webp)

- 在怪物视觉场景上挂脚本

![示例1](https://github.com/QianRuawa/ArchiveLibrary-Optimization-Guide/blob/main/images/43722CF54E4B7DD898D758F331014FA7.webp)

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
### 在脚本上添加IDifficultyMaterialProvider
- GetMeshNodeName 替换材质的MeshInstance3D节点名称
- GetMaterialPathForDifficulty 返回材质资源路径
**默认是修改0号位材质**

**或者你想替换Boss场景下所有模型存在**

代码部分
```csharp
DifficultyMaterialHelper.ApplyMaterialToAllMeshInstances()
```
使用这个就可以
### DifficultyMaterialHelper.ApplyMaterialToAllMeshInstances(Node root, string materialPath)
- root 指定某节点下全部MeshInstance3D节点
- materialPath 替换材质路径

**固定是全部3D节点下0号位材质**
