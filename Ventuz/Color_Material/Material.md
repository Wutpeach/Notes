

# 常规

材料节点控制作为子结构中的每个渲染对象的表面的外观。它由几个选项组成**（具体见思维导图）**，可以添加到它的属性列表中来覆盖相应的选项。这些选项在材料节点的标签下可用，这些标签由属性编辑器中的材料定义顶部的按钮栏表示。

<img src="https://cdn.nlark.com/yuque/0/2021/png/12794363/1624625640314-5a9756c9-46c5-4293-97ce-b7aa66acdef0.png" alt="MaterialOptionTabs.png" style="width:30%;" />

- **你在材料节点中没有调整的所有选项卡都被默认材料或前面的材料节点所继承。**
- **根据材料节点内使用的属性组，图标可能会改变。**
| <img src="https://cdn.nlark.com/yuque/0/2021/png/12794363/1624626037059-b1e82219-66f8-402d-a7db-3f7ec60afcc5.png#" alt="MAT01.png" style="width:20%;" />渲染的预览 | 如果只使用标准或阴影选项卡中的属性组。 |
| :-: | --- |
| <img src="https://cdn.nlark.com/yuque/0/2021/png/12794363/1624626041058-dcbe60a4-0253-49b6-a83d-bbcb6c018942.png" alt="MAT02.png" style="width:20%;" />带有浅蓝色装饰的渲染预览 | 如果 "标准 "或 "阴影 "选项卡中的属性组与任何其他选项一起使用，如某种绘图模式或某种混合方式。 |
| <img src="https://cdn.nlark.com/yuque/0/2021/png/12794363/1624626046184-cf23bc03-6227-4aff-8d26-b440de6e29f5.png" alt="MAT03.png" style="width:20%;" />专门的选项图标 | 如果 "标准 "或 "阴影 "选项卡中的属性组与任何其他选项一起使用，如某种绘图模式或某种混合方式。 |

 <table>
    <tr>
        <td rowspan="3"><strong>Standard</strong></td>
       <td>1. Alpha Options</td>
       <td>1. 影响整体透明度</td>
    </tr>
    <tr>
       <td>2. Lighting Model</td>
       <td>2. 改变光线对表面颜色的影响</td>
    </tr>
    <tr>
       <td>3. Material Stages</td>
       <td>3. 添加纹理和材料状态，改变阴影。</td>
    </tr>
    <tr>
        <td><strong>ShadowOptions</strong></td>
       <td>   Shadow Options</td>
       <td>   改变与影子有关的行为</td>
    </tr>
    <tr>
        <td><strong>Drawing Style</strong></td>
       <td>   Draw Mode</td>
       <td>   适用于几何图形的绘制模式（直线、实体、精灵等）。</td>
    </tr>
    <tr>
        <td rowspan="2"><strong>Blending</strong></td>
       <td>1. Color Write</td>
       <td>1. 改变写入模式为指定的颜色通道</td>
    </tr>
    <tr>
       <td>2. Alpha Blending</td>
       <td>2. 调整几何图形在背景上的混合。</td>
    </tr>
    <tr>
        <td rowspan="2"><strong>Testing</strong></td>
       <td>1. Alpha Testing</td>
       <td>1. 应用一个针对对象的阿尔法的自定义测试。</td>
    </tr>
    <tr>
       <td>2. ZBuffer</td>
       <td>2. 定义了一个自定义的几何体闭塞测试</td>
    </tr>
 </table


----

# 标准
## Alpha Options

Alpha控制着场景层次结构中所有后续对象的透明度。为了达到正确的透明度效果，必须注意正确的绘制顺序。透明的对象必须在其后面的对象之后进行渲染。

<table>
   <tr>
       <td><strong>AlphaValue</strong></td>
      <td>控制以百分比表示的整体Alpha透明度。这个值也可以用来对整个材质的透明度进行动画处理。</td>
   </tr>
   <tr>
       <td rowspan="4"><strong>AlphaFlags</strong></td>
      <td>下拉菜单允许检查将影响Alpha计算的选项。</td>
   </tr>
   <tr>
       <td><b>Reltive to base alpha（相对基础Alpha）</b>，指定了如果一个以上的Alpha节点影响到一个物体时，如何计算产生的Alpha值。在相对模式下（标志被选中），Alpha值被相乘。在绝对模式下（标志未被选中），最后一个Alpha节点指定透明度，所有早期的节点都不再有影响。</td>
   </tr>
   <tr>
       <td><b>Block on full transparency(在完全透明时锁定对象)</b>，如果Alpha值被设置为0%物体将会被屏蔽，因此既不能验证也不能渲染。这是一种性能优化，但可能会产生意想不到的后果。<br />例如：<br />
被屏蔽的对象不再是可触摸的。<br />
你需要取消对全透明时的阻挡，以便拥有不可见的触摸区域。</td>
    </tr>
       </tr>
   <tr>
       <td><b>Improve transparency（提高透明度）</b>可以防止物体的内部在凹陷的网格上变得可见。
你需要取消对全透明时的阻挡，以便拥有不可见的触摸区域。</td>
    </tr>
</table>


> Alpha值会影响到受影响物体的每一个像素，包括所有应用于它们的照明、纹理等。为了忽略例如镜面效果，可以使用照明模型中的**Opacity**属性或不透明度纹理。

----

## Lighting Model
照明模型定义了关于材料和光线如何互动的规则。在着色器中，每个光源根据距离以及表面、眼睛和光线之间的角度来计算它对漫反射、环境光和镜面光的贡献。

### Inherit（继承）
控制以百分比表示的整体Alpha透明度。这个值也可以用来对整个材质的透明度进行动画处理。

### Base Color
Base Color模式继承了场景中使用的照明模型或前面的材料节点，但能够覆盖其**Base Color**属性和Opacity
例如，这可以用来快速改变一个三维物体的颜色，非常迅速。

- **Base Color**设置了纯白光照到表面时使用的颜色。你可以通过输入数值或使用颜色选择器来定义一个自定义颜色。也可以直接输入一个颜色名称。支持的颜色名称的完整列表可以在这里找到。
- **Opacity**，你可以控制半透明性。这将创建一个透明的物体，但保持镜面效果。例如，你可以调整这个值来创建一个玻璃瓶材料。你不能在这里指定一个不同的镜面颜色，这将被定义在Lightsources属性中的镜面颜色所继承。
> Opacity和Alpha Options中的Alpha的区别在于可以在不影响Specular的情况下调整透明度，常用于调整玻璃材质等

### No Light
这是最简单的照明模型。它忽略了所有的光源，只使用基色作为纯色。无光照明模型就像一个自发光的材料（具体请看Ventuz的RandomPoints演示文件）。 |

