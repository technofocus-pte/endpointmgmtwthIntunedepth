**Laboratorio 7 – Crear e implementar Configuration Profiles**

**Resumen**

En este laboratorio, usemos Microsoft Intune para crear y aplicar un
Configuration profile para un dispositivo Windows 11.

**Prerrequisitos**

Se debe completar los siguientes laboratorios antes de este laboratorio:

- Laboratorio \#1-Gestionar Identities in Microsoft Entra ID

- Laboratorio \#2-Sincronizar Identities mediante Microsoft Entra
  Connect

- Laboratorio \#5-Gestionar Device Enrollment en Microsoft Intune

- Laboratorio \#6-Inscripción de dispositivos en Microsoft Intune

Ojo: También necesita un celular que puede recibir mensajes de textos
para asegurar la autenticación de inicio de sesión Windows Hello a
Microsoft Entra ID.

**Ejercicio 1: Cree y aplique un Configuration profile**

**Escenario**

Necesita usar Microsoft Entra y Microsoft Intune para gestionar los
miembros del departamento de desarrolladores en Contoso. Se le ha pedido
evaluar soluciones que habilitarán a los usuarios para trabajar de
manera más eficiente y segura en los dispositivos Windows 11 devices.
Cindy White se ha ofrecido para ayudarle probar y evaluar la solución y
proporcionar un feedback. Tambíen le ha dado unos requisitos principales
que se deben incluir y aplicar al dispositivo Windows del desarrollador:

- La sección Gaming en Settings no debe ser visible.

- La sección Privacy en Settings debe ser restringida cuanto posible.

- La carpeta **C:\DevProjects** debe ser excluido de Windows Defender.

- El proceso devbuild.exe debe ser excluido de Windows Defender.

- No se debe mostrar las aplicaciones más usadas y recién añadidas en el
  menú de inicio.

**Tarea 1: Verifique los device settings**

1.  Inicie sesión
    en [*SEA-WS1*](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10) como **Cindy**
    White con sus credenciales !!**Cindy@M365xXXXXXX.onmicrosoft.com**!!
    Con el PIN !!**102938**!! o contraseña !!**P@55w.rd1234**!!

![A screenshot of a computer Description automatically
generated](./media/image1.png)

2.  En el taskbar, seleccione **Start** y seleccione **Settings**.

![A screenshot of a computer Description automatically
generated](./media/image2.png)

3.  En la lista de navegación **Settings**, verifique que puede ver
    configuraciones de **Gaming**.

![A screenshot of a computer Description automatically
generated](./media/image3.png)

4.  Seleccione la configuración **Personalization** y luego seleccione
    Personalization, seleccione **Start**. Tome nota de **Show recently
    added apps** y **Show most used apps**.

![](./media/image4.png)

![A screenshot of a computer Description automatically
generated](./media/image5.png)

5.  En la aplicación **Settings**, seleccione **Privacy & security**.

6.  En la página **Privacy & security**, tome nota de las
    opciones **Security**, **Windows permissions**, y **App
    permissions**.

![A screenshot of a computer Description automatically
generated](./media/image6.png)

7.  En la página **Privacy & security**, seleccione **Windows
    Security** y seleccione **Open Windows Security**.

![](./media/image7.png)

![A screenshot of a computer security Description automatically
generated](./media/image8.png)

8.  En la página **Windows Security**, seleccione **Virus & threat
    protection**.

9.  En la página **Virus & threat protection**, en **Virus & threat
    protection settings**, seleccione **Manage settings**.

![A screenshot of a computer Description automatically
generated](./media/image9.png)

10. Baje a **Exclusions** y seleccione **Add or remove exclusions**. En
    el cuadro de diálogo User Account Control, seleccione **Yes**.

![A screenshot of a computer Description automatically
generated](./media/image10.png)

![A screenshot of a computer Description automatically
generated](./media/image11.png)

11. En la página **Exclusions**, verifique que no se ha configurado
    ninguna exclusión.

12. Cierre la ventana **Windows Security**.

![A screenshot of a computer Description automatically
generated](./media/image12.png)

13. Cierre la ventana **Settings**.

**Tarea 2: Cree un Configuration profile en función de los requisitos
del escenario**

1.  Cambie
    a [*SEA-SVR1*](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10).

2.  Vuelva a la pestaña **Microsoft Intune admin center**,
    seleccione **Devices** desde la barra de navegación.

