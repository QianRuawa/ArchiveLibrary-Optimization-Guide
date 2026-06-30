# 3D场景配置制作教程
**节点要求**
```
SubViewportContainer(用于显示 SubViewport 内容的容器)
—SubViewport(游戏世界的界面，不会创建窗口，也不会直接绘制到屏幕上)
——Camera3D(3D场景的摄像头)
——Node3D(你的3D模型会自动生成)(建议用obj来制作)
——WorldEnvironment(其实不怎么需要)
——AnimationPlayer(这个是光环动画)
—PlayerExtraAnimation(额外动画)
```
**注意Boss和角色创建是一样的**
### 特别注意一下
**创建SubViewport节点时**
准备发布时，请你开启这个，不然使用3D制作的场景都会出现模型冲突！
![示例1](https://github.com/QianRuawa/ArchiveLibrary-Optimization-Guide/blob/main/images/7ca610281875ebaa3241189451e509a7.webp)

## 角色配置
![示例1](https://github.com/QianRuawa/ArchiveLibrary-Optimization-Guide/blob/main/images/AFE8999EFB421D45763A8CC8163F60B3.webp)