### Gouraud
Gouraud照明模型做了一个简单的光线计算，不产生镜面高光，这导致了一个平滑的照明。
基色用于材料扩散的着色，不透明度再次改变其透明度，见基色。
Gouraud在材料属性中增加了**Emissive**和**Ambient**。
- **Ambient**允许编辑用于环境区域的颜色。环境色是用来遮蔽网格中远离光线的部分。环境色是与基础色相乘的，所以环境色永远不会比漫反射部分更亮。注意：你必须在光源的属性中定义一个环境色，因为它也会与之相乘。
- **Emissive**将被添加到生成的材质的颜色中，不受任何光源的影响。
- **Options**，你可以启用**FlatShading**，将每个多边形渲染成一个平面，没有插值法线来生成光滑的表面。**TwoSided**（双面）启用双面照明。它以法线的相反矢量对每个（未剔除的）多边形进行第二次照明。当你使用一个多边形的背面并希望它得到适当的照明时，你将需要这个功能。最常见的情况是你在创建透明物体时需要这个。在 "Draw Mode --> Solid "节点中，将Culling设置为 "无"（以查看背面的多边形），并让它们被光源照亮。在下面的图片的右边，你可以看到透明球体的多边形的内侧在外侧朝向光线时是明亮的。在左边，当它们自己朝向光线时，它们是明亮的，这导致了一个更正确的结果（但也是一个更高的性能消耗）。
- **Blachdiffuse**,关闭漫反射
![twosided_compare.png](https://cdn.nlark.com/yuque/0/2021/png/12794363/1624757322408-6d7a639d-2cc1-45bf-897c-f6dcc3ce6d63.png) |

### Phong
Phong照明模型增加了**Specular**，镜面颜色和镜面**功率(Sharpness)**可以单独编辑和控制。
镜面性改变了你的材质上的镜面斑点的颜色，它取决于相应的多边形对着光线的距离和这个光源的镜面通道。
- **Sharpness**控制被镜面光点突出的区域和过渡到较暗的区域。
- **Roughness**值在使用基于图像的照明或SkyBox时，可以控制反射的粗糙（1）或光滑（0）的程度。**Roughness**和**Sharpness**以不同的方式表达类似的属性。**Roughness**只对基于图像的照明起作用，而**Sharpness**只对Phong-highlight起作用。如果你添加了一个材料阶段的粗糙度，该值将默认被添加到材料阶段提供的纹理中。那么你就必须把这个值设置为（0）。

### Incidence Lighting
**入射式照明模型**是最灵活、最强大的一种。在它里面，颜色和镜面是由梯度纹理驱动的，而不是单一颜色。梯度范围取决于光线与物体表面的角度。入射光照模型可以接受一个或两个一维渐变或纹理或一个二维纹理。
- 对于入射光，有一个**预设列表**可供快速挑选。可用的选项有BlueBack、Rainbow、Anisotropic（各向异性）和Colourful。除了使用的纹理外，每个都使用相同的值来创造入射效果。
此外，入射式照明打开了两个Loader，可以加载用于驱动**照明的颜色**和**镜面区域**的纹理。
- **LOADER 1**控制BaseColor的颜色。当你只使用单一的2D纹理时，它将从同一个纹理中导出Color（颜色）和Specular（镜面），因此它将使用第一个水平线的值作为颜色梯度。因此，我们推荐使用一维纹理，因为它们允许对颜色和镜面进行单独和更精确的控制。
- **LOADER 2**控制Specular。当你只使用单一的二维纹理时，它将从同一纹理中导出颜色和镜面，因此它将使用第一条垂直线的值来进行镜面渐变。因此，我们建议使用一维纹理，因为它们允许对颜色和镜面进行单独和更精确的控制。
- **FlipSpecular**，用来翻转用于控制Specularity的纹理的值。
- **FullRange**，你可以将映射的数值范围从0扩展到180度，允许光线出现在阴影的一面。

## Material Stages
Ventuz中的分层材质方法可以创建非常复杂的材质，将许多纹理和效果结合到一个单一的材质节点中。所有这些纹理层或效果被称为材质阶段，每一个特点都有自己的属性和选项。
要了解Ventuz中这些材料阶段的分层是如何工作的，请看下面的截图。请注意，Ventuz中的材料阶段是独立于顺序的。因此，你可以在任何时候添加任何阶段，引擎将在内部设置其顺序。
下面的截图显示了一套完整的材料阶段是如何工作的，该材料是在HDR环境中使用。
<img src="https://cdn.nlark.com/yuque/0/2021/png/12794363/1624757875447-45c6ccd0-0a1f-465f-94e7-bc9fda83ca37.png" alt="materialstages_example.png" style="width:40%;" />
<img src="https://cdn.nlark.com/yuque/0/2021/png/12794363/1624764117461-573c24c5-72a2-4828-ac78-03b96650eb54.png" alt="Snipaste_2021-06-27_11-21-42.png" style="width:30%;" />

### Texture
Texture可能是材料中最常使用的材料阶段。它只是从纹理源属性中获取一个纹理，对其进行采样和映射，然后将RGB和A通道应用到所选择的材质通道上。

### Normal Map(法线贴图)
法线贴图允许使用专门的纹理来模拟高程度的细节，而不需要大量复杂的几何体。虽然它们在直视时创造了非常逼真的细节，但在剖面上它们不起作用，因为它们实际上没有改变几何形状。法线图是以颜色值表示空间变换的图像，因此每个颜色通道代表三维轴上的变换。
法线贴图与普通纹理具有相同的_**Sampler**_和**Mapping Options。Target、Oper**_**ation**_和_**Masking**_可以被设置。
高级用户可以使用Alpha Target、Operation和Masking来移除法线贴图中不需要的Alpha通道，让贴图作为普通灰度纹理（Alpha、Roughness、Masking等）。
法线贴图只有一个控制法线贴图强度的 "_**Amount**_"。数值也可以是负数。
_**Normal Map Generator(法线贴图生成器)**_是创作法线贴图的一个简单方法。选择法线贴图生成器作为纹理加载器，它将把图像的灰度值解释为高度贴图并创建一个合适的法线贴图。
Amount 控制效果的强度，数值越大，浮雕看起来就越深。另外，数量可以是一个负值，以反转法线图的方向。通过Filtering，你可以选择用于计算假浮雕的过滤方法。可用的选项有软（默认，三个像素的邻域）和硬（两个像素的邻域）。
_**Normal Map Generator**_会将灰度值放在 alpha 通道中，这对于_**mixing displacement（混合位移）**_和_**normal mapping(法线贴图)**_是很方便的。输入纹理的原始alpha通道会被忽略。

### UV Distort
UV扭曲材料阶段可以用来改变一个UV集。改变后的集合可以被其他材料阶段使用，方法是在它们的映射选项中把使用的UV集合改为UV扭曲集合。
> 请注意，你需要将材料阶段的使用的UV集设置为UV扭曲，以便使用UV扭曲阶段的结果。这样你就可以定义哪些阶段应该使用变形集，哪些阶段应该使用原始集。

### Displacement Map(置换贴图)
有时也被称为高度贴图，与法线贴图不同，这种贴图实际上是在移动顶点，并创建真实的几何体。因此，它的计算量要大得多，此外，还需要在贴图下有一个高分辨率的几何体来支持细节。
一般来说，它的特点是与任何纹理可用的参数相同，所以请参考纹理材料阶段以了解更多信息，还有两个额外的属性。
_**Amount**_：控制效果的强度，数值越大，顶点移位越多。
_**偏移（Bias）：**_滑块控制位移产生的几何体的偏移量--这对补偿几何体的非位移区域很有用，可以尽可能地接近原始几何体。

### Texture Set纹理集
Texture Set允许在一次操作中加载一组纹理，而不必为每个纹理阶段分配正确的纹理。只需选择其中一个纹理，其余的纹理就会根据纹理文件名的命名惯例被加载到正确的纹理阶段。
这是一个强大的工作流程工具，已经设计并测试了由 Substance Painter 生成的纹理集，有一个预设可以使用 Ventuz 使用的适当设置和命名惯例来生成所有纹理。基本上，你只需要遵循下面列出的纹理命名惯例，就可以一次性加载一组纹理。

| 谥号 | 材料状态 |
| --- | --- |
| _BaseColor.EXT | Base |
| _Normal.EXT | Normal Map |
| _Specular.EXT | Specular |
| _Gloss.EXT | Glossiness |
| _AmbientOcclusion.EXT | Base |
| _Metal.EXT | Base |
| _Roughness.EXT | Roughness |
| _Emissive.EXT | Emissive |

文件用于拾取纹理集中的任何纹理。如果其余的纹理遵循正确的命名惯例，它们将被加载并自动分配给正确的纹理目标。**通过Targets（目标）下拉列表，您可以标记哪些纹理将被加载**，由此决定它们将被应用于哪些纹理阶段。

- _**NormAmount**_控制法线贴图效果的数量。
- _**DispAmount**_控制位移量。
- _**DispBias**_在法线方向上偏移整个位移效果，数值越高，顶点就越向外移动，数值越低，位移的几何体就越向内移动。
- _**Reload（重新加载）**_触发了对纹理组中所有纹理的重新加载。

### Compact Texture Sets紧凑型纹理集
与 "标准纹理集 "的工作方式相同。
此外，你可以利用基础纹理中的Alpha通道，添加一个 "grayscale（灰度） "图像，就像Ambient Occlusion（环境遮蔽）一样。如果你满足以下条件，它将被加载并映射成如下所示。

| 谥号 | 材料状态 |
| --- | --- |
| _BaseAO.EXT | Base |
| _SpecRough.EXT | Specular |

> .EXT "可以是任何一种支持的图像文件格式。
> 例如：你的纹理应该被命名为 "YourTextureName_BaseColor.jpg"，然后将被解释为一个BaseColor纹理。

通过TextureComp阶段，你可以加载一个纹理并将其分割成R、G、B、A通道，并将每个通道分配给一个自己的目标通道。例如，这样就可以把红色通道的信息分配给控制粗糙度，绿色通道可以是环境遮挡，蓝色可以控制光泽度。
FuncR,G,B,A可以选择颜色通道的目标以及功能。数量控制每个通道的强度。

### Color
颜色材质阶段将一个恒定的颜色和Alpha值应用到定义的通道上。给定的颜色值和Alpha值是相乘的，所以都会影响到材质上的结果。

### Image Based Lighting Irradiance基于图像的照明辐照度

<img src="https://cdn.nlark.com/yuque/0/2021/jpeg/12794363/1624766925135-45477b9f-00bf-4a2c-944b-a33a63eae924.jpeg" alt="MatStagIBL_IRRAD.jpg" style="width:33%;" />

这个阶段使用基于图像的照明技术，简称IBL。IBL使用外部图像作为光源来照亮3D场景，这将导致更高的准确性和真实性。
由于创造照明效果所需的色彩信息是巨大的，通常IBL与使用高动态范围图像，或HDRI，作为照明源有关。HDRIs支持每个通道更高的颜色深度，超过8/10比特，这意味着他们可以写出的颜色变化的数量是巨大的。大多数情况下，HDRIs每个颜色通道使用16f(float)或32f(float)比特，这意味着可以对它们进行一些极端的颜色校正操作而不会有任何视觉损失，例如，模仿曝光。

> 请确保在你所使用的3D图层的渲染模式中把IBL变成HDR，以便充分利用其功能。

<table>
   <tr>
      <td rowspan="2">
          <strong>Irradiance/loader</strong>
      </td>
      <td>
         是用来加载外部纹理作为照明源的。它将自动得到一个环境（Cubemap / LongLat）加载器。这个加载器会自动检测加载的地图类型。展开加载器，手动选择贴图类型。纹理类型可以是自动检测、LatLong（看起来像一个非常宽的水平纹理）、HorizontalCrossCubemap或VerticalCrossCubemap（看起来像所有的面都排列成一个十字架，但方向不同，取决于水平或垂直排列）或DdsCubemap（包括MipMaps）。
      </td>
   </tr>
   <tr>
      </td>
      <td>
         通过Mapping（贴图）下拉菜单，你可以选择纹理的定位方式。
      </td>
   </tr>
   <tr>
      <td>
          <strong>Color</strong>
      </td>
      <td>
         可以选择来自外部纹理的颜色信息的设置。单独的设置可以用于材料目标、混合操作和纹理屏蔽。
      </td>
   </tr>
   <tr>
      <td>
          <strong>Alpha</strong>
      </td>
      <td>
         下拉菜单可以选择来自外部纹理的Alpha信息的设置。你可以根据外部贴图调整基于图像的辐照度照明的数量。
      </td>
   </tr>
   <tr>
      <td>
          <strong>LodBias</strong>
      </td>
      <td>
         调整MipMap的水平。谨慎起见，增加锐度会对你的渲染性能产生严重影响。但是对于辐照度纹理，你应该选择最佳的MipMap级别（-16）。一般来说，你会创建并使用只有一个MipMap级别的DDS纹理。为了强迫渲染引擎使用最佳的MipMap级别，你可以调整这个值。辐照度纹理通常只有128px²，它既不消耗大量的RAM，也不应该在发生一般的MipMaping时看到人工制品，因为这个纹理是用于照明的。
      </td>
   </tr>
   <tr>
      <td>
          <strong>LimitDynamicRange（限制动态范围）</strong>
      </td>
      <td>
         夹住了较亮的数值，有效地限制了最终结果的动态范围--将它与HDR渲染模式结合起来使用，可以正确地看到其效果。
      </td>
   </tr>
   <tr>
      <td>
          <strong>Exposure</strong>
      </td>
      <td>
         控制作为照明源的图像的动态范围，它模仿摄影中使用的曝光设置。例如，1 EV的差异对应于一个标准的2次方曝光步骤。EV值的表现与任何其他照片编辑软件套件的表现相同。
      </td>
   </tr>
</table>

### Image Based Lighting Specular基于图像的照明高光
<img src="https://cdn.nlark.com/yuque/0/2021/jpeg/12794363/1624766932657-590064c6-10ab-40c3-82c0-149cfe113675.jpeg" alt="MatStagIBL_SPECULAR.jpg" style="width:33%;" />

<table>
   <tr>
      <td rowspan="2">
         <strong>Specular/ loader</strong>
      </td>
      <td>
         是用来加载外部纹理作为照明源的。它将自动得到一个环境（Cubemap / LongLat）加载器。这个加载器会自动检测加载的地图类型。展开加载器，手动选择贴图类型。纹理类型可以是自动检测、LatLong（看起来像一个非常宽的水平纹理）、HorizontalCrossCubemap或VerticalCrossCubemap（看起来像所有的面都排列成一个十字架，但方向不同，取决于水平或垂直排列）或DdsCubemap（包括MipMaps）。
      </td>
   </tr>
   <tr>
      <td>
         通过Mapping（贴图）下拉菜单，你可以选择纹理的定位方式。
      </td>
   </tr>
   <tr>
      <td>
          <strong>Color</strong>
      </td>
      <td>
         可以选择来自外部纹理的颜色信息的设置。单独的设置可以用于材料目标、混合操作和纹理屏蔽。
      </td>
   </tr>
   <tr>
      <td>
          <strong>Alpha</strong>
      </td>
      <td>
         下拉菜单可以选择来自外部纹理的Alpha信息的设置。你可以根据外部贴图调整基于图像的辐照度照明的数量。
      </td>
   </tr>
   <tr>
      <td>
          <strong>PreFilterMethod（预过滤方法）</strong>
      </td>
      <td>
         你可以选择用来在用于IBL效果的图片中的mipmaps之间进行插补的过滤方法。目前，我们已经用Knaldtech Lys实现了一个工作流程，所以过滤器和它们的名字与这个软件中使用的惯例有关--接下来的两个参数也是如此。Lys的工作方式是创建一组mipmaps，其中较小的mipmaps有大部分粗糙度信息，最大的mipmaps有大部分镜面信息，因此在这些粗糙度和镜面mipmaps之间插值时必须使用一些过滤方法。请看Lys的文档。这里。
      </td>
   </tr>
   <tr>
      <td>
          <strong>Log2UserScale</strong>
      </td>
      <td>
         控制 "一个用户可配置的斜率，允许镜面功率值在MIP级别上的可变分布"。你必须将这个值设置为与LYS中MipMap计算所用的值相同。
      </td>
   </tr>
   <tr>
      <td>
          <strong>Log2MipOffset</strong>
      </td>
      <td>
         它控制 "从底部1×1立方体地图MIP层的偏移。默认值为3，相当于给8×8级分配一个specular power为1"。
      </td>
   </tr>
   <tr>
      <td>
          <strong>DefaultMinRoughness</strong>
      </td>
      <td>
         你可以选择一个粗糙度值来开始使用。通过使用一个较高的值，材料会显得更粗糙，因为它使用较低的MipMap作为起点。
      </td>
   </tr>
   <tr>
      <td>
          <strong>LodBias</strong>
      </td>
      <td>
         调整Mipmap的细节水平。对这个要小心，让它更清晰会破坏渲染性能。
      </td>
   </tr>
   <tr>
      <td>
          <strong>LimitDynamicRange（限制动态范围）</strong>
      </td>
      <td>
         夹住了较亮的数值，有效地限制了最终结果的动态范围--将它与HDR渲染模式结合起来使用，可以正确地看到其效果。
      </td>
   </tr>
   <tr>
      <td>
          <strong>Exposure</strong>
      </td>
      <td>
         作为照明源的图像的动态范围，它模仿摄影中使用的曝光设置。例如，1 EV的差异对应于一个标准的2次方曝光步骤。EV值的表现与任何其他照片编辑软件套件的表现相同。
      </td>
   </tr>
</table>

### Rim Lighting
<img src="https://cdn.nlark.com/yuque/0/2021/jpeg/12794363/1624766938897-1387d8dc-4b61-4b79-b928-e9334844510c.jpeg" alt="MatStagRIM.jpg" style="width:33%;" />
边缘光是传统摄影中经常使用的一种效果，用于分离前景和背景。它是基于从后面或以陡峭的角度照亮物体，在物体轮廓周围形成一个光圈。这个材料阶段模仿了这种效果，经常被用来创造类似入射式照明的照明效果，但有一些微妙的区别。它还用于各种特殊的阴影和效果，其中物体表面的角度很重要。

| **纹理（Texture）** | 加载纹理以用于边缘光效果。可用的选项与任何其他纹理相同 |
| :-: | --- |
| **目标（Target）** | 选择材料目标，在那里将应用边缘光效果。可以单独检查目标、操作和遮蔽的选项。默认的目标是Emissive。你可以以SpecularLight为目标，使用Multiply模式来为反射创造类似菲涅尔的效果。 |
| **UvMode** | 打开一个下拉菜单，可以选择用于在几何体上应用边缘光的UV映射。选项可以在法线和反射之间单独选择， |
| **Mapping** | 可以来自相机、方向或位置。颜色值可以直接输入，也可以通过使用取色器来设置用于边缘区域的颜色。根据选择的预设，会使用不同的默认颜色。功率控制边缘光的功率，或边缘光覆盖的区域，数值越高，边缘光覆盖的区域就越少。 |
| **Gain(增益)** | 控制边缘光区域过渡的对比度，数值越高，对比度就越小，暗部和亮部之间的过渡就越严酷。 |
| **FullRange（全范围）** | 是用来切换边缘光效果的全范围计算的。你也可以反转边缘照明效果的方向。 |

### Cel Shading
<img src="https://cdn.nlark.com/yuque/0/2021/jpeg/12794363/1624766950731-9a054507-b504-419d-b215-ba95aa6ac5ef.jpeg" alt="MatStagCEL.jpg" style="width:33%;" />
单元着色模拟了一种卡通式的渲染，通过使用硬梯度来呈现海报化的外观。梯度定义了颜色的坡度，通常在颜色之间有硬的过渡，即所谓的硬停顿。它可以是一个纹理，也可以是一个一维渐变，可以用渐变编辑器来定义。你可以使用加载器（Loader）下拉菜单来加载用于Cel Shading效果的纹理。可用的选项与其他纹理的选项相同--参见上面的纹理阶段以供参考。我们还为你提供了一个Cel Shading纹理的例子。Specular（镜面）是用来在计算中加入镜面高光。所以镜面效果将是cel shading的。如果你关闭这个功能，镜面将像标准材质一样被着色。

### Hatch Shading
<img src="https://cdn.nlark.com/yuque/0/2021/jpeg/12794363/1624766975353-3a010b9a-3a7a-4a19-8282-5b1c0c47534d.jpeg" alt="MatStagHATCH.jpg" style="width:33%;" />
Hatch Shading使用纹理查询来模拟铅笔或画笔的笔触（或其他效果，取决于纹理）。由于它的计算方式，并不是所有的贴图和过滤方法都对这个阶段有意义，所以只提供一个子集。然而，这种方法的真正威力，在与**Hatch Node**本身结合使用时才会显现出来。
预设下拉菜单允许选择如何计算Hatch纹理。选项有_**Hatch Texture Node、Cross、Lines、Curves和Letters**_
<img src="https://cdn.nlark.com/yuque/0/2021/png/12794363/1624767093627-f0557eae-2851-4b9c-afeb-1c2d8e4940c0.png" alt="Snipaste_2021-06-27_12-10-40.png" style="width:33%;" />

| **Hatch Texture Node** | 使用NodeTextureHatch节点创建的纹理，而其他选项在不同的_**预设纹理**_之间切换。 |
| --- | --- |
| **Mapping** | 可以用来切换使用的贴图方法或投影。你可以在UV0、UV1、模型空间三平面、世界空间三平面和摄像机空间三平面之间切换。 |
| **ScaleU/V** | 在每个坐标中缩放Hatch纹理 |
| **ScaleAll** | 将同时控制UV |
| **MipmapBias** | 可以用来选择一个不同的MipMap或自定义Hatch纹理内的Hatch图案。 |
| **Triplanarpness三平面模式** | 可以调整三平面的清晰度。 |
| **Invert** | 是用来选择将被Hatch纹理覆盖的区域，这意味着较暗的区域将有Hatch纹理，而较亮的区域将保持不被触及。 |
| **InkColor** | 可以给Hatch上色--也可以用它给外部纹理中的黑色区域上色。也可以调整用于选择应用于舱口背景的颜色的_**PaperColor**_，也就是外部纹理中的白色区域。 |
| **Specular** | 用于在计算中添加镜面高光。 |

### Vertex Noise顶点噪波
Vertext Noise是使用一种算法来产生顶点位移。这意味着Vertext Noise可以很容易地（而且通常是）作为一种动画效果使用。
> Vertext Noise和Perlin Vertx噪声之间的区别仅仅是使用的计算算法。**Vertext Noise**是一种更有规律的波纹，而**Perlin Vertx**是一种更不规则、随机的效果。顶点噪声使用X、Y和Z的频率与数量相结合来创造波纹效果。

| _**ApproximateNormals（近似法线）**_ | 可以在位移的表面上进行近似法线计算，因此在产生的几何体中的着色和光照得到了很大的改善。特别是当你应用法线贴图时，你会注意到其中的差别。 |
| --- | --- |
| _**Animate**_ | 偏移了用于位移顶点的Noise函数。顾名思义，这是一个非常好的方法，可以让位移效果变成动画，创造出有趣的效果。我们建议使用一个无止境的数字，比如一个定时器节点。 |
| _**Scale **_ | 这个滑块对用于位移顶点的整个噪声函数进行缩放。 |
| _**Frequency X/Y/Z**_ | 控制每个轴的频率--噪声产生的位移的迭代量。 |
| _**FrequencyAll**_ | 控制X、Y和Z轴的顶点位移算法的频率。 |
| _**Amount X/Y/Z**_ | 控制用于在X、Y和Z轴执行顶点位移的噪声函数的振幅。 |
| _**AmountAll**_ | 作为第二个控制层，用于在每个轴上单独设置位移量--这些值是X、Y和Z轴的倍数，所以它可以用来一次控制所有的位移量，例如，用于动画效果。 |

### Perlin Vertex Noise佩林顶点噪波
**Perlin Vertx**与上述**Vertext Noise**类似，但使用Perlin算法来计算位移。这导致了一个带有衰减和偏置的随机效果。八度改变效果的颗粒（所以更多的八度意味着更细的颗粒）。

| **ApproximateNormals（近似法线）** | 可以在位移的表面上进行近似法线计算，因此在产生的几何体中的着色和光照得到了很大的改善。特别是当你应用法线贴图时，你会注意到其中的差别。 |
| --- | --- |
| **Animate** | 偏移了用于位移顶点的Noise函数。顾名思义，这是一个非常好的方法，可以让位移效果变成动画，创造出有趣的效果。我们建议使用一个无止境的数字，比如一个定时器节点。 |
| **Amount** | 控制位移量。 |
| **Bias（偏移）** | 控制由算法生成的数值的偏移。 |
| **ScaleUV** | 控制效果的缩放比例。 |
| **Octaves** | 控制噪声算法中使用的八度音。 |
| **Falloff** | 作为位移量的第二个控制层。它淡化了八度之间的位移量，所以它生成了更平滑的位移曲线。 |

### Flipbook Control
Flipbook控件可以用来定义应该使用某个纹理阵列中的哪种纹理。为此有不同类型的控件。
所有控件都有一个_**Flags属性**_，显示某些选项。你可以改变Flipbook控件在动画结束后的行为。

- **Clamp**重复其最后一帧
- **Wrap**重新开始
- **Mirror**在重新开始前倒退播放动画
- **Smooth**在帧之间增加了一个像素级的插值，使它们看起来更加连续

<img src="https://cdn.nlark.com/yuque/0/2021/png/12794363/1624767715418-b6050fc2-90bd-4874-84eb-3b8d682f0a52.png" alt="Snipaste_2021-06-27_12-21-47.png" style="width:33%;" />

#### Player
播放器控件将在每一帧渲染给定动画的另一个图像。当速度为100%时，它将每帧使用一张图片。你可以调整这个属性，让它运行得更快或更慢。此外，你还可以为播放添加一个偏移量。粒子系统的动画属性在0...1的范围内被解释。
#### Frame Indexer
帧索引器只是显示具有给定索引的帧。粒子系统的动画属性被直接用作索引。因此它的范围是0...MaxIndex。
#### Percentage Position(百分比位置)
百分比位置控制将显示动画中给定位置的帧。0%是开始，100%是结束。粒子系统的动画属性在0...1的范围内被解释。
#### Sampling Between Frames(帧间取样)
根据控制器的类型，几个帧的寻址工作是不同的。这在启用_**Smooth**_标志时尤其明显。这些工作方式在本节底部的图片中有所说明。

- **Player:**0%和100%或者0和1分别位于第一帧和最后一帧之间。也就是说，要准确地击中第一帧，你需要有半帧的偏移量（取决于你的纹理阵列的长度。
- **Percentage Position:**百分比位置。0%和{{100%}}正好是第一帧。要在第一帧和最后一帧之间取样，你需要减去半帧的偏移（取决于你的纹理阵列的长度）。
- **Frame Indexder:**0正好是第一帧。-0.5正好是第一帧和最后一帧之间。

<img src="https://cdn.nlark.com/yuque/0/2021/png/12794363/1624768282472-94b714b7-acc3-4c55-aa7e-3514f8c1bb36.png" alt="FlipbookFrameSampling.png" style="width:70%;" />

> 如果启用**Smooth**，采样器将在帧之间进行线性插值。如果禁用，并且你在帧之间的精确中心取样，那么帧的选择是随机的和不可预测的。

# 阴影
可以为每个材料启用Shadow Options。你可以选择阴影选项或者阴影选项与全局渐变。

<img src="https://cdn.nlark.com/yuque/0/2021/png/12794363/1624768539691-08a0d3a2-601e-4bbd-b754-901a3d6dfcef.png" alt="Snipaste_2021-06-27_12-35-26.png" style="width:33%;" />

接收阴影选项使材质能够接收阴影，包括来自自身的阴影。这可以作为一种优化或防止丑陋的自我阴影。
"投射"（Cast）可以投射阴影--这与 "阴影过滤器"（Shadow Filter）的行为类似，但与它们相比，这个选项可以用在有多个材质的层次节点上--比如粒子系统。它对于防止透明材质投射阴影也很有用。
SimpleCasterShader标志（默认为启用)可以启用一个简单的着色器代码。当SimpleCasterShader被启用时，对象的处理将不考虑alpha、Vertex和Perlin Noise。比如说。如果你有一个球体并对球体应用顶点噪声，你会看到一个没有顶点变形的简单球体。这是一个重要的优化，因为它可以防止在渲染阴影时不断切换着色器。请看下面的图片。

