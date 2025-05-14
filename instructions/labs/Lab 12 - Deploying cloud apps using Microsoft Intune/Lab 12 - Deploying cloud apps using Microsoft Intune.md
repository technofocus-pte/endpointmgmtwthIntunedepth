Laboratorio 12 - Implementar cloud apps mediante Microsoft Intune

**Resumen**

En este laboratorio, crea e implementa cloud-based apps mediante Intune
y el Company Portal Website.

**Prerrequisitos**

Se debe completar los siguientes laboratorios antes de este laboratorio:

- Laboratorio \#1-Gestionar Identities en Microsoft Entra ID

- Laboratorio \#2-Sincronizar Identities mediante Microsoft Entra
  Connect

- Laboratorio \#5-Gestione Device Enrollment en Microsoft Intune

- Laboratorio \#6-Inscripción de dispositivos en Microsoft Intune

- Laboratorio \#7-Crear e implementar los Configuration Profiles

**Ojo**: También necesita un celular que puede recibir mensajes de texto
para asegurar la autenticación del inicio de sesión de Windows Hello a
Microsoft Entra ID.

Ejercicio 1: Agregue un Microsoft Store App a Microsoft Intune

**Escenario**

Usa Microsoft Intune para gestionar desktops y aplicaciones para Contoso
Corporation. El departamento de Research suele conectarse a vario
servidores para realizar tareas y ha pedido que el Microsoft Remote
Desktop app sea disponible para los miembros de Research para instalar
como sea necesario. El Microsoft Remote Desktop está disponible en
Microsoft Store, pero decide agregar la aplicación a Intune para que los
usuarios puedan accederla desde el sitio web del Company Portal. Un
Research member llamado Aaron Nicholls ha aceptado probar el proceso de
instalación después de que publique la aplicación al portal.

Tarea 1: Agregue Microsoft Remote Desktop a Microsoft Intune

1.  En [***SEA-SVR1***](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17),
    si es necesario, inicie sesión
    como [**Contoso\Administrator**](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17) con
    la contraseña !\![**Pa55w.rd**](urn:gd:lg:a:select-vm)!!  y
    cierre **Server Manager**.

2.  En el taskbar, seleccione **Microsoft Edge**.

3.  En Microsoft Edge, tecle !!
    [**https://Intune.microsoft.com**](urn:gd:lg:a:select-vm) !! en el
    address bar, y luego presione **Enter**.

4.  Inicie sesión con las Office 365 Tenant credentials desde la pestaña
    Home.

5.  En la página **Microsoft Intune admin center**, seleccione **Apps**.

> ![A screenshot of a computer Description automatically
> generated](./media/image1.png)

6.  En la página **Apps**, en el panel de navegación, seleccione **All
    apps**.

7.  En el panel de details, seleccione **+Add**.

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)

8.  En la página **Select app type**, haga clic en el menú despegable, y
    luego seleccione **Microsoft store app (new)**.

> ![A screenshot of a computer Description automatically
> generated](./media/image3.png)
>
> Lea la información sobre la aplicación Microsoft store y haga clic
> en **Select**. Se abre la página **Add App**.

9.  En la página **App information**, haga clic en el enlace **Search
    the** **Microsoft Store app (new)**.

> ![A screenshot of a computer Description automatically
> generated](./media/image4.png)

10. En la pestaña **Search the** **Microsoft Store app (new)** busque y
    seleccione !\![**Microsoft Remote
    Desktop**](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17)!!
    y haga clic en el botón Select.

> ![A screenshot of a computer Description automatically
> generated](./media/image5.png)

11. Volviendo a la pestaña Add App, introduzca la siguiente información
    y seleccione **Next**:

    - Category: **Business**

    - Show this as a featured app in the Company Portal: **Yes**

> ![A screenshot of a computer Description automatically
> generated](./media/image6.png)

12. En la pestaña **Assignments**, haga clic en **+ Add group**

> ![A screenshot of a computer Description automatically
> generated](./media/image7.png)

13. En la página **Select groups**, seleccione el **Research,
    Sales** group, y haga clic en **Select**.

