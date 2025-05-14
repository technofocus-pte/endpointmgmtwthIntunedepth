**实验 5 - 管理设备注册到 Microsoft Intune**

**总结**

在本实验中，您将通过查看和分配许可证、配置 Windows
自动注册和配置注册限制，为使用 Microsoft Intune 进行设备管理做准备。

**先决条件**

在此实验之前，必须完成以下实验：

- 实验 \#1 - 在 Microsoft Entra ID 中管理身份

- 实验 \#2 - 使用 Microsoft Entra Connect 同步标识

**注意：**您还需要一部可以接收短信的移动电话，该短信用于保护 Windows
Hello 登录对 Entra ID 的身份验证。

**场景**

您需要准备使用 Microsoft Intune
进行设备管理。首先，您需要确保为用户分配了适当的设备管理许可证。作为验证测试，您将为
Aaron Nicholls 分配所需的许可证。您还需要确保加入或注册到 Microsoft
Entra ID 的任何 Windows 设备都将自动注册到 Intune。系统还要求你确保限制
Sales 组的成员将个人 Android 和 iOS 设备注册到
Intune，并将注册设备限制增加到 10 台设备。最后，您需要将 Allan Deyoung
配置为设备注册管理员，以允许他注册 1000 台设备。

**任务 1：查看和分配设备管理许可证**

1.  在 [*SEA-SVR1*](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10)上，导航到
    **Microsoft 365 管理中心**窗口。

![](./media/image1.png)

2.  导航并选择 **Billing** （计费），然后单击 **Licenses** （许可证）。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image2.png)

3.  在 **Licenses** （许可证） 页面中，记下租户中可用的许可证。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image3.png)

4.  选择并单击“**Enterprise Mobility + Security
    E5**”。请注意已分配此许可证的所有用户。您可以从此位置分配和删除许可证。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image4.png)

![](./media/image5.png)

5.  选择一个用户以查看分配给该用户的许可证。记下企业移动性 + 安全性 E5
    许可证中包含的服务。Microsoft Intune 是此许可证支持的服务之一。

![](./media/image6.png)

6.  在 **Microsoft 365 管理中心**导航窗格中，选择 “**Active users**”。

![](./media/image7.png)

7.  搜索并选择 !!**Cindy White**!!

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image8.png)

8.  在 **Cindy White 用户**页面上，单击 **Licenses and
    apps**（许可证和应用程序）。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image9.png)

9.  在“**Settings**”下的“**Usage location**”字段中，选择“**United
    States**”，然后单击“**Enterprise Mobility + Security E5 and Office
    365 E5 (no teams)**”复选框，然后单击“**Save changes**”。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image10.png)

***注：** 在为用户分配许可证之前，必须为用户设置使用位置。*

![](./media/image11.png)

**任务 2：使用 PowerShell 设置用户的密码**

1.  在 [***SEA-SVR1***](urn:gd:lg:a:select-vm)中 右键单击 **Start
    button**，然后选择 **Windows PowerShell (Admin)**。

![](./media/image12.png)

2.  在 **User Account Control** （用户帐户控制） 对话框中，选择 **Yes**
    （是）。

![](./media/image13.png)

3.  在 **Windows PowerShell** 窗口中，键入以下命令，然后按 **Enter**：

!!**Connect-MsolService**!!

![A computer screen with white text Description automatically
generated](./media/image14.png)

4.  在 “**Sign in to your account**” 对话框中，使用 “主页” 选项卡中的
    Office 365 租户凭据登录。

**注意 – 如果系统提示您更改 Tenant admin credentials
密码，请确保提供更新的密码。**

![A screenshot of a computer Description automatically
generated](./media/image15.png)

![A screenshot of a computer screen Description automatically
generated](./media/image16.png)

5.  在 **Windows PowerShell** 窗口中，键入以下命令以重置 **Cindy White**
    的密码

!!**Get-MsolUser | Where-Object DisplayName -EQ "Cindy White" |
Set-MsolUserPassword -NewPassword P@55w.rd1234 -ForceChangePassword
$false**!!

![A computer screen shot of a program Description automatically
generated](./media/image17.png)

**任务 3：启用 Windows 自动注册到 Microsoft Intune**

1.  在 **SEA-SVR1** 中，在 **Microsoft Edge**
    中打开一个新选项卡，然后在地址栏中键入 !!**https://Endpoint.microsoft.com**!!
    ，然后按 **Enter** 键。如果系统提示登录，请提供 **Office 365
    租户管理员**的凭据。

2.  在 Microsoft Intune 管理中心，选择“**Devices**”。

![A screenshot of a computer Description automatically
generated](./media/image18.png)

3.  导航并单击 **Enrollment** （注册）。确保选择 **Windows**
    选项卡，然后导航到 **Enrollment options** 部分并单击 **Automatic
    Enrollment**。

![](./media/image19.png)

4.  在 **MDM user scope** 行上，选择 **All** 单选按钮，然后选择 **Save**
    。

![](./media/image20.png)

5.  点击 **Devices | Enrollment** 链接，如下图所示。

![](./media/image21.png)

**注意：**通过执行此步骤，您为使用 Windows 设备执行 Azure AD
加入的任何用户启用了自动注册到 Intune。

**任务 4：配置注册限制**

1.  导航到 **Devices onboarding** 部分，然后单击
    **Enrollment**。然后，单击 **Android** 选项卡，如下图所示。

