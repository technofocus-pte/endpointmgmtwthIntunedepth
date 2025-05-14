**Lab 11- Überwachen von Geräte- und Benutzeraktivitäten in Intune**

**Zusammenfassung**

In dieser Übung überwachen Sie die Anmeldeaktivität der Benutzer,
Überwachungsprotokolle und Geräteaktivitäten.

**Voraussetzungen**

Die folgenden Übungen müssen vor diesem Lab abgeschlossen werden:

1.  Lab \#1 - Verwalten von Identitäten in Microsoft Entra ID

2.  Lab \#2 - Synchronisieren von Identitäten mit Microsoft Entra
    Connect

3.  Lab \#5 - Verwalten der Geräteregistrierung bei Microsoft Intune

4.  Lab \#6 - Registrieren von Geräten bei Microsoft Intune

5.  Lab \#7 - Erstellen und Bereitstellen von Konfigurationsprofilen

**Hinweis**: Sie benötigen außerdem ein Mobiltelefon, das
Textnachrichten empfangen kann, die zum Sichern der Windows
Hello-Anmeldeauthentifizierung bei Microsoft Entra ID verwendet werden.

**Szenario**

Sie müssen die Anmeldeaktivität von Cindy White und die allgemeinen
Informationen überprüfen, die in den Überwachungsprotokollen
bereitgestellt werden. Sie müssen auch die Hardware auf [*SEA-WS1
überprüfen*](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10)
und bestätigen, dass das diesem Gerät zugewiesene Konfigurationsprofil
erfolgreich angewendet wurde.

**Aufgabe 1: Überwachen der Benutzeraktivität**

1.  Wechseln Sie zu
    *[SEA-SVR1](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10)*
    und melden Sie sich bei Bedarf mit den angegebenen Zugangsdaten an.

2.  Navigieren Sie auf der **Microsoft Entra Admin** Center-Seite,
    wählen Sie **Users** aus, und klicken Sie dann auf **All Users**.

> ![](./media/image1.png)

3.  Navigieren Sie auf der Seite **Users** und wählen Sie **Allan
    Deyoung**.

> ![](./media/image2.png)

4.  Navigieren Sie auf der **Allan Deyoung-**Benutzerseite **und klicken
    Sie auf Sign-in logs**.

> ![A screenshot of a computer Description automatically
> generated](./media/image3.png)

5.  Auf der **Allan Deyoung | Sign-in logs** Seite, klicken Sie auf den
    ersten Eintrag unter dem **User sign-ins (interactive)**.

> ![A screenshot of a computer Description automatically
> generated](./media/image4.png)

6.  Wählen Sie jede der Hauptseiten aus, einschließlich **Basic
    info**, **Location**, **Device info**, **Authentication Details**
    und **Conditional Access**. Scrollen Sie nach unten und sehen Sie
    sich die Informationen auf jeder Seite an. Nachdem Sie die auf jeder
    Seite bereitgestellten Informationen sorgfältig überprüft haben,
    schließen Sie den Bereich.

> ![](./media/image5.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image6.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image7.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image8.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image9.png)

7.  Wählen Sie im Navigationsbereich Benutzer die Option **Audit logs**.

8.  Im Detailbereich werden Überwachungsinformationen zu administrativen
    Änderungen an Benutzern angezeigt. Untersuchen Sie die
    Informationen, indem Sie die verschiedenen Einträge auswählen.

> ![A screenshot of a computer Description automatically
> generated](./media/image10.png)
>
> ![](./media/image11.png)

**Aufgabe 2: Überwachen der Geräteaktivität**

1.  Wechseln Sie zum **Microsoft Intune Admin** Center-Fenster,
    navigieren Sie und klicken Sie auf **Devices**.

![](./media/image12.png)

2.  Wählen Sie im Navigationsbereich Geräte die Option **Overview**.

> ![A screenshot of a computer Description automatically
> generated](./media/image13.png)

3.  Scrollen Sie nach unten und lesen Sie Folgendes:

- Configuration policy assignment failures

- Noncompliant devices.

- Deployment status per Windows update ring.

> ![](./media/image14.png)

4.  Scrollen Sie nach unten zum Abschnitt **Manage Devices** und klicken
    Sie auf **Configuration**. Überprüfen Sie die Konfigurationsdetails.

> ![](./media/image15.png)

5.  Scrollen Sie nach oben, und wählen Sie **Alle Devices** aus. Klicken
    Sie in der Menüleiste **Devices | All devices** die Informationen zu
    den Geräten angezeigt, z. B. Gerätename, Verwaltet von, Besitz,
    Konformität, Betriebssystem und Betriebssystemversion. Klicken Sie
    auf **SEA-WS1**.

> ![](./media/image16.png)

6.  Wählen Sie im Navigationsbereich SEA-WS1 die Option **Hardware**
    aus, und untersuchen Sie die Hardwareinventur.

> ![A screenshot of a computer Description automatically
> generated](./media/image17.png)

7.  Wählen Sie im Navigationsbereich SEA-WS1 die Option **Discovered
    apps** aus**,** und untersuchen Sie den App-Bestand.

> ![A screenshot of a computer Description automatically
> generated](./media/image18.png)

8.  Wählen Sie im Navigationsbereich SEA-WS1 die Option **Device
    configuration** aus, und notieren Sie sich im Detailbereich die
    Gerätekonfigurationsprofile, die dem Gerät zugewiesen sind. In der
    Spalte **State** sollte **Succeeded** angezeigt werden, was
    bedeutet, dass die Profile erfolgreich auf das Gerät angewendet
    wurden.

> ![](./media/image19.png)

9.  Auf der Seite **SEA-WS1 | Device configuration**, klicken Sie auf
    **Contoso Developer – standard**.

> ![](./media/image20.png)

10. Auf **Contoso Developer – standard**, notieren Sie sich jede
    Einstellung, die Sie im Profil konfiguriert haben.

> Der **State** sollte **Succeeded** neben allen anzeigen.
>
> ![](./media/image21.png)

**Ergebnisse**: Nach Abschluss dieser Übung haben Sie die
Benutzeranmeldeaktivität, die Überwachungsprotokolle und die
Geräteaktivität erfolgreich überwacht.
