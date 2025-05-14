实验 16 - 在 Microsoft Entra 中为用户帐户配置自助密码重置

**总结**

在本实验中，你将为 **Microsoft Entra ID**
中的用户帐户配置和验证自助密码重置 （SSPR）。

**先决条件**

在此实验之前，必须完成以下实验：

- 实验 \#2 - 使用 Microsoft Entra Connect 同步标识

- 实验 \#5 - 管理设备注册到 Microsoft Intune

**场景**

Help Desk
表示，大量支持票证与密码重置有关。系统要求您为用户提出一个解决方案来重置自己的密码。对于从
AD DS 同步的帐户，该过程应重置其 Microsoft Entra 和 AD DS 密码。

任务 1：配置密码写回

1.  登录 [***SEA-SVR1***](urn:gd:lg:a:select-vm) 为 !!**[Contoso\Administrator](urn:gd:lg:a:send-vm-keys)!!** 用密码
    !!**[Pa55w.rd](urn:gd:lg:a:send-vm-keys)!!** 并关闭 **Server
    Manager**。

2.  在桌面上，双击 **Azure AD Connect**。

> ![A screenshot of a computer Description automatically
> generated](./media/image1.png)

3.  在 “**Welcome to Azure AD Connect**” 页上，选择 “**Configure**” 。

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)

4.  在 **Additional tasks** （其他任务） 页面上，选择 **Customize
    synchronization options** （自定义同步选项），然后选择 **Next**
    （下一步）。

> ![A screenshot of a computer Description automatically
> generated](./media/image3.png)

5.  在 **Connect to Azure AD** （连接到 Azure AD）
    页面上，如果需要，键入 !!**admin@M365xXXXXXXX.onmicrosoft.com!!** 在
    **USERNAME** （用户名） 文本框中，键入 **PASSWORD**，然后选择
    **Next** （下一步）。

> ![A screenshot of a computer Description automatically
> generated](./media/image4.png)

6.  在 **Connect to your directories** （连接到您的目录） 页面上，选择
    **Next** （下一步）。

7.  在 **Domain and OU filtering** （域和 OU 筛选） 页面上，选择
    **Next** （下一步）。

8.  在 **Optional features** （可选功能） 页面上，选择 **Password
    writeback**（密码写回），然后选择 **Next**（下一步）。

> ![A screenshot of a computer Description automatically
> generated](./media/image5.png)

9.  在 “**Ready to configure**” 页面上，选择 “**Configure**” 。

> ![A screenshot of a computer Description automatically
> generated](./media/image6.png)
>
> ![A computer screen shot of a computer Description automatically
> generated](./media/image7.png)
>
> **注意：**配置可能需要几分钟时间。

10. 在 **Configuration complete** （配置完成） 页面上，选择 **Exit**
    （退出）。

> ![A screenshot of a computer Description automatically
> generated](./media/image8.png)

任务 2：启用自助式密码重置。

1.  在任务栏上，选择 **Microsoft Edge**，导航到 **Microsoft Entra
    管理中心** **https://Entra.Microsoft.com**.

2.  使用 **Office 365 租户管理员**凭据登录。

> ![A screenshot of a computer Description automatically
> generated](./media/image9.png)
>
> 此时将打开 **Microsoft Entra 管理中心**。

3.  在 **Microsoft Entra 管理中心**的导航窗格中，展开 “**Identity**”
    ，然后选择 “**Users**” 。

4.  在 **Users** （用户） 导航窗格中，选择 **Password reset**
    （密码重置）。

> ![A screenshot of a computer Description automatically
> generated](./media/image10.png)

5.  在 **Password reset | Properties** 窗口中，选择 “**All**”
    以启用对所有用户的自助密码重置。选择 **Save** （保存）。

> ![A screenshot of a computer Description automatically
> generated](./media/image11.png)
>
> ![A screenshot of a computer screen Description automatically
> generated](./media/image12.png)

6.  在 **Password reset | Properties** 边栏选项卡中，选择
    “**Authentication methods**” 。

> ![A screenshot of a computer Description automatically
> generated](./media/image13.png)

7.  对于用户可用的方法，请确保选择 **Mobile Phone** （移动电话） 和
    **Email** （电子邮件），然后选择 **Security
    Questions**（安全问题）。

8.  对于 **Number of questions required to register**
    （注册所需的问题数），选择 **3**。

9.  对于 **Number of questions required to
    reset**（重置所需的问题数），选择 **3**。

> ![A screenshot of a computer Description automatically
> generated](./media/image14.png)

10. 在 **Select security questions** 部分中，选择 **No security
    questions configured**，然后选择
    **Predefined**。选择您选择的三个问题，然后选择 **OK** （确定）
    两次。

> ![A screenshot of a computer Description automatically
> generated](./media/image15.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image16.png)

11. 选择 **Save** （保存）。

> ![A screenshot of a computer Description automatically
> generated](./media/image17.png)

12. 选择 “**Registration**” ，为 “**Require users to register when
    signing in**” 和 “**Number of days before users are asked to
    re-confirm their authentication information**” 选择 “**Yes**”
    ，将值设置为 **90**，然后选择 “**Save**” 。

> ![A screenshot of a computer Description automatically
> generated](./media/image18.png)

13. 在导航窗格中，选择 **On-premises integration**（本地集成）。

