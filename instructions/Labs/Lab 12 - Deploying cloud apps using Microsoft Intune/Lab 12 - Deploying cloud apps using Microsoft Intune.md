Lab12 - Bereitstellen von Cloud-Apps mit Microsoft Intune

**Zusammenfassung**

In diesem Lab erstellen und implementieren Sie cloudbasierte Apps
mithilfe von Intune und der Unternehmensportal-Website.

**Voraussetzungen**

Die folgenden Übungen müssen vor diesem Lab abgeschlossen werden:

1.  Labs \#1 - Verwalten von Identitäten in Microsoft Entra ID

2.  Labs \#2 - Synchronisieren von Identitäten mit Microsoft Entra
    Connect

3.  Labs \#5 - Verwalten der Geräteregistrierung bei Microsoft Intune

4.  Labs \#6 - Registrieren von Geräten bei Microsoft Intune

5.  Labs \#7 - Erstellen und Bereitstellen von Konfigurationsprofilen

**Hinweis**: Sie benötigen außerdem ein Mobiltelefon, das
Textnachrichten empfangen kann, die zum Sichern der Windows
Hello-Anmeldeauthentifizierung bei Microsoft Entra ID verwendet werden.

Übung 1: Hinzufügen einer Microsoft Store-App zu Microsoft Intune

**Szenario**

Sie verwenden Microsoft Intune, um Desktops und Apps für die Contoso
Corporation zu verwalten. Die Forschungsabteilung stellt häufig eine
Verbindung mit verschiedenen Servern her, um Aufgaben auszuführen, und
hat darum gebeten, dass die Microsoft Remote Desktop-App für
Forschungsmitglieder zur Installation bei Bedarf verfügbar ist.
Microsoft Remote Desktop ist im Microsoft Store verfügbar, aber Sie
entscheiden sich, die App Intune hinzuzufügen, damit Benutzer über die
Unternehmensportal-Website darauf zugreifen können. Ein
Forschungsmitglied namens Aaron Nicholls hat sich bereit erklärt, den
Installationsprozess zu testen, nachdem Sie die App im Portal
veröffentlicht haben.

Aufgabe 1: Hinzufügen von Microsoft Remote Desktop zu Microsoft Intune

1.  Melden [***Sie sich auf
    SEA-SVR1***](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17)
    bei Bedarf als
    [**Contoso\Administrator**](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17)
    mit dem Kennwort an !\![**Pa55w.rd**](urn:gd:lg:a:select-vm)!! und
    schließen Sie **den Server-Manager**.

2.  Wählen Sie in der Taskleiste**Microsoft Edge**.

3.  Geben Sie in Microsoft Edge!!
    [**https://Intune.microsoft.com**](urn:gd:lg:a:select-vm) !! ein in
    der Adressleiste und drücken Sie dann **Enter**.

4.  Melden Sie sich mit den Anmeldeinformationen für den Office
    365-Mandanten auf der Registerkarte Home an.

5.  Auf der **Microsoft Intune admin center**, wählen Sie **Apps** aus.

> ![A screenshot of a computer Description automatically
> generated](./media/image1.png)

6.  Auf der **Apps** Seite, wählen Sie im Navigationsbereich die Option
    **All apps**.

7.  Wählen Sie im Detailbereich **+Add**.

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)

8.  Auf der **Select app type** Seite, klicken Sie auf das
    Dropdown-Menü, und wählen Sie dann **Microsoft store app (new)**
    aus.

> ![A screenshot of a computer Description automatically
> generated](./media/image3.png)
>
> Lesen Sie die Informationen zur Microsoft Store-App, und klicken Sie
> dann auf **Select**. Die Seite **Add App** wird geöffnet.

