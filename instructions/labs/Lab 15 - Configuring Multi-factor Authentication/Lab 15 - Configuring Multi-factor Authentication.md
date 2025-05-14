Laboratorio 15 – Configurar el Multi-factor Authentication

**Resumen**

En este laboratorio, configurará el per-user multi-factor authentication
(MFA) y aplicar MFA con un conditional access policy.

Ejercicio 1: Configure el per-user multi-factor authentication.

**Escenario**

Para proporcionar seguridad adicional para las instancias del inicio de
sesión del usuario, necesita configurar y probar multi-factor
authentication (MFA). Usted decide probar el per-user MFA. Alex Wilber
ha acrodado validar las configuraciones para usted.

Tarea 1: Validar el sign-in antes de habilitar MFA

1.  Cambie e inicie sesión
    en [**SEA-WS3**](urn:gd:lg:a:select-vm) como !\![**Admin**](urn:gd:lg:a:send-vm-keys)!!
    con la contraseña !\![**Pa55w.rd**](urn:gd:lg:a:send-vm-keys)!!

2.  En el taskbar, seleccione **Microsoft Edge**. En el address bar,
    introduzca !\![**outlook.office.com**](urn:gd:lg:a:send-vm-keys)!!
     y presione Enter.

3.  En la página **Sign in**, introduzca
    !!**AlexW@M365xXXXXXXX.onmicrosoft.com**!! Y luego
    seleccione **Next**.

4.  En la página **Enter password**, introduzca !!**P@55w.rd1234**!! y
    seleccione **Sign in**. en el prompt de Edge Save password,
    seleccione **Save**.

> Se abre Outlook en la Web. Note que se requiere solo la contraseña
> para iniciar sesión en Outlook en el Web.

5.  En la esquina superior derecha, seleccione el **Account manager for
    Alex Wilber** y luego seleccione **Sign out**.

> ![](./media/image1.png)

6.  Cierre Microsoft Edge.

Tarea 2: Habilite MFA para un ususario

1.  Cambie a [**SEA-SVR1**](urn:gd:lg:a:select-vm).
    En [**SEA-SVR1**](urn:gd:lg:a:select-vm), si es necesario, inicie
    sesión
    como [**Contoso\Administrator**](urn:gd:lg:a:send-vm-keys) con la
    contraseña !! [**Pa55w.rd**](urn:gd:lg:a:send-vm-keys)!!  y
    cierre **Server Manager**.

2.  En el taskbar seleccione **Microsoft Edge**, navegue a **Microsoft
    Entra admin center** !!**https://Entra.Microsoft.com**!!

3.  Inicie sesión con las **Office 365 Tenant admin** credentials.

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)
>
> Se abre el **Microsoft Entra admin center**.

4.  En el **Microsoft Entra admin center**, en el panel de navegación,
    expanda **Identity**, y seleccione **Users**.

5.  Seleccione **All users** y luego, en la parte superior del panel de
    resultados, seleccione **Per-user MFA**. Puede que necesite
    seleccionar los tres puntitos para ver la opción **Per-user MFA**.

> ![A screenshot of a computer Description automatically
> generated](./media/image3.png)

6.  En la página multi-factor authentication, seleccione **service
    settings**.

> ![A screenshot of a computer Description automatically
> generated](./media/image4.png)

7.  Baje a la sesión de **verification options**.

> Tome nota de los diferentes métodos que se pueden configurar para la
> verificación del usuario.

8.  En la sección **remember multi-factor authentication on trusted
    device**, seleccione la casilla junto a **Allow users to remember
    multi-factor authentication on devices they trust**.

9.  Junto a **Number of days users can trust devices for**,
    introduzca **30** y seleccione **save**. Seleccione **close** cuando
    se le pide.

> ![](./media/image5.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image6.png)

10. En la parte superior de la página, en **multi-factor
    authentication**, seleccione **users**.

> ![A screenshot of a computer Description automatically
> generated](./media/image7.png)

11. En la lista de usuarios, seleccione la casilla junto a **Alex
    Wilber**.

12. En la página de Alex Wilber, seleccione **Enable**.

