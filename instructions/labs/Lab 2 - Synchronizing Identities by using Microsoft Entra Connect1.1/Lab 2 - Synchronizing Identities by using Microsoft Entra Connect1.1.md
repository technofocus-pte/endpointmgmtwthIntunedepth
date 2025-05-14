实验 02 - 使用 Microsoft Entra Connect 同步标识

**总结**

在本实验中，您将配置从 Active Directory 域服务到 Microsoft Entra ID
的同步

**场景**

Contoso Corporation 目前将 AD DS 和 Microsoft Entra ID
中的用户作为单独的进程进行管理。这非常耗时，并且会导致信息不一致。您的任务是使用
Microsoft Entra Connect 同步工具连接两个目录来解决此问题。

## 任务 0：使用 PowerShell 脚本启用 TLS 1.2 

1.  在 **SEA-SVR1** 上，使用密码 **Pa55w.rd** 以
    **Contoso\Administrator** 身份登录

2.  在开始菜单上，键入 [**PowerShell**](urn:gd:lg:a:send-vm-keys) ，右键单击
    PowerShell，然后选择 **run as administrator**。

![](./media/image1.png)

3.  在 PowerShell 上运行以下脚本。

**If** (-Not (Test-Path
'HKLM:\SOFTWARE\WOW6432Node\Microsoft\\NETFramework\v4.0.30319'))

{

New-Item 'HKLM:\SOFTWARE\WOW6432Node\Microsoft\\NETFramework\v4.0.30319'
-Force | Out-Null

}

New-ItemProperty -Path
'HKLM:\SOFTWARE\WOW6432Node\Microsoft\\NETFramework\v4.0.30319' -Name
'SystemDefaultTlsVersions' -Value '1' -PropertyType 'DWord' -Force |
Out-Null

New-ItemProperty -Path
'HKLM:\SOFTWARE\WOW6432Node\Microsoft\\NETFramework\v4.0.30319' -Name
'SchUseStrongCrypto' -Value '1' -PropertyType 'DWord' -Force | Out-Null

**If** (-Not (Test-Path
'HKLM:\SOFTWARE\Microsoft\\NETFramework\v4.0.30319'))

{

New-Item 'HKLM:\SOFTWARE\Microsoft\\NETFramework\v4.0.30319' -Force |
Out-Null

}

New-ItemProperty -Path
'HKLM:\SOFTWARE\Microsoft\\NETFramework\v4.0.30319' -Name
'SystemDefaultTlsVersions' -Value '1' -PropertyType 'DWord' -Force |
Out-Null

New-ItemProperty -Path
'HKLM:\SOFTWARE\Microsoft\\NETFramework\v4.0.30319' -Name
'SchUseStrongCrypto' -Value '1' -PropertyType 'DWord' -Force | Out-Null

**If** (-Not (Test-Path
'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS
1.2\Server'))

{

New-Item
'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS
1.2\Server' -Force | Out-Null

}

New-ItemProperty -Path
'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS
1.2\Server' -Name 'Enabled' -Value '1' -PropertyType 'DWord' -Force |
Out-Null

New-ItemProperty -Path
'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS
1.2\Server' -Name 'DisabledByDefault' -Value '0' -PropertyType 'DWord'
-Force | Out-Null

**If** (-Not (Test-Path
'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS
1.2\Client'))

{

New-Item
'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS
1.2\Client' -Force | Out-Null

}

New-ItemProperty -Path
'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS
1.2\Client' -Name 'Enabled' -Value '1' -PropertyType 'DWord' -Force |
Out-Null

New-ItemProperty -Path
'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS
1.2\Client' -Name 'DisabledByDefault' -Value '0' -PropertyType 'DWord'
-Force | Out-Null

写-Host 'TLS 1.2 has been enabled. You must restart the Windows Server
for the changes to take affect.' -ForegroundColor Cyan

![](./media/image2.png)

4.  重新启动 Windows Server VM。

![](./media/image3.png)

任务 1：使用 Microsoft Entra Connect 配置目录同步

1.  在 [***SEA-SVR1***](urn:gd:lg:a:select-vm)上，
    如有必要，以[**Contoso\Administrator**](urn:gd:lg:a:send-vm-keys) 身份登录，密码为 !\![**Pa55w.rd**](urn:gd:lg:a:send-vm-keys)!!

2.  在任务栏上，选择 Microsoft Edge。

3.  在地址栏中，输入
    !\![**http://www.microsoft.com/en-us/download/details.aspx?id=47594**](urn:gd:lg:a:send-vm-keys)!!

4.  在 Microsoft Entra Connect 页面上，选择 “**Download**” 。

> Microsoft Entra Connect 会自动下载到 **SEA-SVR1** 上的 **Downloads**
> 文件夹。
>
> ![A screenshot of a computer Description automatically
> generated](./media/image4.png)

5.  单击 **Open file** 以获取下载的文件**AzureADConnect.msi**。

> ![A screenshot of a phone Description automatically
> generated](./media/image5.png)

6.  在 **Microsoft Azure Active Directory Connect** 向导的 “**Welcome to
    Azure AD Connect**”页面上，选中 “**I agree to the license terms and
    privacy notice**” 复选框，然后选择 “**Continue**” 。

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image6.png)

7.  在 **Express Settings** （快速设置） 页面上，选择 **Customize**
    （自定义）。

> ![](./media/image7.png)

8.  在 **Install required components** （安装所需组件） 页面上，选择
    **Install** （安装）。

> ![](./media/image8.png)

9.  在 **User sign-in** （用户登录） 页面上，确保 **Password Hash
    Synchronization** （密码哈希同步） 处于选中状态，然后选择 **Next**
    （下一步）。

> ![](./media/image9.png)

10. 在 “**Connect to Azure AD**” 页面的 “**USERNAME**” 和 “**PASSWORD**”
    框中，输入您的 **Office 365 租户凭据**，然后选择 “**Next**” 。

> ![](./media/image10.png)

11. 在 **Connect your directories** （连接目录） 页面上，确保
    **Contoso.com** 列在 **FOREST** 下，然后选择 **Add Directory**
    （添加目录）。

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image11.png)

12. 在 **AD forest account** 窗口中，选择“ **Create New AD
    Account**”选项，然后在“**ENTERPRISE ADMIN
    USERNAME**”字段中键入[**Contoso\Administrator**](urn:gd:lg:a:send-vm-keys)，然后键入!\![**Pa55w.rd**](urn:gd:lg:a:send-vm-keys)!!
    在 **PASSWORD** 字段中。选择 “**OK**”，然后选择 “**Next**” 。

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image12.png)
>
> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image13.png)

13. 在 **Azure AD sign-in configuration** 页上，确保在 **USER PRINCIPAL
    NAME** 下拉列表中，选择了 **userPrincipalName** 值。

> ![](./media/image14.png)

14. 选择 **Continue without matching all UPN suffixes to verified
    domains**，然后选择 “**Next**” 。

15. 在 **Domain and OU filtering** （域和 OU 筛选） 页面上，选择 **Sync
    selected domains and OUs** （同步选定的域和 OU）。

16. 展开 **Contoso.com**，清除 **Contoso.com**
    旁边的复选框，并确保仅选中以下复选框：**IT, Managers, Marketing,
    Research** 和 **Sales**。选择 **Next**（下一步）。

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image15.png)

