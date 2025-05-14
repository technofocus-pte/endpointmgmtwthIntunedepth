**Übung 5: Verwalten der Geräteregistrierung bei Microsoft Intune**

**Zusammenfassung**

In dieser Übung bereiten Sie sich auf die Geräteverwaltung mit Microsoft
Intune vor, indem Sie Lizenzen überprüfen und zuweisen, die automatische
Windows-Registrierung konfigurieren und Registrierungseinschränkungen
konfigurieren.

**Voraussetzungen**

Zu den folgenden Labs müssen vor diesem Lab abgeschlossen werden:

1.  Übung \#1 - Verwalten von Identitäten in Microsoft Entra ID

2.  Übung \#2 - Synchronisieren von Identitäten mit Microsoft Entra
    Connect

**Hinweis**: Sie benötigen außerdem ein Mobiltelefon, das
Textnachrichten empfangen kann, die zum Sichern der Windows
Hello-Anmeldeauthentifizierung bei der Entra ID verwendet werden.

**Szenario**

Sie müssen sich auf die Geräteverwaltung mit Microsoft Intune
vorbereiten. Zunächst müssen Sie sicherstellen, dass den Benutzern die
entsprechenden Lizenzen für die Geräteverwaltung zugewiesen werden. Als
Verifizierungstest weisen Sie Aaron Nicholls die erforderlichen Lizenzen
zu. Sie müssen auch sicherstellen, dass jedes Windows-Gerät, das mit
Microsoft Entra ID verbunden oder registriert ist, automatisch bei
Intune registriert wird. Sie wurden auch gebeten, sicherzustellen, dass
Mitglieder der Gruppe "Vertrieb" daran gehindert werden, persönliche
Android- und iOS-Geräte bei Intune zu registrieren, und dass das Limit
für Registrierungsgeräte auf 10 Geräte erhöht wird. Schließlich müssen
Sie Allan Deyoung als Geräteregistrierungs-Manager konfigurieren, damit
er 1000 Geräte registrieren kann.

**Aufgabe 1: Überprüfen und Zuweisen von Lizenzen für die
Geräteverwaltung**

1.  Navigieren Sie
    [auf](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10)
    *SEA*-*SVR1* **zum Microsoft 365 Admin** Center-Fenster.

![](./media/image1.png)

2.  Navigieren Sie, wählen Sie **Billing** und klicken Sie dann auf
    **Licenses**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image2.png)

3.  In auf der Seite **Licenses** die Lizenzen, die im Mandanten
    verfügbar sind.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image3.png)

4.  Wählen Sie aus und klicken Sie auf **Enterprise Mobility + Security
    E5**. Notieren Sie sich alle Benutzer, denen diese Lizenz zugewiesen
    wurde. Sie können Lizenzen von diesem Speicherort aus zuweisen und
    entfernen.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image4.png)

![](./media/image5.png)

5.  Wählen Sie einen Benutzer aus, um die Lizenzen anzuzeigen, die dem
    Benutzer zugewiesen sind. Beachten Sie die Dienste, die in der
    Enterprise Mobility + Security E5-Lizenz enthalten sind. Microsoft
    Intune ist einer der unterstützten Dienste für diese Lizenz.

![](./media/image6.png)

6.  Wählen Sie im Navigationsbereich des **Microsoft 365 Admin Centers**
    die Option **Active users**.

![](./media/image7.png)

7.  Suchen und auswählen !!**Cindy White**!!

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image8.png)

8.  Klicken Sie auf der Benutzerseite von **Cindy White** auf **Licenses
    and apps**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image9.png)

9.  Wählen Sie unter **Settings** im Feld **Usage location** die Option
    **Untied States** aus, klicken Sie auf das Kontrollkästchen für
    **Enterprise Mobility + Security E5 and Office 365 E5 (no teams),**
    und klicken Sie dann auf **Save changes.**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image10.png)

***Hinweis**: Bevor Sie einem Benutzer eine Lizenz zuweisen können, muss
für den Benutzer ein Verwendungsort festgelegt sein.*

![](./media/image11.png)

**Aufgabe 2: Festlegen des Kennworts des Benutzers mithilfe von
PowerShell**

1.  Klicken Sie in [***SEA-SVR1***](urn:gd:lg:a:select-vm) mit der
    rechten Maustaste auf die Schaltfläche **Start**, und wählen Sie
    dann **Windows PowerShell (Administrator)**.

![](./media/image12.png)

2.  Wählen Sie im Dialogfeld **User Account Control** die Option
    **Yes**.

![](./media/image13.png)