![A screenshot of a computer Description automatically
generated](./media/image13.png)

3.  En la página **Devices | Overview**, seleccione **Windows** como se
    ve en la imagen.

![A screenshot of a computer Description automatically
generated](./media/image14.png)

4.  En la página **Windows | Windows devices**, navegue y haga clic en
    **Configuration profiles**.

![A screenshot of a computer Description automatically
generated](./media/image15.png)

5.  En la página **Windows | Configuration profiles**, en la pestaña
    **Policies**, haga clic en **+ Create** y seleccione **+ New
    Policy**.

![A screenshot of a computer Description automatically
generated](./media/image16.png)

6.  En el panel **Create a profile** que aparece en la parte derecha,
    seleccione las siguientes opciones, y seleccione **Create**:

- Platform: **Windows 10 and later**

- Profile type: **Templates**

- Template name: !!!!

![A screenshot of a profile Description automatically
generated](./media/image17.png)

7.  En el **Basics** blade, introduzca la siguiente información, y
    seleccione **Next**:

- Name: !!Contoso Developer - standard!!

- Description: !!Basic restrictions and configuration for Contoso
  Developers.!!

![](./media/image18.png)

8.  En el **Configurations settings** blade, expanda **Control Panel and
    Settings**.

![A screenshot of a computer Description automatically
generated](./media/image19.png)

9.  Seleccione **Block** junto a las opciones **Gaming** y **Privacy**.

![A screenshot of a computer Description automatically
generated](./media/image20.png)

10. En el **Device restrictions** blade, expanda **Start**.

![A screenshot of a computer Description automatically
generated](./media/image21.png)

11. Baje y seleccione **Block** junto a **Most used apps**, **Recently
    added apps** y **Recently opened items in Jump Lists**.

![A screenshot of a computer Description automatically
generated](./media/image22.png)

12. En el **Device restrictions** blade, baje y expanda **Microsoft
    Defender Antivirus**.

![A screenshot of a computer Description automatically
generated](./media/image23.png)

13. En **Microsoft Defender Antivirus,** baje y expanda **Microsoft
    Defender Antivirus Exclusions**.

![](./media/image24.png)

14. En **Microsoft Defender Antivirus Exclusions** proporcione los
    siguientes detalles y haga clic en el botón **Next**:

- Files and folders box - !!**C:\DevProjects**!!

- Processes box - !!**DevBuild.exe**!!

![](./media/image25.png)

15. En la pestaña **Assignments**, haga clic en el botón **Next**.

![A screenshot of a computer Description automatically
generated](./media/image26.png)

16. En la pestaña **Applicability Rules**, haga clic en el botón
    **Next**.

![A screenshot of a computer Description automatically
generated](./media/image27.png)

17. En la pestaña **Review + create**, haga clic en el botón **Create**.

![A screenshot of a computer Description automatically
generated](./media/image28.png)

18. Se debería aparecer el Configuration profile.

![A screenshot of a computer Description automatically
generated](./media/image29.png)

**Tarea 3: Cree el Contoso Developer device group**

1.  En el Microsoft Intune admin center, en el panel de navegación,
    seleccione **Groups**.

![A screenshot of a computer Description automatically
generated](./media/image30.png)

2.  En el **Groups | All groups** blade, seleccione **New group**.

![A screenshot of a computer Description automatically
generated](./media/image31.png)

3.  En el **New Group** blade, introduzca la siguiente información:

- Group type: **Security**

- Group name: !!Contoso Developer devices!!

- Group description: !!All Windows devices in Contoso Developer
  department!!

- Membership type: **Assigned**

4.  En **Members**, seleccione **No members selected**.

![](./media/image32.png)

5.  En el **Add members** blade, en el cuadro **Search,** tecle !!Sea!!
    . Seleccione **SEA-WS1** y elija **Select**.

![A screenshot of a computer Description automatically
generated](./media/image33.png)

6.  En el **New Group** blade, seleccione **Create**.

![](./media/image34.png)

7.  En el **Groups | All groups** blade, verifique que se ve **Contoso
    developer devices** group.

![](./media/image35.png)

**Tarea 4: Cree un dynamic Azure AD device group**

1.  En el **Groups | All Groups** blade, en el panel de details,
    seleccione **New group**.

