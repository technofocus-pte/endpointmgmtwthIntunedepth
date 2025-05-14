**Laboratorio 5 - Gestione Device Enrollment en Microsoft Intune**

**Resumen**

En este laboratorio, se prepara para device management mediante
Microsoft Intune al revisar y asignar licencias, configurando Windows
automatic enrollment, y configurando restricciones de enrollment.

**Prerrequisitos**

Se deben completar los siguientes laboratorios antes de este
laboratorio:

- Laboratorio \#1-Gestionar Identities en Microsoft Entra ID

- Laboratorio \#2-Sincronizar Identities mediante Microsoft Entra
  Connect

**Ojo**: También necesitará un celular que puede recibir mensajes de
texto para asegurar la autenticación de inicio de sesión Windows Hello a
Entra ID.

**Escenario**

Tiene que prepararse para device management mediante Microsoft Intune.
Primero, tiene que asegurarse de que se hayan asignado licencias
apropriadas para device management. Como una prueba de verificación,
asignará las licencias requeridas a Aaron Nicholls. También tiene que
asegurarse de que cualquier dispositivo Windows que se junta o registra
a Microsoft Entra ID será insrito automáticamente en Intune. También se
le ha pedido que asegure que se restringen los miembros de Sales group
de inscribir dispositivos Android y iOS personales en Intune y que se
aumente el Enrollment Device Limit a 10 devices. Finalmente, tiene que
configurar al Allan Deyoung como el Device enrollment manager para
permitirle la inscripción de 1000 dispositivos.

**Tarea 1: Revise y asigne licencias para device management**

1.  En [*SEA-SVR1*](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10),
    navegue a la ventana **Microsoft 365 admin center**.

![](./media/image1.png)

2.  Navegue y seleccione **Billing**, y haga clic en **Licenses**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image2.png)

3.  En la página licencias **Licenses**, tome nota de las licencias
    disponibles en el tenant.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image3.png)

4.  Seleccione y haga clic en **Enterprise Mobility + Security E5**.
    Note si se ha asignado esta licencia a todos los usuarios. Puede
    asignar o quitar licencias desde esta ubicación.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image4.png)

![](./media/image5.png)

5.  Seleccione un usuario para ver las licencias asignadas a este
    usuario. Tome nota de los servicios incluidos en la licencia
    Enterprise Mobility + Security E5. Microsoft Intune es uno de los
    servicios permitidos para esta licencia.

![](./media/image6.png)

6.  En el panel de navegación **Microsoft 365 admin center**,
    seleccione **Active users**.

![](./media/image7.png)

7.  Busque y seleccione !!**Cindy White**!!

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image8.png)

8.  En la página **Cindy White user**, haga clic en **Licenses and
    apps**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image9.png)

9.  En **Settings**, en el campo **Usage location**, seleccione **United
    States** y haga clic en la casilla de verificación de **Enterprise
    Mobility + Security E5 and Office 365 E5 (no teams)** y haga clic en
    **Save changes**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image10.png)

***Ojo**: Antes de asignar una licencia al usuario, el usuario debe
tener establecido un usage location.*

![](./media/image11.png)

**Tarea 2: Estableceer la contraseña del usuario utilizando PowerShell**

1.  En [***SEA-SVR1***](urn:gd:lg:a:select-vm), haga clic derecho en
    **Start button**, y seleccione **Windows PowerShell (Admin)**.

![](./media/image12.png)

2.  En el cuadro de diálogo **User Account Control**,
    seleccione **Yes**.

![](./media/image13.png)

3.  En la ventana **Windows PowerShell**, tecle el siguiente command, y
    presione **Enter**:

!!**Connect-MsolService**!!

![A computer screen with white text Description automatically
generated](./media/image14.png)

4.  En el cuadro de diálogo **Sign in to your account**, inicie sesión
    con sus Office 365 Tenant credentials desde la pestaña Home.

**Ojo – Si se le ha pedido cambiar la contraseña de Tenant admin
credentials, asegúrese de proporcionar la contraseña actualizada.**

![A screenshot of a computer Description automatically
generated](./media/image15.png)

![A screenshot of a computer screen Description automatically
generated](./media/image16.png)

5.  En la ventana **Windows PowerShell**, tecle el siguiente command
    para reestablecer las contraseñas de **Cindy White**

!!**Get-MsolUser | Where-Object DisplayName -EQ "Cindy White" |
Set-MsolUserPassword -NewPassword P@55w.rd1234 -ForceChangePassword
$false**!!

![A computer screen shot of a program Description automatically
generated](./media/image17.png)

**Tarea 3: Habilite Windows Automatic Enrollment en Microsoft Intune**

1.  En **SEA-SVR1**, abra una nueva pestaña en **Microsoft Edge**, y
    luego en la barra de direcciones
    tecle !!**https://Endpoint.microsoft.com**!! y presione **Enter**.
    Se le pide iniciar sesión, proporcione las credenciales de **Office
    365 Tenant Admin**.

2.  En el Microsoft Intune admin center, seleccione **Devices**.

![A screenshot of a computer Description automatically
generated](./media/image18.png)

3.  Navegue y haga clic en **Enrollment**. Asegure que está seleccionado
    la pestaña **Windows**, y navegue a la sección **Enrollment
    options** y haga clic en **Automatic Enrollment**.

![](./media/image19.png)

4.  En la fila **MDM user scope**, seleccione el botón de
    alternancia **All** y seleccione **Save**.

![](./media/image20.png)