3.  Geben Sie im **Windows PowerShell-Fenster** den folgenden Befehl
    ein, und drücken Sie dann **Enter**:

!!**Connect-MsolService**!!

![A computer screen with white text Description automatically
generated](./media/image14.png)

4.  Melden Sie sich im Dialogfeld **Sign in to your account** mit den
    Anmeldeinformationen für den Office 365-Mandanten auf der
    Registerkarte Start an.

**Hinweis – Wenn Sie aufgefordert wurden, das Kennwort für die
Mandantenadministratoranmeldeinformationen zu ändern, stellen Sie
sicher, dass Sie das aktualisierte Kennwort eingeben.**

![A screenshot of a computer Description automatically
generated](./media/image15.png)

![A screenshot of a computer screen Description automatically
generated](./media/image16.png)

5.  Geben Sie im **Windows PowerShell-Fenster** den folgenden Befehl
    ein, um die Kennwörter der **Cindy White**

!!**Get-MsolUser | Where-Object DisplayName -EQ "Cindy White" |
Set-MsolUserPassword -NewPassword P@55w.rd1234 -ForceChangePassword
$false**!!

![A computer screen shot of a program Description automatically
generated](./media/image17.png)

**Aufgabe 3: Aktivieren der automatischen Windows-Registrierung bei
Microsoft Intune**

1.  Öffnen Sie in **SEA-SVR1** eine neue Registerkarte in **Microsoft
    Edge** und geben Sie dann in der Adressleiste
    !!**https://Endpoint.microsoft.com**!! und drücken Sie dann
    **Enter**. Wenn Sie aufgefordert werden, sich anzumelden, geben Sie
    die Anmeldeinformationen des **Office 365 Tenant Admin**.

2.  Wählen Sie im Microsoft Intune Admin Center die Option **Devices**.

![A screenshot of a computer Description automatically
generated](./media/image18.png)

3.  Navigieren Sie und klicken Sie auf **Enrollment**. Stellen Sie
    sicher, dass die Registerkarte **Windows** ausgewählt ist,
    navigieren Sie dann zum Abschnitt **Enrollment options** und klicken
    Sie auf **Automatic Enrollment**.

![](./media/image19.png)

4.  Wählen Sie in der Zeile **MDM user scope** das Optionsfeld **All**
    und dann **Save**.

![](./media/image20.png)

5.  Klicken Sie auf **Devices | Enrollment** wie in der folgenden
    Abbildung gezeigt.

![](./media/image21.png)

**Hinweis**: Durch Ausführen dieses Schritts haben Sie die automatische
Registrierung bei Intune für jeden Benutzer aktiviert, der eine Azure
AD-Verknüpfung mit einem Windows-Gerät ausführt.

**Aufgabe 4: Konfigurieren von Registrierungseinschränkungen**

1.  Navigieren Sie zum Abschnitt **Devices onboarding** und klicken Sie
    auf **Enrollment**. Klicken Sie dann auf die Registerkarte
    **Android**, wie in der Abbildung unten gezeigt.

![](./media/image22.png)

2.  Scrollen Sie nach unten zum Abschnitt **Enrollment options** und
    klicken Sie auf **Device platform restriction**.

![](./media/image23.png)

3.  Wählen Sie die Registerkarte **Android restrictions** und dann
    +**Create restriction**.

![](./media/image24.png)

![](./media/image25.png)

4.  Geben Sie auf der Seite **Create restriction** im Feld **Name** den
    Wert "!!**Android Personal Device Restriction**!! ein und wählen Sie
    dann **Next**.

![](./media/image26.png)

5.  Wählen Sie auf der Seite Plattformeinstellungen unter **Personally
    owned** die Option **block** für die folgenden Gerätetypen aus und
    klicken Sie auf die Schaltfläche **Next**:

    - Android Enterprise (work profile)

    - Android device administrator

![](./media/image27.png)

6.  Wählen Sie auf der Seite **Scope tags** die Option **Next**.

![A screenshot of a computer Description automatically
generated](./media/image28.png)

7.  Auf der Seite **Assignments** unter **Included groups**, wählen Sie
    **Add groups** aus.

![A screenshot of a computer Description automatically
generated](./media/image29.png)

8.  Geben Sie in der Suchleiste für **Select groups to include** den
    Namen **Sales** ein, wählen Sie ihn dann aus und klicken Sie dann
    auf die Schaltfläche **Next**.

![A screenshot of a computer Description automatically
generated](./media/image30.png)

9.  Klicken Sie auf der Registerkarte **Assignments** auf die
    Schaltfläche **Next**.

