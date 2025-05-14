Lab17 - 配置和验证设备合规性

**总结**

在本实验中，您将通过配置用于确定托管设备状态的合规性策略和关联的条件访问规则来验证设备合规性。

**先决条件**

在此实验之前，必须完成以下实验：

- 实验 \#1 - 在 Microsoft Entra ID 中管理身份

- 实验 \#2 - 使用 Microsoft Entra Connect 同步标识

- 实验 \#5 - 管理设备注册到 Microsoft Intune

- 实验 \#6 - 将设备注册到 Microsoft Intune

- 实验 \#7 - 创建和部署配置文件

练习 1：配置合规性策略。

**场景**

Contoso 希望确保在 Microsoft Intune 中注册的 Windows
设备满足最低配置规范。以下是必需的规格：

- 最低 Windows作系统版本：10.0.19041.329

- 需要 Microsoft Defender 反恶意软件。

如果设备满足这些要求，它将被标记为合规。如果设备不满足这些要求，则应将设备标记为不合规。

任务 1：创建并分配合规性策略

1.  登录 [***SEA-SVR1***](urn:gd:lg:a:select-vm) 为 !!**[Contoso\Administrator](urn:gd:lg:a:send-vm-keys)!!** 用密码
    !!**[Pa55w.rd](urn:gd:lg:a:send-vm-keys)!!** 

2.  在任务栏上，选择 **Microsoft Edge**。在 Microsoft Edge
    中，键入 !!**https://Intune.microsoft.com!!** ，然后按 **Enter**。

3.  使用 **Office 365 租户管理员凭据**登录。

> ![A screenshot of a computer Description automatically
> generated](./media/image1.png)

4.  从导航窗格中，选择 **Devices**（设备），然后选择 Manage
    devices（管理设备）下的 **Compliance**（合规性）。

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)

5.  在 “**Compliance | Policies**” 边栏选项卡中，在详细信息窗格中选择
    “**+ Create Policy**” 。

> ![A screenshot of a computer Description automatically
> generated](./media/image3.png)

6.  在 **Create a policy** （创建策略） 边栏选项卡上，提供以下值并选择
    **Create** （创建）：

    - 平台： **Windows 10 and later**

> ![A screenshot of a computer Description automatically
> generated](./media/image4.png)

7.  在 **Basics** 选项卡上，提供以下值，然后选择 **Next**：

    - 名字： !!**[Compliance1](urn:gd:lg:a:send-vm-keys)!!**

> ![](./media/image5.png)

8.  在 **Compliance settings** （合规性设置） 选项卡上，展开 **Device
    Health** （设备运行状况） 并查看可用设置。

> ![A screenshot of a computer Description automatically
> generated](./media/image6.png)

9.  在 **Compliance settings** （合规性设置） 选项卡上，展开 **Device
    Properties** （设备属性）。在 **Minimum OS version**
    字段中，键入 !!**[10.0.19041.329](urn:gd:lg:a:send-vm-keys)!!**

> ![A screenshot of a computer Description automatically
> generated](./media/image7.png)

10. 在 **Compliance settings** （合规性设置） 选项卡上，展开 **System
    Security** （系统安全）。将 **Microsoft Defender Antimalware**
    设置设置为 “**Require**” ，然后选择 “**Next**” 。

> ![](./media/image8.png)

11. 在 **Actions for noncompliance** （针对不符合性的作）
    选项卡上，请注意 **Mark device noncompliant** default setting
    （将设备不符合性标记为不符合性） 的作是 **immediately** （立即）。

> ![A screenshot of a computer Description automatically
> generated](./media/image9.png)
>
> 查看如何配置设备标记为不合规的天数，以及配置其他作。

12. 选择 **Next**（下一步）。在 **Assignments** （分配） 选项卡上，选择
    **Add groups** （添加组）。选择 **Windows Devices**，选择
    **Select**，然后选择**Next**。

> ![A screenshot of a computer Description automatically
> generated](./media/image10.png)
>
> **注意：Windows Devices** 组是在创建和部署配置文件 - 实验室中创建的。

13. 选择 **Create**。

> ![A screenshot of a computer Description automatically
> generated](./media/image11.png)

14. 在导航菜单中，选择 “**Devices**” ，然后在 “设备” 导航窗格中，选择
    “**Compliance**” 。

> ![A screenshot of a computer Description automatically
> generated](./media/image12.png)

15. 在 **Compliance** （合规性） 页面上，选择 **Compliance settings**
    （合规性设置）。

> ![A screenshot of a computer Description automatically
> generated](./media/image13.png)

16. 在 **Compliance policy settings** （合规性策略设置） 页面上，在
    **Mark devices with no compliance policy assigned as**
    （将未分配合规策略的设备标记为） 旁边，选择 **Not Compliant**
    （不合规），然后选择 **Save** （保存）。

> ![A screenshot of a computer Description automatically
> generated](./media/image14.png)
>
> 此设置将确保任何未分配合规性策略的设备都将设置为 **Not compliant**
> （不合规）。

**结果：**完成本练习后，您将成功配置合规性策略。

练习 2：创建条件访问策略以强制实施合规性。

**场景**

当用户使用标记为不符合的设备时，他们应该无法访问其电子邮件。系统要求你配置强制实施此规则的条件访问策略，并验证它是否按预期运行。

任务 1：创建条件访问策略

1.  在 [***SEA-SVR1***](urn:gd:lg:a:select-vm)上， 在 **Microsoft Intune
    管理中心**中选择 “**Devices**”，然后选择 “**Conditional access**”。

> ![A screenshot of a computer Description automatically
> generated](./media/image15.png)