<table>
   <tr>
      <td>
         <strong>SimpleCasterShadow ON (default)</strong>
      </td>
      <td>
         <strong>SimpleCasterShadow OFF</strong>
      </td>
   </tr>
   <tr>
      <td>
      <img src="https://cdn.nlark.com/yuque/0/2021/png/12794363/1624768693785-00e1ee73-319c-481b-83f7-1e1466bb705a.png" alt="ShadowSimpleOn.png" style="width:55%;" /> 
      </td>
      <td>
      <img src="https://cdn.nlark.com/yuque/0/2021/png/12794363/1624768700075-d09b500e-2354-4813-bd70-0d46d1275bc9.png" alt="ShadowSimpleOff.png" style="width:55%;" /> 
      </td>
   </tr>
   <tr>
      <td>
      <img src="https://cdn.nlark.com/yuque/0/2021/png/12794363/1624768808513-1d7030bd-57bc-4179-a957-c2812fce9f4b.png" alt="ShadowSimpleOnAlpha.png" style="width:55%;" /> 
      </td>
      <td>
      <img src="https://cdn.nlark.com/yuque/0/2021/png/12794363/1624768817917-2179c672-c9ca-4643-a36b-607722be200d.png" alt="ShadowSimpleOffAlpha.png" style="width:55%;" /> 
      </td>
   </tr>