> ![A screenshot of a computer Description automatically
> generated](./media/image8.png)

13. En el mensaje **About enabling multi-factor auth**,
    seleccione **enable multi-factor auth**.

> ![A screenshot of a computer Description automatically
> generated](./media/image9.png)

14. En el mensaje **Updates successful**, seleccione **close**. Tome
    nota que el **Multi-Factor Auth Status** para Alex Wilber ahora
    es **Enabled**.

> ![A screenshot of a computer Description automatically
> generated](./media/image10.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image11.png)

15. Cierre Microsoft Edge.

Tarea 3: Registre y Valide MFA

1.  Cambie a [**SEA-WS3**](urn:gd:lg:a:select-vm). En el taskbar,
    seleccione **Microsoft Edge**.

2.  En la barra de,
    introduzca !\![**outlook.office.com**](urn:gd:lg:a:send-vm-keys)!!
     y presione Enter.

3.  En la página **Pick an account**,
    seleccione !\![**AlexW@M365xXXXXXXX.onmicrosoft.com**](mailto:AlexW@M365xXXXXXXX.onmicrosoft.com)!!

> ![A screenshot of a computer Description automatically
> generated](./media/image12.png)

4.  En la página **Enter password**, introduzca !!**P@55w.rd1234**!! Y
    seleccione **Sign in**.

5.  En la página **More information required**, seleccione **Next**. Se
    abre la página Keep you account secure.

> ![A screenshot of a computer Description automatically
> generated](./media/image13.png)
>
> Normalmente, puede querer usar el Microsoft Authenticator app para
> gestionar multi-factor authentication. Pero para este escenario del
> laboratorio, va a usar mensajes de texto.

6.  En la página **Keep your account secure**, seleccione **I want to
    set up a different method**.

> ![A screenshot of a computer Description automatically
> generated](./media/image14.png)

7.  En el cuadro de diálogo **Choose a different method**,
    seleccione **Phone**, y luego seleccione **Confirm**.

> ![A screenshot of a computer Description automatically
> generated](./media/image15.png)

8.  En la página **Phone**, introduzca su número de celular que puede
    recibir textos y seleccione **Next**.

> ![A screenshot of a computer screen Description automatically
> generated](./media/image16.png)

9.  Después de recibir el código de verificación como mensaje de texto,
    introduzca el código en la casilla en la página **Phone** y luego
    seleccione **Next**.

> ![](./media/image17.png)

10. En el mensaje SMS verified, seleccione **Next** y luego
    seleccione **Done**.

> ![A screenshot of a computer screen Description automatically
> generated](./media/image18.png)
>
> ![](./media/image19.png)

11. En el mensaje Stay signed in, seleccione **No**.

> ![A screenshot of a computer error Description automatically
> generated](./media/image20.png)
>
> Outlook en el Web abre el inbox de Alex Wilber.

12. En la esquina superior derecha, seleccione el **Account manager for
    Alex Wilber** y luego seleccione **Sign out**.

> ![](./media/image21.png)
>
> **Ojo**: los usuarios solo tienen que registrarse la primera vez que
> usen MFA. Los próximos inicios de sesión solo requieren proporcionar
> el código de validación que recibió como texto en el número que
> introduzcó a la hora de registración.

13. En la barra de direccione,
    introduzca !\![**outlook.office.com**](urn:gd:lg:a:send-vm-keys)!!
     y presione Enter.

14. En la página **Pick an account**,
    seleccione !!**AlexW@M365xXXXXXXXX.onmicrosoft.com**!!

15. En la página **Enter password**, introduzca !!**P@55w.rd1234**!! y
    seleccione **Sign in**.

> ![A screenshot of a computer error Description automatically
> generated](./media/image22.png)
>
> Se abre el prompt **Verify your identity**. Note que contiene las
> últimas dos cifras de su número de teléfono.

16. En el prompt **Verify your identity**, seleccione su número de
    teléfono de texto.

17. En la página **Enter code**, introduzca el código mandado a su
    número de celular, y luego seleccione **Verify**.

