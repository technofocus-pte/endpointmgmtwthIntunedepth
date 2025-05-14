实验 18 - 使用 Microsoft Intune 配置终结点安全性

**总结**

在本实验中，您将创建一个策略，以便在 Microsoft Intune 中为托管设备配置
Microsoft Defender。

**先决条件**

在此实验之前，必须完成以下实验：

- 实验 \#5 - 管理设备注册到 Microsoft Intune

- 实验 \#6 - 将设备注册到 Microsoft Intune

- 实验 \#7 - 创建和部署配置文件

**场景**

系统要求你确保 Contoso 开发人员组已正确配置 Microsoft Defender。已要求：

- 防止篡改保护。

- 在 Windows
  安全中心应用中隐藏“帐户保护”、“应用程序和浏览器控制”、“设备安全”、“设备性能和运行状况”和“家庭选项”区域

- 必须添加公司名称和电话号码。

- 此外，还需要配置实时保护、修复和扫描设置。

设置将通过在已注册的设备 SEA-WS1 和未注册的设备 SEA-CL1
上进行测试来验证。

任务 1：在 Intune 中配置 Windows 安全体验

1.  切换并登录 [***SEA-SVR1***](urn:gd:lg:a:select-vm) 作为 !!**[Contoso\Administrator](urn:gd:lg:a:send-vm-keys)!!** 用密码
    !!**[Pa55w.rd](urn:gd:lg:a:send-vm-keys)!!**

2.  在任务栏上，选择 **Microsoft Edge**。

3.  在 Microsoft Edge
    中，键入 !!**https://Intune.microsoft.com!!**，然后按 **Enter**。

4.  以 Office 365 租户管理员身份登录。

> ![A screenshot of a computer Description automatically
> generated](./media/image1.png)

5.  从导航窗格中，选择 **Endpoint security**（终端节点安全），然后选择
    **Antivirus**（防病毒）。

> ![](./media/image2.png)

6.  在 **Endpoint security |Antivirus** 窗格中，选择 **+ Create
    Policy**。

> ![A screenshot of a computer Description automatically
> generated](./media/image3.png)

7.  在 **Create a profile** （创建配置文件） 窗格中，对于 **Platform**
    （平台），选择 **Windows 10、Windows 11 和 Windows Server**。

8.  在 **Profile** （配置文件） 列表中，选择 **Windows Security
    experience**。然后选择 **Create** （创建）。

> ![A screenshot of a computer Description automatically
> generated](./media/image4.png)

9.  在 基本信息 选项卡的 **Name** 字段中，输入 !!**[Windows Security
    Settings](urn:gd:lg:a:send-vm-keys)!!**。 选择 **Next**（下一步）。

> ![A screenshot of a computer Description automatically
> generated](./media/image5.png)

10. 在 **Defender** 下，配置以下设置：

    - TamperProtection (Device): **On**

> ![A screenshot of a computer Description automatically
> generated](./media/image6.png)

11. 在 **Windows Defender Security Center** 下，配置以下设置：

    - 禁用账户保护 UI： **Enable**

    - 禁用应用程序浏览器 UI： **Enable**

    - 禁用设备安全 UI： **Enable**

    - 禁用系列 UI： **Enable**

    - 禁用运行状况 UI： **Enable**

> ![A screenshot of a computer Description automatically
> generated](./media/image7.png)

12. 在 **Enable Customized Toasts** （启用自定义 Toast） 旁边，选择
    **Enable** （启用）。

13. 在 **Company name** 字段中，选择
    **Configured**，然后输入 !!**[Contoso
    IT](urn:gd:lg:a:send-vm-keys)!!**

14. 对于 **Phone**（电话），选择
    **Configured**（已配置），然后输入 !!**[555-1234](urn:gd:lg:a:send-vm-keys)!!**，然后选择
    **Next**。

> ![A screenshot of a computer Description automatically
> generated](./media/image8.png)

15. 在 “**Scope tags**” 页上，选择 “**Next**” 。

> ![A screenshot of a computer Description automatically
> generated](./media/image9.png)

16. 在 **Assignments** （分配） 选项卡上的 **Included groups**
    （包含的组） 下，选择 **Add groups** （添加组）。选择 **Contoso
    Developer Devices** 组，单击 “**Select**”，然后选择 “**Next**” 。

> ![A screenshot of a computer Description automatically
> generated](./media/image10.png)

17. 在 **Review + create** 选项卡上，查看信息并选择 **Save**。

> ![A screenshot of a computer Description automatically
> generated](./media/image11.png)

任务 2：在 Intune 中配置 Microsoft Defender 防病毒策略

1.  在 **Endpoint security |Antivirus** （防病毒） 窗格中，选择 **Create
    Policy** （创建策略）。

> ![A screenshot of a computer Description automatically
> generated](./media/image12.png)

