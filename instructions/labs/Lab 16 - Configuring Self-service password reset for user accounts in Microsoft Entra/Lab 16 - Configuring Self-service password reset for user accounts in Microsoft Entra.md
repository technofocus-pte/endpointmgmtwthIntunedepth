Laboratorio 16 - Configurar Self-service password reset para cuentas de
usuarios en Microsoft Entra

**Resumen**

En este laboratorio, configurará y validará self-service password reset
(SSPR) para cuentas de usuarios en **Microsoft Entra ID**.

**Prerrequisitos**

Se debe completar los siguientes laboratorios antes de este laboratorio:

- Laboratorio \#2-Sincronizar Identities mediante Microsoft Entra
  Connect

- Laboratorio \#5-Gestione Device Enrollment en Microsoft Intune

**Escenario**

El Help Desk ha indicado que muchos de los support tickets están
relacionados con el reestablecimiento de contraseñas. Le han pedido
proporcionar una solución para que los usuarios puedan reestablecer sus
contraseñas independientemente. En el caso de las cuentas sincronizadas
con AD DS, el proceso reestablecerá la contraseña para ambas cuentas de
Microsoft Entra y AD DS password.

Tarea 1: Configure el password writeback

1.  Inicie sesión
    en [***SEA-SVR1***](urn:gd:lg:a:select-vm) como !!**[Contoso\Administrator](urn:gd:lg:a:send-vm-keys)!!** Con
    la contraseña !!**[Pa55w.rd](urn:gd:lg:a:send-vm-keys)!!** y
    cierre **Server Manager**.

2.  En el desktop, haga doble clic en **Azure AD Connect**.

> ![A screenshot of a computer Description automatically
> generated](./media/image1.png)

3.  En la página **Welcome to Azure AD Connect**,
    seleccione **Configure**.

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)

4.  En la página **Additional tasks**, seleccione **Customize
    synchronization options**, y luego seleccione **Next**.

> ![A screenshot of a computer Description automatically
> generated](./media/image3.png)

5.  En la página **Connect to Azure AD**, si es necesario
    tecle !!**admin@M365xXXXXXXX.onmicrosoft.com!!** En el cuadro de
    texto **USERNAME**, tecle el **PASSWORD**, y luego
    seleccione **Next**.

> ![A screenshot of a computer Description automatically
> generated](./media/image4.png)

6.  En la página **Connect to your directories**, seleccione **Next**.

7.  En la página **Domain and OU filtering**, seleccione **Next**.

8.  En la página **Optional features**, seleccione **Password
    writeback**, y luego seleccione **Next**.

> ![A screenshot of a computer Description automatically
> generated](./media/image5.png)

9.  En la página **Ready to configure**, seleccione **Configure**.

> ![A screenshot of a computer Description automatically
> generated](./media/image6.png)
>
> ![A computer screen shot of a computer Description automatically
> generated](./media/image7.png)
>
> **Ojo**: la configuración puede tardar unos minutos.

10. En la página **Configuration complete**, seleccione **Exit**.

> ![A screenshot of a computer Description automatically
> generated](./media/image8.png)

Tarea 2: Habilite self-service password reset.

1.  En el taskbar seleccione **Microsoft Edge**, navegue a **Microsoft
    Entra admin center** **https://Entra.Microsoft.com**.

2.  Inicie sesión con sus **Office 365 Tenant admin** credentials.

> ![A screenshot of a computer Description automatically
> generated](./media/image9.png)
>
> Se abre el **Microsoft Entra admin center**.

3.  En el **Microsoft Entra admin center**, en el panel de navegación,
    expanda **Identity**, y seleccione **Users**.

4.  En el panel de navegación de **Users**, seleccione **Password
    reset**.

> ![A screenshot of a computer Description automatically
> generated](./media/image10.png)

5.  En la ventana **Password reset | Properties**,
    seleccione **All** para habilitar self-service password reset para
    todos los usuarios. Seleccione **Save**.

> ![A screenshot of a computer Description automatically
> generated](./media/image11.png)
>
> ![A screenshot of a computer screen Description automatically
> generated](./media/image12.png)

6.  En el **Password reset | Properties** blade,
    seleccione **Authentication methods**.

> ![A screenshot of a computer Description automatically
> generated](./media/image13.png)

7.  Para los métodos disponibles a los usuarios, asegure que están
    seleccionados **Mobile Phone** y **Email**, y luego
    seleccione **Security Questions**.

8.  Para el **Number of questions required to register**,
    seleccione **3**.

9.  Para el **Number of questions required to reset**, seleccione **3**.

> ![A screenshot of a computer Description automatically
> generated](./media/image14.png)

10. En la sección **Select security questions**, seleccione **No
    security questions configured**, y seleccione **Predefined**.
    Seleccione tres preguntas de su elección, y luego
    seleccione **OK** dos veces.

> ![A screenshot of a computer Description automatically
> generated](./media/image15.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image16.png)

11. Seleccione **Save**.

> ![A screenshot of a computer Description automatically
> generated](./media/image17.png)

12. Seleccione **Registration**. Seleccione **Yes** en **Require users
    to register when signing in**, y establezca el valor de **Number of
    days before users are asked to re-confirm their authentication
    information** a **90,** y seleccione **Save**.

> ![A screenshot of a computer Description automatically
> generated](./media/image18.png)

13. En el panel de navegación, seleccione **On-premises integration**.