> ![A screenshot of a computer error message Description automatically
> generated](./media/image23.png)
>
> Note que puede seleccionar una casilla para que no pida una
> verificación de nuevo en los próximos 30 días.

18. Como as **Microsoft Authenticator App** asegura más seguridad y una
    experiencia fluida, se le pedirá configurarla, pero por ahora haga
    clic en **Skip for now**

> ![A screenshot of a computer error Description automatically
> generated](./media/image24.png)

19. En el mensaje Stay signed in, seleccione **No**. Outlook en el Web
    abre el inbox de Alex Wilber.

> ![A screenshot of a computer error Description automatically
> generated](./media/image25.png)

20. En la esquina superior derecha, seleccione el **Account manager for
    Alex Wilber** y luego seleccione **Sign out**.

> ![A computer screen shot of a computer screen Description
> automatically generated](./media/image26.png)

21. Cierre Microsoft Edge.

Tarea 3: Quite el per-user MFA

1.  Cambie a [**SEA-SVR1**](urn:gd:lg:a:select-vm).
    En [**SEA-SVR1**](urn:gd:lg:a:select-vm), si es necesario, inicie
    sesión
    como [**Contoso\Administrator**](urn:gd:lg:a:send-vm-keys) con la
    contraseña !\![**Pa55w.rd**](urn:gd:lg:a:send-vm-keys)!! y cierre
    **Server Manager**.

2.  En el taskbar seleccione **Microsoft Edge**, navegue a **Microsoft
    Entra admin center** !!**https://Entra.Microsoft.com**!!

3.  Inicie sesión con las **Office 365 Tenant admin** credentials.

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)
>
> Se abre **Microsoft Entra admin center**.

4.  En el **Microsoft Entra admin center**, en el panel de navegación,
    expanda **Identity**, y luego seleccione **Users**.

5.  Seleccione **All users** y luego en la parte superior del panel de
    resultados **Per-user MFA**. Puede que necesite seleccionar los tres
    puntos para ver la opción **Per-user MFA**.

> ![A screenshot of a computer Description automatically
> generated](./media/image3.png)

6.  En la parte superior de la página, en **multi-factor
    authentication**, seleccione **users**.

7.  En la lista de usuarios, seleccione la casilla junto a **Alex
    Wilber**.

> Tome nota que el **Multi-Factor Auth Status** para Alex Wilber ahora
> es **Enforced** (antes era Enabled). Esto porque Alex se ha registrado
> y ahora usa MFA.
>
> ![A screenshot of a computer Description automatically
> generated](./media/image27.png)

8.  En la página de Alex Wilber, seleccione **Manage user settings.**

> ![A screenshot of a computer Description automatically
> generated](./media/image28.png)

9.  En la casilla Manage user settings, seleccione la casilla de
    verificación junto a las tres opciones, seleccione **save** y luego
    seleccione **close**.

> ![A screenshot of a computer Description automatically
> generated](./media/image29.png)
>
> Estas opciones se quitarán todas las configuraciones MFA guardadas
> para Alex.
>
> ![A white rectangular frame with black border Description
> automatically generated](./media/image30.png)

10. En la lista de usuario, seleccione la casilla junto a **Alex
    Wilber**.

11. En la página de Alex Wilber, seleccione **Disable**.

> ![A screenshot of a computer Description automatically
> generated](./media/image31.png)

12. En el mensaje **Disable multi-factor authentication**,
    seleccione **yes**.

> ![](./media/image32.png)

13. En el mensaje **Updates successful**, seleccione **close**.

> ![A white screen with black text Description automatically
> generated](./media/image33.png)
>
> Tome nota que el **Multi-Factor Auth Status** para Alex Wilber ahora
> es **Disabled**.
>
> ![A screenshot of a computer Description automatically
> generated](./media/image34.png)

14. Cierre Microsoft Edge.

**Resultados**: Después de completar este ejercicio, habrá configurado
el per-user multi-factor authentication.

Ejercicio 2: Configure el multi-factor authentication con conditional
access

**Escenario**