2.  在 **Create a profile** （创建配置文件） 窗格中，对于 **Platform**
    （平台），选择 **Windows 10、Windows 11 和 Windows Server**。

3.  在 “**Profile**” 列表中，选择 “**Microsoft Defender
    Antivirus**”，然后选择 “**Create**” 。

> ![A screenshot of a computer Description automatically
> generated](./media/image13.png)

4.  在 **Basics** 选项卡的 **Name** 字段中，输入 !!**[Microsoft Defender
    Antivirus Settings](urn:gd:lg:a:send-vm-keys)!!**，选择
    **Next**（下一步）。

> ![A screenshot of a computer Description automatically
> generated](./media/image14.png)

5.  在 **Configuration settings** （配置设置） 选项卡上，配置以下设置：

    - 允许入侵防御系统： **Allowed**

    - 允许扫描所有下载的文件和附件： **Allowed**

    - 允许实时监控： **Allowed**

> ![](./media/image15.png)

- 运行扫描前检查签名： **Enabled**

- 保留已清理恶意软件的天数： !!**[60](urn:gd:lg:a:send-vm-keys)!!**

> ![A screenshot of a computer Description automatically
> generated](./media/image16.png)

- 安排快速扫描时间： !!**[60](urn:gd:lg:a:send-vm-keys)!!** (表示凌晨
  1：00)

> ![A screenshot of a computer Description automatically
> generated](./media/image17.png)

- 提交样本同意书： **Send safe samples automatically**

> ![A screenshot of a computer Description automatically
> generated](./media/image18.png)

6.  在 **Configuration settings** （配置设置） 选项卡上，选择 **Next**
    （下一步）。

7.  在 “**Scope tag**” 页上，选择 “**Next**” 。

> ![A screenshot of a computer Description automatically
> generated](./media/image19.png)

8.  在 **Assignments** （分配） 选项卡上的 **Included groups**
    （包含的组） 下，选择 **Add groups** （添加组）。

9.  选择 **Contoso Developer Devices** 组，然后选择 **Select**
    （选择），然后选择 **Next** （下一步）。

> ![A screenshot of a computer Description automatically
> generated](./media/image20.png)

10. 在 **Review + create** 选项卡上，查看信息并选择 **Save**。

> ![A screenshot of a computer Description automatically
> generated](./media/image21.png)

任务 3：同步托管设备

1.  在 **Microsoft Intune 管理中心**，选择 “**Devices**” ，然后选择
    “**All devices**” 。

2.  在 **Devices | All devices** 窗格中，选择 “**SEA-WS1**” ，然后在
    “**SEA-WS1**” 边栏选项卡上，选择工具栏上的 “**Sync**” ，然后选择
    “**Yes**” 。

> ![](./media/image22.png)
>
> 等待 3-4 分钟，以便同步完成。

3.  关闭 Microsoft Edge。

任务 4：验证配置

1.  切换到 [***SEA-CL1***](urn:gd:lg:a:select-vm)。
    如有必要，请以 !!**[Contoso\Administrator](urn:gd:lg:a:send-vm-keys)!!** 使用密码 !!**[Pa55w.rd](urn:gd:lg:a:send-vm-keys)!!**.

2.  在 [***SEA-CL1***](urn:gd:lg:a:select-vm)上， 选择
    **Start**（开始），键入 !!**[Windows
    Security](urn:gd:lg:a:send-vm-keys)!!**, 然后在 Windows
    安全中心图标下选择 **Open** 。

> ![](./media/image23.png)
>
> 请注意，将显示所有安全选项。这是因为 SEA-CL1 未注册到 Intune。
>
> ![A screenshot of a computer security system Description automatically
> generated](./media/image24.png)

3.  关闭 Windows Security
    并注销 [***SEA-CL1***](urn:gd:lg:a:select-vm)。

4.  切换到 [***SEA-WS1***](urn:gd:lg:a:select-vm)，并以
    **!!Cindy@M365x27131290.onmicrosoft.com!!** 使用密码
    **!!P@55w.rd12345!!**。

5.  选择 **Start**（开始），键入 !!**[Windows
    Security](urn:gd:lg:a:send-vm-keys)!!**, 然后在 Windows
    安全中心图标下选择 **Open**。

> ![](./media/image25.png)
>
> 请注意，不会显示在 Intune
> 策略中配置的所有限制区域。 [***SEA-WS1***](urn:gd:lg:a:select-vm) 已在
> Intune 中注册，该 Intune 已应用安全设置。
>
> ![A screenshot of a computer Description automatically
> generated](./media/image26.png)

6.  关闭 Windows Security
    并注销 [***SEA-WS1***](urn:gd:lg:a:select-vm)。

**结果：**完成本练习后，您将成功创建并应用策略，以在 Intune
中为托管设备配置 Microsoft Defender。