14. Verifique que se está ejecutando su on-premises writeback client y
    asegure está seleccionado la casilla de **Enable password write back
    for synced users**. Si es necesario, seleccione **Save**.

> ![A screenshot of a computer Description automatically
> generated](./media/image19.png)

15. Cierre Microsoft Edge.

Tarea 3: Valide el self-service password reset

1.  Cambie a [***SEA-WS3***](urn:gd:lg:a:select-vm). Si es necesario,
    inicie sesión como !!**[Admin](urn:gd:lg:a:send-vm-keys)!!** con la
    contraseña !!**[Pa55w.rd](urn:gd:lg:a:send-vm-keys)!!**

2.  En el taskbar, seleccione **Microsoft Edge**. Navegue
    a !!**https://mysignins.microsoft.com/!!**

3.  En la página **Pick an account**, seleccione **Use another
    account**.

> ![A screenshot of a computer Description automatically
> generated](./media/image20.png)

4.  En la página **Sign in**, introduzca
    !!**Cindy@M365xXXXXXX.onmicrosoft.com!!** Y seleccione **Next**.

5.  En la página **Enter password**, introduzca **!!P@55w.rd1234!!** y
    seleccione **Sign in**. Si Microsoft Edge le pide guardar la
    contraseña, seleccione **Save**.

> ![A screenshot of a computer error Description automatically
> generated](./media/image21.png)

6.  Se le pedirá **More information required**, haga clic en **Next**

> ![A screenshot of a computer error Description automatically
> generated](./media/image22.png)

7.  Proporcione los detalles y haga clic en **Next.**

> ![A screenshot of a computer Description automatically
> generated](./media/image23.png)

8.  Introduzca el código de 6 cifras y haga clic en **Next**

> ![](./media/image24.png)

9.  Haga clic en Next de nuevo.

> ![A screenshot of a computer Description automatically
> generated](./media/image25.png)

10. Haga clic en **Done**.

> ![](./media/image26.png)

11. Podrá ver la página **My Account**

> ![](./media/image27.png)

12. Para cambiar la **Contraseña,** visite el enlace -
    **!!https://mysignins.microsoft.com/security-info!!**

13. Complete la verificación, al hacer clic en el texto +XXXXXXXXXXXXXX

> ![A screenshot of a computer error Description automatically
> generated](./media/image28.png)

14. Proporcione el código de 6 cifras y haga clic en Verify.

> ![A screenshot of a computer error Description automatically
> generated](./media/image29.png)

15. Haga clic en **Skip for now.**

> ![A screenshot of a computer error Description automatically
> generated](./media/image30.png)

16. En la página **Security info**, haga clic en **Change** para el
    Password.

> ![A screenshot of a login page Description automatically
> generated](./media/image31.png)

17. En la página **Change your password**, introduzca la siguiente
    información y seleccione **Submit**:

    - Create new password: **!!P@55w.rd12345!!**

    - Confirm new password: **!!P@55w.rd12345!!**

> ![A screenshot of a login box Description automatically
> generated](./media/image32.png)

18. Haga clic en el botón Done.

> ![](./media/image33.png)

19. Cierre Microsoft Edge y cierre sesión
    de [***SEA-WS3***](urn:gd:lg:a:select-vm).

Tarea 4: Ejecute Azure AD Connect Sync

Note que este paseo normalmente no es necesario para password writeback,
pero se recomienda para abordar los problemas de entornos del
laboratorio y asegurar que se sincroniza AD DS con Microsoft Entra.

1.  Cambie a [***SEA-SVR1***](urn:gd:lg:a:select-vm) y haga clic derecho
    en **Start** y seleccione **Windows PowerShell (Admin)**.

> ![A screenshot of a computer Description automatically
> generated](./media/image34.png)

2.  En el **Windows PowerShell** command prompt, tecle el siguiente
    command y presione **Enter**:

> **!!Start-ADSyncSyncCycle -PolicyType Delta!!**
>
> ![A screenshot of a computer Description automatically
> generated](./media/image35.png)

3.  Cierre Windows PowerShell, y espere unos 3-4 minutos.

Tarea 5: Verifique el password writeback

1.  Cambie a [***SEA-CL1***](urn:gd:lg:a:select-vm) y cierre la sesión
    si es necesario. En [***SEA-CL1***](urn:gd:lg:a:select-vm),
    seleccione **Other user**, e intente iniciar sesión
    como !!**Contoso\Cindy!!** con la contraseña !!**P@55w.rd1234!!**

> ![A screenshot of a computer Description automatically
> generated](./media/image36.png)

2.  Asegure que recibe el mensaje que el username o password es
    incorrecto.

> ![A screenshot of a computer screen Description automatically
> generated](./media/image37.png)

3.  Ahora inicie sesión como !!**Contoso\Cindy!!** con la contraseña
    !!**P@55w.rd12345!!** La contraseña que se estableció con el SSPR
    feature.

4.  Debe estar dentro con esta **nueva contraseña**.

Esto confirma que la contraseña que cambió en el My Sign in portal se
escribió en la cuenta local de Active Directory Domain Services (AD DS).

![A screenshot of a computer error Description automatically
generated](./media/image38.png)

> Ojo – Si recibe est mensaje a la hora de iniciar sesión, confirma que
> la ***autenticación fue exitosa***, pero la cuenta no tenía permiso de
> iniciar sesión en SEA-CL1 debido al group membership issue.

**Resultados**: Después de completar este ejercicio, habrá configurado y
validado el self-service password reset.