Para proporcionar seguridad adicional para las instancias de inicios de
sesión de usuarios, necesita configurar y probar multi-factor
authentication (MFA). Decide que un conditional access policy
proporciona una flexibilidad mejor para sus requisitos de MFA. Alex
Wilber ha aacordado validar las configuraciones para usted.

Tarea 1: Valide el sign-in antes de habilitar conditional access con MFA

1.  Cambie e inicie sesión
    en [**SEA-WS3**](urn:gd:lg:a:select-vm) como !\![**Admin**](urn:gd:lg:a:send-vm-keys)!!
     con la contraseña !\![**Pa55w.rd**](urn:gd:lg:a:send-vm-keys)!!

2.  En el taskbar, seleccione **Microsoft Edge**. En la barra de
    direcciones,
    introduzca !\![**outlook.office.com**](urn:gd:lg:a:send-vm-keys)!! y
    presione Enter.

3.  En la página **Sign in**,
    introduzca !!**AlexW@M365xXXXXXXX.onmicrosoft.com**!!  y luego
    seleccione **Next**.

4.  En la página **Enter password**, introduzca !!**P@55w.rd1234**!!  y
    seleccione **Sign in**. En el prompt Edge Save password prompt,
    seleccione **Save**.

> Se abre Outlook en el Web. Tome nota que solo se requiere una
> contraseña para iniciar sesión en Outlook on the Web.

5.  En la esquina superior derecha, seleccione **Account manager for
    Alex Wilber** y luego seleccione **Sign out**.

> ![A screenshot of a computer Description automatically
> generated](./media/image1.png)

6.  Cierre Microsoft Edge.

Tarea 2: Configure conditional access con MFA

1.  Cambie a [**SEA-SVR1**](urn:gd:lg:a:select-vm).
    En [**SEA-SVR1**](urn:gd:lg:a:select-vm), si es necesario, inicie
    sesión
    como [**Contoso\Administrator**](urn:gd:lg:a:send-vm-keys) con la
    contraseña !\![**Pa55w.rd**](urn:gd:lg:a:send-vm-keys)!!  y
    cierre **Server Manager**.

2.  En el taskbar seleccione **Microsoft Edge**, navegue a **Microsoft
    Entra admin center** !!**https://Entra.Microsoft.com**!!

3.  Inicie sesión con las **Office 365 Tenant admin**.

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)
>
> Se abre **Microsoft Entra admin center**.

4.  En el **Microsoft Entra admin center**, en el panel de navegación,
    expanda **Identity**, y luego expanda **Protection**, y por fin
    **Conditional Access.**

> ![A screenshot of a computer Description automatically
> generated](./media/image35.png)

5.  En la página **Conditional Access**, seleccione **Policies**, y
    seleccione **+ New policy**.

> ![A screenshot of a computer Description automatically
> generated](./media/image36.png)

6.  En la página **New Conditional access policy**, en el cuadro
    de **Name**, introduzca !\![**Contoso MFA
    Policy**](urn:gd:lg:a:send-vm-keys)!!.

7.  En **Assignments**, seleccione **0 users or workload identities
    selected**.

> ![A screenshot of a computer Description automatically
> generated](./media/image37.png)

8.  En el panel Users and groups, seleccione la opción junto a **Select
    users and groups** y luego seleccione la casilla junto a **Users and
    groups**.

9.  En la página **Select**, seleccione **Alex Wilber** y luego
    seleccione **Select**.

> ![A screenshot of a computer Description automatically
> generated](./media/image38.png)
>
> Note que normalmente especificaría un grupo, pero para este ejercicio
> solo vamos a probar esta configuración para Alex Wilber.

10. Seleccione **No target resources selected** en Target resources y
    haga clic en **Select apps**.

> ![A screenshot of a computer Description automatically
> generated](./media/image39.png)

11. En la página **Select**, seleccione la casilla junto a **Office
    365** y luego seleccione **Select**.

> ![A screenshot of a computer Description automatically
> generated](./media/image40.png)

12. En **Access controls**, en la sección **Grant**, seleccione **0
    controls selected**.

> ![A screenshot of a computer Description automatically
> generated](./media/image41.png)

