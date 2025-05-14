Laboratorio 17 – Configurar y validar el device compliance

**Resumen**

En este laboratorio, valida el device compliance al configurar las
políticas y el conditional access rule asociado usado para determinar el
estado de un managed device.

**Prerrequisitos**

Debe completar los siguientes following laboratorios antes de este
laboratorio:

- Laboratorio \#1-Gestionar Identities en Microsoft Entra ID

- Laboratorio \#2-Sincronizar Identities mediante Microsoft Entra
  Connect

- Laboratorio \#5-Gestione Device Enrollment en Microsoft Intune

- Laboratorio \#6-Inscripción de dispositivos en Microsoft Intune

- Laboratorio \#7-Crear e implementar los Configuration Profiles

Ejercicio 1: Configurar los compliance policies.

**Escenario**

A Contoso le gustaría asegurar que los dispositivos Windows que se
inscriben en Microsoft Intune cumplen una especificación de
configuración mínima. Se requieren las siguientes específicaciones:

- Minimum Windows operating system version: 10.0.19041.329

- Se requiere Microsoft Defender Antimalware.

Si un dispositivo cumple estos requisitos, será marcado como compliant.
Si un dispositivo no lo haec, será marcado como non-compliant.

Tarea 1: Cree y asigne un compliance policy

1.  Inicie sesión en [***SEA-SVR1***](urn:gd:lg:a:select-vm) como
    !!**[Contoso\Administrator](urn:gd:lg:a:send-vm-keys)!!** Con la
    contraseña !!**[Pa55w.rd](urn:gd:lg:a:send-vm-keys)!!** 

2.  En el taskbar, seleccione **Microsoft Edge**. En Microsoft Edge,
    tecle !!**https://Intune.microsoft.com!!** en el address bar, y
    presione **Enter**.

3.  Inicie sesión con **Office 365 Tenant Admin credentials**.

> ![A screenshot of a computer Description automatically
> generated](./media/image1.png)

4.  Desde el panel de navegación seleccione **Devices**, luego
    seleccione **Compliance** en Manage devices.

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)

5.  En el **Compliance | Policies** blade, en el panel de detalles
    seleccione **+ Create Policy**.

> ![A screenshot of a computer Description automatically
> generated](./media/image3.png)

6.  En el **Create a policy** blade, proporcione el siguiente valor y
    cree **Create**:

    - Platform: **Windows 10 and later**

> ![A screenshot of a computer Description automatically
> generated](./media/image4.png)

7.  En la pestaña **Basics**, proporcione el siguiente valor y
    seleccione **Next**:

    - Name: !!**[Compliance1](urn:gd:lg:a:send-vm-keys)!!**

> ![](./media/image5.png)

8.  En la pestaña **Compliance settings**, expanda **Device Health** y
    revise las configuraciones disponibles.

> ![A screenshot of a computer Description automatically
> generated](./media/image6.png)

9.  En la pestaña **Compliance settings**, expanda **Device
    Properties**. En el campo **Minimum OS version**, tecle
    !!**[10.0.19041.329](urn:gd:lg:a:send-vm-keys)!!**

> ![A screenshot of a computer Description automatically
> generated](./media/image7.png)

10. En la pestaña **Compliance settings**, expanda **System Security**.
    Establezca el **Microsoft Defender Antimalware** a **Require** y
    seleccione **Next**.

> ![](./media/image8.png)

11. En la pestaña **Actions for noncompliance**, note que la
    configuración predeterminada de la action de **Mark device
    noncompliant** es **immediately**.

> ![A screenshot of a computer Description automatically
> generated](./media/image9.png)
>
> Revise cómo puede configurar el número de días después de los cual el
> dispositivo se marca como noncompliant, y configuration additional
> actions.

12. Seleccione **Next**. En la pestaña **Assignments**, seleccione **Add
    groups**. Seleccione **Windows Devices**, elija **Select**, y luego
    seleccione **Next**.

> ![A screenshot of a computer Description automatically
> generated](./media/image10.png)
>
> **Ojo**: Se creó el **Windows Devices** group en Crear e Implementar
> Configuration Profiles - Laboratorio.

13. Seleccione **Create**.

> ![A screenshot of a computer Description automatically
> generated](./media/image11.png)

14. En el menú de navegación, seleccione **Devices** y en el panel
    Devices navigation, seleccione **Compliance**.

> ![A screenshot of a computer Description automatically
> generated](./media/image12.png)

15. En la página **Compliance**, seleccione **Compliance settings**.

> ![A screenshot of a computer Description automatically
> generated](./media/image13.png)

16. En la página **Compliance policy settings**, junto a **Mark devices
    with no compliance policy assigned as**, seleccione **Not
    Compliant** y luego seleccione **Save**.

> ![A screenshot of a computer Description automatically
> generated](./media/image14.png)
>
> Esta configuración asegurará que cualquier dispositivo que no tenga un
> compliance policy asignado será marcado como **Not compliant**.

**Resultados**: Después de completar este ejercicio, habrá configurado
un compliance policy.

Ejercicio 2: Crear un conditional access policy para obligar el
cumplimiento.

**Escenario**

Cuando un usuario usa un dispositivo que se marca como non-compliant, no
debería poder acceder su e-mail. Le han preguntado que configure un
conditional access policy que ejerce este rule, y verifique si funciona
como esperado.

Tarea 1: Cree un conditional access policy

1.  En [***SEA-SVR1***](urn:gd:lg:a:select-vm), en el **Microsoft Intune
    admin center** seleccione **Devices**, y luego
    seleccione **Conditional access**.

> ![A screenshot of a computer Description automatically
> generated](./media/image15.png)

