# **ラボ 19 - Microsoft Deployment Toolkit を使用した Windows 11 の展開**

**要約**

このラボでは、Microsoft Deployment Toolkit を使用して、Windows 11
オペレーティング システム イメージを作成して展開します。

**シナリオ**

SEA-WS4という新しいWindows
11仮想マシンを展開する必要があります。Microsoft Deployment
Toolkitを使用して、Hyper-Vで作成された仮想マシンにオペレーティングシステムを展開することにしました。MDTで新しい展開共有を構成し、SEA-WS4を展開する手順を実行するタスクシーケンスを構成します。

### **タスク 1:新しいDeployment Shareの作成**

1.  Switch
    to [**SEA-SVR2**](urn:gd:lg:a:select-vm)に切り替えて、!!**[Contoso\Administrator](urn:gd:lg:a:send-vm-keys)!!にサインインする**!!**[Pa55w.rd](urn:gd:lg:a:send-vm-keys)!!パスワードを使用する。**

> ![Screenshot](./media/image1.png)

2.  タスクバーで**File
    Explorer**を選択してから!!**[E:\Labfiles\ISOs](urn:gd:lg:a:send-vm-keys)!!**を観覧する**。**

> ![Screenshot](./media/image2.png)

3.  **Win11_21H2_Eval.isoを右クリックして、Mount**を選択する。
    ISOはDVDドライブ**D**としてマウントされます。

> ![Screenshot](./media/image3.png)
>
> ![Screenshot](./media/image4.png)

4.  **File Explorer**を閉じる。

5.  **Start menu**をせんたくして、**Microsoft Deployment
    Toolkit**を拡張し、**Deployment Workbench**を選択する。

> ![Screenshot](./media/image5.png)

6.  **Deployment Workbench**中に**Deployment
    Shares**を右クリックし**、New Deployment Share**を選択する。

> ![Screenshot](./media/image6.png)
>
>  **New Deployment Share Wizard** が開きます。

7.  **PathページでDeployment share
    path**の下に値を!!**[E:\DeploymentShare](urn:gd:lg:a:send-vm-keys)!!** に変更してから**Next**を選択する。

> ![Screenshot](./media/image7.png)

8.  **ShareページでShare
    name**をに注意するが変更しない。**Next**を選択する。

> ![Screenshot](./media/image8.png)

9.  **Descriptive
    Nameページで**デフォルト値を受け取る後**Next**を選択する。

> ![Screenshot](./media/image9.png)

10. **Optionsページで以下を構成してNext**を選択する：

    - Ask to set the local Administrator password: **Enabled**

    - 他全てのチェックボックス: **Disabled**

> ![Screenshot](./media/image10.png)

11. **Summaryページで情報を確認してからNext**を選択する。

> ![Screenshot](./media/image11.png)

12. **Confirmationページで、処理が正常に完了したことを確認してからFinish**を選択する。

> ![Screenshot](./media/image12.png)

13. **Deployment Shares**の下に**MDT Deployment
    Share**フォールだを拡張する**。**

> **Deployment Share**に構成できるさまざまなノードに注意してください。

### **タスク 2: Deployment ShareにOperating Systemファイルを追加する。**

1.  Deployment Workbench中に**Deployment Shares**を拡張し、**MDT
    Deployment Share**を拡張してから**Operating Systems**を選択する。

> ![Screenshot](./media/image13.png)

2.  **Operating Systems**を右クリックしてから**Import Operating
    Systemを選択する。**Import Operating System Wizardが開きます。

> ![Screenshot](./media/image14.png)

3.  **Import Operating System Wizard**の中に、**OS Type**ページで**Full
    set of source files**を選択してから**Next**を選択する。

> ![Screenshot](./media/image15.png)

4.  **Source**ページで**Source
    Directory**の下に!!**[D:\\](urn:gd:lg:a:send-vm-keys)!!を入力して、Next**を選択する。

> ![Screenshot](./media/image16.png)