</table>

如果你选择了带有全局渐变的阴影选项，就有渐变选项可用。_**FadeDiffuse, FadeSpecular, FadeAmbient**_控制这些通道的强度。如果你降低任何一个通道的值，阴影就会更加突出。如果你想防止反射穿过阴影，这就非常有用。
_**ShadowToAlpha**_将阴影转移到alpha通道上。在调低物体的alpha值的同时，它淡化了整个物体，包括阴影。_**ShadowToAlpha**_允许淡出物体但保留阴影。为了达到最好的效果，使用一个黑色的物体作为阴影接收器。把整体的Alpha值调低到零，然后用_**ShadowToAlpha**_滑块把阴影再次带入，达到所需的量。当Alpha值为0%时，记得取消Alpha部分的 "**Block on full transparency （全透明封锁）** "标志。

# 绘图模式
| <img src="https://cdn.nlark.com/yuque/0/2021/png/12794363/1624769365838-0c376fe9-1b3f-4afb-8ee2-4831f8019435.png" alt="RenderOptions_Sprites.png" style="width:10%;" /> **Render Sprites（顶点）** |  在每个顶点的位置而不是几何体的多边形上渲染精灵。 |
| :-: | --- |
| <img src="https://cdn.nlark.com/yuque/0/2021/png/12794363/1624769375671-5f3ef589-af8c-4867-b143-34dcde9e948a.png" alt="RenderOptions_Lines.png" style="width:10%;" />**Render Lines** |  沿着几何体的多边形的边缘渲染可定制的线条。 |
| <img src="https://cdn.nlark.com/yuque/0/2021/png/12794363/1624769380841-b16862ed-4005-41e1-ba3d-eff92fe6f175.png" alt="RenderOptions_Wireframe.png" style="width:10%;" />**Render Wireframe** | 沿着一个几何体的多边形边缘渲染线条，对性能的影响很小。 |
| <img src="https://cdn.nlark.com/yuque/0/2021/png/12794363/1624769386084-725e855b-77a3-418a-b83a-e64a589add66.png" alt="RenderOptions_Path.png" style="width:10%;" />**Render Path** | 将一个顶点列表渲染成一个可定制的路径。 |
| <img src="https://cdn.nlark.com/yuque/0/2021/png/12794363/1624769390267-b01b5f73-c68b-4a29-a9b8-5ea756782674.png" alt="RenderOptions_Solid.png" style="width:10%;" />**Render Solid** |  将几何图形渲染成实体多边形。 |

