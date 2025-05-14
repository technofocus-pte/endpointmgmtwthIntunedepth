Laboratorio 22: Configurar Cloud Attach y Co-Management mediante
Configuration Manager

**Resumen**

En este laboratorio, habilitará Cloud Attach y configure Co-Management
mediante Microsoft Endpoint Configuration Manager y Microsoft Intune.

**Prerrequisitos**

Se debe completar los siguientes laboratorios antes de este laboratorio:

- Laboratorio 01-Gestionar Identities en Microsoft Entra ID

- Laboratorio 02-Sincronizar Identities mediante Azure AD Connect

- Laboratorio 03-Configurar y gestionar Microsoft Entra ID join

- Laboratorio 05-Gestione Device Enrollment en Intune

**Escenario**

Contoso tiene un Microsoft Endpoint Configuration Manager implementation
y Microsoft Intune. Necesita configurar la intregración entre dos
servicios y habilitar co-gestión para sus dispositivos Windows
gestionados. Habilitará Cloud Attach, configurará co-management, y luego
validará las configuraciones mediante SEA-CL1.

Tarea 1: Prepare el entorno

1.  Cambie a [***SEA-SVR1***](urn:gd:lg:a:select-vm) e inicie sesión
    como [**Contoso\Administrator**](urn:gd:lg:a:send-vm-keys) con la
    contraseña !\![**Pa55w.rd**](urn:gd:lg:a:send-vm-keys)!! .

2.  Desde Server Manager, seleccione **Tools**, y luego
    seleccione **Active Directory Users and Computers**.

> ![](./media/image1.png)

3.  En el panel de navegación, seleccione **Seattle Clients**.

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)

4.  Haga clic derecho en **SEA-CL1** y luego seleccione **Move**.

> ![A computer screen shot of a computer Description automatically
> generated](./media/image3.png)

5.  En el cuadro de diálogo **Move**, seleccione **Entra clients** y
    luego seleccione **OK**.

> ![A screenshot of a computer Description automatically
> generated](./media/image4.png)

6.  Cierre **Active Directory Users and Computers**.

7.  En el taskbar, haga clic derecho en **Start** y seleccione **Windows
    Powershell (Admin)**.

> ![A screenshot of a computer Description automatically
> generated](./media/image5.png)

8.  En la ventana **Windows PowerShell**, tecle el siguiente command, y
    presione **Enter**:

> !!**Start**-ADSyncSyncCycle -PolicyType **Initial**!!
>
> ![A screenshot of a computer screen Description automatically
> generated](./media/image6.png)

9.  Cierre la ventana PowerShell.

10. Cambie a [***SEA-CL1***](urn:gd:lg:a:select-vm).

11. En el taskbar, haga clic derecho **Start**, seleccione **Shut down
    or sign out** y luego seleccione **Restart**.

> ![](./media/image7.png)
>
> **Ojo**: El reboot activará el hybrid Azure AD join en SEA-CL1.

12. Después de que se reiniciará [***SEA-CL1***](urn:gd:lg:a:select-vm),
    inicie sesión
    como [**Contoso\Administrator**](urn:gd:lg:a:send-vm-keys) con la
    contraseña [**Pa55w.rd**](urn:gd:lg:a:send-vm-keys).

13. En el taskbar, haga clic derecho **Start** y seleccione **Windows
    Terminal (Admin)**.

> ![](./media/image8.png)

14. En la ventana **Windows PowerShell**, tecle el siguinte command, y
    presione **Enter**:

> !!dsregcmd /**status**!!

15. En el output en **Device State**, verifique que se
    ven **AzureAdJoined : YES** y **DomainJoined : YES**.

> ![](./media/image9.png)
>
> **Ojo**: Se no se ha unido el dispositivo a Azure AD, espere a que se
> complete el Azure AD Connect y reinicie SEA-CL1 de nuevo.

16. Cierre todas las ventanas en [***SEA-CL1***](urn:gd:lg:a:select-vm).

Tarea 2: Cree un device collection

1.  Cambie a [***SEA-CFG1***](urn:gd:lg:a:select-vm), inicie sesión
    como [**Contoso\Administrator**](urn:gd:lg:a:send-vm-keys) con la
    contraseña [**Pa55w.rd**](urn:gd:lg:a:send-vm-keys).

2.  En el taskbar, seleccione **Configuration Manager Console**. Se abre
    el Microsoft Endpoint Configuration Manager console.

> ![A screenshot of a computer Description automatically
> generated](./media/image10.png)

3.  En el **Assets and Compliance** workspace, seleccione **Device
    Collections**.

4.  Haga clic derecho en **Device Collections** y luego
    seleccione **Create Device Collection**. Se abre el Create Device
    Collection Wizard.

> ![](./media/image11.png)

5.  En la página **General**, configure el siguiente y luego
    seleccione **Next**:

    - Name: !\![**Co-managed Devices**](urn:gd:lg:a:send-vm-keys)!!

    - Limiting collection: **All Desktop and Server Clients**

> ![](./media/image12.png)
>
> ![](./media/image13.png)
>
> ![](./media/image14.png)

6.  En la página **Membership Rules**, seleccione **Next**.

> ![A screenshot of a computer Description automatically
> generated](./media/image15.png)

7.  En el Configuration Manager warning, seleccione **OK**. Agregará un
    direct member más tarde.

> ![A screenshot of a computer error Description automatically
> generated](./media/image16.png)

8.  En la página **Summary**, seleccione **Next** y en la
    página **Completion**, seleccione **Close**.

> ![A screenshot of a computer Description automatically
> generated](./media/image17.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image18.png)

Tarea 3: Asigne un dispositivo a un Collection existente

1.  En el **Assets and Compliance** workspace, seleccione **Devices**.

> Tome nota de los dispositivos enlistados. Cualquier dispositivo que
> tenga un círculo verde con una verificación blanca es activo.

2.  En el panel de detalles, seleccione **SEA-CL1**.

3.  Haga clic en **SEA-CL1**, apunte a **Add Selected Items**, y luego
    seleccione **Add Selected Items to Existing Device Collection**.

> ![](./media/image19.png)

4.  En el cuadro de diálogo **Select Collection**,
    seleccione **Co-managed Devices**, y seleccione **OK**.

> ![](./media/image20.png)

5.  Para verificar, en el **Assets and Compliance** workspace,
    seleccione **Device Collections** y haga doble clic en **Co-managed
    Devices**.

> ![](./media/image21.png)
>
> ![](./media/image22.png)
>
> Se debe enlistar **SEA-CL1** como un miembro de esta colección.

Tarea 4: Cloud attach Endpoint Configuration Manager

1.  En el Microsoft Endpoint Configuration Manager console, seleccione
    el **Administration** workspace.

> ![](./media/image23.png)

2.  En el **Administration** workspace, expanda **Cloud Services** y
    luego seleccione **Cloud Attach**.

> ![A screenshot of a computer Description automatically
> generated](./media/image24.png)

3.  En el ribbon, seleccione **Configure Cloud Attach**. Se abre
    el **Cloud Attach Configuration Wizard**.

> ![](./media/image25.png)
>
> ![](./media/image26.png)

4.  En el **Cloud Attach Configuration Wizard**, en la página **Cloud
    attach**, seleccione **Sign In**.

5.  Inicie sesión
    como [**admin@M365x19242953.onmicrosoft.com**](urn:gd:lg:a:send-vm-keys) con
    la contraseña [**9whL~;H8ke=D1^95%D**](urn:gd:lg:a:send-vm-keys).

6.  En la página **Cloud attach**, seleccione **Customize settings**, y
    seleccione **Next**.

> ![](./media/image27.png)

7.  En la alerta **Create AAD Application**, seleccione **Yes**.

> ![A screenshot of a computer Description automatically
> generated](./media/image28.png)

8.  En la página **Configure upload**, acepte el predeterminado y
    seleccione **Next**.

> ![A screenshot of a computer Description automatically
> generated](./media/image29.png)

9.  En la página **Enablement**, junto a **Automatic enrollment in
    Intune**, seleccione **Pilot**.

10. En la página **Enablement**, junto a **Intune Auto Enrollment**,
    seleccione **Browse**.

> ![](./media/image30.png)

11. En el cuadro de diálogo **Select Collection**,
    seleccione **Co-managed Devices** y luego seleccione **OK**.
    Seleccione **Next**.

> ![A screenshot of a computer Description automatically
> generated](./media/image31.png)

12. En la página **Summary**, seleccione **Next** y luego la
    página **Completion**, seleccione **Close**.

> ![A screenshot of a computer Description automatically
> generated](./media/image32.png)

Tarea 5: Configure los Workloads

1.  En el Microsoft Endpoint Configuration Manager console, seleccione
    el **Administration** workspace.

2.  En el **Administration** workspace, expanda **Cloud Services** y
    luego seleccione **Cloud Attach**.

3.  En el panel de detalles, seleccione **CoMgmtSettingsProd** y luego
    en el ribbon seleccione **Properties**.

> ![A screenshot of a computer Description automatically
> generated](./media/image33.png)
>
> Se abre el **CoMgmtSettingsProd Properties** box.

4.  Seleccione **Workloads**. En la página **Workloads**, arrastre el
    slider a **Pilot Intune** para los siguientes workloads:

    - **Compliance policies**

    - **Client apps**

    - **Windows Update policies**

> ![](./media/image34.png)

5.  Seleccione el **Staging page**. En el **Staging**,
    seleccione **Browse** junto a **Compliance policies**, **Client
    Apps**, y **Windows Update Policies** y seleccione el **Co-managed
    Devices** collection para cada workload.

6.  Seleccione **OK** para cerrar el cuadro **CoMgmtSettingsProd
    Properties**.

> ![](./media/image35.png)

Tarea 6: Valide que SEA-CL1 es co-managed

1.  Cambie a [***SEA-SVR1***](urn:gd:lg:a:select-vm).

2.  En el taskbar seleccione **Microsoft Edge**, en el address bar
    tecle [**https://entra.microsoft.com**](https://entra.microsoft.com),
    y presione **Enter**.

3.  Inicie sesión como el
    usuario [**admin@M365x19242953.onmicrosoft.com**](urn:gd:lg:a:send-vm-keys),
    y use la contraseña.

4.  Si aparece el prompt **Stay signed in?**, seleccione **No**.

> Se abre el Microsoft Entra admin center.

5.  En el Microsoft Entra admin center, en el panel de navegación,
    seleccione **Identity.**

> ![](./media/image36.png)

6.  En la página **Devices|All devices**, Verifique que se
    enlista **SEA-CL1** y que **Join Type** es **Microsoft Entr hybrid
    Join**.

> ![](./media/image37.png)

7.  En Microsoft Edge abre otra pestaña y
    tecle [**https://intune.microsoft.com**](https://intune.microsoft.com) en
    el address bar, and y presione **Enter**.

8.  En el panel de navegación, seleccione **Devices** y luego
    seleccione **All devices**.

9.  Verifique que se enlista **SEA-CL1** con la configuración **Managed
    by** se establece como **Co-managed**.

> ![](./media/image38.png)
>
> Puede tardar un poco en aparecer. Actualice el panel de detalles como
> sea necesario. La máquina aparece con un numbre diferente, haga clic
> en el dispositivo para confirmar que muestra **SEA-CL1**.

10. Seleccione **SEA-CL1** y en el panel de detalles para mostrar la
    información relacionada con el estado de Co-management.

11. Cierre Microsoft Edge.

**Resultados**: Después de completar el ejercicio, habrá habilitado
Cloud Attach y configurado co-management mediante Microsoft Endpoint
Configuration Manager y Microsoft Intune.
