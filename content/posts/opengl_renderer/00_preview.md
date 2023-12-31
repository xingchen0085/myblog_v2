---
title: " OpenGL渲染器00_预览"
date: 2021-11-16T14:34:07+08:00
draft: false
Tags:
  - OpenGL渲染
  - 图形学
Categories:
  - OpenGL
---

- [x] OpenGL基础绘制
  - [x] 环境搭建
    - [x] 编辑器环境
      - [x] Clion
      - [x] Visio Studio（不深入）
    - [x] 构建环境
      - [x] Cmake+MinGW
    - [x] glfw
    - [x] glad
    - [x] ImGui
    - [x] Renderdoc调试器
  - [x] 绘制基础几何
    - [x] VAO、VBO、EBO、GLSL文件
    - [x] 点
    - [x] 线
    - [x] 三角面
    - [ ] glfw事件处理
    - [ ] 三维图形
- [ ] mRender设计
  - [ ] 几大对象
  - [ ] 类图设计
  - [ ] 事件驱动（TODO这个我现在都没想好）
  - [ ] 工厂模式创建物体（也没想好，跟实例化物体那边有点关系，就是一次渲染大批量物体，十万百万的）
- [ ] 架构搭建
  - [ ] 程序入口
  - [ ] 向量和矩阵（不细化，具体在用到时候再写。）
  - [ ] 日志、字符串、文件IO、异常等简单实现
  - [ ] Object、Event等父类简单实现
  - [ ] ShaderUtil编译和管理Shaders
  - [ ] BufferGeometry
  - [ ] Object3D
  - [ ] Scene
  - [ ] Renderer
  - [ ] Camera
  - [ ] 绘制简单几何图形
  - [ ] 绘制三维图形
- [ ] 物体变换（Model Matrix）
  - [ ] obj模型简单读取
  - [ ] 线性变换 rotate、scale
  - [ ] 仿射变换 线性变换+translate
- [ ] 视图变换 （View Matrix和Projection Matrix）
  - [ ] 实现平行相机
  - [ ] 实现透视相机
  - [ ] 实现多视角
  - [ ] 对象拾取
  - [ ] 物体实例化
- [ ] 材质和光照
  - [ ] 贴图
  - [ ] 光照计算
  - [ ] 多光源、可配置光照强度
  - [ ] 粗糙度、金属度等等参数实现
  - [ ] 法线贴图
- [ ] 阴影
  - [ ]  阴影其实没想好，还没看这部分的知识
- [ ] 高级内容
  - [ ] 立方体贴图
  - [ ] 环境贴图、天空盒
  - [ ] 蒙皮
  - [ ] 雾
  - [ ] 文字渲染
  - [ ] 粒子、精灵
  - [ ] 动画
- [ ] 接下来的还没想好... 