> ![A screenshot of a computer Description automatically
> generated](./media/image8.png)

14. Haga clic en el botón **Next**.

> ![A screenshot of a computer Description automatically
> generated](./media/image9.png)

15. En la pestaña Review + create, haga clic en el botón **Create**.

> ![](./media/image10.png)

16. Se abre la página Microsoft Remote Desktop.

> Tome nota de Properties, Device install status, y User install status
> nodes.
>
> ![A screenshot of a computer Description automatically
> generated](./media/image11.png)

Tarea 2: Oblique el policy synchronization desde el Microsoft Intune
console

1.  En el **Microsoft Intune admin center**, seleccione **Devices** y
    luego seleccione **All devices**.

2.  En el panel de details, seleccione **SEA-WS1**.

> ![A screenshot of a computer Description automatically
> generated](./media/image12.png)

3.  En el **SEA-WS1** blade, seleccione **Sync** y cuando se le pide,
    seleccione **Yes**.

> ![A screenshot of a computer Description automatically
> generated](./media/image13.png)
>
> Microsoft Intune contactará al dispositivo y sincronizar todas las
> políticas. Puede tardar unos 5 minutos.

Tarea 3: Instale una aplicación desde el Company Portal Website

1.  Inicie sesión en  como **Cindy White** con sus credenciales
    !!**Cindy@M365xXXXXXX.onmicrosoft.com**!! Con la contraseña
    !!**P@55w.rd1234**!! O con el PIN !!**102938**!!

2.  En el taskbar, seleccione **Microsoft Edge**.

3.  Si es necesario, en la página **Welcome to Microsoft Edge**,
    seleccione **Confirm and continue**. Cierre la página Welcome.

