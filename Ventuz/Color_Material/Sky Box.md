[toc]
# 表格总览
| ![SkyBox.png](https://cdn.nlark.com/yuque/0/2021/png/12794363/1624843844768-f6a0b7c7-0439-4975-889f-2f285f2f5c73.png)Sky Box | 模拟一个环境，并能够使用图像对场景进行照明。 |
| --- | --- |

基于图像的照明(Image-based lighting)是一种奇妙的技术，它利用高动态范围(High Dynamic Range)的图像来创造逼真和复杂的照明。除了实现基于图像的照明(lighting)和反射(reflections)，天盒节点还允许你渲染一个立方体环境。
你最多可以为SkyBox节点添加三个纹理。每一个都必须是符合相应使用要求的Cubemap。它们通常是在Ventuz之外使用合适的软件创建的。

![Snipaste_2021-06-28_10-43-33.png](https://cdn.nlark.com/yuque/0/2021/png/12794363/1624848237541-bc95ca99-261c-4349-9d5d-ebcd77e95ff1.png)

| 【推荐】[cmftStudio_win64.zip](https://www.yuque.com/attachments/yuque/0/2021/zip/12794363/1624847748111-6e3d1f33-e96c-4eb0-a4f8-a019e2d02b0e.zip?_lake_card=%7B%22uid%22%3A%221624847740420-0%22%2C%22src%22%3A%22https%3A%2F%2Fwww.yuque.com%2Fattachments%2Fyuque%2F0%2F2021%2Fzip%2F12794363%2F1624847748111-6e3d1f33-e96c-4eb0-a4f8-a019e2d02b0e.zip%22%2C%22name%22%3A%22cmftStudio_win64.zip%22%2C%22size%22%3A5229031%2C%22type%22%3A%22application%2Fx-zip-compressed%22%2C%22ext%22%3A%22zip%22%2C%22progress%22%3A%7B%22percent%22%3A99%7D%2C%22status%22%3A%22done%22%2C%22percent%22%3A0%2C%22id%22%3A%227RmuY%22%2C%22card%22%3A%22file%22%7D) |
| ------------------------------------------------------------ |
| [ModifiedCubeMapGen-1_66.zip](https://www.yuque.com/attachments/yuque/0/2021/zip/12794363/1624844939172-a6817170-1117-42cc-8858-bc267d72695e.zip?_lake_card=%7B%22uid%22%3A%221624844934271-0%22%2C%22src%22%3A%22https%3A%2F%2Fwww.yuque.com%2Fattachments%2Fyuque%2F0%2F2021%2Fzip%2F12794363%2F1624844939172-a6817170-1117-42cc-8858-bc267d72695e.zip%22%2C%22name%22%3A%22ModifiedCubeMapGen-1_66.zip%22%2C%22size%22%3A266321%2C%22type%22%3A%22application%2Fx-zip-compressed%22%2C%22ext%22%3A%22zip%22%2C%22progress%22%3A%7B%22percent%22%3A99%7D%2C%22status%22%3A%22done%22%2C%22percent%22%3A0%2C%22id%22%3A%224yQH9%22%2C%22card%22%3A%22file%22%7D) |
| [IBLBaker-master.zip](https://www.yuque.com/attachments/yuque/0/2021/zip/12794363/1624848442756-a55b498e-6793-4e92-8c66-e1792f3c7bbb.zip?_lake_card=%7B%22uid%22%3A%221624848288849-0%22%2C%22src%22%3A%22https%3A%2F%2Fwww.yuque.com%2Fattachments%2Fyuque%2F0%2F2021%2Fzip%2F12794363%2F1624848442756-a55b498e-6793-4e92-8c66-e1792f3c7bbb.zip%22%2C%22name%22%3A%22IBLBaker-master.zip%22%2C%22size%22%3A245133263%2C%22type%22%3A%22application%2Fx-zip-compressed%22%2C%22ext%22%3A%22zip%22%2C%22progress%22%3A%7B%22percent%22%3A99%7D%2C%22status%22%3A%22done%22%2C%22percent%22%3A0%2C%22id%22%3A%22eGgIJ%22%2C%22card%22%3A%22file%22%7D) |

# Cubemap 布局
Ventuz能够解释几种**Cubemap**的布局。通常情况下，它能够自动区分它们。
## LongLat
<img src="https://cdn.nlark.com/yuque/0/2021/png/12794363/1624844340788-50dac84f-b6ef-40e4-bce4-691c523708e1.png" alt="LongLat.png" style="zoom:50%;" />

**Longitude-Latitude（经纬度)**立体地图是根据极地坐标来保存环境信息的。这就导致了地图上有大量的信息在映射球体的顶部和底部，而赤道线上的信息最少。
## Crosses
<img src="https://cdn.nlark.com/yuque/0/2021/png/12794363/1624844391095-b9342599-eed8-4721-9559-00aa8ee377d6.png" alt="Crosses.png" style="zoom:30%;" />

**Horizontal （横向）**和**Vertical Crosses(纵向)**的十字交叉保存了你的环境信息，基于一个展开的立方体。这种布局是最常见的，因为它因其无缝性而非常容易手动创建。垂直交叉布局是由ATI工具使用的。
## Strips
![Strips.png](https://cdn.nlark.com/yuque/0/2021/png/12794363/1624847686120-8e9ad0ba-0382-4953-8e6f-fdb2e46e3139.png)

**Horizontal Strips(水平条状图)**将你的环境信息保存为一个简单的条状图。这种布局的部分有接缝，因此在[MipMap](https://my.oschina.net/sweetdark/blog/177812)计算中不会相互影响，这可能会导致明显的伪影。

# Irradiance Texture辐照度纹理
辐照度模拟环境如何照亮场景。它通过将环境中的信息映射到受影响物体的材质中的定义通道来控制光线的数量、颜色和质量。通常情况下，辐照度纹理每部分不超过128像素，并且没有[MipMaps](https://my.oschina.net/sweetdark/blog/177812)。
| **Mapping**                              | 改变了纹理在环境中的映射方式，从而改变了它对物体的影响。<br/>- **Simple EnvMap**使用默认设置的相应贴图。<br/>- **EnvMap**显示所有需要调整的属性。 |
| ---------------------------------------- | ------------------------------------------------------------ |
| **Color**                                | 定义了纹理的颜色通道应该应用到受影响物体的哪个材料通道，使用哪种操作以及是否使用Masking。Alpha对纹理的Alpha通道也有同样的作用。 |
| **Amount**                               | 定义了纹理对材料底纹的影响程度。                             |
| **LodBias**                              | LodBias调整MipMap的起始步长--你通常应该把这个值设置为-16来完全禁用MipMaps，因为这只会产生伪影。 |
| **LimitDynamicRange<br/>(限制动态范围)** | LimitDynamicRange（限制动态范围）为所有通道的值创建一个上限。当一个纹理像素有一个较高的值时，它将被限制在这个值上。0意味着没有限制。 |
| **Exposure<br/>  (曝光)**                | Exposure（曝光）应用受影响物体的曝光值，独立于HDR 3D层的曝光值。为所有通道的值创建一个上限。当一个纹理像素有一个较高的值时，它将被限制在这个值上。0意味着没有限制。Exposure（曝光）应用受影响物体的曝光值，独立于HDR 3D层的曝光值。 |

# Specular Texture
镜面纹理影响目标物体的反射，同时考虑到它们的粗糙度。一个物体越粗糙，反射就越模糊，或者说越模糊。
大多数属性与辐照度纹理的作用相同。**PrefilterMethod、Log2UserScale、Log2MipOffset和DefaultMinRoughness的设置应该和你计算纹理的软件一样。**

| **PrefilterMethod**
**(预过滤方法)** | 定义了一个关于如何在Specular Texture的不同细节级别之间取样的方程式。用户必须知道导出纹理时使用的是哪种PrefilterMethod。
**Log2Power**，他需要知道设置的**User Scale**和**Mip Map Offset**，并相应地设置**Log2UserScale**和**Log2MipOffset**属性
**Default**，用户必须定义设定的**Minimum Roughness**。
粗糙度是通过使用更高的MipMap steps来模拟的。 |
| --- | --- |
| **LodBias** | 定义了在哪一个步长上开始没有粗糙度的地方。材料越粗糙，使用的MipMap就越高。通常情况下，当使用Default prefilter方法时，将此值设置为负值，否则就将其设置为0。 |
| **Sky Box Texture** | 如果你想使用一个不影响物体材质的简单天空立体图，你可以使用**Sky Box Texture** Group。在这里你可以插入第三个纹理，然后在背景中进行渲染--在一个始终与摄像机对齐的球体上。 |

# SkyBox类别
| **Rotate** | 属性使天空围绕世界的Y轴旋转，影响所有使用的纹理。 |
| --- | --- |
| **RotateOffSetSky** | 是一个额外的旋转，只应用于天空盒纹理。 |
| **Drawsky** | 设置背景图像（即环境贴图）在渲染器中是否可见。
如果你想把Specular Texture（镜面纹理）作为天空盒而不是专门的天盒来绘制，你可以把SkyBox类别中的DrawSky布尔值设置为true。这样一来，Specular Texture就会被绘制到SkyBox中。 |

# HDRI&IBL
## 基于图像的照明 - IBL
我们的渲染引擎支持HDRI和IBL。因此，我们有可能创造出更逼真的材料。其中一个新功能就是==Roughness==。

> 具体请看SkyBox的演示文件，使用贴图控制粗糙度

提示：

- **金属材料**
1. 无底色

- **塑料材料**
1. 基色
1. 只有Specular值而没有颜色
## 图层3D根节点必须切换到引擎=HDR 
天空盒不仅可以创建一个漂亮的360°背景，它还将用于反射和漫反射照明。
你可以用来自天空的光照亮你的整个场景。
SkyBox的主要目的是用于HDR，但它也可以使用非HDR图像。

> 你可以单独调整每个元素的曝光值，并独立于全局3D层HDR曝光。

在这里你可以加载你的Irradiance Texture。这个贴图将照亮你的场景/模型。
如果你使用MipMaps（DDS），你必须将LodBias调整为-16，以禁用MipMap并防止出现伪影。
Specular, 这里你要加载你的Specular-reflection Texture。这个纹理将被用于SpecularChannel并创建一个反射
为了控制反射的数量，你将调整MaterialNode中的SPECULAR值。
如果你使用的是MipMaps（DDS），你必须调整LodBias的负值，以控制反射环境纹理的清晰度。