### Render Sprites
渲染精灵（Render Sprites）模式将在物体的每个顶点的位置渲染一个纹理。
顶点可以被Culling--正面、背面或没有面可以被排除在渲染之外。
<img src="https://cdn.nlark.com/yuque/0/2021/png/12794363/1624769752821-619f1331-eef7-4d30-b057-73163104ad20.png" alt="Snipaste_2021-06-27_12-55-26.png" style="width:25%;" />

- _**Aspect （纵横比）**_是用公式2x计算的。因此，如果你需要一个16:9的_**Aspect**_，你需要输入0.83（也就是log2（16/9））。如果你需要一个9:16的_**Aspect**_，则只需输入-0.83
- _**Scale(缩放) **_改变了精灵是否应该随着与摄像机的距离而缩放。
- 如果_**ZNearFadeoutEnable**_被启用，精灵在靠近摄像机时就会淡出alpha，阈值可以用_**ZNearFadeout**_来设置。
- _**PointSpriteUV**_定义了为精灵生成的UV被应用到哪个UV集。例如，将其设置为UV1可以为精灵使用一个纹理，但仍在几何体的原始UV0集上使用另一个纹理。
- 如果需要，精灵可以在屏幕上的X和Y位置上_**Offset**_原始顶点的位置。
- 如果_**EnableRotation**_被打开，_**Rotation**_会改变精灵的2D旋转。
- **Billboard**修改方向
   - **Toward Camera**:将精灵对准摄像机。
   - **Along Forward**: 沿着粒子的前进向量旋转。
   - **Along Speed**: 沿着粒子的速度旋转。通常情况下，这只存在于模拟之后。
   - **Along Direction**: 使用Billboard Reference来创建一个旋转矢量，粒子将与之对齐。
   - **Toward Position**:朝着Billboard Reference给出的位置旋转。
   - **Toward Axis**: 朝着Billboard Reference中定义的轴线旋转。
   - **Normals Toward Position**:只改变法线对某个位置的方向，但保持粒子的旋转不变。
   - **Normals Toward Axis**: 只改变法线对某一轴的方向，但保持粒子的旋转不变。
   - **Invert**: 可以用来反转产生的矢量。只适用于朝向位置和朝向轴的广告牌。
   - **Update Normal**: 当粒子系统中的任何修改器改变方向时，精灵的法线需要在渲染过程中进行更新。如果你想保持粒子法线的原始方向，请关闭这个选项。

