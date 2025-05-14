**Lab 8 - Verwenden eines Konfigurationsprofils zum Konfigurieren des
Kioskmodus**

**Zusammenfassung**

In dieser Übung verwenden wir Microsoft Intune, um ein
Konfigurationsprofil zum Ausführen des Einzel-App-Kioskmodus auf einem
Windows 11-Gerät zu erstellen und anzuwenden.

**Voraussetzungen**

Zu den folgenden Labs müssen vor diesem Lab abgeschlossen werden:

1.  Lab 05 – Verwalten der Geräteregistrierung bei Microsoft Intune

Hinweis: Sie benötigen außerdem ein Mobiltelefon, das Textnachrichten
empfangen kann, die zum Sichern der Windows
Hello-Anmeldeauthentifizierung bei der Entra ID verwendet werden.

**Übung 1: Erstellen und Anwenden eines Konfigurationsprofils**

**Szenario**

Sie wurden aufgefordert, **SEA-WS2** als Windows 11-Kiosk zu
konfigurieren, um Contoso-Besuchern das Surfen im Internet zu
ermöglichen. Sie müssen sicherstellen, dass der Kiosk wie folgt
konfiguriert ist:

1.  Eine einzige App, Vollbild-Kiosk.

2.  Automatische Anmeldung.

- Bietet Zugriff auf den Microsoft Edge-Browser, der im Modus
  Öffentliches Browsing (InPrivate) konfiguriert werden muss. Die
  Startseite sollte für http://bing.com konfiguriert sein.

**Aufgabe 1: Registrieren von SEA-WS2 bei Microsoft Intune**

1.  Melden Sie sich bei
    [*SEA-WS2*](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10)
    als **Admin** mit dem Kennwort von !!**Pa55w.rd**!! an.

2.  Wählen Sie auf der Taskleiste **Start** und dann **Settings**.

![](./media/image1.png)

3.  Wählen Sie im Fenster **Settings** die Option **Accounts**.

![A screenshot of a computer Description automatically
generated](./media/image2.png)

4.  Wählen Sie auf der Seite Konten die Option **Access work or school**
    aus.

![A screenshot of a computer Description automatically
generated](./media/image3.png)

5.  Auf der **Access work or school** Seite, wählen Sie **Connect** aus.

![A screenshot of a computer Description automatically
generated](./media/image4.png)

6.  Im **Microsoft account** Fenster, wählen Sie **Join this device to
    Microsoft Entra ID**.

![A screenshot of a computer screen Description automatically
generated](./media/image5.png)

7.  Geben Sie auf **Sign**
    [**in**!!**AllanD@M365xXXXXXX.onmicrosoft.com**](mailto:in!!AllanD@M365xXXXXXX.onmicrosoft.com)!!
    ein und wählen Sie dann **Next**.

![](./media/image6.png)

8.  Geben Sie auf der Seite **Enter Password** das Mandantenkennwort:
    !!**P@55w.rd1234**!! ein und wählen Sie dann **Sign in**.

![A screenshot of a computer Description automatically
generated](./media/image7.png)

9.  Wählen Sie im Dialogfeld **Make sure this is your organization** die
    Option **Join**.

![A screenshot of a computer error Description automatically
generated](./media/image8.png)

10. Auf der Seite **You're all set!** lesen Sie die Informationen und
    wählen Sie dann **Done**.

![A screenshot of a computer screen Description automatically
generated](./media/image9.png)

11. Vergewissern Sie sich, dass im Abschnitt **Access work or school**
    die Option **Connect to Contoso´s Azure AD** angezeigt wird.

![A screenshot of a computer Description automatically
generated](./media/image10.png)

12. Wählen Sie **Connected to Contoso's Azure AD** und wählen Sie dann
    **Info**.

![A screenshot of a computer Description automatically
generated](./media/image11.png)

13. Scrollen Sie nach unten, und wählen Sie dann **Sync**. Dadurch wird
    eine Gerätesynchronisierung mit Intune erzwungen.

![A screenshot of a computer Description automatically
generated](./media/image12.png)

14. Schließen Sie das Fenster **Settings**.

**Aufgabe 2: Erstellen der Gerätegruppe "Contoso Kiosk"**

1.  Wechseln Sie
    [auf](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10)
    dem *SEA-SVR1* zur Registerkarte **Microsoft Entra Admin Center**.
    Navigieren Sie, wählen Sie **Groups** aus, und klicken Sie dann auf
    **All Groups**.

![](./media/image13.png)

2.  Auf der Seite **Groups | All groups,** wählen Sie **New group** aus.

![A screenshot of a computer Description automatically
generated](./media/image14.png)

3.  Auf dem Blatt **New Group**, geben Sie die folgenden Informationen
    ein:

- Group type: **Security**

- Group name: !! Contoso Kiosk Devices!!

- Group description: !!All Windows devices configured as a Kiosk!!

- Membership type: **Assigned**

4.  Unter **Members**, wählen Sie **No members selected** aus.

![](./media/image15.png)

5.  Auf **Add members**, in der **Search** box geben Sie **Sea** ein.
    Markieren Sie **SEA-WS2** und wählen Sie **Select**.

![](./media/image16.png)

6.  Wählen Sie auf dem Blatt **New Group** die Option **Create**.

![A screenshot of a computer Description automatically
generated](./media/image17.png)

7.  Klicken Sie auf der Seite **Groups | All groups** und aktualisieren
    Sie die Seite, und stellen Sie sicher, dass die Gruppe **Contoso
    Kiosk Devices** angezeigt wird.