14. 验证您的本地写回客户端是否正在运行，并确保选中 **Enable password
    write back for synced users** （为同步用户启用密码回写）
    复选框。如果需要，请选择 **Save** （保存）。

> ![A screenshot of a computer Description automatically
> generated](./media/image19.png)

15. 关闭 Microsoft Edge。

任务 3：验证自助式密码重置

1.  切换到 [***SEA-WS3***](urn:gd:lg:a:select-vm)。 如有必要，请以
    !!**[Admin](urn:gd:lg:a:send-vm-keys)!!** 使用密码 !!**[Pa55w.rd](urn:gd:lg:a:send-vm-keys)!!**

2.  在任务栏上，选择 **Microsoft
    Edge**。浏览至 !!**https://mysignins.microsoft.com/!!**

3.  在 **Pick an account** （选择账户） 页面上，选择 **Use another
    account** （使用其他账户）。

> ![A screenshot of a computer Description automatically
> generated](./media/image20.png)

4.  在 **Sign in** （登录）
    页面上，输入 !!**Cindy@M365xXXXXXX.onmicrosoft.com!!** ，然后选择
    **Next**。

5.  在 **Enter password** （输入密码）
    页面上，输入 **!!P@55w.rd1234!!**，然后选择 **Sign in**
    （登录）。如果 Microsoft Edge 提示保存密码，请选择 **Save**
    （保存）。

> ![A screenshot of a computer error Description automatically
> generated](./media/image21.png)

6.  系统将提示您 **More information required** （需要更多信息），单击
    **Next** （下一步）

> ![A screenshot of a computer error Description automatically
> generated](./media/image22.png)

7.  提供详细信息，然后单击 **Next**。

> ![A screenshot of a computer Description automatically
> generated](./media/image23.png)

8.  输入 6 位代码，然后单击 **Next**

> ![](./media/image24.png)

9.  再次单击 Next（下一步）。

> ![A screenshot of a computer Description automatically
> generated](./media/image25.png)

10. 点击 **Done**。

> ![](./media/image26.png)

11. 您应该能够访问 **My Account** 页面

> ![](./media/image27.png)

12. 要更改 Password，请访问链接 -
    **!!https://mysignins.microsoft.com/security-info!!**

13. 通过单击文本 +XXXXXXXXXXXXXX 完成验证

> ![A screenshot of a computer error Description automatically
> generated](./media/image28.png)

14. 提供 6 位数代码，然后单击 Verify （验证）。

> ![A screenshot of a computer error Description automatically
> generated](./media/image29.png)

15. 单击 **Skip for now。**

> ![A screenshot of a computer error Description automatically
> generated](./media/image30.png)

16. 在 **Security info** （安全信息） 页面上，单击 **Change** （更改）
    作为密码。

> ![A screenshot of a login page Description automatically
> generated](./media/image31.png)

17. 在 **Change your password** （更改密码）
    页面上，输入以下信息，然后选择 **Submit** （提交）：

    - 创建新密码： **!!P@55w.rd12345!!**

    - 确认新密码： **!!P@55w.rd12345!!**

> ![A screenshot of a login box Description automatically
> generated](./media/image32.png)

18. 点击 Done 按钮。

> ![](./media/image33.png)

19. 关闭 Microsoft Edge 并注销 [***SEA-WS3***](urn:gd:lg:a:select-vm)。

任务 4：运行 Azure AD Connect Sync

请注意，此步骤通常对于密码写回不是必需的，但建议执行此步骤以解决实验室环境中固有的问题，并确保
AD DS 与 Microsoft Entra 同步。

1.  切换到 [***SEA-SVR1***](urn:gd:lg:a:select-vm) 并右键单击 **Start**
    开始 然后选择 **Windows PowerShell （Admin）。**

> ![A screenshot of a computer Description automatically
> generated](./media/image34.png)

2.  在 **Windows PowerShell** 命令提示符下，键入以下命令，然后按
    **Enter**：

> **!!Start-ADSyncSyncCycle -PolicyType Delta!!**
>
> ![A screenshot of a computer Description automatically
> generated](./media/image35.png)

3.  关闭 Windows PowerShell，然后等待大约 3-4 分钟。

任务 5：验证密码写回

1.  切换到 [***SEA-CL1***](urn:gd:lg:a:select-vm) 并在必要时注销。在 [***SEA-CL1***](urn:gd:lg:a:select-vm)上，
    选择 **Other
    user**（其他用户），然后尝试以 !!**Contoso\Cindy!!** 使用密码 !!**P@55w.rd1234!!**

> ![A screenshot of a computer Description automatically
> generated](./media/image36.png)

2.  确保您收到用户名或密码不正确的消息。

> ![A screenshot of a computer screen Description automatically
> generated](./media/image37.png)

3.  现在以 !!**Contoso\Cindy!!** 使用密码 !!**P@55w.rd12345!!** 使用
    SSPR 功能设置的密码。

4.  这次，您应该使用 **new password** 成功登录。

这将确认您在 “我的登录”门户中更改的密码已写回到本地 Active Directory
域服务 （AD DS） 帐户。

![A screenshot of a computer error Description automatically
generated](./media/image38.png)

> 注意 –
> 如果您在登录期间收到上述消息，则确认***身份验证成功***，但由于组成员资格问题，帐户无权登录
> SEA-CL1。

**结果：**完成本练习后，您将成功配置并验证自助式密码重置。
