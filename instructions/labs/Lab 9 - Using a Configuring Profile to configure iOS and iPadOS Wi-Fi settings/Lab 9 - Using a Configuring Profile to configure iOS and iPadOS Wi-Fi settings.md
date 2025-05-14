**实验 9 - 使用配置配置文件配置 iOS 和 iPadOS Wi-Fi 设置。**

**总结**

在本实验中，我们将使用 Microsoft Intune 创建并应用配置文件，以运行为 iOS
和 iPadOS 设备配置 Wi-Fi 设置。

**练习 1：创建配置文件。**

**场景**

系统要求您创建一个配置描述文件，用于为已注册的 iOS 和 iPadOS
设备自动配置 Wi-Fi 设置。您需要确保 Wi-Fi 设置配置如下：

- 网络名称： **Contoso Wi-Fi**

- SSID： **MainOffice**

- 自动连接： **Enable**

- 安全类型： **WPA/WPA2-Personal**

- 预共享密钥： **ContosoWiFi123**

- 分配给： **A new security group named iOS_iPadOS Devices**

**任务 1：创建 iOS_iPadOS 设备组**

1.  切换到 [*SEA-SVR1*](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10)。在
    **Microsoft Entra 管理中心**窗口中，导航并选择 “**Groups**
    ”，然后单击 “**All groups**”。

> ![A screenshot of a computer Description automatically
> generated](./media/image1.png)

2.  在 “**Groups | All groups**” 边栏选项卡中，选择“**New group**”。

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)

3.  在 “**New Group**”
    边栏选项卡上，输入以下信息，然后单击“**Create**”按钮，如下图所示：

    - 组类型： **Security**

    - 组名： !!**iOS_iPadOS Devices**!!

    - 组介绍： !!**All iOS and iPadOS devices**!!

    - 成员身份类型： **Assigned**

> ![A screenshot of a group Description automatically
> generated](./media/image3.png)

4.  在“**Groups | All groups**”边栏选项卡，刷新页面并验证是否显示
    “**iOS_iPadOS Devices** ”组。

> ![A screenshot of a computer Description automatically
> generated](./media/image4.png)

**任务 2：根据方案要求创建配置文件**

1.  切换到 **Microsoft Intune
    管理中心**选项卡，从导航栏中选择“**Devices**”。

> ![A screenshot of a computer Description automatically
> generated](./media/image5.png)

2.  在 **Devices | Overview** 页中，选择 “**iOS/iPadOS**”，如下图所示。

> ![A screenshot of a computer Description automatically
> generated](./media/image6.png)

3.  在 **iOS/iPadOS** 页面上，导航并单击 **Configuration
    profiles**（配置文件）。

4.  在 **iOS/iPadOS | Configuration profiles** 页面的 **Policies**
    选项卡中，单击 **+ Create** 并选择 **+ New Policy**。

> ![](./media/image7.png)

5.  在 **Create a profile** （创建配置文件）
    边栏选项卡中，选择以下选项，然后选择 **Create** （创建）：

    - 平台： **iOS/iPadOS**

    - 配置文件类型： **Templates**

    - 模板名称： **Wi-Fi**

> ![A screenshot of a computer Description automatically
> generated](./media/image8.png)

6.  在“**Basics**”边栏选项卡中，输入以下信息，然后选择“**Next**”：

    - 名字： !!**iOS/iPadOS Wi-Fi Policy**!!

    - 描述： !!**Wi-Fi settings for iOS/iPadOS Devices**!!

> ![A screenshot of a computer Description automatically
> generated](./media/image9.png)

7.  在 “**Configuration settings**” 边栏选项卡上，选择 “**Wi-Fi type**”
    旁边的 “**Basic**”。

> 其他选项根据所选类型显示。

8.  在 “**Configuration settings**” 边栏选项卡上，选择以下选项，然后选择
    “**Next**”：

    - 网络名称： !!**Contoso Wi-Fi**!!

    - SSID： !! **MainOffice**!!

    - 自动连接： **Enable**

    - 安全类型： **WPA/WPA2-Personal**

    - 预共享密钥： !!**ContosoWiFi123**!!

> ![A screenshot of a computer Description automatically
> generated](./media/image10.png)

9.  在 **Assignments** 边栏选项卡上的 **Included groups** 下，选择 **Add
    groups**。

> ![A screenshot of a computer Description automatically
> generated](./media/image11.png)

10. 在 **Select groups to include** （选择要包含的组） 窗口中，选择
    **iOS_iPadOS Devices**（设备），然后单击 **Select**（选择）。

> ![](./media/image12.png)

11. 在 **Assignments** 选项卡中，单击 **Next** 按钮。

> ![A screenshot of a computer Description automatically
> generated](./media/image13.png)

12. 在 **Review + create** 选项卡中，单击 **Create** 按钮。

> ![A screenshot of a computer Description automatically
> generated](./media/image14.png)

13. 验证是否列出了 **iOS/iPadOS Wi-Fi Policy**。

> ![A screenshot of a computer Description automatically
> generated](./media/image15.png)
>
> **结果：**完成本练习后，您将成功创建并分配配置文件，以便为 iOS 和
> iPadOS 设备配置 Wi-Fi 设置。