2.  Haga clic en **Policies** y luego seleccione **+ New policy**,

> ![A screenshot of a computer Description automatically
> generated](./media/image16.png)

3.  En el **New** blade, en el **Name** text box,
    tecle !\![**Conditional1!! **](urn:gd:lg:a:send-vm-keys)y luego
    seleccione **0 users or workload identities selected**.

> ![A screenshot of a computer Description automatically
> generated](./media/image17.png)

4.  En el **Users and groups** blade, seleccione el botón **All users**.

> ![A screenshot of a computer screen Description automatically
> generated](./media/image18.png)

5.  En el **New** blade, seleccione **No target resources selected**,
    seleccione el botón **Select apps**, seleccione !!**Office 365
    Exchange Online!!**, y haga clic en **Select**.

> ![A screenshot of a computer Description automatically
> generated](./media/image19.png)

6.  En el **New** blade, en la sección **Conditions**, seleccione **0
    conditions selected**.

> ![A screenshot of a computer Description automatically
> generated](./media/image20.png)

7.  En la lista de conditions, en **Device platforms**, seleccione **Not
    configured**. En la sección de **Configure**, seleccione **Yes**,
    seleccione el botón **Select device platforms**, seleccione la
    casilla **Windows**, y luego seleccione **Done**.

> ![A screenshot of a computer Description automatically
> generated](./media/image21.png)

8.  En el **New** blade en **Access controls**, en la sección **Grant**,
    seleccione **0 controls selected**.

9.  Seleccione la casilla **Require device to be marked as compliant**,
    y luego seleccione **Select**.

> ![A screenshot of a computer Description automatically
> generated](./media/image22.png)

10. En el **New** blade, seleccione **On** para la opción **Enable
    policy** y luego seleccione **Create**.

> ![A screenshot of a computer Description automatically
> generated](./media/image23.png)

11. Close Microsoft Edge.

Tarea 2: Verifique si funciona el conditional access policy

1.  Cambie a [***SEA-WS3***](urn:gd:lg:a:select-vm) e inicie
    sesión !!**[Admin](urn:gd:lg:a:send-vm-keys)!!** con la
    contraseña !!**[Pa55w.rd](urn:gd:lg:a:send-vm-keys)!!**.

2.  En [***SEA-WS3***](urn:gd:lg:a:select-vm), en el taskbar,
    seleccione **Microsoft Edge**. En Microsoft Edge,
    tecle [**outlook.office.com**](urn:gd:lg:a:send-vm-keys) y presione
    Enter.

3.  En el cuadro de diálogo pick an account,
    seleccione !!**Cindy@M365xXXXXXXX.onmicrosoft.com!!**

4.  En la página **Enter password**, introduzca !!**P@55w.rd12345!!** Y
    seleccione **Sign in**. Si aparece el prompt Microsoft Edge Save
    password, seleccione **Update**.

> ![A screenshot of a computer error Description automatically
> generated](./media/image24.png)

5.  Verifique que recibe el mensaje **"** **Sign in with your work
    account"**.

> ![A screenshot of a computer Description automatically
> generated](./media/image25.png)

6.  Seleccione **More details**. Debe ver más infomación sobre por qué
    se le han bloqueado.

> ![A screenshot of a computer error Description automatically
> generated](./media/image26.png)
>
> **Ojo**: Esto porque SEA-WS3 no está juntado a Microsoft Entra ID y no
> está gestionado por Microsoft Intune, por eso no marcado como
> compliant.

7.  **Cierre** la ventana del navegador.

8.  Cambie a [***SEA-WS1***](urn:gd:lg:a:select-vm), e inicie sesión
    como !!**Cindy@M365xXXXXXXX.onmicrosoft.com!!** Con la página
    **password**, introduzca !!**P@55w.rd12345!!** 

> **Ojo**: SEA-WS1 es un dispositivo Windows gestionado que está
> inscrito en Intune.

9.  En el taskbar, seleccione **Microsoft Edge**. En Microsoft Edge,
    tecle [**Outlook.office.com**](urn:gd:lg:a:send-vm-keys) y luego
    presione **Enter**.

10. Verifique que puede acceder el mailbox de Cindy.

> ![A screenshot of a computer Description automatically
> generated](./media/image27.png)
>
> **Ojo**: Esto porque **SEA-WS1** es un dispositivo gestionado y
> marcado como compliant.

11. Cierre Microsoft Edge y cierre la sesión
    de [***SEA-WS1***](urn:gd:lg:a:select-vm).

Tarea 3: Deshabilite el conditional access policy

1.  En [***SEA-SVR1***](urn:gd:lg:a:select-vm), en el **Microsoft Intune
    admin center** !\!<https://intune.microsoft.com>!!
    seleccione **Devices**, y seleccione **All devices**.

> ![](./media/image28.png)
>
> Note que **SEA-WS1** es compliant, por lo cual se le permitió a Cindy
> acceder a su mailbox.

2.  Desde el panel de navegación seleccione **Devices**, y
    seleccione **Conditional access**.

> ![](./media/image29.png)

3.  En la página de **Conditional Access**, seleccione **Policies**, y
    haga clic en **Conditional1**.

> ![A screenshot of a computer Description automatically
> generated](./media/image30.png)

4.  En la página **Conditional1**, en la parte inferior de la página,
    seleccione **Off** y luego seleccione **Save**.

> ![A screenshot of a computer Description automatically
> generated](./media/image31.png)

5.  Cierre Microsoft Edge.

**Resultados**: Después de completar este ejercicio, habrrá configurado
un conditional access policy para determinar el device compliance.