5.  **Destination** ページでデフォルトの保存先ディレクトリ名を!!**[Windows
    11 Enterprise
    x64](urn:gd:lg:a:send-vm-keys)!!** に変更してから**Next**を選択する。

> ![Screenshot](./media/image17.png)

6.  **Summary**ページで情報をレビューしてから**Next**を選択する。

> ![Screenshot](./media/image18.png)
>
> Operating systemのソースファイルがdeployment shareにコピーされます。

7.  **Confirmation**ページで処理が正常に完了したことを確認して**、Finish**を選択する。

> ![Screenshot](./media/image19.png)

8.  **Deployment Workbench中に、Operating
    Systemsが選択されているままに、**operating
    systemが表示していることを確認する。

### **タスク 3: Deployment Shareにアプリケーションを追加する**

1.  Deployment Workbenchの中に、**Deployment Shares**を拡張して、**MDT
    Deployment Share**を拡張し、**Applications**を選択する。

2.  **Applicationsを右クリックし、New Application**を選択する。New
    Application Wizardが開きます。

> ![Screenshot](./media/image20.png)

3.  **New Application Wizard**の中に、**Application
    TypeページでApplication with source
    files**を選択して、**Next**を選択する。

> ![Screenshot](./media/image21.png)

4.  **Details**ページで以下を構成して**Next**を選択する：

    - Publisher: !!**[Microsoft](urn:gd:lg:a:send-vm-keys)!!**

    - Application Name: !!**[XML Notepad](urn:gd:lg:a:send-vm-keys)!!**

> ![Screenshot](./media/image22.png)

5.  **Source**ページで**Source
    directory**の下に!!**[E:\Labfiles\Apps](urn:gd:lg:a:send-vm-keys)!!** を入力して、**Next**を選択する。

> ![Screenshot](./media/image23.png)

6.  **Destination**ページでデフォルト保存先ディレクトリ名を受け取り**、Next**を選択する。

> ![Screenshot](./media/image24.png)

7.  **Command Details**ページで**Command
    line**の下に!!**[XmlNotepadSetup.msi
    /q](urn:gd:lg:a:send-vm-keys)!!**を入力して**、Next**を選択する。

> ![Screenshot](./media/image25.png)

8.   **Summary**ページで情報をレビューしてから**Next**を選択する。

> ![Screenshot](./media/image26.png)

9.  **Confirmation**ページで処理が正常時完了したことを確認して**Finish**を選択する。

### **タスク 4: MDT Task Sequenceの作成**

1.  Deployment Workbenchの中に、**Deployment Shares**を拡張して、**MDT
    Deployment Shareを拡張し**、**Task Sequences**を選択する。

2.  **Task Sequencesを右クリックし、New Task Sequence**を選択する。**New
    Task Sequence Wizard**が開きます。

> ![Screenshot](./media/image27.png)

3.  **General Settingsページで**、以下を構成して**Next**を選択する：

    - Task sequence ID: !!**[001](urn:gd:lg:a:send-vm-keys)!!**

    - Task sequence name: !!**[Deploy Windows 11
      Enterprise](urn:gd:lg:a:send-vm-keys)!!**

> ![Screenshot](./media/image28.png)

4.  **Select Template**ページで**Standard Client Task
    Sequence**を選択して、**Next**を選択する。

> ![Screenshot](./media/image29.png)

5.  **Select OS**ページで**、Windows 10 Enterprise
    Evaluation**を選択して**、Next**を選択する。

> ![Screenshot](./media/image30.png)

6.  **Specify Product Key**ページで**Do not specify a product key at
    this time**を選択してから**Next**を選択する。

> ![Screenshot](./media/image31.png)

7.  **OS Settings**ページで以下を構成してから**Next**を選択する：

    - Full Name: !!**[User](urn:gd:lg:a:send-vm-keys)!!**

    - Organization: !!**[Contoso
      Corporation](urn:gd:lg:a:send-vm-keys)!!**

    - Internet Explorer Home
      Page: !!**[about:blank](urn:gd:lg:a:send-vm-keys)!!**

