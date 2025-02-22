---
title: "What is AppData, and what are Local, LocalLow, and Roaming?"
source: "https://www.xda-developers.com/appdata/"
author:
  - "[[Adam Conway]]"
published: 2023-01-21
created: 2025-02-21
description: "AppData on Windows is an important part of how the operating system works, but what are its three subfolders, and what do they do?"
tags:
  - "clippings"
---
如果您有一台 Windows 11 PC，那么您可能听说过 AppData。它是一个包含三个子文件夹的文件夹：Local、LocalLow 和 Roaming。了解不同类型的 AppData 文件夹及其用途有助于故障排除、管理存储空间等。如果您想知道这些文件夹的用途以及它们为何如此重要，那么您来对地方了。在本文中，我们将解释三种主要类型的 AppData 文件夹之间的区别以及每种文件夹中通常存储哪些类型的信息。

如果您想知道之前在哪里听说过 AppData，那么您可能过去在游戏模组方面遇到过它。Minecraft 等游戏*实际上*将其文件存储在 AppData 中，您需要将文件放在其中才能安装模组。还有其他应用程序，例如*The Elder Scrolls V: Skyrim*，但*Minecraft*很可能是您第一次听说它的地方。

    [![最适合在家办公的电脑](https://static1.xdaimages.com/wordpress/wp-content/uploads/2023/04/best-pcs-for-working-from-home.jpg)](https://www.xda-developers.com/best-laptops-work-from-home/)

有关的

##### [2024 年最适合在家办公的 PC](https://www.xda-developers.com/best-laptops-work-from-home/ "2024 年最适合在家办公的 PC")

如果您正在寻找一台可以融入您的家庭办公环境的新电脑，请查看我们的一些建议。

## 什么是 AppData？

### 每个人都知道

![AppDataFeatureImage-已加水印](https://static1.xdaimages.com/wordpress/wp-content/uploads/2023/01/appdatafeatureimage-watermarked.jpg)

在 Windows 上安装程序时，通常会将其安装在**C:\\Program Files**中，如果是 32 位程序，则安装在**C:\\Program Files (x86)**中。该应用程序将为计算机上的所有用户安装，并且需要管理员权限才能写入。存储在此文件夹中的任何应用程序设置也将传播给所有用户。

这就是 AppData 的作用所在。它是一个隐藏文件夹，位于每个用户文件夹下。它位于**C:\\Users\\<用户名>\\AppData**，包含与程序运行能力无关的程序特定信息，例如用户配置。在 AppData 文件夹中，您将找到以下文件：

- 用户特定安装
- 应用程序配置文件
- 缓存文件

如果您曾经安装过一个程序，并询问您是否要为所有用户安装它，那么它基本上是在询问您是否要将其安装到 Program Files 或 AppData 中。Python[就是这样一个执行此操作的程序](https://www.xda-developers.com/how-to-install-python/)，Discord 也会安装到用户的 AppData 中。此外，AppData 中有三个子文件夹，它们之间的区别很重要。

### 什么是本地？

本地文件夹用于存储无法从用户配置文件中移动的文件，并且通常包含可能太大而无法与服务器同步的文件。例如，它可能包含视频游戏运行所需的一些文件或 Web 浏览器缓存，这些文件可能太大或不适合传输到其他任何地方。开发人员还可能使用本地文件夹来存储与此特定计算机上的文件路径相关的信息。将这些配置文件移动到另一台机器可能会导致程序停止工作，因为文件路径不匹配。

存储在这里的其他文件往往是日志文件、临时文件或非必要数据。

### 什么是 LocalLow？

LocalLow 与 Local 非常相似，但名称中的“低”是指授予应用程序的较低级别的访问权限。例如，隐身模式下的浏览器可能被限制只能访问 LocalLow 文件夹，以防止其能够访问存储在 Local 中的正常用户数据。本质上，这针对的是使用更受限制的安全权限运行的应用程序。

### 什么是漫游？

如果您在域中使用 Windows 计算机（即具有处理您登录的中央域控制器的计算机网络），那么您可能熟悉漫游文件夹。如果您登录同一个域，此文件夹中的文件将同步到其他设备，因为它们对于使用您的设备很重要。这可能是您的 Web 浏览器收藏夹和书签、重要的应用程序设置等。

如果存储的数据可以在设备之间无任何问题地移动，则建议使用此文件夹。例如，Minecraft 将其世界文件、屏幕截图等存储在漫游文件夹中，因为这些文件都可以被带走并迁移到新设备，并且新设备有望正常工作。

漫游非常适合企业环境，包括 Outlook 配置文件和联网打印机配置等设置。它通过存储用户特定的设置和文件，帮助在网络内的不同机器上实现用户环境的一致性。

## 如何在 Windows 上查找 AppData

### 这很容易

在 Windows 上的任何默认安装中查找 AppData 非常简单，但除非您知道自己在做什么，否则不应该乱动它。

1. 同时 按下**Windows 键 + R。**
2. 根据您要转到漫游文件夹还是本地文件夹， 输入“ **%appdata%** ”或“ **%localappdata% ”。**
3. 按**Enter**。

单词周围的百分号告诉运行提示查看本地系统变量以找到 AppData 和 LocalAppData 文件夹的位置。由于这些位置会根据每个用户而变化，因此不可能由系统变量来管理这些位置，因此它们会随每个新用户帐户一起创建。

![应用程序数据-隐藏项目-水印](https://static1.xdaimages.com/wordpress/wp-content/uploads/2023/01/appdata-hidden-items-watermarked.jpg)

在 Windows 10 上，单击顶部的**“查看”**并勾选“隐藏项目”，以确保可以看到**隐藏文件**夹。在 Windows 11 上，单击顶部的**“查看” ，将鼠标悬停在****“显示”**上，然后单击**“隐藏项目”**。

![Windows-11-隐藏文件](https://static1.xdaimages.com/wordpress/wp-content/uploads/2023/01/windows-11-hidden-files.jpg)

或者，您可以在 Windows 资源管理器中导航到**C:\\Users\\<user>\\AppData 。**

现在，无论您使用的是 Windows 10 还是 Windows 11，您都应该能够找到您的 AppData。默认情况下，它是隐藏的，在大多数情况下，您不必访问它，这样做可能会扰乱您的计算机功能。但如果您需要，您现在知道在哪里可以找到它。

![窗户上有光线照射，并显示 Windows 11 文字](https://static1.xdaimages.com/wordpress/wp-content/uploads/2021/06/Windows-11-hero-page.jpg)

有关的

##### Windows 11：你需要知道的一切

Windows 11 是微软最新、最出色的操作系统，它包含大量变化。以下是您需要了解的内容。