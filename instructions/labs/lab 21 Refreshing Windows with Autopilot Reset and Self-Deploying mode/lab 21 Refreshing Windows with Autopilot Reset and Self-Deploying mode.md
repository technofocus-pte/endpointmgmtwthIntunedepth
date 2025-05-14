实验 21：使用 Autopilot 重置和自部署模式刷新 Windows。

**总结**

在本实验中，您将学习如何执行远程 Autopilot 重置。

**先决条件**

在此实验之前，必须完成以下实验：

- 实验 01 - 在 Microsoft Entra ID 中管理身份

- 实验 02 - 使用 Azure AD Connect 同步身份

- 实验 21 - 使用 Microsoft 部署工具包部署 Windows 11

- 实验 20 - 使用 Autopilot 部署 Windows 11

**场景**

SEA-WS4 已使用 Windows Autopilot 进行部署。您需要测试另一个涉及
Autopilot 重置的预配方案。您将创建一个配置了 Windows Autopilot
自部署模式的新部署配置文件。

任务 1：配置自部署 Windows Autopilot 部署配置文件

1.  切换到  [***SEA-SVR1***](urn:gd:lg:a:select-vm)。

> ![](./media/image1.png)

2.  在 **Microsoft Edge** 中，打开一个新选项卡并导航到
     [**https://intune.microsoft.com**](https://intune.microsoft.com)。如果出现提示，请使用 [**admin@M365xXXXXXXXX.onmicrosoft.com**](mailto:admin@M365xXXXXXXXX.onmicrosoft.com) 和
    paswword 登录。

3.  在 **Microsoft Intune 管理中心**，选择 “**Devices**” 。

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)

4.  在 **Device onboarding** （设备载入） 部分中，选择 **Enrollment**
    （注册）。

> ![A screenshot of a computer Description automatically
> generated](./media/image3.png)

5.  在 Windows enrollment （Windows 注册）
    边栏选项卡上的详细信息窗格中，选择 **Deployment
    Profiles**（部署配置文件）。

> ![](./media/image4.png)

6.  在 “**Windows AutoPilot deployment profiles**” 边栏选项卡上，选择
    “**Contoso Profile 1**” ，然后选择 “**Properties**” 。

> ![](./media/image5.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image6.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image7.png)

7.  向下滚动到 **Assignments**（分配），然后选择 **Edit**（编辑）。

> ![A screenshot of a computer Description automatically
> generated](./media/image8.png)

8.  在 **IT Devices** 旁边，选择 **Remove**。

> ![](./media/image9.png)

9.  选择 “**Review and save**” ，然后选择 “**Save**” 。

> ![A screenshot of a computer Description automatically
> generated](./media/image10.png)

10. 关闭 **Contoso Profile 1|Properties**（属性） 页面。

11. 在 “**Windows AutoPilot deployment profiles**” 边栏选项卡上，选择
    “**Create profile**” ，然后选择 “**Windows PC**” 。

> ![A screenshot of a computer Description automatically
> generated](./media/image11.png)

12. 在 **Basics** 选项卡的 **Name** 文本框中，键入 [**Contoso profile
    2**](urn:gd:lg:a:send-vm-keys)。

13. 对于 “**Convert all targeted devices to Autopilot**” ，选择 “**No**”
    ，然后选择 “**Next**” 。

> ![](./media/image12.png)

14. 在 “**Out-of-box experience (OOBE)**” 选项卡上，确保 “**Deployment
    mode**” 设置为 “**Self-Deploying**” 。

> ![](./media/image13.png)

15. 确保设置了以下选项：

    - 语言 （区域） ：**Operating system default**

    - 自动配置键盘：**Yes**

    - 应用设备名称模板：**Yes**

    - 输入名称：[**Contoso-%RAND:2%**](urn:gd:lg:a:send-vm-keys)

> ![A screenshot of a computer Description automatically
> generated](./media/image14.png)

16. 选择 **Next**（下一步）。