5.  Haga clic en el enlace **Devices | Enrollment** como se ve aquí en
    la imagen.

![](./media/image21.png)

**Ojo**: al realizar este paso, ha habilitado automatic enrollment en
Intune para cualquier usuario que realiza un Azure AD join con un
dispositivo Windows.

**Tarea 4: Configure las restricciones Enrollment**

1.  Navegue a la sección **Devices onboarding** y haga clic en
    **Enrollment**. A continuación, haga clic en la pestaña **Android**
    como se ve en la imagen.

![](./media/image22.png)

2.  Baje a la sección **Enrollment options** y haga clic en **Device
    platform restriction**.

![](./media/image23.png)

3.  Seleccione la pestaña **Android restrictions**, y
    seleccione +**Create restriction**.

![](./media/image24.png)

![](./media/image25.png)

4.  En la página **Create restriction**, en el cuadro **Name**,
    introduzca !!**Android Personal Device Restriction**!!
    Seleccione **Next**.

![](./media/image26.png)

5.  En la página de Platform settings, en **Personally owned**,
    seleccione **Block** para los siguientes tipos de dispositivos y
    haga clic en el botón **Next**:

    - Android Enterprise (work profile)

    - Android device administrator

![](./media/image27.png)

6.  En la página **Scope tags**, seleccione **Next**.

![A screenshot of a computer Description automatically
generated](./media/image28.png)

7.  En la página **Assignments**, en **Included groups**,
    seleccione **Add groups**.

![A screenshot of a computer Description automatically
generated](./media/image29.png)

8.  En el **Search bar** del panel **Select groups to include**, tecle y
    seleccione **Sales**, y haga clic en el botón **Select**.

![A screenshot of a computer Description automatically
generated](./media/image30.png)

9.  En la pestaña **Assignments**, haga clic en el botón **Next**.

![A screenshot of a computer Description automatically
generated](./media/image31.png)

10. En la página **Review + create**, seleccione **Create**.

![A screenshot of a computer Description automatically
generated](./media/image32.png)

Note que se ha asignado Android Personal Device Restriction con una
prioridad de 1.

![A screenshot of a computer Description automatically
generated](./media/image33.png)

11. En la página **Devices | Enrollment**, en la pestaña **Windows**,
    navegue a la sección **Enrollment options** y haga clic en **Device
    limit restriction**.

![A screenshot of a computer Description automatically
generated](./media/image34.png)

Note que hay un Default device limit restriction que se ha asignado a
All Users. Este default restriction establece un device enrollment limit
a 5 dispositivos por cada usuario.

12. En **Enrollment device limit restrictions**, seleccione + **Create
    restriction**.

![A screenshot of a computer Description automatically
generated](./media/image35.png)

13. En la página Create restriction, en el cuadro **Name**,
    introduzca !!**Sales Device Enrollment Limit**!!
    Seleccione **Next**.

![A screenshot of a computer Description automatically
generated](./media/image36.png)

14. En la página **Device limit**, seleccione **10**, y luego
    seleccione **Next**.

![A screenshot of a computer Description automatically
generated](./media/image37.png)

15. En la página **Scope tags**, seleccione **Next**.

![A screenshot of a computer Description automatically
generated](./media/image38.png)

16. En la página **Assignments**, en **Included groups**,
    seleccione **Add groups**.

![A screenshot of a computer Description automatically
generated](./media/image39.png)

17. En el cuadro de búsqueda de la página **Select groups to include**
    tecle y seleccione **Sales** y haga clic en el botón **Select**.

![](./media/image40.png)

18. Haga clic en el botón **Next**.

![A screenshot of a computer Description automatically
generated](./media/image41.png)

19. En la página **Review + create**, seleccione **Create**.

![A screenshot of a computer Description automatically
generated](./media/image42.png)

20. Recargue la página. Note el Sales Device Enrollment Limit,
    configurado con un Device limit de 10 y asignado con un priority de
    1.

![A screenshot of a computer Description automatically
generated](./media/image43.png)

**Tarea 5: Configure un Device enrollment manager**

1.  En **Microsoft Intune admin center**, seleccione **Devices**.

![](./media/image44.png)

2.  Navegue a la sección **Device onboarding** y haga clic en
    **Enrollment**, y luego haga clic en la pestaña **Device enrolment
    managers**.

![](./media/image45.png)

3.  En el panel **Enroll devices**, seleccione **Device enrollment
    managers**.

Notice that, by default, there are no Device enrollment managers
configured.

4.  En la página **Enroll devices|Device enrollment managers**,
    seleccione **Add**.

![A screenshot of a computer Description automatically
generated](./media/image46.png)

5.  En la página **Add user**, en User name, introduzca la dirección del
    email de Allan [DeYoung
     !!**AllanD@M365xXXXXXXX.onmicrosoft.com**](mailto:DeYoung !!AllanD@M365xXXXXXXX.onmicrosoft.com)!!
     (sustituya **XXXXXX** con su tenant name) y seleccione **Add**.

![A screenshot of a computer Description automatically
generated](./media/image47.png)

**Allan ahora puede incribir hasta 1000 dispositivos.**

6.  En Microsoft Intune admin center, en el panel de navegación,
    seleccione **Home**.

![A screenshot of a computer Description automatically
generated](./media/image48.png)

7.  Cierre Microsoft Edge.

**Resultados**: Después de completar este ejercicio, habrá revisado y
asignado las licencias, configurado el Windows automatic enrollment,
habilitado y asignado los enrollment restrictions, y configurado un
Device enrollment manager.