![A screenshot of a computer Description automatically
generated](./media/image36.png)

2.  En el **Group** blade, proporcione los siguientes valores:

- Group type: **Security**

- Group name: !!Windows Devices!!

- Membership type: **Dynamic Device**

3.  En la sección **Dynamic Device Members**, seleccione **Add dynamic
    query**.

![A screenshot of a computer Description automatically
generated](./media/image37.png)

4.  En el **Dynamic membership rules** blade, en la sección **Rule
    syntax**, seleccione **Edit**.

![A screenshot of a computer Description automatically
generated](./media/image38.png)

5.  En el cuadro de texto **Edit rule syntax**, agregue una regla de
    simple membership rule y seleccione **OK**.

!!**(device.deviceOSType -contains "Windows")**!!

![A screenshot of a computer Description automatically
generated](./media/image39.png)

6.  En el **Dynamic membership rules** blade, seleccione **Save**.

![A screenshot of a computer Description automatically
generated](./media/image40.png)

7.  En la página **New Group**, seleccione **Create**.

![A screenshot of a computer Description automatically
generated](./media/image41.png)

**Tarea 5: Asigne un Configuration profile a Windows devices**

1.  Mientras en la página **Microsoft Intune admin center**,
    seleccione **Devices** desde la barra de navegación.

![](./media/image42.png)

2.  En la página **Devices | Overview**, seleccione **Windows** como se
    ve en la imagen.

![](./media/image43.png)

3.  En página **Windows | Windows devices**, navegue y haga clic
    **Configuration profiles**.

![](./media/image44.png)

4.  En el **Devices | Configuration profiles** blade, en el panel de
    details, seleccione el **Contoso Developer – standard** profile.

![A screenshot of a computer Description automatically
generated](./media/image45.png)

5.  En el **Contoso Developer – standard** blade, baje a la
    sección **Assignments**, y seleccione **Edit**.

![A screenshot of a computer Description automatically
generated](./media/image46.png)

6.  En la página Assignments, en **Included groups** seleccione **Add
    groups**.

![A screenshot of a computer Description automatically
generated](./media/image47.png)

7.  En el **Select groups to include** blade, en el cuadro **Search**,
    tecle y seleccione !!**Contoso Developer devices**!!  Y haga clic en
    el botón **Select**.

![](./media/image48.png)

14. Volviendo a la página **Device restrictions** blade,
    seleccione **Review + save**, y seleccione **Save**.

![A screenshot of a computer Description automatically
generated](./media/image49.png)

![](./media/image50.png)

**Tarea 6: Verifique que se aplica el Configuration profile**

1.  Cambie
    a *[SEA-WS1](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10).* Inicie
    sesión con la cuenta Cindy White.

- Username - !!**Cindy@M365xXXXXXXX.onmicrosoft.com**!!

- Password – !!**P@55w.rd1234**!!

2.  En el taskbar, seleccione **Start** y luego seleccione **Settings**.

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)

3.  En la ventana **Settings**, seleccione **Accounts**. En la página
    Accounts, seleccione **Access work or school**.

![A screenshot of a computer Description automatically
generated](./media/image51.png)

4.  Haga clic en el dropdown junto **Connected to Contoso’s Azure AD** y
    seleccione el botón **Info**.

![](./media/image52.png)

5.  En la página **Managed by Contoso**, baje, y en Device sync status,
    seleccione **Sync**. Espere a que se complete la sincronización.

![A screenshot of a computer Description automatically
generated](./media/image53.png)

![A screenshot of a computer Description automatically
generated](./media/image54.png)

6.  Cierre la aplicación **Settings**.

> **Ojo**: El progreso de la sync puede tardar unos 15 minutos antes de
> que se aplique al dispositivo Windows 11. Cerrar la sesión o reiniciar
> el dispositivo puede ayudar a acelerar el proceso.

7.  En [*SEA-WS1*](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10),
    seleccione **Start** de nuevo y seleccione **Settings**. Verifique
    que se ha quitado la configuración **Gaming**.

![A screenshot of a computer Description automatically
generated](./media/image2.png)

![A screenshot of a computer Description automatically
generated](./media/image55.png)

8.  Seleccione **Privacy & security** y note que muchas de las
    configuraciones de privacidades ahora están ocultas.

![](./media/image56.png)