17. 在 **Assignments** （分配） 选项卡上的 **Included groups**
    （包含的组） 下，选择 **Add groups** （添加组）。

> ![A screenshot of a computer Description automatically
> generated](./media/image15.png)

18. 选择 **IT Devices** 组，然后单击 **Select**。选择
    **Next**（下一步）。

> ![](./media/image16.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image17.png)

19. 在 “**Review + create**” 边栏选项卡上，查看信息，然后选择
    “**Create**” 。

> ![A screenshot of a computer Description automatically
> generated](./media/image18.png)

任务 2：执行 Autopilot 重置

1.  在 **Microsoft Intune 管理中心**，选择 “**Devices**” ，然后选择
    “**All devices**” 。

2.  选择 Autopilot PC （以名称 DESKTOP 开头）。

> ![A screenshot of a computer Description automatically
> generated](./media/image19.png)

3.  在菜单栏中，选择椭圆，然后选择  **Autopilot Reset**。

> ![A screenshot of a computer Description automatically
> generated](./media/image20.png)

4.  在消息提示符处，选择 **Yes** （是）。

> ![A screenshot of a computer Description automatically
> generated](./media/image21.png)

5.  切换到[***SEA-SVR2***](urn:gd:lg:a:select-vm) 并最大化 **SEA-WS4**
    窗口。

> **注意：**SEA-WS4 应仍从上一个实验运行
>
> **注意：**将设备更新到最新版本，然后单击重新启动。

6.  重新启动**SEA-WS4**。

> ![A screenshot of a computer Description automatically
> generated](./media/image22.png)
>
> **注意：** 此过程可能需要 30
> 分钟，在此过程中会重启几次。在此任务完成时，您的教师可以继续学习下一个模块。请务必在下一次实验会话中返回完成任务
> 3。

任务 3：验证 Autopilot 部署

1.  在登录页面上，输入 [**Cindy@M365x19242953.onmicrosoft.com**](mailto:Cindy@M365x19242953.onmicrosoft.com) 密码为 
    [**P@55w.rd1234**](mailto:P@55w.rd1234)。

2.  在 “**Use Windows Hello with your account**” 中，选择 “**OK**” 。

> ![A screenshot of a computer Description automatically
> generated](./media/image23.png)

3.  在 **Verify your identity** （验证您的身份） 页面上，选择 Text
    verification method （文本验证方法）。

4.  在 **Enter code** （输入代码）
    页面上，输入已发送到您的移动设备的代码，然后选择 **Verify**
    （验证）。

> ![A screenshot of a computer Description automatically
> generated](./media/image24.png)

5.  在 **Setup up a PIN** 对话框的 **New PIN** 和 **Confirm PIN**
    字段中，输入 [**102938**](urn:gd:lg:a:send-vm-keys)，然后选择
    **OK**。

> ![](./media/image25.png)

6.  在 **All set！**页面上，选择 **OK**。

7.  选择 **Start** （开始），然后选择 **Settings** （设置）。

> ![](./media/image26.png)

8.  选择 “**Accounts**” ，然后选择 “**Access work or school**”
    。验证设备是否已连接到 Contoso 的 Azure AD。

> ![](./media/image27.png)

9.  选择 “**Connected to Contoso's Azure AD**”，然后选择 “**Info**” 。

> ![](./media/image28.png)

10. 在 **Managed by Contoso** （由 Contoso 管理）
    页面上，向下滚动，然后选择 **Sync** （同步）。

> ![](./media/image29.png)

11. 在 **SEA-WS4** 上，关闭 **Settings** 窗口。

12. 关闭 **SEA-WS4** 并关闭 **SEA-WS4** 窗口。

13. 在 [***SEA-SVR2***](urn:gd:lg:a:select-vm)上，关闭 Hyper-V 管理器。

**结果：**完成本练习后，您将使用自部署模式为 Windows 11 设备配置了
Autopilot 重置。
