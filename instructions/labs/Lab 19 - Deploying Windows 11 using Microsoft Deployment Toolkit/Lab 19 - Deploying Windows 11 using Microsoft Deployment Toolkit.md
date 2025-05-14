# **Laboratorio 19 - Implementar Windows 11 mediante Microsoft Deployment Toolkit**

**Resumen**

En este laboratorio, usará el Microsoft Deployment Toolkit para crear e
implementar un Windows 11 operating system image.

**Escenario**

Necesita implementar un nuevo Windows 11 virtual machine llamado
SEA-WS4. Decide usar Microsoft Deployment Toolkit para implementar el
sistema operativo a una máquina virtual creada en Hyper-V. Configurará
un nuevo Deployment Share en MDT y configurará el task sequence que
realice los pasos para implementar SEA-WS4.

### **Tarea 1: Cree un nuevo Deployment Share**

1.  Cambie a [**SEA-SVR2**](urn:gd:lg:a:select-vm), inicie sesión
    como !!**[Contoso\Administrator](urn:gd:lg:a:send-vm-keys)!!** Con
    la contraseña !!**[Pa55w.rd](urn:gd:lg:a:send-vm-keys)!!**

> ![Screenshot](./media/image1.png)

2.  En el taskbar, seleccione **File Explorer** y luego navegue
    a !!**[E:\Labfiles\ISOs](urn:gd:lg:a:send-vm-keys)!!**

> ![Screenshot](./media/image2.png)

3.  Haga clic derecho en **Win11_21H2_Eval.iso** y luego
    seleccione **Mount**. El ISO se monta como DVD Drive **D**.

> ![Screenshot](./media/image3.png)
>
> ![Screenshot](./media/image4.png)

4.  Cierre **File Explorer**.

5.  Seleccione **Start menu**, expanda **Microsoft Deployment Toolkit**,
    y luego seleccione **Deployment Workbench**.

> ![Screenshot](./media/image5.png)

6.  En el **Deployment Workbench**, haga clic derecho en **Deployment
    Shares** y luego seleccione **New Deployment Share**.

> ![Screenshot](./media/image6.png)
>
> Se abre el **New Deployment Share Wizard**.

7.  En la página **Path**, en **Deployment share path**, cambie el valor
    a !!**[E:\DeploymentShare](urn:gd:lg:a:send-vm-keys)!!** Y luego
    seleccione **Next**.

> ![Screenshot](./media/image7.png)

8.  En la página **Share**, tome nota del **Share name**, pero no lo
    cambie. Seleccione **Next**.

> ![Screenshot](./media/image8.png)

9.  En la página **Descriptive Name**, acepte el valor predeterminado y
    seleccione **Next**.

> ![Screenshot](./media/image9.png)

10. En la página **Options**, configure lo siguiente, y luego
    seleccione **Next**:

    - Ask to set the local Administrator password: **Enabled**

    - All other check boxes: **Disabled**

> ![Screenshot](./media/image10.png)

11. En la página **Summary**, revise la información y
    seleccione **Next**.

> ![Screenshot](./media/image11.png)

12. En la página **Confirmation**, asegure que se completó el proceso
    exitosamente y seleccione **Finish**.

> ![Screenshot](./media/image12.png)

13. En **Deployment Shares**, expanda la carpeta **MDT Deployment
    Share**.

> Tome nota de various nodes que se pueden configurar para el deployment
> share.

### **Tarea 2: Agregue los archivos Operating System files al Deployment Share**

1.  En el Deployment Workbench, expanda **Deployment Shares**,
    expanda **MDT Deployment Share**, y seleccione **Operating
    Systems**.

> ![Screenshot](./media/image13.png)

2.  Haga clic derecho en **Operating Systems** y seleccione **Import
    Operating System**. Se abre el Import Operating System Wizard.

> ![Screenshot](./media/image14.png)

3.  En el **Import Operating System Wizard**, en la página **OS Type**,
    seleccione **Full set of source files** y luego seleccione **Next**.

> ![Screenshot](./media/image15.png)

