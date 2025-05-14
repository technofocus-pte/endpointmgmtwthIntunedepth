Lab 23: Verwalten von Windows-Qualitäts- und Featureupdates

**Zusammenfassung**

In dieser Übung konfigurieren Sie die Einstellungen für
Windows-Qualitäts- und Featureupdates mithilfe von Intune.

**Voraussetzungen**

Die folgenden Übungen müssen vor diesem Lab abgeschlossen werden:

1.  Lab 01 – Verwalten der Geräteregistrierung bei Intune

2.  Lab 06 – Registrieren von Geräten bei Intune

3.  Lab 07 - Erstellen und Bereitstellen von Konfigurationsprofilen

**Hinweis**: Sie benötigen außerdem ein Mobiltelefon, das
Textnachrichten empfangen kann, die zum Sichern der Windows
Hello-Anmeldeauthentifizierung bei Azure AD verwendet werden.

**Szenario**

Sie wurden aufgefordert, einen Updatering so zu konfigurieren, dass er
sich nur auf die Geräte auswirkt, die Mitglied der Gruppe "Contoso
Developer Devices" sind. Diese Gruppe muss die folgenden Anforderungen
erfüllen:

- Quality update deferral period (days): **15**

- Feature update deferral period (days): **45**

- Option to pause Windows updates: **Disable**

- Option to check for Windows updates: **Enable**

- Delivery optimization: Download Mode: **HTTP only, no peering (0)**

Aufgabe 1: Überprüfen der aktuellen Updateeinstellungen für ein
einzelnes Gerät

1.  Wechseln Sie zu [***SEA-WS1***](urn:gd:lg:a:select-vm), melden Sie
    sich als **Cindy White** mit der PIN
    [**102938**](urn:gd:lg:a:select-vm) an.

2.  Wählen Sie **Start** und dann das Symbol **Settings** aus.

> ![](./media/image1.png)

3.  In Settings wählen Sie **Windows Update** aus.

> Beachten Sie, dass Sie die Möglichkeit haben, Updates für einen
> bestimmten Zeitraum anzuhalten.

4.  Auf der Seite **Windows Update**, wählen Sie **Advanced options**
    aus.

> ![](./media/image2.png)

5.  Wählen Sie auf der Seite **Advanced options** die Option **Delivery
    Optimization** aus.

> ![A screenshot of a computer Description automatically
> generated](./media/image3.png)

6.  Überprüfen Sie auf der Seite **Delivery Optimization**, ob die
    Option **Allow downloads from other PCs** aktiviert ist.

7.  Wählen Sie **Devices on the internet and my local network** aus.

> ![A screenshot of a computer Description automatically
> generated](./media/image4.png)

8.  In Settings wählen Sie **Windows Update** aus.

> ![A screenshot of a computer Description automatically
> generated](./media/image5.png)

9.  Wählen Sie **Advanced options**, und wählen Sie dann **Configured
    update policies** aus.

> ![A screenshot of a computer Description automatically
> generated](./media/image6.png)
>
> Beachten Sie, dass auf dem Gerät keine Aktualisierungsrichtlinien
> festgelegt sind.
>
> ![A screenshot of a computer Description automatically
> generated](./media/image7.png)

10. Wählen Sie im Navigationsbereich **Windows Update**.

Aufgabe 2: Überprüfen der angewendeten Einstellungen

1.  Auf der **Windows Update** Seite, wählen Sie **Update history** aus.

> ![A screenshot of a computer update Description automatically
> generated](./media/image8.png)

2.  Überprüfen Sie die aufgelisteten Updates, und wählen Sie dann
    **Uninstall updates** aus.

> ![A screenshot of a computer update Description automatically
> generated](./media/image9.png)

3.  Überprüfen Sie die Updates, die unter **Installed Updates**
    aufgeführt sind. Schließen Sie Installed Updates.

> ![A screenshot of a computer Description automatically
> generated](./media/image10.png)

4.  Schließen Sie die **Settings** app.

Aufgabe 3: Konfigurieren von Updateeinstellungen mithilfe von Intune

1.  Wechseln Sie zu [***SEA-SVR1,***](urn:gd:lg:a:send-vm-keys) und
    melden Sie sich als
    [**Contoso\Administrator**](urn:gd:lg:a:send-vm-keys) mit dem
    Kennwort [**Pa55w.rd**](urn:gd:lg:a:send-vm-keys) an.

2.  Wählen Sie in der Taskleiste **Microsoft Edge** aus.

