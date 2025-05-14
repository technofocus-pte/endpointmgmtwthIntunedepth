Laboratorio de práctica 26: Gestión de Update policies para iOS y iPadOS

**Resumen**

En este laboratorio, configurará un Update policy para usarlo en manejar
las actualizaciones del sistema operativo para iOS y iPadOS.

**Escenario**

Todos los desarrolladores en Contoso tienen iPhones y iPads en la
versión más reciente de iOS/iPadOS. Ha inscrito estos dispositivos a
través de Automated Device Enrollment de Apple y necesita configurar un
update policy para el OS del dispositivo. Necesita asegurar lo
siguiente:

- Version to install: Latest update.

- Only permit automatic updates to take place between Wednesday at 12AM
  to Thursday at 12AM.

Tarea 1: Cree un Update policy para dispositivos iOS/iPadOS

1.  En [***SEA-SVR1***](urn:gd:lg:a:select-vm), si es necesario, inicie
    sesión
    como [**Contoso\Administrator**](urn:gd:lg:a:send-vm-keys) con la
    contraseña [**Pa55w.rd**](urn:gd:lg:a:send-vm-keys) y
    cierre **Server Manager**.

2.  En el taskbar, seleccione **Microsoft Edge**.

3.  En Microsoft Edge,
    tecle [**https://intune.microsoft.com**](https://intune.microsoft.com) en
    el address bar, y presione **Enter**.

4.  Inicie sesión
    como [**admin@M365x19242953.onmicrosoft.com**](urn:gd:lg:a:send-vm-keys) con
    la contraseña.

5.  En la página **Microsoft Intune admin center**,
    seleccione **Devices**.

6.  En el **Devices|By platform** blade, en **Policy**, seleccione
    **iOS/iPadOS**.

> ![](./media/image1.png)

7.  Seleccione **Update Policies for iOS/iPadOS**

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)

8.  En el panel de detalles, seleccione **Create profile**.

9.  En la pestaña **Basics**, configure las siguientes opciones y
    seleccione **Next**:

    - Name: !\![**iOS/iPadOS update
      policy**](urn:gd:lg:a:send-vm-keys)!!

    - Description: !\![**Policy to manage system updates for iOS and
      iPadOS**](urn:gd:lg:a:send-vm-keys)!!

> ![](./media/image3.png)

10. En la pestaña **Update policy settings**, configure las siguientes
    opciones y seleccione **Next**:

    - Select version to install: **Latest update**

    - Schedule type: **Update during scheduled time**

    - Time zone: **UTC:00**

    - Time window:

    - Start day: **Wednesday**

      - Start time: **12 AM**

      - End day: **Thursday**

      - End time: **12 AM**

> ![](./media/image4.png)

11. En la pestaña **Assignments**, seleccione **Next**.

> ![A screenshot of a computer Description automatically
> generated](./media/image5.png)

12. En la pestaña **Review + create**, revise las configuraciones y
    seleccione **Create**.

13. En el **Devices | Update policies for iOS/iPadOS** blade, en el
    panel de detalles, verifique que se enlista **iOS/iPadOS update
    policy**.

> ![A screenshot of a computer Description automatically
> generated](./media/image6.png)

14. Cierre Microsoft Edge.

**Resultados**: Después de completar este ejercicio, habrá configurado
un Update policy para iOS y iPadOS.