17. 在 **Unique identified your users** （唯一标识您的用户）
    页面上，选择 **Next** （下一步）。

18. 在 **Filter users and devices** （筛选用户和设备） 页面上，选择
    **Next** （下一步）。

19. 在 **Optional features** （可选功能）
    页面上，查看可用选项，但不要进行任何更改。确保已选择 **Password hash
    synchronization** （密码哈希同步），然后选择 **Next** （下一步）。

> ![](./media/image16.png)

20. 在 **Ready to configure** （准备配置） 页面上，确保 **Start the
    synchronization process when configuration completes**
    处于选中状态，然后选择 **Install** （安装）。

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image17.png)

21. 配置完成后，选择 **Exit** （退出）。

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image18.png)
>
> **注意：**此时，开始从本地 Active Directory 域服务 （AD DS） 和
> Microsoft Entra ID 同步对象。您应该等待大约 3-4 分钟，以便此过程完成。

22. 关闭所有打开的窗口。

任务 2：验证 Microsoft Entra ID 中的同步

1.  在 **Microsoft Edge** 中打开一个新选项卡并导航到 Microsoft Entra
    管理中心用户页面 -
    !\![**https://entra.microsoft.com/#view/Microsoft_AAD_UsersAndTenants/UserManagementMenuBlade/~/AllUsers/menuId/**](https://entra.microsoft.com/#view/Microsoft_AAD_UsersAndTenants/UserManagementMenuBlade/~/AllUsers/menuId/)!!
    如果系统提示登录，请使用 Lab 界面的“主页”选项卡中的 Office 365
    租户凭据。

> ![A screenshot of a computer Description automatically
> generated](./media/image19.png)

2.  验证是否看到来自本地 AD DS 的用户。确保这些用户在 **On-premises sync
    enabled** （已启用本地同步） 列中具有值 **Yes** （是）。

> ![](./media/image20.png)

3.  在 Navigation （导航） 窗格中，选择 Expand **Groups**
    （展开组），然后选择 **All groups** （所有组）。

> ![A screenshot of a computer Description automatically
> generated](./media/image21.png)

4.  验证是否看到来自本地 AD DS （） 的组

> ![A screenshot of a computer Description automatically
> generated](./media/image22.png)

5.  选择 **Managers** 组。

> ![A screenshot of a computer Description automatically
> generated](./media/image23.png)

6.  在 **Managers** group （经理组） 页面上，选择 **Members**
    （成员），然后确保您看到 users。

> ![A screenshot of a computer Description automatically
> generated](./media/image24.png)
>
> ![A screenshot of a group of people Description automatically
> generated](./media/image25.png)
>
> **请注意，您无法在此组中添加或删除成员，因为它来自本地 AD DS。**

15. 关闭 Microsoft Edge。

**结果：**完成本练习后，您将成功配置 Microsoft Entra Connect，以将身份从
Active Directory 域服务同步到 Microsoft Entra ID
