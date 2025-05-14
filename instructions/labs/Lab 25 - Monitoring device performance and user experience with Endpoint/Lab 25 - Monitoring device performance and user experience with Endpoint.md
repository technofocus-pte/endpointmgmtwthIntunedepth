# Laboratorio 25: Monitorear el device performance y user experience con Endpoint analytics

**Resumen**

En este laboratorio, habilitará Endpoint analytics para monitorear las
puntuaciones e insights de user experience.

**Prerrequisitos**

Debe seguir los siguientes laboratorios antes de este laboratorio:

- Laboratorio 05-Gestione Device Enrollment en Intune

- Laboratorio 06-Inscripción de dispositivos en Intune

- Laboratorio 07-Crear e implementar los Configuration Profiles

**Escenario**

Se le ha pedido monitorear el startup performance, application
reliability, y user experience, con qué frecuencia los usuarios
reinician su dispositivo. Para adquirir esta información, tiene que
habilitar Endpoint analytics.

### Tarea 1: Habilitar Endpoint analytics

1.  En [**SEA-SVR1**](urn:gd:lg:a:select-vm), si es necesario, inicie
    sesión
    como [**Contoso\Administrator**](urn:gd:lg:a:send-vm-keys) con la
    contraseña !\![**Pa55w.rd**](urn:gd:lg:a:send-vm-keys)!! y
    cierre **Server Manager**.

2.  En el taskbar, seleccione **Microsoft Edge**.

3.  En Microsoft Edge, tecle
    !\![**https://intune.microsoft.com**](https://intune.microsoft.com)!! en
    el address bar, y presione **Enter**.

4.  Inicie sesión
    como [**admin@M365x19242953.onmicrosoft.com**](urn:gd:lg:a:send-vm-keys) con
    la contraseña.

5.  En la página **Microsoft Intune admin center**,
    seleccione **Reports**.

6.  En el **Reports** blade, en **Analytics**, seleccione **Endpoint
    analytics**.

> ![](./media/image1.png)

7.  En la página **Endpoint analytics**, asegure que **Collect device
    data from** está establecido a **All cloud-managed devices**, y
    luego seleccione **Start**.

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)
>
> Tome nota del mensaje en la parte superior de la página Overview.
> Puede llevar unas 24 horas para que aparezcan las puntuaciones e
> insights en la página.
>
> ![A screenshot of a computer Description automatically
> generated](./media/image3.png)

8.  Cambie a [**SEA-WS1**](urn:gd:lg:a:select-vm) y reinicie el
    dispositivo.

9.  Inicie sesión como **Cindy White** con la contraseña
    : [**102938**](urn:gd:lg:a:send-vm-keys).

10. Cambie a [**SEA-SVR1**](urn:gd:lg:a:select-vm).

11. En la página **Microsoft Intune admin center**,
    seleccione **Devices** y luego seleccione **All devices**.

12. Seleccione **SEA-WS1**.

> ![](./media/image4.png)

13. En la página **SEA-WS1**, seleccione **Sync** y luego
    seleccione **Yes**.

> ![A screenshot of a computer Description automatically
> generated](./media/image5.png)

14. En la página **SEA-WS1**, en **Monitor**, seleccione **User
    experience**. ![A screenshot of a computer Description automatically
    generated](./media/image6.png)

15. Revise las pestañas **Endpoint analytics**, **Startup performance**,
    y **Application reliability**.

> ![A screenshot of a computer Description automatically
> generated](./media/image7.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image8.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image9.png)
>
> Puede que no haya ninguna información reportada debido al retraso del
> tiempo, sin embargo, lea los detalles visibles en cada pestaña.

16. En la página **Microsoft Intune admin center**,
    seleccione **Reports**.

17. En el **Reports** blade, en **Analytics**, seleccione **Endpoint
    analytics**.

> ![](./media/image10.png)
>
> Note que el mismo tipo de información está disponible en Endpoint
> analytics, sin embargo, se basa en todos los dispositivos inscritos.
>
> ![A screenshot of a computer Description automatically
> generated](./media/image11.png)

18. Navegue por los Reports disponibles en la página Endpoint analytics.

19. Cierre Microsoft Edge.

**Resultados**: Después de completar este ejercicio, habrá habilitado
Endpoint analytics para monitorear las puntuaciones e insights de device
performance y user experience.