Billboard Reference参考使用了一个转换属性组。对齐使你可以选择哪些轴被锁定在广告牌上。VR选项锁定了X和Y轴，对于有动画滚动的摄像机很有用。
### Render Lines
<img src="https://cdn.nlark.com/yuque/0/2021/png/12794363/1624770593676-d0c72373-b8ff-405e-b6bd-0e472a5901ab.png" alt="RenderLinesSample.png" style="width:25%;" />
_**LineCulling**_有一套Culling模式，可以从渲染中去除某些边缘。

- Show ALL显示全部。渲染所有可见的边缘。
- Show Rim显示边缘。只渲染从当前视角看是最外层的边缘。
- Show Front显示正面。只渲染朝向摄像机的边缘。
- Show Back显示背面。只渲染远离摄影机的边缘。
- Show Front+Rim,显示正面+边缘，背面+边缘，正面+背面。上述模式的组合。
- Remove Flat Tesselation移除平面镶嵌。移除两个具有相同法线的面之间的所有边缘。

**Width（宽度）**改变了线条的厚度
_**WidthMode（宽度模式）**_改变了宽度受透视影响的方式。
<img src="https://cdn.nlark.com/yuque/0/2021/png/12794363/1624770851464-142cb08e-fcba-4e31-b3d3-5697408d87ec.png" alt="Snipaste_2021-06-27_13-13-57.png" style="width:25%;" />

- _**Unperspective(不透视)**_使线条在屏幕上保持恒定的宽度。
- _**Perspective Unscaled（未按比例的透视）**_将透视变形应用于线条，但不使用前面的轴节点的缩放。
- _**Perspective Scaled（按比例透视）**_同时进行--关于透视和所有轴。
- _**平面优化（Planar Optimization）**_可以用来防止投影失真--在高宽比或高视场设置中出现。这对于以线条形式呈现的平面物体很有用，但对于三维物体应该禁用，以保持其空间印象。