4.  En la página **Source**, en **Source Directory**,
    introduzca !!**[D:\\](urn:gd:lg:a:send-vm-keys)!!** Y luego
    seleccione **Next**.

> ![Screenshot](./media/image16.png)

5.  En la página **Destination**, cambie el destination directory name
    predeterminado a !!**[Windows 11 Enterprise
    x64](urn:gd:lg:a:send-vm-keys)!!** Y luego seleccione **Next**.

> ![Screenshot](./media/image17.png)

6.  En la página **Summary**, revise la información y
    seleccione **Next**.

> ![Screenshot](./media/image18.png)
>
> Se copian los operating system source files en el deployment share.

7.  En la página de confirmación **Confirmation**, asgure que se
    completó el proceso exitosamente y seleccione **Finish**.

> ![Screenshot](./media/image19.png)

8.  En el **Deployment Workbench**, con **Operating
    Systems** seleccionado, verifique que se ve el operating system.

### **Tarea 3: Agregue aplicaciones al Deployment Share**

1.  En el Deployment Workbench, expanda **Deployment Shares**,
    expanda **MDT Deployment Share**, y luego
    seleccione **Applications**.

2.  Haga clic derecho en **Applications** y luego seleccione **New
    Application**. Se abre el New Application Wizard.

> ![Screenshot](./media/image20.png)

3.  En el **New Application Wizard**, en la página **Application Type**,
    seleccione **Application with source files** y luego
    seleccione **Next**.

> ![Screenshot](./media/image21.png)

4.  En la página **Details**, configure lo siguiente, y luego
    seleccione **Next**:

    - Publisher: !!**[Microsoft](urn:gd:lg:a:send-vm-keys)!!**

    - Application Name: !!**[XML Notepad](urn:gd:lg:a:send-vm-keys)!!**

> ![Screenshot](./media/image22.png)

5.  En la página **Source**, en **Source directory**,
    introduzca !!**[E:\Labfiles\Apps](urn:gd:lg:a:send-vm-keys)!!** Y
    luego seleccione **Next**.

> ![Screenshot](./media/image23.png)

6.  En la página **Destination**, acepte el destination directory name
    predeterminado y luego seleccione **Next**.

> ![Screenshot](./media/image24.png)

7.  En la página **Command Details**, en **Command
    line** introduzca !!**[XmlNotepadSetup.msi
    /q](urn:gd:lg:a:send-vm-keys)!!** y seleccione **Next**.

> ![Screenshot](./media/image25.png)

8.  En la página **Summary**, revise la información y
    seleccione **Next**.

> ![Screenshot](./media/image26.png)

9.  En la página **Confirmation**, asegure que se completó el proceso
    exitosamente y seleccione **Finish**.

### **Tarea 4: Cree un MDT Task Sequence**

1.  En el Deployment Workbench, expanda **Deployment Shares**,
    expanda **MDT Deployment Share**, y seleccione **Task Sequences**.

2.  Haga clic derecho **Task Sequences** y seleccione **New Task
    Sequence**. Se abre el **New Task Sequence Wizard**.

> ![Screenshot](./media/image27.png)

3.  En la página **General Settings**, configure lo siguiente y
    seleccione **Next**:

    - Task sequence ID: !!**[001](urn:gd:lg:a:send-vm-keys)!!**

    - Task sequence name: !!**[Deploy Windows 11
      Enterprise](urn:gd:lg:a:send-vm-keys)!!**

> ![Screenshot](./media/image28.png)

4.  En la página **Select Template**, seleccione **Standard Client Task
    Sequence**, y luego seleccione **Next**.

> ![Screenshot](./media/image29.png)

5.  En la página **Select OS**, seleccione **Windows 10 Enterprise
    Evaluation** y luego seleccione **Next**.

> ![Screenshot](./media/image30.png)

6.  En la página **Specify Product Key**, seleccione **Do not specify a
    product key at this time**, y luego seleccione **Next**.

> ![Screenshot](./media/image31.png)