13. En la página **Grant**, seleccione **Grant access**, seleccione la
    casilla junto a **Require multi-factor authentication**, y luego
    haga clic en **Select**.

> ![A screenshot of a computer Description automatically
> generated](./media/image42.png)

14. En **Enable policy**, seleccione **On**.

15. Seleccione **Create** para crear el Contoso MFA Policy. Note que se
    enlista la política con un Estado a **On**.

> ![A screenshot of a computer Description automatically
> generated](./media/image43.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image44.png)

16. En el **Microsoft Entra admin center**, seleccione **Users**. En la
    lista de usuarios, seleccione **Alex Wilber**.

> ![A screenshot of a computer Description automatically
> generated](./media/image45.png)

17. En la página Alex Wilber, seleccione **Authentication methods**.

> ![](./media/image46.png)
>
> Note que ya se ha configurado un número para Alex

18. Cierre Microsoft Edge.

Tarea 3: Valide el conditional access MFA

1.  Cambie a [**SEA-WS3**](urn:gd:lg:a:select-vm). En el taskbar,
    seleccione **Microsoft Edge**.

2.  En el address bar,
    introduzca !\![**outlook.office.com**](urn:gd:lg:a:send-vm-keys)!!
     y presione Enter.

3.  En la página **Pick an account**, seleccione
    !!**AlexW@M365xXXXXXXX.onmicrosoft.com**!!

> ![A screenshot of a computer Description automatically
> generated](./media/image12.png)

4.  En la página **Enter password**, introduzca !!**P@55w.rd1234**!! y
    seleccione **Sign in**.

5.  En el prompt **Verify your identity**, seleccione su número celular
    del texto.

> ![A screenshot of a computer error Description automatically
> generated](./media/image22.png)

6.  En la página **Enter code**, introduzca el código mandado a su
    número, y luego seleccione **Verify**.

> ![A screenshot of a computer error message Description automatically
> generated](./media/image23.png)
>
> Note que puede seleccionar una casilla para que no pida una
> verificación de nuevo para los siguientes 30 días.

7.  En el mensaje Stay signed in, seleccione **No**. Se abre Outlook on
    the Web al inbox de Alex Wilber.

> ![A screenshot of a computer error Description automatically
> generated](./media/image25.png)

8.  En la esquina superior derecha, seleccione el **Account manager for
    Alex Wilber** y luego seleccione **Sign out**.

> ![A computer screen shot of a computer screen Description
> automatically generated](./media/image26.png)

9.  Cierre Microsoft Edge.

Tarea 4: Quite el conditional access MFA

1.  Cambie a [**SEA-SVR1**](urn:gd:lg:a:select-vm).
    En [**SEA-SVR1**](urn:gd:lg:a:select-vm), si es necesario, inicie
    sesión
    como [**Contoso\Administrator**](urn:gd:lg:a:send-vm-keys) con la
    contraseña !\![**Pa55w.rd**](urn:gd:lg:a:send-vm-keys)!!  y
    cierre **Server Manager**.

2.  En el taskbar seleccione **Microsoft Edge**, navegue a **Microsoft
    Entra admin center**  !!**https://Entra.Microsoft.com**!!

3.  Inicie sesión con las **Office 365 Tenant admin** credentials.

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)
>
> Se abre **Microsoft Entra admin center**.

4.  En el **Microsoft Entra admin center**, en el panel de navegación,
    expanda **Identity**, y luego expanda **Protection**, y por fin
    **Conditional Access.**

> ![A screenshot of a computer Description automatically
> generated](./media/image35.png)

5.  En la página **Conditional Access** seleccione **Policies** y luego
    seleccione **Contoso MFA Policy**.

6.  En la página **Contoso MFA Policy**, seleccione **Delete** y luego
    seleccione **Delete**.

> ![A screenshot of a computer Description automatically
> generated](./media/image47.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image48.png)

7.  Para el Delete confirmation, haga clic en el botón Delete.

> ![A screenshot of a computer error Description automatically
> generated](./media/image49.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image50.png)

8.  Cierre Microsoft Edge.

**Resultados**: Después de completar este ejercicio, habrá configurado
multi-factor authentication con un conditional access policy.
