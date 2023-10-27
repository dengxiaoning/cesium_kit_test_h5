## cesium_dev_kit

[![Build Status][build-main]][build-status]
[![NPM Package][npm]][npm-url]
[![Build Size][build-size]][build-size-url]
[![NPM DownloadsWeekly][npm-download]][npmtrends-url]
[![license][license-uri]][license-link]

## 简介

这是一个 Cesium 开发工具包，包含图层加载、坐标转换、坐标拾取、相机控制、测量、标绘、模型加载、模型平移旋转缩放、模型/3Dtiles 视角位置调整、模型拖拽、天气（雨，雪，雾）场景、雷达扫描、信息框、流动线、发光线、动态墙等各种发光材质、后置场景效果、通视分析、透视分析、坡度分析、淹没分析、方量分析、地形开挖等各种分析案例。

## 功能展示

- 材质
  ![material](https://github.com/dengxiaoning/cesium_dev_kit/blob/main/src/assets/image/preview/material.gif)
- 分析
  ![analysis](https://github.com/dengxiaoning/cesium_dev_kit/blob/main/src/assets/image/preview/analysis.gif)
- 标绘
  ![plot](https://github.com/dengxiaoning/cesium_dev_kit/blob/main/src/assets/image/preview/plot.gif)
- 拖拽
  ![drag](https://github.com/dengxiaoning/cesium_dev_kit/blob/main/src/assets/image/preview/drag.gif)
- 雷达扫描
  ![radar](https://github.com/dengxiaoning/cesium_dev_kit/blob/main/src/assets/image/preview/radar.gif)

## 在线预览

[https://www.benpaodehenji.com/cesiumDevKit](https://www.benpaodehenji.com/cesiumDevKit)

## 引入 Css

```html
<link rel="stylesheet" href="./libs/Cesium/Widgets/widgets.css" />
```

## 引入 Cesium 库

```html
<script type="text/javascript" src="./libs/Cesium/Cesium.js"></script>
```

## 引入其他依赖库

```html
<script type="text/javascript" src="./libs/dat.gui.min.js"></script>
<script type="text/javascript" src="./libs/libgif.js"></script>
<script type="text/javascript" src="./libs/turf.min.js"></script>
<script type="text/javascript" src="./libs/echarts.min.js"></script>
```

## 引入 cesium_dev_kit 工具包

[直接到 npm 下载 index.umd.js 到本地](https://www.npmjs.com/package/cesium_dev_kit?activeTab=code)

```html
<script type="text/javascript" src="./libs/index.umd.js"></script>
```

## 使用

### 1、引入所有模块

```javaScript
      const tempData = [
      {
        id: 3,
        name: '高德地图02',
        type: 'UrlTemplateImageryProvider',
        classConfig: {
          url: 'https://webst02.is.autonavi.com/appmaptile?style=6&x={x}&y={y}&z={z}',
        },
        interfaceConfig: {},
        offset: '0,0',
        invertswitch: 0,
        filterRGB: '#ffffff',
        showswitch: 1,
        weigh: 13,
        createtime: 1624346908,
        updatetime: 1647395260,
      }]
const {
      viewer,   // viewer
      material, // 材质模块（修改实体材质）
      graphics, // 图形模块（如创建PolygonGraphics对象等）
      math3d, // 三维数学工具
      primitive, // 图元操作对象（如使用primivite创建polygon等）
      draw, // 绘制模块（如多边形，矩形）
      passEffect, // 后置处理模块
      customCesiumPlugin,
      control, // 控制模块（如模型位置调整，拖拽等）
      plugin, // 额外插件（如拓展css3的动画 ，地形裁剪）
      base, // 基础模块（如坐标转换，图层初始化等）
      analysis, // 分析模块（如坡度，坡向，可视域，通视分析）
      attackArrowObj, // 标绘（攻击）
      straightArrowObj,// 标绘（直击）
      pincerArrowObj, // 标绘（钳击）
      } = new cesium_dev_kit.initCesium({
      cesiumGlobal: Cesium, // 全局Cesium对象
      containerId: 'cesiumContainer', // 容器id
      viewerConfig: { // 同官方的viewer配置相同
        infoBox: false,
        shouldAnimate: true,
      },
      extraConfig: {// 其他配置
        logo:true, // 是否显示logo
        depthTest:true // 是否开启深度测试
      },
      MapImageryList: tempData // 底图配置
      defaultStatic // 默认服务器地址以及材质等基础信息配置，具体请参考static\defaultStaticConf\index.js
      })
```

### 2、按需引入

```javaScript
    // 工具初始化
    const drawObj = new cesium_dev_kit.Draw({
      cesiumGlobal: Cesium,
      containerId: 'cesiumContainer',
      viewerConfig: {
        infoBox: false,
        shouldAnimate: true,
      },
      extraConfig: {},
      MapImageryList: []
    })
    // 定义操作变量
    const viewer = drawObj.viewer,
      draw = drawObj.draw,
      plotEntitiesId = [],
      StraightArrowObj = drawObj.straightArrowObj,
      AttackArrowObj = drawObj.attackArrowObj,
      PincerArrowObj = drawObj.pincerArrowObj;
```

## 使用范例

- ES6 使用案例
  [https://github.com/dengxiaoning/cesium_kit_test](https://github.com/dengxiaoning/cesium_kit_test)

- H5 使用案例
  [https://github.com/dengxiaoning/cesium_kit_test_h5](https://github.com/dengxiaoning/cesium_kit_test_h5)

##

## 浏览器支持

本地开发推荐使用`Chrome 80+` 浏览器

支持现代（chrome，Firefox，Microsoft edge，etc.）浏览器, 不支持 IE

## 鸣谢

[cesium-d3kit](https://github.com/zhangti0708/cesium-d3kit)<br/>
[drawarrowforcesium](https://gitcode.net/mirrors/gitgitczl/drawarrowforcesium)<br/>
[vue3-ts-cesium-map-show](https://gitee.com/hawk86104/vue3-ts-cesium-map-show)<br/>

本项目包括但不限于借鉴和参考以上资料，非常感谢作者分享

## 项目不足与优化

- 1、cesium 工具类未使用 typeScript
- 2、未配备使用文档（请参考案例）
- 3、未作异常捕捉和处理

<small>感兴趣朋友可以一起讨论交流继续完善功能，让工作效更高效、开发更简单、生活更惬意。</small>

[npm]: https://img.shields.io/npm/v/cesium_dev_kit
[npm-url]: https://www.npmjs.com/package/cesium_dev_kit
[build-size]: https://img.shields.io/bundlephobia/minzip/cesium_dev_kit/1.0.57
[build-size-url]: https://img.shields.io/bundlephobia/minzip/cesium_dev_kit
[npm-download]: https://img.shields.io/npm/dt/cesium_dev_kit
[npmtrends-url]: https://www.npmtrends.com/cesium_dev_kit
[license-uri]: https://img.shields.io/npm/l/cesium_dev_kit.svg
[license-link]: https://npm.im/cesium_dev_kit
[build-status]: https://github.com/dengxiaoning/cesium_dev_kit
[build-main]: https://img.shields.io/github/actions/workflow/status/dengxiaoning/cesium_dev_kit/project-build.yml?branch=main