> ![Screenshot](./media/image32.png)

8.  **Admin Password**ページで**Use the specified local Administrator
    password**を選択して、両方のボックス中に !!**[Pa55w.rd](urn:gd:lg:a:send-vm-keys)!!** を入力する。**Next**を選択する。

> ![Screenshot](./media/image33.png)

9.  **Summary**ページで、情報をレニューして**、Next**を選択する。

> ![Screenshot](./media/image34.png)

10. **Confirmation**ページで、処理が正常に完了したことを確認してから**Finish**を選択する。

> ![Screenshot](./media/image35.png)

11. **Deployment Workbench**の中に、**Task
    Sequences**を選択したままに**、** **Deploy Windows 11
    Enterprise** Task sequence が表示することを確認する。

> ![Screenshot](./media/image36.png)

12. **Deploy Windows 11 Enterprise** Task
    sequenceを右クリックし、**Properties**を選択する。

> ![Screenshot](./media/image37.png)

13. **Task Sequence**タブを選択する。

14. **Validation**ノードを拡張して**Validate**を選択する。

15. **Propertiesページで** **Ensure minimum memory**と**Ensure minimum
    processor speed**の横のチェックボックスをオフにする。

> その他の変更を行わない。
>
> **Deploy Windows 11 Enterprise
> Properties**ウィンドで**OK**を選択する。
>
> ![Screenshot](./media/image38.png)

### **タスク 5: Deployment Share PropertiesとWindows PE設定を構成する。**

1.  Deployment Workbench中に**Deployment Shares**を拡張してから**MDT
    Deployment Share**を選択する。

2.  **MDT Deployment Shareを右クリックし、Properties**を選択する。

> ![Screenshot](./media/image39.png)

3.  **MDT Deployment Share
    Propertiesウィンドに、Generalタブで、**deployment
    shareが作成された時に提供された情報に注意する。 

> ![Screenshot](./media/image40.png)

4.  **Rulesタブを選択する。**

> RulesタブがCustomSettings.iniファイルの内容を表示します。この値が
> deployment shareの作成時にも提供された。
>
> ![Screenshot](./media/image41.png)

5.  **Windows PE**タブを選択する**。**

> Windows PEタブがWindows PE boot
> diskを作成するためのオプションを提供します。

6.  **Windows PEタブでPlatform**の横に**x64**を選択する。

7.  **Windows PE Customizationsセクション内にScratch space
    size**を横に**64**を選択する。

> ![Screenshot](./media/image42.png)

8.  **Featuresタブを選択して次の**Feature
    Packsの横のチェックボックスをオンにする：

    - DISM Cmdlets

    - Windows PowerShell

    - Microsoft Data Access Components (MDAC/ADO) support

> ![Screenshot](./media/image43.png)
>
> ![Screenshot](./media/image44.png)

9.  **Monitoring**タブを選択する**。**

10. **MonitoringタブでEnable monitoring for this deployment
    share**の横のチェックボックスをオンにする。

11. **MDT Deployment Share Properties**ウィンドに**OK**を選択する。

> ![Screenshot](./media/image45.png)

12. **MDT Deployment Shareを右クリックし、Update Deployment
    Share**を選択する。Update Deployment Share Wizardが開きます。

> ![Screenshot](./media/image46.png)

13. **Options**ページで**Optimize the boot image updating
    process**を選択してから**Next**を選択する。

> ![Screenshot](./media/image47.png)

14. **Summary**ページで**Next**を選択する。

> ![Screenshot](./media/image48.png)
>
> Deployment ShareがWindows
> PEファイルの更新と作成を開始します。この処理が完了するまでに数分かかります。

15. **Confirmation**ページで**、**処理が正常に完了したことを確認してから**Finish**を選択する。

> ![Screenshot](./media/image49.png)

### **タスク 6: MDTを使用してWindows 11を展開する**

