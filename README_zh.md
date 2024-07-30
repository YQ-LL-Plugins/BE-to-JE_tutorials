# BE-to-JE_tutorials

[English](README.md) | 简体中文

> Minecraft基岩版存档转换到Java版的简明教程

## 地图转换器

推荐项目：[kbinani/je2be-core: Map converter for Minecraft Java, Bedrock, Xbox360, and PS3 Edition](https://github.com/kbinani/je2be-core)

- 此项目可以几乎完美地在JE和BE格式之间转换存档，包括所有类型的方块、容器和物品、实体，甚至自定义地图画
- Windows版：https://www.microsoft.com/store/apps/9PC9MFX9QCXS
- 网页版：[https://je2be.app](https://je2be.app/)

<img src="assets/image-20240730194651156.png" alt="image-20240730194651156" style="zoom:50%;" />

## 服务器玩家物品栏迁移

对于BDS服务器存档，除了转换地图之外，还需要导出各玩家物品栏和末影箱并手动转换到Java版。可以使用现有插件来辅助迁移工作，流程如下：

1. 配置 BDS1.21.3 + LeviLamina 0.13.4，加载要转换的基岩版存档
2. 安装插件 [YQ-LL-Plugins/BDS-InventoryExporter](https://github.com/YQ-LL-Plugins/BDS-InventoryExporter)，启动服务器。服务器启动完毕后，插件将把所有玩家的物品栏和末影箱导出为NBT格式，存放到`plugins/InventoryExporter/saved`
3. 使用工具将NBT数据转换到Java版，并直接导入Java版存档中
4. 如果上一步无法实现，另一种方法：
   - 安装 LegacyScriptEngine-QuickJs 和插件 [YQ-LL-Plugins/ImportInventoryAsChest](https://github.com/YQ-LL-Plugins/ImportInventoryAsChest)
   - 将`BDS-InventoryExporter`导出的NBT数据全部复制到`plugins/ImportInventoryAsChest/saved`
   - 进入游戏，执行`importinv`命令
   - 插件将在z增大方向生成箱子阵列，按顺序储存所有玩家的物品栏和末影箱，并用告示牌记录箱子对应的玩家名称
   - 使用`je2be`将存档转换为Java版，手动将物品重新分发给玩家