![](./media/image18.png)

**Aufgabe 3: Erstellen eines Konfigurationsprofils basierend auf den
Szenarioanforderungen**

1.  Kehren Sie zum Microsoft Intune Admin Center zurück, und wählen Sie
    in der Navigationsleiste **Devices** aus.

![A screenshot of a computer Description automatically
generated](./media/image19.png)

2.  Auf der **Devices | Overview** Seite, wählen Sie **Windows** wie in
    der folgenden Abbildung gezeigt.

![A screenshot of a computer Description automatically
generated](./media/image20.png)

3.  Auf der Seite **Windows | Windows devices**, navigieren Sie und
    klicken Sie auf **Configuration profiles**.

![A screenshot of a computer Description automatically
generated](./media/image21.png)

4.  Auf der Seite **Windows | Configuration profiles**, in **Policies**,
    klicken Sie auf**+ Create** und wählen Sie**+ New Policy** aus.

![A screenshot of a computer Description automatically
generated](./media/image22.png)

5.  Auf **Create a profile**, Wählen Sie die folgenden Optionen aus, und
    wählen Sie dann **Create**:

- Platform: **Windows 10 and later**

- Profile type: **Templates**

- Template name: !!**Kiosk**!!

![A screenshot of a computer Description automatically
generated](./media/image23.png)

6.  Geben Sie auf dem Blatt **Basics** die folgenden Informationen ein,
    und wählen Sie dann **Next**:

- Name: !!Contoso Kiosk Policy!!

- Description: !!Basic settings for Contoso Kiosk Devices.!!

![A screenshot of a computer Description automatically
generated](./media/image24.png)

7.  In **Configuration settings**, neben **Select a kiosk mode**, wählen
    Sie **Single app, full-screen kiosk** aus.

Zusätzliche Optionen werden basierend auf dem ausgewählten Modus
angezeigt.

8.  In **Configuration settings**, Wählen Sie die folgenden Optionen
    aus, und wählen Sie dann **Next**:

- User logon type: **Auto logon (Windows 10, version 1803 and later, or
  Windows 11)**

- Application type: **Add Microsoft Edge browser**

- Edge Kiosk URL: !! **http://bing.com**!!

- Microsoft Edge kiosk mode type: **Public Browsing (InPrivate)**

- Refresh browser after idle time: **5**

- Specify Maintenance Window for App Restarts: **Not configured**

> ![A screenshot of a computer Description automatically
> generated](./media/image25.png)

9.  Wählen Sie auf dem Blatt **Assignments** unter **Included Groups**
    die Option **Add groups**.

![A screenshot of a computer Description automatically
generated](./media/image26.png)

10. Im Fenster **Select groups to include**, wählen Sie !!**Contoso
    Kiosk Devices**!! aus, und klicken Sie dann auf **Select**.

![A screenshot of a computer Description automatically
generated](./media/image27.png)

11. Klicken Sie auf der Registerkarte **Assignment** auf die
    Schaltfläche **Next**.

![A screenshot of a computer Description automatically
generated](./media/image28.png)

12. Klicken Sie auf der Registerkarte **Applicability Rules** auf die
    Schaltfläche **Next**.

![A screenshot of a computer Description automatically
generated](./media/image29.png)

13. Klicken Sie auf der Registerkarte **Review + create** auf die
    Schaltfläche **Create**.

![A screenshot of a computer Description automatically
generated](./media/image30.png)

14. The Configuration profile will be listed.

![A screenshot of a computer Description automatically
generated](./media/image31.png)

**Aufgabe 4: Überprüfen, ob das Konfigurationsprofil angewendet wird**

1.  Melden Sie sich bei
    [*SEA-WS2*](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10)
    als **Admin** mit dem Passwort!! **Pa55w.rd**!! an

&nbsp;

1.  Wählen Sie auf der Taskleiste **Start** und dann **Settings**.

![A screenshot of a computer Description automatically
generated](./media/image1.png)

2.  Wählen Sie im Fenster **Settings** die Option **Accounts**.

![A screenshot of a computer Description automatically
generated](./media/image2.png)

3.  Wählen Sie auf der Seite **Accouts** die Option **Access work or
    school**.

![A screenshot of a computer Description automatically
generated](./media/image3.png)

5.  Wählen Sie **Connected to Contoso's Azure AD** und wählen Sie dann
    **Info** aus.

![A screenshot of a computer Description automatically
generated](./media/image11.png)

6.  Scrollen Sie nach unten, und wählen Sie dann **Sync**. Dadurch wird
    eine Gerätesynchronisierung mit Intune erzwungen.

![A screenshot of a computer Description automatically
generated](./media/image12.png)

7.  Schließen Sie das Fenster **Settings.**

> ![](./media/image32.png)

5.  Starten Sie **SEA-WS2** neu.

Beachten Sie, dass sich **SEA-WS2** automatisch anmeldet und ein Profil
erstellt. Nachdem die Anmeldung abgeschlossen ist, wird Microsoft Edge
mit InPrivate-Browsen konfiguriert. Wenn sich SEA-WS2 nicht automatisch
anmeldet, wiederholen Sie die Schritte 1 bis 7, um sicherzustellen, dass
die Richtlinie auf dem Gerät aktualisiert wurde.

![](./media/image33.png)

**Ergebnisse**: Nach Abschluss dieser Übung haben Sie erfolgreich ein
Konfigurationsprofil erstellt und zugewiesen, um ein Windows 11-Gerät
als Einzel-App-Kiosk zu konfigurieren.