1.   [**SEA-SVR2**](urn:gd:lg:a:select-vm)で、タスクバーで**Hyper-V
    Manager**を選択する。

> ![Screenshot](./media/image50.png)

2.  Hyper-V Manager内に**Virtual Switch Manager**を選択する。

> ![Screenshot](./media/image51.png)

3.  リストに**External**を選択してから**Create Virtual
    Switch**を選択する。

> ![Screenshot](./media/image52.png)

4.  **Virtual Switch Properties**ページ内に**Name**の下に[**External
    network**](urn:gd:lg:a:send-vm-keys)を入力して、**OK**を選択し、**Yes**を選択する。

> ![Screenshot](./media/image53.png)
>
> ![Screenshot](./media/image54.png)

5.  Hyper-V
    Manager中に**SEA-SVR2を選択してから**Actionsペインの中に**Newを選択して、Virtual
    Machine**を選択する。

> ![Screenshot](./media/image55.png)

6.  **Before you Begin**ページで**Next**を選択する。

> ![Screenshot](./media/image56.png)

7.  **Specify Name and
    Location**ページで**、Nameボックスの中に**!!**[SEA-WS4](urn:gd:lg:a:send-vm-keys)!!**を入力する。

8.  **Store the virtual machine in a different
    locationの横のチェックボックスをオンにし、** **Locationの横**!!**[E:\Labfiles\VirtualMachines](urn:gd:lg:a:send-vm-keys)!!**を入力する。**Next**を選択する。

> ![Screenshot](./media/image57.png)

9.  **Specify Generation**ページに**Generation
    2**が選択されていることを確認して**、Next**を選択する。

> ![Screenshot](./media/image58.png)

10. **Assign Memory**ページで**Startup
    memory**の横に!!**[8192](urn:gd:lg:a:send-vm-keys)!!**を入力してから**Next**を選択する。

> ![Screenshot](./media/image59.png)

11. **Configure Networking**ページで **Connection**の横に**、External
    Networkを選択して、Next**を選択する。

> ![Screenshot](./media/image60.png)

12. **Connect Virtual Hard Disk**ページで**Create a virtual hard
    disk**を選択して、以下を入力し**、Next**をクリックする：

    - Name: !!**[SEA-WS4.vhdx](urn:gd:lg:a:send-vm-keys)!!**

    - Location: !!**[E:\Labfiles\VirtualMachines](urn:gd:lg:a:send-vm-keys)!!**

    - Size: !!**[60](urn:gd:lg:a:send-vm-keys)!!**

> ![Screenshot](./media/image61.png)

13. **Installation OptionsページでInstall an operating system from a
    bootable image fileを選択して、以下を構成する：**

    - Image file
      (.iso): !!**[E:\DeploymentShare\Boot\LiteTouchPE_x64.iso](urn:gd:lg:a:send-vm-keys)!!**

> ![Screenshot](./media/image62.png)

14.  **Next、とそれからFinish**を選択する。

> ![Screenshot](./media/image63.png)

15. Hyper-V
    Manager内に**SEA-WS4**を右クリックし、**Settings**を選択する。

> ![Screenshot](./media/image64.png)

16. **Security**を選択してから**Enable Trusted Platform
    Module**の横にあるチェックボックスをオンにする。

> ![Screenshot](./media/image65.png)

17. **Processor**を選択して、バーチャルプロセッサ数を!!**[2](urn:gd:lg:a:send-vm-keys)!!**に変更する。

18. **OK** を選択してSettings dialog boxを閉じる。

> ![Screenshot](./media/image66.png)

19. Hyper-V
    Manager内に**SEA-WS4**を選択して、**Connect**を選択し、**Start**を選択する。

> ![Screenshot](./media/image67.png)
>
> ![Screenshot](./media/image68.png)

20. コンピュータが起動したら、キーボードの任意のキーを押して、MDT
    展開ウィザードを起動します。必要に応じてウィンドウを最大化します。

> ![Screenshot](./media/image69.png)