9.  Seleccione la configuración **Personalization** y seleccione
    **Start**. Verifique que **Show recently added apps** y **Show most
    used apps** están en **Off** y deactivados.

![](./media/image57.png)

![A screenshot of a computer Description automatically
generated](./media/image58.png)

10. En la aplicación **Settings**, seleccione **Privacy and Security**.

11. En la página **Privacy & Security**, seleccione **Windows
    Security** y luego seleccione **Open Windows Security**.

![](./media/image59.png)

![A screenshot of a computer security Description automatically
generated](./media/image60.png)

12. En la página **Windows Security**, seleccione **Virus & threat
    protection**.

13. En la página **Virus & threat protection**, seleccione **Manage
    settings** en **Virus & threat protection settings**.

![A screenshot of a computer Description automatically
generated](./media/image9.png)

14. Baje a **Exclusions** y seleccione **Add or remove exclusions**.
    Seleccione **Yes** en User Account Control message.

![A screenshot of a computer Description automatically
generated](./media/image61.png)

![A screenshot of a computer Description automatically
generated](./media/image62.png)

15. En la página **Exclusions**, verifique que se
    ve **C:\DevProjects** y **DevBuild.exe**.

![A screenshot of a computer Description automatically
generated](./media/image63.png)

16. Cierre la página **Windows Security** y cierre la
    aplicación **Settings**.

**Resultados**: Después de completar este ejercicio, habrá creado y
asignado un Configuration profile para un dispositivo.

**Ejercicio 2: Modifique un Configuration profile policy asignado.**

**Escenario**

Había una exepción en la política Contoso que específica que los
miembros del departamento de desarrolladores no deben tener los Privacy
options bloqueados en Settings en sus dispositivos. Se debe implementar
y probar este cambio.

**Tarea 1: Cambie las configuraciones en un Configuration profile
asignado**

1.  Cambie a **SEA-SVR1**. Vuelva a la pestaña **Microsoft Intune admin
    center**, seleccione **Devices** desde la barra de navegación.

![](./media/image42.png)

2.  En la página **Devices | Overview**, seleccione **Windows** como se
    ve en la imagen.

![](./media/image43.png)

3.  En la página **Windows | Windows devices**, navegue y haga clic en
    **Configuration profiles**.

![](./media/image44.png)

4.  En el **Devices | Configuration profiles** blade, en el panel de
    details seleccione **Contoso Developer - standard**.

![](./media/image64.png)

5.  En el **Contoso Developer - standard** blade, baje hasta la
    sección **Configuration settings**, y luego seleccione **Edit**.

![A screenshot of a computer Description automatically
generated](./media/image65.png)

6.  En la página **Device restrictions**, expanda **Control Panel and
    Settings**.

![A screenshot of a computer Description automatically
generated](./media/image66.png)

7.  Junto a **Privacy**, asegure que está seleccionado **Not
    configured**.

![A screenshot of a computer Description automatically
generated](./media/image67.png)

8.  Seleccione **Review + save**, y seleccione **Save**.

![](./media/image68.png)

**Tarea 2: Obligue el device synchronization desde Microsoft Intune
admin center**

1.  En [*SEA-SVR1*](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10),
    en el **Microsoft Intune admin center**, seleccione **Devices** en
    el panel de navegación y seleccione **All devices** y luego
    seleccione **SEA-WS1**.

![A screenshot of a computer Description automatically
generated](./media/image69.png)

2.  En el **SEA-WS1** blade, seleccione **Sync** y cuando se le pide,
    seleccione **Yes**.

![](./media/image70.png)

**Ojo**: Intune conectará el dispositivo y sincronizará todas las
políticas. Puede tardar hasta 5 minutos.

**Tarea 3: Verifique los cambios
en [*SEA-WS1*](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10)**

1.  Cambie
    a [*SEA-WS1*](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10).
    En el taskbar, seleccione **Start** y seleccione **Settings**.

![A screenshot of a computer Description automatically
generated](./media/image2.png)

2.  En la aplicación **Settings**, seleccione **Privacy & security** y
    verifique que se ven de nuevo todas las opciones de personalización.

![A screenshot of a computer Description automatically
generated](./media/image71.png)

3.  Cierre todas las ventanas y cierre la sesión de **SEA-WS1**.

**Resultados**: Después de completar este ejercicio, habrá modificado y
asignado un Configuration profile, modificado un Configuration profile,
y verificado los cambios.
