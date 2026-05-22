# DiscreteGestureBasics-WPF

Kinect v2 + WPF 示例项目，用于同时追踪最多 6 个人，并通过 Visual Gesture Builder 数据库检测 `Seated` 坐姿手势。

## 快速开始

### 1. 准备环境

- Windows
- Visual Studio 2013 或更高版本
- .NET Framework 4.5
- Kinect for Windows SDK 2.0
- Kinect v2 传感器

确认安装 SDK 后存在环境变量：

```powershell
echo $env:KINECTSDK20_DIR
```

### 2. 获取项目

```bash
git clone https://github.com/MADMAX110/DiscreteGestureBasics-WPF.git
cd DiscreteGestureBasics-WPF
```

### 3. 打开工程

```powershell
start .\DiscreteGestureBasics-WPF\DiscreteGestureBasics-WPF.sln
```

也可以直接双击：

```text
DiscreteGestureBasics-WPF/DiscreteGestureBasics-WPF.sln
```

### 4. 构建运行

在 Visual Studio 中选择：

```text
Debug | Win32
```

然后运行项目。连接 Kinect 后，站到传感器前等待追踪；坐下时界面会显示 `Seated: True` 和识别置信度。

命令行构建可使用：

```powershell
msbuild .\DiscreteGestureBasics-WPF\DiscreteGestureBasics-WPF.sln /p:Configuration=Debug /p:Platform=Win32
```

## 项目说明

- `MainWindow.xaml.cs`：初始化 Kinect，读取 Body Frame，维护最多 6 个追踪目标。
- `GestureDetector.cs`：加载 `Database/Seated.gbd`，检测 `Seated` 手势。
- `GestureResultView.cs`：保存每个 Body 的检测结果、置信度和显示状态。
- `KinectBodyView.cs`：绘制骨架、关节、手部状态和边界提示。
- `Database/Seated.gbd`：Visual Gesture Builder 生成的坐姿手势数据库。

## 目录结构

```text
DiscreteGestureBasics-WPF
├── README.md
└── DiscreteGestureBasics-WPF
    ├── DiscreteGestureBasics-WPF.sln
    ├── DiscreteGestureBasics-WPF.csproj
    ├── MainWindow.xaml
    ├── MainWindow.xaml.cs
    ├── GestureDetector.cs
    ├── GestureResultView.cs
    ├── KinectBodyView.cs
    ├── Database/Seated.gbd
    └── Images/
```

## 常见问题

找不到 `Microsoft.Kinect.dll`：确认已安装 Kinect for Windows SDK 2.0，并检查 `KINECTSDK20_DIR`。

显示 `No ready Kinect found!`：检查 Kinect 电源、USB 连接、驱动安装，以及是否被其他程序占用。

识别不到坐姿：确认人体完整进入 Kinect 视野，骨架绘制稳定后再测试坐下动作。

## 备注

本项目基于 Microsoft Kinect 示例 `Discrete Gesture Basics - WPF`，适合学习 Kinect v2 人体追踪、WPF 显示和 VGB 离散手势识别流程。