9.  Auf der **App information** Seite, klicken Sie auf **Search the**
    **Microsoft Store app (new**.

> ![A screenshot of a computer Description automatically
> generated](./media/image4.png)

10. Suchen Sie auf der Registerkarte **Search the** **Microsoft Store
    app (new)** nach !\![**Microsoft Remote
    Desktop**](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17)!!
    Klicken Sie dann auf die Schaltfläche **Select**.

> ![A screenshot of a computer Description automatically
> generated](./media/image5.png)

11. Geben Sie auf der Registerkarte App hinzufügen die folgenden
    Informationen ein, und wählen Sie dann **Next**:

    - Category: **Business**

    - Show this as a featured app in the Company Portal: **Yes**

> ![A screenshot of a computer Description automatically
> generated](./media/image6.png)

12. Auf der Schaltfläche **Assignments**, klicken Sie auf **+ Add
    group**

> ![A screenshot of a computer Description automatically
> generated](./media/image7.png)

13. Auf der Seite **Select groups**, wählen Sie **Research,
    Sales** group, und klicken Sie dann auf **Select**.

> ![A screenshot of a computer Description automatically
> generated](./media/image8.png)

14. Klicken Sie auf die Schaltfläche **Next**.

> ![A screenshot of a computer Description automatically
> generated](./media/image9.png)

15. Klicken Sie auf der Registerkarte Review + create auf die
    Schaltfläche **Create**.

> ![](./media/image10.png)

16. Die Seite Microsoft Remote Desktop wird geöffnet.

> Notieren Sie sich die Knoten Eigenschaften, Geräteinstallationsstatus
> und Benutzerinstallationsstatus.
>
> ![A screenshot of a computer Description automatically
> generated](./media/image11.png)

Aufgabe 2: Erzwingen der Richtliniensynchronisierung über die Microsoft
Intune-Konsole

1.  In **Microsoft Intune admin center**, wählen Sie **Devices** und
    wählen Sie dann **All devices**.

2.  Wählen Sie im Detailbereich **SEA-WS1**.

> ![A screenshot of a computer Description automatically
> generated](./media/image12.png)

3.  Wählen Sie auf dem Blatt **SEA-WS1** die Option **Sync** aus und
    wenn Sie dazu aufgefordert werden, wählen Sie **Yes**.

> ![A screenshot of a computer Description automatically
> generated](./media/image13.png)
>
> Microsoft Intune kontaktiert das Gerät und synchronisiert alle
> Richtlinien. Dies kann bis zu 5 Minuten dauern.

Aufgabe 3: Installieren einer App der Unternehmensportal-Website

1.  Melden Sie sich bei als **Cindy White** mit ihren Zugangsdaten
    !!Cindy@M365xXXXXXX.onmicrosoft.com!! an mit Passwort
    !!**P@55w.rd1234**!! oder mit der PIN !!**102938**!!

2.  Wählen Sie in der Taskleiste **Microsoft Edge**.

3.  Wählen Sie bei Bedarf auf der Seite **Welcome to Microsoft
    Edge** die Option **Confirm and continue**. Schließen Sie die
    Willkommensseite.

4.  Navigieren Sie in der Adressleiste
    zu!\![**https://portal.manage.microsoft.com**](urn:gd:lg:a:send-vm-keys)!!

5.  Melden Sie sich als !!**Cindy@M365xXXXXXX.onmicrosoft.com**!!

> ![](./media/image14.png)

6.  Wählen Sie im Contoso-Webportal die Option **Devices**.

> ![A screenshot of a computer Description automatically
> generated](./media/image15.png)

7.  Wählen Sie auf der Seite Geräte die Option **Tap here to tell us
    which device you're using or add a new device**.

> ![](./media/image16.png)

8.  Wählen Sie im Dialogfeld **Which device are you using** die Option
    neben **SEA-WS1** aus, und klicken Sie dann auf die Schaltfläche
    **Select**.

> ![A screenshot of a computer Description automatically
> generated](./media/image17.png)
>
> Beachten Sie, dass sich die Meldung jetzt in Apps wird installiert,
> auf: **SEA-WS1**
>
> ![](./media/image18.png)

9.  Wählen Sie in der oberen linken Ecke die Navigationsschaltfläche
    aus, und wählen Sie dann **Downloads & updates**.

> ![A screenshot of a computer Description automatically
> generated](./media/image19.png)

10. Überprüfen Sie in den aufgelisteten Ergebnissen den Status, als
    sollte die **Microsoft Remote Desktop** App angezeigt werden
    **Installed**.

> Hinweis: Es kann bis zu 10 bis 20 Minuten dauern, bis die App
> angezeigt wird.
>
> ![A screenshot of a computer Description automatically
> generated](./media/image20.png)

11. Klicken Sie auf das **Start menu** und vergewissern Sie sich, dass
    **Remote Desktop** im Startmenü angezeigt wird.

> ![A screenshot of a computer Description automatically
> generated](./media/image21.png)

**Ergebnisse**: Nach Abschluss dieser Übung haben Sie erfolgreich eine
Microsoft Store-App aus Microsoft Intune hinzugefügt und installiert.

Übung 2: Konfigurieren und Bereitstellen von Microsoft 365 Apps über
Microsoft Intune

**Szenario**

Alle Benutzer der Forschungsabteilung bei Contoso benötigen Microsoft
365 Apps. Sie wurden gebeten, die 64-Bit-Versionen von Microsoft Excel,
Outlook, PowerPoint und Word auf ihren Windows-Geräten bereitzustellen.
Sie müssen auch sicherstellen, dass sie für den aktuellen Kanal für
Updates konfiguriert sind.

Aufgabe 1: Überprüfen der installierten Apps auf SEA-WS1

1.  Wählen Sie auf [***SEA-WS1***](urn:gd:lg:a:send-vm-keys) auf der
    Taskleiste **Start** und dann die App **Setting** aus.

> ![A screenshot of a computer Description automatically
> generated](./media/image22.png)

2.  In der **Settings** app, wählen Sie **Apps**, und dann **Apps &
    features**.

> ![A screenshot of a computer Description automatically
> generated](./media/image23.png)
>
> Stellen Sie sicher, dass **Microsoft 365 Apps for Enterprise – en-us**
> nicht aufgeführt ist.
>
> ![A screenshot of a computer Description automatically
> generated](./media/image24.png)

3.  Schließen Sie alle geöffneten Fenster.

Aufgabe 2: Hinzufügen von Microsoft 365-Apps zu Microsoft Intune

1.  Wechseln Sie zu [***SEA-SVR1***](urn:gd:lg:a:send-vm-keys), während
    Sie im **Microsoft Intune Admin Center** die Option **Apps**.

2.  In **Apps | Overview**, wählen Sie **All Apps**. Wählen Sie im
    Detailbereich **+Add**.

> ![A screenshot of a computer Description automatically
> generated](./media/image25.png)

3.  In **Select app type**, unter **Microsoft 365 Apps**, wählen Sie
    **Windows 10 and later**, und klicken Sie dann auf **Select**.

> ![A screenshot of a computer Description automatically
> generated](./media/image26.png)

4.  Konfigurieren Sie auf dem Blatt **Microsoft 365 Apps hinzufügen**
    die folgenden Optionen, und wählen Sie **Next**:

    - Suite Name: !\![**Microsoft 365 Apps
      (Research)**](urn:gd:lg:a:select-vm)!!

    - Suite Description: !\![**Microsoft 365 Apps for the Research
      department at Contoso**](urn:gd:lg:a:select-vm) !! (Select **Edit
      Description** to enter this information.)

> ![A screenshot of a computer Description automatically
> generated](./media/image27.png)

5.  Erweitern Sie auf der Registerkarte **Configure app suite** die
    Dropdownliste Office-Apps auswählen, und wählen Sie die folgenden
    **Office-Apps** aus:

    - Excel

    - Outlook

    - PowerPoint

    - Word

> ![A screenshot of a computer Description automatically
> generated](./media/image28.png)

6.  Konfigurieren Sie auf der Registerkarte **Configure app suite** die
    folgenden Optionen, und wählen Sie **Next**:

    - Architecture: **64-bit**

    - Default file format: **Office Open XML Format**

    - Update channel: **Current Channel**

    - Accept the Microsoft Software License Terms on behalf of
      users: **Yes**

> ![A screenshot of a computer Description automatically
> generated](./media/image29.png)

7.  Auf der Schaltfläche **Assignments**, im Bereich **Required**,
    wählen Sie **Add group** aus.

> ![A screenshot of a computer Description automatically
> generated](./media/image30.png)

8.  Auf **Select groups**, wählen Sie **Research**, und wählen Sie
    **Select**.

> ![A screenshot of a group Description automatically
> generated](./media/image31.png)

9.  Wählen Sie **Next** aus.

> ![A screenshot of a computer Description automatically
> generated](./media/image32.png)

10. Auf der Schaltfläche **Review + Create**, wählen Sie **Create** aus.

> ![A screenshot of a computer Description automatically
> generated](./media/image33.png)

11. Auf der Seite **Microsoft 365 Apps (Research)**, wählen Sie
    **Properties**.

> ![A screenshot of a computer Description automatically
> generated](./media/image34.png)

12. Vergewissern Sie sich im Detailbereich, dass **Research** im
    Abschnitt **Assignment** unter **Required** aufgeführt ist.

> ![A screenshot of a computer Description automatically
> generated](./media/image35.png)

Aufgabe 3: Erzwingen der Richtliniensynchronisierung über die Microsoft
Intune-Konsole

1.  Im **Microsoft Intune admin center**, wählen Sie **Devices** und
    wählen Sie dann **All devices**.

2.  Wählen Sie im Detailbereich **SEA-WS1**.

> ![A screenshot of a computer Description automatically
> generated](./media/image36.png)

3.  Wählen Sie auf dem Blatt **SEA-WS1** die Option **Sync** aus, und
    wählen Sie bei Aufforderung **Yes** aus.

> ![A screenshot of a computer Description automatically
> generated](./media/image37.png)
>
> Microsoft Intune kontaktiert das Gerät und synchronisiert alle
> Richtlinien. Dies kann bis zu 5 Minuten dauern.

Aufgabe 4: Überprüfen, ob Microsoft 365 Apps installiert sind

1.  Wenn Sie bereits bei [*SEA-WS1*](urn:gd:lg:a:send-vm-keys?rc=10) als
    **Cindy White**.

> **Hinweis** – möglicherweise müssen Sie ca. 10 bis 15 Minuten warten,
> bis die Microsoft 365 Suite auf dem Gerät installiert ist.

1.  Melden Sie sich ab und melden Sie sich erneut bei als **Cindy
    White** mit ihren
    [Zugangsdaten!!**Cindy@M365xXXXXXX.onmicrosoft.com**](mailto:Zugangsdaten!!Cindy@M365xXXXXXX.onmicrosoft.com)!!
    und mit Passwort [!!**P@55w.rd1234**](mailto:!!P@55w.rd1234)!! an.

&nbsp;

2.  Wählen Sie auf [***SEA-WS1***](urn:gd:lg:a:send-vm-keys) auf der
    Taskleiste **Start** und dann die App **Settings** aus.

> ![A screenshot of a computer Description automatically
> generated](./media/image38.png)

3.  Wählen Sie in der App **Settings** die Option **Apps** und auf der
    Seite **Apps & Features** aus.

> ![A screenshot of a computer Description automatically
> generated](./media/image23.png)

4.  Suchen Sie nach !!**Microsoft 365**!! und stellen Sie sicher, dass
    **Microsoft 365 Apps for Enterprise – en-us** aufgeführt ist.

> ![A screenshot of a computer Description automatically
> generated](./media/image39.png)

5.  Schließen Sie die App **Settings** und wählen Sie die Schaltfläche
    **Start** aus.

6.  Im Abschnitt **Recommended** sollten Sie die neu installierten Apps
    sehen können, die aus den Microsoft 365 Apps in Microsoft Intune
    ausgewählt wurden.

> ![A screenshot of a computer Description automatically
> generated](./media/image40.png)

Aufgabe 5: Überwachen des App-Installationsstatus in Microsoft Intune

1.  Wechslen Sie zu [***SEA-SVR1***](urn:gd:lg:a:select-vm) und im
    **Microsoft Intune admin center**, wählen Sie **Apps** aus.

> ![](./media/image41.png)

2.  Auf **Apps | Overview**, wählen Sie **Monitor** und wählen Sie dann
    **App install status**.

> ![A screenshot of a computer Description automatically
> generated](./media/image42.png)

3.  Wählen Sie im Detailbereich **Microsoft 365 Apps (Research)**.

> ![A screenshot of a computer Description automatically
> generated](./media/image43.png)

4.  Überprüfen Sie im Detailbereich, ob unter **Device Statuts** und
    unter **Users Status,** Installiert **1** angezeigt wird.

> ![A screenshot of a computer Description automatically
> generated](./media/image44.png)
>
> **Hinweis**: Dies bedeutet, dass die App auf einem Gerät und für einen
> Benutzer installiert ist. Beachten Sie, dass es einige Zeit dauern
> kann, bis die Informationen angezeigt werden, und dass sie als
> **Install pending** angezeigt werden können.
>
> **Hinweis:** Sie können **Lab 13** starten und nach **30-45** Minuten
> erneut überprüfen.

![A screenshot of a computer Description automatically
generated](./media/image45.png)

5.  Wählen Sie **Device install status** aus.

> Im Detailbereich sehen Sie die Geräte, auf denen die App installiert
> ist, sowie den Namen des Benutzers. In der Spalte **Device Name**
> sollte **SEA-WS1** und in der Spalte **Status** \>**Installed**
> aufgeführt sein. Das bedeutet, dass die App auf **SEA-WS1**
> installiert ist.
>
> ![A screenshot of a computer Description automatically
> generated](./media/image46.png)

6.  In **Microsoft Intune admin center**, wählen Sie **Devices** aus.

7.  In **Devices | Overview**, wählen Sie **All devices** und wählen Sie
    dann im Detailbereich **SEA-WS1**.

> ![A screenshot of a computer Description automatically
> generated](./media/image47.png)

8.  In **SEA-WS1**, wählen Sie **Managed Apps** aus.

9.  In **SEA-WS1 | Managed Apps**, wählen Sie im Detailbereich die
    Option **Microsoft 365 Apps (Research)** aus.

> ![A screenshot of a computer Description automatically
> generated](./media/image48.png)
>
> Im Fenster **Microsoft 365 Apps (Research) – Installation Details**
> können Sie den gesamten Lebenszyklus der Anwendung anzeigen, d. h.
> wann sie erstellt, zugewiesen wurde, die Installationszeit und den
> Installationsstatus sowie den Zeitpunkt, zu dem das Gerät das letzte
> Mal eingecheckt wurde (synchronisiert mit Microsoft Intune).
>
> ![A screenshot of a computer Description automatically
> generated](./media/image49.png)

10. Schließen Sie alle geöffneten Fenster.

**Ergebnisse**: Nach Abschluss dieser Übung haben Sie Microsoft 365 Apps
von Microsoft Intune erfolgreich konfiguriert und bereitgestellt.