2.  单击 **Policies**，然后选择 **+ New policy**，

> ![A screenshot of a computer Description automatically
> generated](./media/image16.png)

3.  在 **New** blade 的 **Name**
    文本框中，键入 !\![**Conditional1!! **](urn:gd:lg:a:send-vm-keys)
    ，然后选择 **0 users or workload identities selected**（0
    个用户或已选择的工作负载身份）。

> ![A screenshot of a computer Description automatically
> generated](./media/image17.png)

4.  在 **Users and groups** 边栏选项卡上，选择 **All users** 单选按钮。

> ![A screenshot of a computer screen Description automatically
> generated](./media/image18.png)

5.  在 “**New**” 边栏选项卡上，选择 “**No target resources selected**”
    ，选择 “**Select apps**” 单选按钮，然后选择 !!**Office 365 Exchange
    Online!!**，然后单击 “**Select**” 。

> ![A screenshot of a computer Description automatically
> generated](./media/image19.png)

6.  在 “**New**” 边栏选项卡的 “**Conditions**” 部分中，选择 “**0
    conditions selected**” 。

> ![A screenshot of a computer Description automatically
> generated](./media/image20.png)

7.  在条件列表中，在 **Device platforms** （设备平台） 下，选择 **Not
    configured** （未配置）。在 **Configure** 部分中，选择 **Yes**，选择
    **Select device platforms** 单选按钮，选中 **Windows**
    复选框，然后选择 **Done**。

> ![A screenshot of a computer Description automatically
> generated](./media/image21.png)

8.  在 **Access controls** 下的 **New** blade 的 **Grant** 部分中，选择
    **0 controls selected**。

9.  选中 **Require device to be marked as compliant** 复选框，然后选择
    **Select**。

> ![A screenshot of a computer Description automatically
> generated](./media/image22.png)

10. 在 “**New**” 边栏选项 **On**，为 “**Enable policy**”
    选项选择，然后选择 “**Create**” 。

> ![A screenshot of a computer Description automatically
> generated](./media/image23.png)

11. 关闭 Microsoft Edge。

任务 2：验证条件访问策略是否正常工作

1.  切换到 [***SEA-WS3***](urn:gd:lg:a:select-vm) 并以 !!**[Admin](urn:gd:lg:a:send-vm-keys)!!** 使用密码 !!**[Pa55w.rd](urn:gd:lg:a:send-vm-keys)!!**。

2.  在 [***SEA-WS3***](urn:gd:lg:a:select-vm) 的任务栏上，选择
    **Microsoft Edge**。在 Microsoft Edge
    中，键入 [**outlook.office.com**](urn:gd:lg:a:send-vm-keys) ，然后按
    Enter。

3.  在 选取帐户
    对话框中，选择 !!**Cindy@M365xXXXXXXX.onmicrosoft.com!!**

4.  在 **Enter password** （输入密码）
    页面上，输入 !!**P@55w.rd12345!!** ，然后选择 **Sign in**
    （登录）。如果出现 Microsoft Edge Save password 提示，请选择
    **Update**。

> ![A screenshot of a computer error Description automatically
> generated](./media/image24.png)

5.  确认您收到消息 **"** **Sign in with your work account"**。

> ![A screenshot of a computer Description automatically
> generated](./media/image25.png)

6.  选择 **More details**。您应该会看到有关您被阻止的原因的更多信息。

> ![A screenshot of a computer error Description automatically
> generated](./media/image26.png)
>
> **注意：**这是因为 SEA-WS3 未加入 Microsoft Entra ID，也不由 Microsoft
> Intune 管理，因此未标记为合规。

7.  **关闭**浏览器窗口**。**

8.  切换到 [***SEA-WS1***](urn:gd:lg:a:select-vm)，并以
    !!**Cindy@M365xXXXXXXX.onmicrosoft.com!!**
    使用**密码**页面，输入 !!**P@55w.rd12345!!** 

> **注意：**SEA-WS1 是在 Intune 中注册的托管 Windows 11 设备。

9.  在任务栏上，选择 **Microsoft Edge**。在 Microsoft Edge
    中，键入 [**Outlook.office.com**](urn:gd:lg:a:send-vm-keys) ，然后按
    **Enter**。

10. 验证您是否可以访问 Cindy 的邮箱。

> ![A screenshot of a computer Description automatically
> generated](./media/image27.png)
>
> **注意：**这是因为 **SEA-WS1** 是托管设备并标记为合规。

11. 关闭 Microsoft Edge 并注销 [***SEA-WS1***](urn:gd:lg:a:select-vm)。

任务 3：禁用条件访问策略

1.  在 [***SEA-SVR1***](urn:gd:lg:a:select-vm)上， 在 **Microsoft Intune
    管理中心** !\!<https://intune.microsoft.com>!! 选择 “**Devices**”
    ，然后选择 “**All devices**” 。

> ![](./media/image28.png)
>
> 请注意，**SEA-WS1** 是合规的，这就是允许 Cindy 访问其邮箱的原因。

2.  从导航窗格中，选择 **Devices**（设备），然后选择 **Conditional
    access**（条件访问）。

> ![](./media/image29.png)

3.  在 “**Conditional Access**” 页上，选择 “**Policies**”，然后单击
    “**Conditional1**” 。

> ![A screenshot of a computer Description automatically
> generated](./media/image30.png)

4.  在 **Conditional1** 页面底部的页面上，选择 **Off**，然后选择
    **Save**。

> ![A screenshot of a computer Description automatically
> generated](./media/image31.png)

5.  关闭Microsoft Edge。

**结果：**完成本练习后，您将成功配置条件访问策略以确定设备合规性。
