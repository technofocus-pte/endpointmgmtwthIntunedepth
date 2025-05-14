实践实验室 26：管理 iOS 和 iPadOS 的更新策略

**总结**

在本实验中，您将配置用于管理 iOS 和 iPadOS作系统更新的更新策略。

**场景**

Contoso 的所有开发人员都拥有运行最新 iOS/iPadOS 版本的 iPhone 和
iPad。您已通过 Apple
的自动设备注册注册了这些设备，并且需要为设备作系统配置更新策略。您需要确保以下几点：

- 要安装的版本：最新更新。

- 仅允许在星期三凌晨 12 点到星期四凌晨 12 点之间进行自动更新。

任务 1：为 iOS/iPadOS 设备创建更新策略

1.  如有必要，在 [***SEA-SVR1***](urn:gd:lg:a:select-vm) 上，
    使用密码[**Pa55w.rd**](urn:gd:lg:a:send-vm-keys)
    以[**Contoso\Administrator**](urn:gd:lg:a:send-vm-keys) 身份登录并关闭
    **Server Manager**。

2.  在任务栏上，选择 **Microsoft Edge**。

3.  在 Microsoft Edge
    中，在地址栏中键入 [**https://intune.microsoft.com**](https://intune.microsoft.com) ，然后按
    **Enter**。

4.  使用密码以 [**admin@M365x19242953.onmicrosoft.com**](urn:gd:lg:a:send-vm-keys) 身份登录。

5.  在 **Microsoft Intune 管理中心**页面上，选择 “**Devices**” 。

6.  在 **Devices|By platform** 边栏选项卡，在 “Policy” 下，选择
    “**iOS/iPadOS**” 。

> ![](./media/image1.png)

7.  选择 **Update Policies for iOS/iPadOS**

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)

8.  在详细信息窗格中，选择 **Create profile** （创建配置文件）。

9.  在 **Basics** 选项卡上，配置以下选项，然后选择 **Next**：

    - 名字： !\![**iOS/iPadOS update
      policy**](urn:gd:lg:a:send-vm-keys)!!

    - 描述： !\![**Policy to manage system updates for iOS and
      iPadOS**](urn:gd:lg:a:send-vm-keys)!!

> ![](./media/image3.png)

10. 在 **Update policy settings** （更新策略设置）
    选项卡上，配置以下选项，然后选择 **Next** （下一步）：

    - 选择要安装的版本： **Latest update**

    - 计划类型： **Update during scheduled time**

    - 时区： **UTC:00**

    - 时间窗口：

    - 开课日期：**Wednesday**

      - 开始时间： **12 AM**

      - 结束日期： **Thursday**

      - 结束时间： **12 AM**

> ![](./media/image4.png)

11. 在 **Assignments** （分配） 选项卡上，选择 **Next** （下一步）。

> ![A screenshot of a computer Description automatically
> generated](./media/image5.png)

12. 在 “**Review + create**” 选项卡上，查看设置，然后选择 “**Create**”
    。

13. 在 “**Devices | Update policies for iOS/iPadOS**”
    边栏选项卡的详细信息窗格中，验证是否列出了 **iOS/iPadOS update
    policy**。

> ![A screenshot of a computer Description automatically
> generated](./media/image6.png)

14. 关闭Microsoft Edge。

**结果：**完成本练习后，您将成功配置了 iOS 和 iPadOS 的更新策略。