4.  En el address bar navegue
    a !\![**https://portal.manage.microsoft.com**](urn:gd:lg:a:send-vm-keys)!!

5.  Inicie sesión como !!**Cindy@M365xXXXXXX.onmicrosoft.com**!!

> ![](./media/image14.png)

6.  En el Contoso web portal, seleccione **Devices**.

> ![A screenshot of a computer Description automatically
> generated](./media/image15.png)

7.  En la página Devices, seleccione **Tap here to tell us which device
    you're using or add a new device**.

> ![](./media/image16.png)

8.  En el cuadro de diálogo **Which device are you using**, seleccione
    la opción junto a **SEA-WS1**, y haga clic en el botón **Select**.

> ![A screenshot of a computer Description automatically
> generated](./media/image17.png)
>
> Note que se cambia el mensaje a Apps will be installed
> onto: **SEA-WS1**
>
> ![](./media/image18.png)

9.  En la esquina superior izquierda, seleccione el botón de navegación
    y luego seleccione **Downloads & updates**.

> ![A screenshot of a computer Description automatically
> generated](./media/image19.png)

10. Desde los resultados enlistados, averigüe el estado, la aplicación
    **Microsoft Remote Desktop** debe aparecer como **Installed**.

> Ojo – puede tardar unos 10-20 minutos para que aparezca la aplicación.
>
> ![A screenshot of a computer Description automatically
> generated](./media/image20.png)

11. Haga clic en el **Start** **Menu** y verifique que se ve **Remote
    Desktop** en el Start menu.

> ![A screenshot of a computer Description automatically
> generated](./media/image21.png)

**Resultados**: Después de completar el ejercicio, habrá agregado e
instalado un Microsoft Store App desde Microsoft Intune.

Ejercicio 2: Configure e implemente Microsoft 365 Apps desde Microsoft
Intune

**Escenario**

Todos los usuarios de Research department at Contoso requieren Microsoft
365 Apps. Se le ha pedido implementar las versiones 64-bit de Microsoft
Excel, Outlook, PowerPoint y Word a sus dispositivos Windows. También
tiene que asegurar que están configurados para las actualizaciones
Current Channel.

Tarea 1: Verifique las aplicaciones instaladas en SEA-WS1

1.  En [***SEA-WS1***](urn:gd:lg:a:send-vm-keys), en el taskbar,
    seleccione **Start** y luego seleccione la apliacación **Settings**.

> ![A screenshot of a computer Description automatically
> generated](./media/image22.png)

2.  En la página **Settings app**, seleccione **Apps**, y luego **Apps &
    features**.

> ![A screenshot of a computer Description automatically
> generated](./media/image23.png)
>
> Verifique que no esté ennumerado **Microsoft 365 Apps for enterprise -
> en-us**.
>
> ![A screenshot of a computer Description automatically
> generated](./media/image24.png)

3.  Cierre todas las ventanas abiertas.

Tarea 2: Agregue las aplicaciones Microsoft 365 a Microsoft Intune

1.  Cambie a [***SEA-SVR1***](urn:gd:lg:a:send-vm-keys), cuando está en
    el **Microsoft Intune admin center**, seleccione **Apps**.

2.  En el **Apps | Overview** blade, seleccione **All Apps**. En el
    panel details, seleccione **+Add**.

> ![A screenshot of a computer Description automatically
> generated](./media/image25.png)

3.  En el **Select app type** blade, en **Microsoft 365 Apps**,
    seleccione **Windows 10 and later**, y haga clic en **Select**.

> ![A screenshot of a computer Description automatically
> generated](./media/image26.png)

4.  En el **Add Microsoft 365 Apps** blade, configure las siguientes
    opciones y seleccione **Next**:

    - Suite Name: !\![**Microsoft 365 Apps
      (Research)**](urn:gd:lg:a:select-vm)!!

    - Suite Description: !\![**Microsoft 365 Apps for the Research
      department at Contoso**](urn:gd:lg:a:select-vm) !!
      (Seleccione **Edit Description** para introducir esta imagen.)

> ![A screenshot of a computer Description automatically
> generated](./media/image27.png)

5.  En la pestaña **Configure app suite**, expanda el dropdown **Select
    Office apps**, seleccione las siguientes aplicaciones Office:

    - Excel

    - Outlook

    - PowerPoint

    - Word

> ![A screenshot of a computer Description automatically
> generated](./media/image28.png)

6.  En la pestaña **Configure app suite**, configure las siguientes
    opciones y seleccione **Next**:

    - Architecture: **64-bit**

    - Default file format: **Office Open XML Format**

    - Update channel: **Current Channel**

    - Accept the Microsoft Software License Terms on behalf of
      users: **Yes**

> ![A screenshot of a computer Description automatically
> generated](./media/image29.png)

7.  En la pestaña **Assignments**, en la sección **Required**,
    seleccione **Add group.**

> ![A screenshot of a computer Description automatically
> generated](./media/image30.png)

8.  En el **Select groups** blade, seleccione **Research**, y
    elija **Select**.

> ![A screenshot of a group Description automatically
> generated](./media/image31.png)

9.  Seleccione **Next**.

> ![A screenshot of a computer Description automatically
> generated](./media/image32.png)

10. En la pestaña **Review + Create**, seleccione **Create**.

> ![A screenshot of a computer Description automatically
> generated](./media/image33.png)

11. En la página **Microsoft 365 Apps (Research)**,
    seleccione **Properties**.

> ![A screenshot of a computer Description automatically
> generated](./media/image34.png)

12. En el panel de details verifique que está enumerado **Research** en
    **Required** en la sección **Assignments**.

> ![A screenshot of a computer Description automatically
> generated](./media/image35.png)

Tarea 3: Obligue el policy synchronization desde el Microsoft Intune
console

1.  En el **Microsoft Intune admin center**, seleccione **Devices** y
    luego seleccione **All devices**.

2.  En el panel de details, seleccione **SEA-WS1**.

> ![A screenshot of a computer Description automatically
> generated](./media/image36.png)

3.  En el **SEA-WS1** blade, seleccione **Sync** y cuando se le pide,
    seleccione **Yes**.

> ![A screenshot of a computer Description automatically
> generated](./media/image37.png)
>
> Microsoft Intune contactará el dispositivo y sincronizar todas las
> políticas. Puede llevar hasta 5 minutos.

Tarea 4: Verifique que están instaladas las Microsoft 365 apps

1.  Inicie sesión
    en [*SEA-WS1*](urn:gd:lg:a:send-vm-keys?rc=10) como **Cindy White**.

> **Ojo** – Tiene que esperar unos 10-15 minutos para que se instale
> Microsoft 365 Suite en el dispositivo.

2.  Cierre e inicie sesión de nuevo a  como **Cindy White** mediante sus
    credenciales !!**Cindy@M365xXXXXXX.onmicrosoft.com**!! Con la
    contraseña !!**P@55w.rd1234**!!

3.  En [***SEA-WS1***](urn:gd:lg:a:send-vm-keys), en el taskbar,
    seleccione **Start** y luego la aplicación **Settings**.

> ![A screenshot of a computer Description automatically
> generated](./media/image38.png)

4.  En la aplicación **Settings**, seleccione **Apps** y la
    página **Apps & features**.

> ![A screenshot of a computer Description automatically
> generated](./media/image23.png)

5.  Busque !!**Microsoft 365**!! Y verifique que está
    enlistado **Microsoft 365 Apps for enterprise - en-us**.

> ![A screenshot of a computer Description automatically
> generated](./media/image39.png)

6.  Cierre **Settings** y seleccione el botón **Start**.

7.  En la sección **Recommended** debe poder ver las aplicaciones
    recientemente instaladas que fueron seleccioneados desde Microsoft
    365 Apps en Microsoft Intune .

> ![A screenshot of a computer Description automatically
> generated](./media/image40.png)

Tarea 5: Supervise el app installation status en Microsoft Intune

1.  Cambie a **[*SEA-SVR1*](urn:gd:lg:a:select-vm)** y en **Microsoft
    Intune admin center**, seleccione **Apps**.

> ![](./media/image41.png)

2.  En el **Apps | Overview** blade, seleccione **Monitor** y luego
    seleccione **App install status**.

> ![A screenshot of a computer Description automatically
> generated](./media/image42.png)

3.  En el panel details, seleccione **Microsoft 365 Apps (Research)**.

> ![A screenshot of a computer Description automatically
> generated](./media/image43.png)

4.  En el panel details, en **Device status** y en **User status**,
    verifique que se ve **1** en Installed.

> ![A screenshot of a computer Description automatically
> generated](./media/image44.png)
>
> **Ojo**: Esto indica que se ha instalado la aplicación en un
> dispositivo y para un usuario. Note que puede llevar un poco de tiempo
> en mostrar la información y puede aparecer como **Install Pending**.
>
> **Ojo** – Puede empezar el **Laboratorio 13** y volver más tarde
> después de **30-45** minutos.

![A screenshot of a computer Description automatically
generated](./media/image45.png)

5.  Seleccione **Device install status**.

> En el panel de details, puede ver los dispositivos con la aplicación
> instalada, y también el nombre del usuario. La columna **Device
> Name** debe enlistar **SEA-WS1** y la columna **Status** debe decir
> **Installed**. Esto significa que la aplicación está instalada
> en **SEA-WS1**.
>
> ![A screenshot of a computer Description automatically
> generated](./media/image46.png)

6.  En el **Microsoft Intune admin center**, seleccione **Devices**.

7.  En el **Devices | Overview** blade, seleccione **All devices** y
    luego en el panel details, seleccione **SEA-WS1**.

> ![A screenshot of a computer Description automatically
> generated](./media/image47.png)

8.  En el **SEA-WS1** blade, seleccione **Managed Apps**.

9.  En el **SEA-WS1 | Managed Apps** blade, en el panel details,
    seleccione **Microsoft 365 Apps (Research)**.

> ![A screenshot of a computer Description automatically
> generated](./media/image48.png)
>
> En la ventana **Microsoft 365 Apps (Research) - Installation
> details**, puede ver el lifecycle entero de la aplicación, es decir –
> cuando fue creado, asignado, la hora de instalación, estado, y la
> útlima vez que el dispositivo abrió la aplicación (sincronizado con
> Microsoft Intune).
>
> ![A screenshot of a computer Description automatically
> generated](./media/image49.png)

10. Cierre todas las ventanas abiertas.

**Resultados**: Después de completar este ejercicio, tendrá configurado
e implementado el Microsoft 365 Apps desde Microsoft Intune.