3.  Geben Sie in Microsoft Edge
    [**https://intune.microsoft.com**](urn:gd:lg:a:send-vm-keys) in die
    Adressleiste ein, und drücken Sie dann **Enter**.

4.  Anmelden
    als[**admin@M365x19242953.onmicrosoft.com**](mailto:admin@M365x19242953.onmicrosoft.com) mit
    dem Passwort an.

5.  Wählen Sie im Navigationsbereich **Devices** und dann **Windows 10
    and later Updates** aus.

> ![](./media/image11.png)

6.  Auf der **Devices | Update rings for Windows 10 and later** Seite
    wählen Sie **Create profile** aus.

> ![](./media/image12.png)

7.  Geben Sie auf dem Blatt **Basics** die folgenden Informationen ein,
    und wählen Sie dann **Next**:

    - Name: !\![**Contoso Updates -
      standard**](urn:gd:lg:a:send-vm-keys)!!

    - Description: !\![**Standard Windows updates
      configuration**](urn:gd:lg:a:select-vm)!!

> ![](./media/image13.png)

8.  Geben Sie auf dem Blatt **Update ring settings** die folgenden
    Informationen ein, und wählen Sie dann **Next**:

    - Quality update deferral period
      (days): [**15**](urn:gd:lg:a:send-vm-keys)

    - Feature update deferral period
      (days): [**45**](urn:gd:lg:a:send-vm-keys)

    - Option to pause Windows updates: **Disable**

    - Option to check for Windows updates: **Enable**

> ![](./media/image14.png)

9.  Wählen Sie auf dem Blatt **Assignments** unter **Included Groups**
    die Option **Add groups**.

10. Auf **Select groups to include**, wählen Sie im **Suchfeld**\>
    **Contoso Developer devices** und wählen Sie dann **Select**.

> ![A screenshot of a computer Description automatically
> generated](./media/image15.png)
>
> ![](./media/image16.png)

11. Wählen Sie **Next** aus, und wählen Sie auf dem Blatt **Review +
    Create** die Option **Create** aus.

12. Wählen Sie in der Navigationsleiste **Configuration profiles**.

13. Auf **Devices | Configuration**, wählen Sie im Detailbereich die
    Option **Create policy**.

> ![](./media/image17.png)

14. Wählen Sie auf dem Blatt **Create a profil** die folgenden Optionen
    aus, und wählen Sie dann **Create**:

    - Platform: **Windows 10 and later**

    - Profile type: **Templates**

    - Template name: **Delivery Optimization**

> ![](./media/image18.png)

15. Geben Sie auf dem Blatt **Basics** die folgenden Informationen ein,
    und wählen Sie dann **Next**:

    - Name: !\![**Contoso Developer - Delivery
      optimization**](urn:gd:lg:a:send-vm-keys)!!

    - Description: !\![**Delivery optimization for
      Developer**](urn:gd:lg:a:send-vm-keys)!!

> ![](./media/image19.png)

16. Geben Sie auf dem Blatt **Configuration settings** die folgenden
    Informationen ein, und wählen Sie dann **Next**:

    - Download Mode: **HTTP only, no peering (0)**

> ![A screenshot of a computer Description automatically
> generated](./media/image20.png)

17. Wählen Sie auf dem Blatt **Assignments** unter **Included Groups**
    die Option **Add groups**.

18. Auf **Select groups to include**, wählen Sie **Contoso Developer
    devices** und wählen Sie dann **Select**.

> ![A screenshot of a computer Description automatically
> generated](./media/image21.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image22.png)

19. Wählen Sie zweimal **Next** aus, und wählen Sie auf dem Blatt
    **Review+Cretae** die Option **Create**.

> ![Screenshot](./media/image23.png)

Aufgabe 4: Überprüfen, ob die Updateeinstellungen des Geräts zentral
verwaltet werden

1.  Wechseln Sie zu [***SEA-WS1***](https://intune.microsoft.com).

2.  Wählen Sie **Start** und dann das Symbol **Settings** aus.

> ![](./media/image24.png)

3.  Wählen Sie in der App **Settings** die Option **Accounts** und
    wählen Sie dann **Access work or school** aus.

> ![A screenshot of a computer Description automatically
> generated](./media/image25.png)

4.  Im Bereich **Access work or school**, wählen Sie den Link
    **Connected to Contoso's Azure AD** und wählen Sie dann **Info**.

> ![A screenshot of a computer Description automatically
> generated](./media/image26.png)

5.  Wählen Sie im Dialogfeld **Areas Managed by Contoso** die Option
    **Sync**. Warten Sie, bis die Synchronisierung abgeschlossen ist.

> ![A screenshot of a computer Description automatically
> generated](./media/image27.png)

6.  Wählen Sie in der App **Settings\>Windows Update**.

> Beachten Sie, dass Sie Updates nicht anhalten können.

7.  Wählen Sie **Advanced options** aus.

> ![](./media/image28.png)

8.  Wählen Sie **Delivery Optimization** aus.

> ![A screenshot of a computer Description automatically
> generated](./media/image29.png)
>
> Beachten Sie, dass **Allow downloads from other PCs** nicht verfügbar
> ist.

9.  Wählen Sie in der **Einstellungen**-**App** \>**Windows Update**,
    **Advanced Options** und dann **Configured update policies** aus.

> ![](./media/image30.png)
>
> Notieren Sie sich alle Richtlinien, die auf dem Gerät festgelegt sind.

10. Schließen Sie alle geöffneten Apps und Fenster.

> **Hinweis**: Die Lab-Umgebung ist so konfiguriert, dass keine
> Windows-Updates angewendet werden können, um Verzögerungen und
> unbeabsichtigte Auswirkungen während der Labs zu vermeiden.