LengthRel（相对长度）和LengthAbs（绝对长度）改变线条的长度。
_**LengthRel（相对长度）**_是对边的端点之间的距离的百分比。
_**LengthAbs（绝对长度）**_会增加一个独立于这个距离的额外长度。
_**LengthFromWidth**_是按比例改变线条的长度。
_**CapLength**_将在每条线的末端添加一个给定长度的带有UVs的盖子。
材料阶段使用的UV可以通过UV0和UV1下拉菜单来改变。
<img src="https://cdn.nlark.com/yuque/0/2021/png/12794363/1624771107272-cda8c4f2-4d7f-410a-b3db-dc3aca937d0f.png" alt="Snipaste_2021-06-27_13-18-17.png" style="width:25%;" />

- Original 使用几何体的UV集。

- _Relative_ applies从每行的开始到结束延伸的UV。

- _Absolute_ applies相同比例的UV应用于每条线，因此UV不会在不同长度的线上被拉伸。

- _Stretched（拉伸）_将使用沿线纹理的中心像素，并将其两半应用于线条的盖子。

  <table>
     <tr>
        <td>
            <strong>Relative Uvs</strong> <br /> 每条边显示三个破折号。中间的边缘比较长，所以破折号也比较长。
        </td>
        <td>
        <img src="https://cdn.nlark.com/yuque/0/2021/png/12794363/1624771228819-72a75d20-cca9-4008-bb84-5d238b33ac5c.png" alt="RelLength.png" style="width:25%;" /> 
        </td>
     </tr>
     <tr>
        <td>
           <strong>Absolute Uvs</strong> <br /> 每个破折号都是一样的大小。中间的边缘比较长，所以破折号比较多。
        </td>
        <td>
        <img src="https://cdn.nlark.com/yuque/0/2021/png/12794363/1624771252272-a295cb19-c382-4e50-9084-f3ff044e2e5d.png" alt="AbsLength.png" style="width:25%;" /> 
        </td>
     </tr>
  </table>

### Render Wireframe
渲染线框模式使用DirectX11定义的填充模式来渲染多边形的边缘。这导致了一个非常快速的线条渲染(对性能的影响很小)，但选项很少。你只能打开FrontFaces和BackFaces的Culling，并改变线条的Antialiased(抗锯齿)。
<img src="https://cdn.nlark.com/yuque/0/2021/png/12794363/1624771470913-63313045-bc26-411b-95e7-09cbae8f1e97.png" alt="RenderWireframeSample.png" style="width:50%;" />

### Render Path
Render Path模式是一种特殊的模式，只对顶点列表有意义--而不是一组多边形。关于如何渲染路径的更多细节，请参见路径渲染器。使用 "路径 "模式而不是 "线条 "模式会得到更平滑的结果，因为渲染器可以假定在一个顶点结束的边不超过两条--因此不再需要在边的末端应用帽。你可以在渲染器的选项中打开线框渲染，看看两种模式的具体区别。
_**Width**_改变路径的厚度
_**WidthMode**_改变宽度受透视影响的方式。

- _**Unperspective**_使线条在屏幕上保持恒定的宽度。
- _**Perspective Unscaled**_将透视变形应用到线条上，但不使用前面的轴节点的缩放比例。
- _**Perspective Scaled**_同时进行--关于透视和所有轴。
- **平面优化（Planar Optimization）**可以用来防止投影失真--在高宽比或高视场设置中出现。这对于以线条形式呈现的平面物体很有用，但对于三维物体应该禁用，以保持其空间印象。
> 材料阶段应该使用的UV可以通过UV0和UV1下拉菜单来改变。Original的使用几何体的UV集， Relative applies从路径的起点到终点并沿其宽度应用UV。

# 混合
| <img src="https://cdn.nlark.com/yuque/0/2021/png/12794363/1624772191978-9e738e6d-8305-46f7-9de6-0b277840241a.png" alt="ColorWrite.png" style="width:25%;" />Color Write 颜色读写 | 允许你分别启用/停用RGBA通道。使用户可以选择哪些通道应该受到当前片段的影响。 |
| :----------------------------------------------------------: | ------------------------------------------------------------ |
| <img src="https://cdn.nlark.com/yuque/0/2021/png/12794363/1624772210558-23e1cbd6-85d1-4271-afa6-371bed96c158.png" alt="AlphaBlending.png" style="width:25%;" />混合 | 这个节点用工业标准预设修改了叠加像素的混合规则。             |

### Color Write
材料节点的颜色写入选项使用户可以选择哪些通道应该受到当前片段的影响。
### Alpha Blending Options
#### OFF
当设置为 "关闭 "时，该片段将直接覆盖目标。
> 即使当混合被设置为 "off "时，只有当片段通过了之前的所有测试（闭塞测试、阿尔法测试等）才会被绘制。

#### Simple
| **Overwrite（覆盖）** | 与将混合设置为关闭一样。 |
| --- | --- |
| **Normal（正常）** | 像往常一样混合颜色 - 关于当前片段的Alpha值。 |
| **LinearDodge (Add)（线性减淡-添加）** | 通过增加亮度来减淡颜色，产生的效果比滤色和颜色减淡都强烈。 |
| **Screen(滤色)** | 类似于两张幻灯片通过投影仪投影在屏幕（Screen）的同一个位置，光强增加而变亮。 |
| **Subtract（减去） Rendering from Background** | 像线性闪避一样，它将通过从目标片断中减去源片断来线性地使图像变暗。 |
| **Subtract Background from Rendering** | 这是反向减法，它将使源片段变暗而不是背景变暗。 |
| **Multiply（正片叠底）** | 两种颜色相乘总是会产生一个较暗的图像--这是屏幕混合的反向操作，因为它不会产生低于0（黑色）的箝制。 |
| **Multiply X2（正片叠底X2）** | 类似于multiply，但是当当前源片段比中灰色更深时，会产生比目标片段更深的颜色，如果源片段比中灰色更浅，则产生更浅的颜色。适合于例如夸大图像中的亮点和暗点。 |
| **Glow（光晕？）** | 类似于线性躲避，但完全忽略了来源的阿尔法。 |

- 要提亮图像，可以先从_**滤色**_模式开始尝试，如果感觉视觉冲击力不够，就切换至_**线性减淡**_模式。、
- 将两个较暗的图像合成为一个双重曝光的图像时，可考虑使用_**滤色**_模式。
- 图像合成时，可使用**滤色**等模式，直接去除黑色背景而不必抠图。
- 对Alpha通道等应用**滤色**，可使用菜单：图像/应用图像。
#### Advanced
The blend factors are selected with the **Source** and **Destination** properties:

- **One:** 每个组成部分乘以1。
- **Zero:** 颜色的所有通道都乘以0
- **BlendFactor:** 将每个分量乘以**BlendFactor**属性中指定的颜色的各自分量。
- **InverseBlendFactor:** 将每个分量乘以**BlendFactor**属性中指定的颜色的各自**反**分量。
- **BothInverseSourceAlpha:**源颜色乘以1减去源Alpha，目的颜色乘以源Alpha。
- **SourceAlphaSaturated:** 红色、绿色和蓝色通道被乘以min(alpha_source, 1 - alpha_destination)，alpha被乘以1。这只能用于**Source**，并将覆盖**Destination**中设置的值。
- **InverseDestinationColor:** 将每个分量乘以1减去目标颜色中的相应分量。
- **DestinationColor:** 将所有的通道乘以1减去目标alpha。
- **InverseDestinationAlpha:** 将所有的通道乘以1减去目标alpha。
- **DestinationAlpha:** 将所有通道与目的地的alpha相乘。
- **InverseSourceAlpha:** 将所有通道乘以1减去源阿尔法。
- **SourceAlpha:** 将所有的通道与源的alpha相乘。
- **InverseSourceColor:** 将每个分量乘以1减去源色中各自的分量。
- **SourceColor:** 将每个分量与源颜色中的相应分量相乘。

得到的向量与操作相结合。

- **Add:** Result = Source + Destination
- **Maximum:** Result = MAX(Source, Destination)
- **Minimum:** Result = MIN(Source, Destination)
- **ReverseSubstract:** Result = Destination - Source
- **Substract:** Result = Source - Destination
# 测试
| <img src="https://cdn.nlark.com/yuque/0/2021/png/12794363/1624773275082-d9b2f861-8e19-4a89-891f-40063b3cd918.png" alt="AlphaTesting.png" style="width:25%;" />**Alpha Testing** | 这个节点测试一个像素是否要被绘制。这取决于这个像素的alpha值。 |
| :-: | --- |
| <img src="https://cdn.nlark.com/yuque/0/2021/png/12794363/1624773281252-63c7c29d-e5cf-4def-a399-0a334e89bc8b.png" alt="ZTesting.png" style="width:25%;" />**ZBuffer** | 该节点修改由几何体写入深度缓冲区（Z-Buffer）的深度信息。 |

### Alpha Testing
与Z-Testing和Stencil Testing节点类似，在绘制相应的像素之前，可以使用片段的alpha值来拒绝它。
你可以_**Inherit(继承)**_Alpha测试，把它_**ON**_或_**OFF**_，或者提供一个自定义的Alpha测试（高级）。
_**ON**_，如果Alpha不大于0，测试将失败--这通过不渲染任何不可见的像素有效地节省了性能。如果你需要渲染所有的片段，可以用 "高级 "选项改变阿尔法测试功能，或者把测试关闭。
_**OFF**_，测试将永远不会失败，当前片段总是被渲染。
_**Advanced**_
Alpha测试将片段的alpha值（在它被点亮和纹理被混合后）与_**RefAlpha**_中指定的值进行比较。
<img src="https://cdn.nlark.com/yuque/0/2021/png/12794363/1624773593431-eaa5cfdf-c3ce-41b0-9c30-df7dc6d7accd.png" alt="Snipaste_2021-06-27_13-59-45.png" style="width:25%;" />

- _**Always。**_片段总是通过测试。
- _**GreaterEqual(大于等于)。**_如果片段的alpha值大于或等于参考值，则通过测试。
- _**NotEqual（不等于）。**_ 如果片段的alpha值不等于参考值，则通过测试。
- _**Greater（大于）**_。如果片段的阿尔法值大于（不等于）参考值，则通过测试。
- _**LessEqual(小于等于)。**_如果片段的阿尔法值小于或等于参考值，则通过测试。
- **_Equal(等于)。_**如果片段的阿尔法值等于参考值，则通过测试。
- _**Less(较小)。**_如果片段的阿尔法值小于（不等于）参考值，则通过测试。
- _**Never。**_该片段从未通过测试。
### ZBuffer
Z-Buffer（也叫深度缓冲区）是用来在光栅化过程中确定物体遮挡的。在三角形的渲染过程中，给定像素的Z值会与存储在Z-Buffer中的值进行比较。基于Z测试功能，三角形要么允许过度绘制该像素，要么不允许。
默认行为是接受Z值小于或等于Z-Buffer中的值的像素，使离摄像机较近的物体遮挡住较远的物体。虽然一开始使用与默认值不同的东西似乎很奇怪（在大多数情况下这是最好的选择），但使用不同的比较函数可以用来创造有趣的渲染效果或防止渲染伪影的发生。
#### Simple
_**Test**_属性可以被停用，以便对所有子节点完全不做Z测试。
_**Write**_属性可以被停用，以便只执行Z-test，但一旦渲染了一个像素，就不更新ZBuffer中的值。
在某些情况下，比如在solid物体上渲染wireframe覆盖层，可以通过为一个像素计算的Z值添加一个小的偏移量来避免由于Z对抗问题而产生的视觉伪影。这个偏移量只用于Z测试的比较。如果该像素被绘制并更新了Z-Buffer，将使用原来的Z值。这个偏移量是由一个叫做_**Bias**_的固定偏移量指定的。
#### Advanced
高级Z-Testing选项可以将测试功能本身改为以下设置之一。

- **Inherit(继承):** 比较函数继承自父级Z测试节点，如果不存在，则继承默认的（Less Equal）。
- **Always:** 一个像素总是被画出来，不与Z-Buffer中的值进行比较。
- **GreaterEqual:** 如果一个像素的深度值大于或等于存储在Z-Buffer中的相应值，就会被绘制出来。
- **NotEqual:** 如果一个像素的深度值与存储在Z-Buffer中的相应值不一致，则会被绘制出来。
- **Greater:** 如果一个像素的深度值大于（不等于）存储在Z-Buffer中的相应值，那么该像素就会被绘制出来。
- **LessEqual:** 如果一个像素的深度值小于或等于存储在Z-Buffer中的相应值，就会被绘制出来。
- **Equal:** 如果一个像素的深度值恰好等于存储在Z-Buffer中的相应值，那么该像素就被绘制出来。
- **Less:** 如果一个像素的深度值小于存储在Z-Buffer中的相应值，就会被绘制出来。
- **Never:** 一个像素永远不会被绘制出来。

_**Slope（斜率）**_的使用与_**Bias**_类似。它与被渲染的三角形的最大深度值相乘。它可以用来适应与摄像机的距离的偏移，解决Z-Buffer的分辨率问题。
_**WriteNormals**_可以被关闭，以防止法线被写入。通常只有当_**Write**_属性也被设置为关闭时才会关闭。例如，法线被3D图层上的屏幕空间环境遮蔽（SSAO）效果所使用。因为只有透明物体表面的深度和法线是已知的，所以SSAO不会对透明物体后面的区域进行渲染。通过关闭深度和法线的写入，SSAO现在是为后面的物体计算的（但不是为前面的透明物体）。

| **Z-Write** | YES | NO | NO |
| --- | --- | --- | --- |
| **Normal-Write** | YES | YES | NO |
|  | ![WriteNormalsAndDepth.png](https://cdn.nlark.com/yuque/0/2021/png/12794363/1624774557574-1cf0e273-f5d5-4b16-97c6-4e5fadc65be7.png) | ![WriteNormalsOnly.png](https://cdn.nlark.com/yuque/0/2021/png/12794363/1624774514708-d04864ec-86d3-4f7b-a640-183fd57bf7e3.png) | ![DoNotWriteNormals.png](https://cdn.nlark.com/yuque/0/2021/png/12794363/1624774550435-87d545c1-99bf-4596-9e2f-270ba27f2d93.png) |