7.  En la página **OS Settings**, configure lo siguiente y
    seleccione **Next**:

    - Full Name: !!**[User](urn:gd:lg:a:send-vm-keys)!!**

    - Organization: !!**[Contoso
      Corporation](urn:gd:lg:a:send-vm-keys)!!**

    - Internet Explorer Home
      Page: !!**[about:blank](urn:gd:lg:a:send-vm-keys)!!**

> ![Screenshot](./media/image32.png)

8.  En la página **Admin Password**, seleccione **Use the specified
    local Administrator password**, e
    introduzca !!**[Pa55w.rd](urn:gd:lg:a:send-vm-keys)!!** en ambos
    cuadros de textos. Seleccione **Next**.

> ![Screenshot](./media/image33.png)

9.  En la página **Summary**, revise la información y
    seleccione **Next**.

> ![Screenshot](./media/image34.png)

10. En la página **Confirmation**, asegure que se completa el proceso
    exitosamente y seleccione **Finish**.

> ![Screenshot](./media/image35.png)

11. En el **Deployment Workbench**, con **Task Sequences** seleccionado,
    verifique que se muestra el **Deploy Windows 11 Enterprise** task
    sequence.

> ![Screenshot](./media/image36.png)

12. Haga clic en el **Deploy Windows 11 Enterprise** task sequence, y
    luego seleccione **Properties**.

> ![Screenshot](./media/image37.png)

13. Seleccione la pestaña **Task Sequence**.

14. Expanda el **Validation** node y seleccione **Validate**.

15. En la página **Properties**, quite las verificaciones junto
    a **Ensure minimum memory** y **Ensure minimum processor speed**.

> No haga ningún otro cambio.

16. En la ventana **Deploy Windows 11 Enterprise Properties**,
    seleccione **OK**.

> ![Screenshot](./media/image38.png)

### **Tarea 5: Configure los Deployment Share Properties y Windows PE settings**

1.  En el Deployment Workbench, expanda **Deployment Shares**, y
    seleccione **MDT Deployment Share**.

2.  Haga clic en **MDT Deployment Share** y luego
    seleccione **Properties**.

> ![Screenshot](./media/image39.png)

3.  En la ventana **MDT Deployment Share Properties**, en la
    pestaña **General**, tome nota de la información que se proporcionó
    cuando se creó el deployment share.

> ![Screenshot](./media/image40.png)

4.  Seleccione la pestaña **Rules**.

> La perstaña Rules muestra el contenido del archivo CustomSettings.ini.
> También se proporcionaron estos valores durante la creación del
> deployment share.
>
> ![Screenshot](./media/image41.png)

5.  Seleccione la pestaña **Windows PE**.

> La pestaña Windows PE proporciona opciones de crear un Windows PE boot
> disk.

6.  En la pestaña **Windows PE**, junto a **Platform**,
    seleccione **x64**.

7.  En la sección **Windows PE Customizations**, junto a **Scratch space
    size**, seleccione **64**.

> ![Screenshot](./media/image42.png)

8.  Seleccione la pestaña **Features** y luego seleccione las casillas
    junto a los siguientes Feature Packs:

    - DISM Cmdlets

    - Windows PowerShell

    - Microsoft Data Access Components (MDAC/ADO) support

> ![Screenshot](./media/image43.png)
>
> ![Screenshot](./media/image44.png)

9.  Seleccione la pestaña **Monitoring**.

10. En la pestaña **Monitoring**, seleccione las casillas junto
    a **Enable monitoring for this deployment share**.

11. En la ventana **MDT Deployment Share Properties**,
    seleccione **OK**.

> ![Screenshot](./media/image45.png)

12. Haga clic derecho en **MDT Deployment Share** y luego
    seleccione **Update Deployment Share**. Se abre Update Deployment
    Share Wizard.

> ![Screenshot](./media/image46.png)

13. En la página **Options**, seleccione **Optimize the boot image
    updating process** y luego seleccione **Next**.

> ![Screenshot](./media/image47.png)

14. En la página **Summary**, seleccione **Next**.

> ![Screenshot](./media/image48.png)
>
> El Deployment Share inicia a actualizar y crear los archivos Windows
> PE. Esto tardará unos minutos en completar.

15. En la página **Confirmation**, asegure que se completa el proceso y
    seleccione **Finish**.