![](./media/image22.png)

2.  向下滚动到 **Enrollment options** （注册选项） 部分，然后单击
    **Device platform restriction**（设备平台限制）。

![](./media/image23.png)

3.  选择 “**Android restrictions**” 选项卡，然后选择 **“+Create
    restriction**”。

![](./media/image24.png)

![](./media/image25.png)

4.  在 **Create restriction** （创建限制） 页面的 **Name** （名称）
    框中，输入 !!**Android Personal Device Restriction**!! 选择
    **Next**（下一步）。

![](./media/image26.png)

5.  在 Platform settings （平台设置） 页面的 **Personal owned**
    （个人拥有） 下，为以下设备类型选择 **Block** （阻止），然后单击
    **Next** （下一步） 按钮：

    - Android Enterprise（工作配置文件）

    - Android 设备管理员

![](./media/image27.png)

6.  在 “**Scope tags**”页上，选择“**Next**”。

![A screenshot of a computer Description automatically
generated](./media/image28.png)

7.  在 **Assignments** （分配） 页面的 **Included groups** （包含的组）
    下，选择 **Add groups** （添加组）。

![A screenshot of a computer Description automatically
generated](./media/image29.png)

8.  在 **Select groups to include** （选择要包含的组） 窗格 **Search
    bar** （搜索栏） 中，键入并选择 **Sales**，然后单击 **Select**
    按钮。

![A screenshot of a computer Description automatically
generated](./media/image30.png)

9.  在 **Assignments** 选项卡中，单击 **Next** 按钮。

![A screenshot of a computer Description automatically
generated](./media/image31.png)

10. 在 “**Review + create**”页上，选择“**Create**”。

![A screenshot of a computer Description automatically
generated](./media/image32.png)

请注意，为 Android Personal Device Restriction 分配了优先级 1。

![A screenshot of a computer Description automatically
generated](./media/image33.png)

11. 在 **Devices | Enrollment**
    页面的“**Windows**”选项卡中，导航到“**Enrollment
    options**”部分，然后单击“**Device limit restriction**”限制。

![A screenshot of a computer Description automatically
generated](./media/image34.png)

请注意，有一个分配给 All Users
的默认设备限制。此默认限制将设备注册限制设置为每个用户 5 台设备。

12. 在 “**Enrollment device limit restrictions**” 中，选择 “+ **Create
    restriction**”。

![A screenshot of a computer Description automatically
generated](./media/image35.png)

13. 在 Create restriction （创建限制） 页面的 **Name** （名称）
    框中，输入 !!**Sales Device Enrollment Limit**!! 选择
    **Next**（下一步）。

![A screenshot of a computer Description automatically
generated](./media/image36.png)

14. 在 **Device limit** （设备限制） 页面上，选择 **10**，然后选择
    **Next** （下一步）。

![A screenshot of a computer Description automatically
generated](./media/image37.png)

15. 在 “**Scope tags**”页上，选择“**Next**”。

![A screenshot of a computer Description automatically
generated](./media/image38.png)

16. 在 **Assignments** （分配） 页面的 **Included groups** （包含的组）
    下，选择 **Add groups** （添加组）。

![A screenshot of a computer Description automatically
generated](./media/image39.png)

17. 在 **Select groups to include page** 搜索框中，键入并选择 **Sales**
    然后单击 **Select** 按钮。

![](./media/image40.png)

18. 点击 **Next** 按钮。

![A screenshot of a computer Description automatically
generated](./media/image41.png)

19. 在 “**Review + create**”页上，选择“**Create**”。

![A screenshot of a computer Description automatically
generated](./media/image42.png)

20. 重新加载页面。请注意 Sales Device Enrollment Limit，它配置了 Device
    Limit 10，并分配了优先级 1。

![A screenshot of a computer Description automatically
generated](./media/image43.png)

**任务 5：配置设备注册管理器**

1.  在 **Microsoft Intune 管理中心**，选择“**Devices**”。

![](./media/image44.png)

2.  导航到 **设备载入** 部分，单击 **Enrollment**，然后单击 **Device
    enrolment managers** 选项卡。

![](./media/image45.png)

3.  在 “**Enroll devices**”窗格中，选择 “**Device enrollment
    managers**”。

请注意，默认情况下，未配置任何设备注册管理器。

4.  在 **Enroll devices|Device enrollment managers**
    页上，选择“**Add**”。

![A screenshot of a computer Description automatically
generated](./media/image46.png)

5.  在 **Add user** （添加用户） 页面的 User name （用户名）
    下，输入Allan DeYoung 的电子邮件地址
    [* !!**AllanD@M365xXXXXXXX.onmicrosoft.com***](mailto:DeYoung%E2%80%AF!!AllanD@M365xXXXXXXX.onmicrosoft.com)
    !!（将 **XXXXXX** 替换为您的租户名称），然后选择 **Add** （添加）。

![A screenshot of a computer Description automatically
generated](./media/image47.png)

**Allan 现在最多可以注册 1000 台设备。**

6.  在 Microsoft Intune 管理中心的导航窗格中，选择“**Home**”。

![A screenshot of a computer Description automatically
generated](./media/image48.png)

7.  关闭Microsoft Edge。

**结果：**完成本练习后，您将成功查看和分配许可证、配置 Windows
自动注册、启用和分配注册限制，以及配置设备注册管理器。