![A screenshot of a computer Description automatically
generated](./media/image31.png)

10. Wählen Sie auf der Seite **Review + create** die Option **Create**.

![A screenshot of a computer Description automatically
generated](./media/image32.png)

Beachten Sie die Android-Einschränkung für persönliche Geräte, die mit
der Priorität 1 zugewiesen ist.

![A screenshot of a computer Description automatically
generated](./media/image33.png)

11. Klicken Sie in der Menüleiste im Fenster **Windows** auf **Devices |
    Enrollment**, navigieren Sie zu **Enrollment options** und klicken
    Sie auf das Symbol **Device limit restriction**.

![A screenshot of a computer Description automatically
generated](./media/image34.png)

Beachten Sie, dass es eine Standardeinschränkung für das Gerätelimit
gibt, die allen Benutzern zugewiesen ist. Mit dieser
Standardeinschränkung wird ein Grenzwert für die Geräteregistrierung auf
5 Geräte pro Benutzer festgelegt.

12. Wählen Sie in den **Enrollment device limit restrictions** die
    Option + **Create restriction**.

![A screenshot of a computer Description automatically
generated](./media/image35.png)

13. Geben Sie auf der Seite **Create restriction** im Feld **Name** den
    Namen !!**Sales Device Enrollment Limit**!! ein. Wählen Sie **Next**
    aus.

![A screenshot of a computer Description automatically
generated](./media/image36.png)

14. Wählen Sie auf der Seite **Device limit** die Option **10** aus, und
    wählen Sie dann **Next**.

![A screenshot of a computer Description automatically
generated](./media/image37.png)

15. Wählen Sie auf der Seite **Scope tags** die Option **Next**.

![A screenshot of a computer Description automatically
generated](./media/image38.png)

16. Wählen Sie auf der Seite **Assignments** unter **Included groups**
    die Option **Add groups**.

![A screenshot of a computer Description automatically
generated](./media/image39.png)

17. In the **Select groups to include** page search box type and select
    **Sales** and then click on **Select** button.

![](./media/image40.png)

18. Klicken Sie auf die Schaltfläche **Next**.

![A screenshot of a computer Description automatically
generated](./media/image41.png)

19. Wählen Sie auf der Seite **Review + create** die Option **Create**.

![A screenshot of a computer Description automatically
generated](./media/image42.png)

20. Laden Sie die Seite neu. Beachten Sie das Limit für die
    Registrierung von Verkaufsgeräten, das mit einem Gerätelimit von 10
    konfiguriert und mit der Priorität 1 zugewiesen wurde.

![A screenshot of a computer Description automatically
generated](./media/image43.png)

**Aufgabe 5: Konfigurieren eines Geräteregistrierungs-Managers**

1.  Wählen Sie im **Microsoft Intune admin center** die Option
    **Devices**.

![](./media/image44.png)

2.  Navigieren Sie zum Abschnitt **Device onboarding**, klicken Sie auf
    **Enrollment** und dann auf die Registerkarte **Device enrolment
    managers**.

![](./media/image45.png)

3.  Wählen Sie im Bereich **Enroll devices** die Option **Device
    enrollment managers**.

Beachten Sie, dass standardmäßig keine Geräteregistrierungs-Manager
konfiguriert sind.

4.  Klicken Sie auf der Seite **Enroll devices|Device enrollment
    managers** wählen Sie **Add**.

![A screenshot of a computer Description automatically
generated](./media/image46.png)

1.  Geben Sie auf der Seite **Add user** unter Benutzername die
    E-Mail-Adresse von Allan [DeYoung ein
    !!**AllanD@M365xXXXXXXX.onmicrosoft.com**](mailto:DeYoung !!AllanD@M365xXXXXXXX.onmicrosoft.com)!!
     (ersetzen Sie **XXXXXX** durch Ihren Mandantennamen), und wählen
    Sie dann **Add** aus.

![A screenshot of a computer Description automatically
generated](./media/image47.png)

**Allan darf jetzt bis zu 1000 Geräte registrieren.**

5.  Wählen Sie im Microsoft Intune Admin Center im Navigationsbereich
    die Option **Home**.

![A screenshot of a computer Description automatically
generated](./media/image48.png)

6.  Schließen Sie Microsoft Edge.

**Ergebnisse**: Nach Abschluss dieser Übung haben Sie die Lizenzen
erfolgreich überprüft und zugewiesen, die automatische
Windows-Registrierung konfiguriert, Registrierungseinschränkungen
aktiviert und zugewiesen und einen Geräteregistrierungs-Manager
konfiguriert.