> ![Screenshot](./media/image49.png)

### **Tarea 6: Implemente Windows 11 con MDT**

1.  En [**SEA-SVR2**](urn:gd:lg:a:select-vm), en el taskbar, seleccione
    **Hyper-V Manager**.

> ![Screenshot](./media/image50.png)

2.  En Hyper-V Manager, seleccione **Virtual Switch Manager**.

> ![Screenshot](./media/image51.png)

3.  Seleccione **External** en la lista y haga clic en **Create Virtual
    Switch**.

> ![Screenshot](./media/image52.png)

4.  En la página **Virtual Switch Properties**, en **Name**,
    introduzca [**External network**](urn:gd:lg:a:send-vm-keys),
    seleccione **OK**, y luego seleccione **Yes**.

> ![Screenshot](./media/image53.png)
>
> ![Screenshot](./media/image54.png)

5.  En Hyper-V Manager, seleccione **SEA-SVR2** y en el panel Actions,
    seleccione **New** y luego seleccione **Virtual Machine**.

> ![Screenshot](./media/image55.png)

6.  En la página **Before you Begin**, seleccione **Next**.

> ![Screenshot](./media/image56.png)

7.  En la página **Specify Name and Location**, en el
    cuadro **Name** tecle !!**[SEA-WS4](urn:gd:lg:a:send-vm-keys)!!**.

8.  Seleccione la casilla junto a **Store the virtual machine in a
    different location** y junto a **Location** tecle
    !!**[E:\Labfiles\VirtualMachines](urn:gd:lg:a:send-vm-keys)!!**.
    Seleccione **Next**.

> ![Screenshot](./media/image57.png)

9.  En la página **Specify Generation**, asegure que se
    selecciona **Generation 2** y luego seleccione **Next**.

> ![Screenshot](./media/image58.png)

10. En la página **Assign Memory**, junto a **Startup
    memory** tecle !!**[8192](urn:gd:lg:a:send-vm-keys)!!** y luego
    seleccione **Next**.

> ![Screenshot](./media/image59.png)

11. En la página **Configure Networking**, junto a **Connection**,
    seleccione **External Network** y luego seleccione **Next**.

> ![Screenshot](./media/image60.png)

12. En la página **Connect Virtual Hard Disk**, seleccione **Create a
    virtual hard disk** e introduzca los siguiente y haga clic
    en **Next**:

    - Name: !!**[SEA-WS4.vhdx](urn:gd:lg:a:send-vm-keys)!!**

    - Location: !!**[E:\Labfiles\VirtualMachines](urn:gd:lg:a:send-vm-keys)!!**

    - Size: !!**[60](urn:gd:lg:a:send-vm-keys)!!**

> ![Screenshot](./media/image61.png)

13. En la página **Installation Options**, seleccione **Install an
    operating system from a bootable image file** y configure lo
    siguiente:

    - Image file
      (.iso): !!**[E:\DeploymentShare\Boot\LiteTouchPE_x64.iso](urn:gd:lg:a:send-vm-keys)!!**

> ![Screenshot](./media/image62.png)

14. Seleccione **Next** y luego **Finish**.

> ![Screenshot](./media/image63.png)

15. En Hyper-V Manager, haga clic en **SEA-WS4**, y
    seleccione **Settings**.

> ![Screenshot](./media/image64.png)

16. Seleccione **Security**, y seleccione la casilla junto a **Enable
    Trusted Platform Module**.

> ![Screenshot](./media/image65.png)

17. Seleccione **Processor**, y luego cambie el número de virtual
    processors a !!**[2](urn:gd:lg:a:send-vm-keys)!!**.

18. Seleccione **OK** para cerrar el cuadro de diálogo Settings.

> ![Screenshot](./media/image66.png)

19. En Hyper-V Manager, seleccione **SEA-WS4**, seleccione **Connect**,
    y luego seleccione **Start**.

> ![Screenshot](./media/image67.png)
>
> ![Screenshot](./media/image68.png)

20. Como empieza el computer, presione cualquier botón para invocar el
    MDT Deployment Wizard. Maximice la ventana como necesario.