21. **Welcome**ページで**Run the Deployment Wizard to install a new
    Operating System**を選択する。

> ![Screenshot](./media/image70.png)

22. **Specify credentials for connecting to network
    sharesウィンドに、以下を入力し、OK**を選択する：

    - User Name: !!**[Administrator](urn:gd:lg:a:send-vm-keys)!!**

    - Password: !!**[Pa55w.rd](urn:gd:lg:a:send-vm-keys)!!**

    - Domain: !!**[Contoso](urn:gd:lg:a:send-vm-keys)!!**

> ![Screenshot](./media/image71.png)

23. **Task Sequence**ページで**Deploy Windows 11
    Enterprise**を選択してから**、Next**を選択する。

> ![Screenshot](./media/image72.png)

24. **Computer Details**ページで、**Computer
    name**の横に !!**[SEA-WS4](urn:gd:lg:a:send-vm-keys)!!を入力し、Next**を選択する。

> ![Screenshot](./media/image73.png)

25. **Move Data and Settings**ページで**Next**を選択する。

> ![Screenshot](./media/image74.png)

26. **User Data (Restore)**ページで**Next**を選択する。

> ![Screenshot](./media/image75.png)

27. **Locale and Time**ページで**Next**を選択する。

> ![Screenshot](./media/image76.png)

28. **Applications**ページで**Next**を選択する。

> ![Screenshot](./media/image77.png)

29. **Administrator
    Password**ページで**両方のテキストボックスに**!!**[Pa55w.rd](urn:gd:lg:a:send-vm-keys)!!を入力し、Next**を選択する。

> ![Screenshot](./media/image78.png)

30. **Ready**ページで**Begin**を選択する。

> ![Screenshot](./media/image79.png)
>
> インストールが開始されます。完了するまでに時間がかかるため、
> **必要に応じてインストール中に** SEA-WS4 が再起動されます。

31. **Deployment Workbench**に切り替える。

32. Deployment Workbench内に、**Deployment Shares**を拡張して、**MDT
    Deployment Share**を拡張する。

33. **Monitoring**を選択してから詳細ペインに**SEA-WS4**をダブルクリックする。

> ![Screenshot](./media/image80.png)
>
> デプロイ中に監視ステータスを確認する。
>
> ![A screenshot of a computer Description automatically
> generated](./media/image81.png)

34. **SEA-WS4**に切り替える。

35. インストールが完了すると、デスクトップが開き、デプロイが完了します。デプロイの要約で、
    **\[Finish\]** を選択します**。**

> ![Screenshot](./media/image82.png)

36. **SEA-WS4**をシャットダウンし**、**Virtual Machine Connection
    windowを閉じる。

> ![Screenshot](./media/image83.png)

37. Hyper-V
    Managerの中に**SEA-WS4**を右クリックしてから、**Settings**を選択する。

> ![Screenshot](./media/image84.png)

38. **Settings for SEA-WS4**の中に**SCSI Controller**を拡張してから**DVD
    Drive**を選択する。

39. 詳細ペインの中に、**Media**の下で**None**を選択してから**OK**を選択する。

> ![Screenshot](./media/image85.png)

40. **SEA-WS4**を右クリックし**、Checkpoint**を選択して**、**SEA-WS4の現在の状態のチェックポイントを作成する。 

> ![Screenshot](./media/image86.png)
>
> ![Screenshot](./media/image87.png)

41. [**SEA-SVR2**](urn:gd:lg:a:select-vm)で、**Hyper-V
    Manager**を閉じ**、Deployment Workbench**を閉じる。

42. **File Explorer**を開き、**DVD Drive
    Dを右クリックし、Eject**を選択する。

> ![Screenshot](./media/image88.png)
>
> ![Screenshot](./media/image89.png)

43. **File Explorer**を閉**じ、SEA-SVR2**からサインアウトする。

**結果**: この手順を完了すると、Microsoft Deployment Toolkit を使用して
Windows 11 ワークステーションを作成およびデプロイできます。