> ![Screenshot](./media/image69.png)

21. En la página **Welcome**, seleccione **Run the Deployment Wizard to
    install a new Operating System**.

> ![Screenshot](./media/image70.png)

22. En la ventana **Specify credentials for connecting to network
    shares**, introduzca lo siguiente y seleccione **OK**:

    - User Name: !!**[Administrator](urn:gd:lg:a:send-vm-keys)!!**

    - Password: !!**[Pa55w.rd](urn:gd:lg:a:send-vm-keys)!!**

    - Domain: !!**[Contoso](urn:gd:lg:a:send-vm-keys)!!**

> ![Screenshot](./media/image71.png)

23. En la página **Task Sequence**, seleccione **Deploy Windows 11
    Enterprise** y luego seleccione **Next**.

> ![Screenshot](./media/image72.png)

24. En la página **Details**, junto a **Computer
    name** introduzca !!**[SEA-WS4](urn:gd:lg:a:send-vm-keys)!!** Y
    luego seleccione **Next**.

> ![Screenshot](./media/image73.png)

25. En la página **Move Data and Settings**, seleccione **Next**.

> ![Screenshot](./media/image74.png)

26. En la página **User Data (Restore)**, seleccione **Next**.

> ![Screenshot](./media/image75.png)

27. En la página **Locale and Time**, seleccione **Next**.

> ![Screenshot](./media/image76.png)

28. En la página **Applications**, seleccione **Next**.

> ![Screenshot](./media/image77.png)

29. En la página **Administrator Password**,
    introduzca !!**[Pa55w.rd](urn:gd:lg:a:send-vm-keys)!!** en ambos
    cuadros de textos y luego seleccione **Next**.

> ![Screenshot](./media/image78.png)

30. En la página **Ready**, seleccione **Begin**.

> ![Screenshot](./media/image79.png)
>
> Se inicia la instalación. Llevará un poco de tiempo en completar y
> reiniciará **SEA-WS4** durante la instalación como sea necesario.

31. Cambie a **Deployment Workbench**.

32. En el Deployment Workbench, expanda **Deployment Shares**, y
    expanda **MDT Deployment Share**.

33. Seleccione **Monitoring** y en el panel de detalles, haga doble clic
    en **SEA-WS4**.

> ![Screenshot](./media/image80.png)
>
> Revise el monitoring status durante la implementación.
>
> ![A screenshot of a computer Description automatically
> generated](./media/image81.png)

34. Cambie a **SEA-WS4**.

35. Después de que la instalación sea completa, se abre desktop y
    finaliza la implementación. En el deployment summary,
    seleccione **Finish**.

> ![Screenshot](./media/image82.png)

36. Cierre **SEA-WS4** y cierre la ventana Virtual Machine Connection.

> ![Screenshot](./media/image83.png)

37. En Hyper-V Manager, haga clic en **SEA-WS4** y
    seleccione **Settings**.

> ![Screenshot](./media/image84.png)

38. En el **Settings for SEA-WS4**, expanda **SCSI Controller** y
    seleccione **DVD Drive**.

39. En el panel de detalles, en **Media**, seleccione **None**, y luego
    seleccione **OK**.

> ![Screenshot](./media/image85.png)

40. Haga clic derecho en **SEA-WS4** y seleccione **Checkpoint** para
    crear un checkpoint del estado actual de SEA-WS4.

> ![Screenshot](./media/image86.png)
>
> ![Screenshot](./media/image87.png)

41. En [**SEA-SVR2**](urn:gd:lg:a:select-vm), cierre **Hyper-V
    Manager** y cierre el **Deployment Workbench**.

42. Abra **File Explorer**, haga clic derecho **DVD Drive D** y luego
    seleccione **Eject**.

> ![Screenshot](./media/image88.png)
>
> ![Screenshot](./media/image89.png)

43. Cierre **File Explorer** y cierre sesión de **SEA-SVR2**.

**Resultados**: Después de completar este ejercicio, habrá usado el
Microsoft Deployment Toolkit para crear e implementar un Windows 11
workstation.
