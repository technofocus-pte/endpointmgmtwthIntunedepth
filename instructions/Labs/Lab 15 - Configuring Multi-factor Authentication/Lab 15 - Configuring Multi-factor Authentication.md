Lab 15 - Konfigurieren der Multi-Faktor-Authentifizierung

**Zusammenfassung**

In dieser Übung konfigurieren Sie die Multi-Faktor-Authentifizierung
(Multi-Factor Authentication, MFA) pro Benutzer und wenden MFA mithilfe
einer Richtlinie für bedingten Zugriff an.

Übung 1: Konfigurieren der mehrstufigen Authentifizierung pro Benutzer.

**Szenario**

Um zusätzliche Sicherheit für Benutzeranmeldeereignisse zu
gewährleisten, müssen Sie die mehrstufige Authentifizierung (MFA)
konfigurieren und testen. Sie entscheiden sich, zunächst die MFA pro
Benutzer zu testen. Alex Wilber hat sich bereit erklärt, die
Einstellungen für Sie zu validieren.

Aufgabe 1: Überprüfen der Anmeldung vor dem Aktivieren von MFA

1.  Wechseln Sie und melden Sie sich bei
    [**SEA-WS3**](urn:gd:lg:a:select-vm) an als
    !\![**Admin**](urn:gd:lg:a:send-vm-keys)!! mit dem Passwort
    !\![**Pa55w.rd**](urn:gd:lg:a:send-vm-keys)!! an.

2.  Wählen Sie auf der Taskleiste **Microsoft Edge** aus. Geben Sie in
    der Adressleiste
    !\![**outlook.office.com**](urn:gd:lg:a:send-vm-keys)!! und drücken
    Sie **Enter**.

3.  Geben Sie auf der Sign in Seite
    !!**AlexW@M365xXXXXXXX.onmicrosoft.com**!! und wählen Sie dann
    **Next** aus.

4.  Auf der Seite **Enter password**, geben Sie
    [!!**P@55w.rd1234**](mailto:!!P@55w.rd1234)!! ein und wählen Sie
    **Sign in**. Wählen Sie an der Eingabeaufforderung Edge zum
    Speichern des Kennworts die Option **Save**.

> Outlook im Web wird geöffnet. Beachten Sie, dass nur das Kennwort für
> die Anmeldung bei Outlook im Web erforderlich war.

5.  Wählen Sie in der oberen rechten Ecke den **Account manager for Alex
    Wilber** und dann **Sign out**.

> ![](./media/image1.png)

6.  Schließen Sie Microsoft Edge.

Aufgabe 2: Aktivieren der MFA für einen Benutzer

1.  Wechseln Sie zu [**SEA-SVR1**](urn:gd:lg:a:select-vm). Melden Sie
    sich auf
    [[**SEA-SVR1**](urn:gd:lg:a:select-vm)](urn:gd:lg:a:select-vm) bei
    Bedarf als [**Contoso\Administrator**](urn:gd:lg:a:send-vm-keys) mit
    dem Kennwort !! [**Pa55w.rd**](urn:gd:lg:a:send-vm-keys)!! an und
    schließen Sie den **Server Manager**.

2.  Wählen Sie in der Taskleiste **Microsoft Edge** aus, navigieren Sie
    zu **Microsoft Entra admin
    center** !!**https://Entra.Microsoft.com**!!

3.  Melden Sie sich mit den Anmeldeinformationen des **Office
    365-Mandantenadministrators** an.

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)
>
> Das **Microsoft Entra Admin Center** wird geöffnet.

4.  Im **Microsoft Entra admin center**, im Navigationsbereich,
    erweitern Sie **Identity** und wählen Sie dann **Users** aus.

5.  Wählen Sie **All Users** und dann oben im Ergebnisbereich **Per-user
    MFA**. Möglicherweise müssen Sie zuerst die Auslassungspunkte
    auswählen, um die Option **Per-user MFA** anzuzeigen.

> ![A screenshot of a computer Description automatically
> generated](./media/image3.png)

6.  Wählen Sie auf der Seite für die mehrstufige Authentifizierung die
    Option **service settings**.

> ![A screenshot of a computer Description automatically
> generated](./media/image4.png)

7.  Scrollen Sie nach unten zum Abschnitt mit den
    **Verifizierungsoptionen**.

> Beachten Sie die verschiedenen Methoden, die für die
> Benutzerüberprüfung konfiguriert werden können.

8.  Im Bereich **remember multi-factor authentication on trusted
    device**, aktivieren Sie das Kontrollkästchen Neben **Allow users to
    remember multi-factor authentication on devices they trust**.

9.  Neben **Number of days users can trust devices for**, geben Sie
    **30** ein und wählen Sie dann **save** aus. Wählen Sie
    **close** wenn Sie dazu aufgefordert werden.

> ![](./media/image5.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image6.png)

10. Oben auf der Seite unter**multi-factor authentication**, wählen
    Sie **users** aus.

> ![A screenshot of a computer Description automatically
> generated](./media/image7.png)

11. Aktivieren Sie in der Benutzerliste das Kontrollkästchen neben
    **Alex Wilber**.

12. Wählen Sie auf der Seite "Alex Wilber" die Option **Enable**.

> ![A screenshot of a computer Description automatically
> generated](./media/image8.png)

13. Wählen Sie in der Meldung **About enabling multi-factor auth** die
    Option **enable multi-factor auth**.

> ![A screenshot of a computer Description automatically
> generated](./media/image9.png)

14. Wählen Sie in der Meldung **Updates successful** aus und dann wählen
    Sie **close** aus. Beachten Sie, dass die **Multi-Factor Auth
    Status** für Alex Wilber jetzt **Enabled** ist.

> ![A screenshot of a computer Description automatically
> generated](./media/image10.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image11.png)

15. Schließen Sie Microsoft Edge.

Aufgabe 3: Registrieren und Überprüfen der MFA

1.  Wechseln Sie zu [**SEA-WS3**](urn:gd:lg:a:select-vm). Wählen Sie in
    der Taskleiste **Microsoft Edge**.

2.  Geben Sie in der Adressleiste
    !\![**outlook.office.com**](urn:gd:lg:a:send-vm-keys)!! ein und
    drücken Sie **Enter**.

3.  Wählen Sie auf der Seite **Pick an account** die Option
    !\![**AlexW@M365xXXXXXXX.onmicrosoft.com**](mailto:AlexW@M365xXXXXXXX.onmicrosoft.com)!!

> ![A screenshot of a computer Description automatically
> generated](./media/image12.png)

4.  Auf der Seite **Enter password**, geben Sie
    [!!**P@55w.rd1234**](mailto:!!P@55w.rd1234)!! ein und wählen Sie
    dann **Sign in**.

5.  Wählen Sie auf der Seite **More information required** die Option
    **Next** aus. Die Seite "Schützen Sie Ihr Konto" wird geöffnet.

> ![A screenshot of a computer Description automatically
> generated](./media/image13.png)
>
> In der Regel möchten Sie die Microsoft Authenticator-App verwenden, um
> die mehrstufige Authentifizierung zu verwalten. Für dieses
> Lab-Szenario verwenden Sie jedoch Textnachrichten.

6.  Auf der Seite **Keep your account secure**, wählen Sie **I want to
    set up a different method** aus.

> ![A screenshot of a computer Description automatically
> generated](./media/image14.png)

7.  In der Dialoagbox **Choose a different method**, wählen Sie
    **Phone**, und wählen Sie dann **Confirm** aus.

> ![A screenshot of a computer Description automatically
> generated](./media/image15.png)

8.  Auf der Seite **Phone**, geben Sie Ihre Mobiltelefonnummer ein,
    unter der Sie Textnachrichten empfangen können, und wählen Sie dann
    **Next**.

> ![A screenshot of a computer screen Description automatically
> generated](./media/image16.png)

9.  Nachdem Sie den Verifizierungscode als Textnachricht erhalten haben,
    geben Sie den Code ein, der auf der Seite **Phone** angegeben ist,
    und wählen Sie dann **Next**.

> ![](./media/image17.png)

10. Wählen Sie in der verifizierten SMS-Nachricht **Next** und dann
    **Done**.

> ![A screenshot of a computer screen Description automatically
> generated](./media/image18.png)
>
> ![](./media/image19.png)

11. Wählen Sie in der Nachricht **Stay signed in** die Option **No**.

> ![A screenshot of a computer error Description automatically
> generated](./media/image20.png)
>
> Outlook im Web öffnet sich in Alex Wilbers Posteingang.

12. Wählen Sie in der oberen rechten Ecke den **Account manager for Alex
    Wilber** und dann **Sign out**.

> ![](./media/image21.png)
>
> **Hinweis**: Benutzer müssen sich nur registrieren, wenn sie MFA zum
> ersten Mal verwenden. Bei nachfolgenden Anmeldungen ist nur die Angabe
> des Validierungscodes erforderlich, den Sie per SMS an die
> Telefonnummer gesendet haben, die Sie bei der Registrierung eingegeben
> haben.

13. Geben Sie in der Adressleiste
    !\![**outlook.office.com**](urn:gd:lg:a:send-vm-keys)!! ein und
    drücken Sie **Enter**.

14. Wählen Sie auf der Seite **Pick an Account** die Option
    !!**AlexW@M365xXXXXXXXX.onmicrosoft.com**!!

15. Geben Sie auf der Seite **Enter password** folgendes ein:
    !!**P@55w.rd1234**!! und wählen Sie **Sign in**.

> ![A screenshot of a computer error Description automatically
> generated](./media/image22.png)
>
> Die Eingabeaufforderung **Verify your identity** wird geöffnet.
> Beachten Sie, dass es die letzten beiden Ziffern Ihrer Telefonnummer
> enthält.

16. Wählen Sie in der Eingabeaufforderung **Verify your identity** Ihre
    SMS-Telefonnummer aus.

17. Geben Sie auf der Seite **Enter code** den Code ein, der an Ihr
    Mobiltelefon gesendet wurde, und wählen Sie dann **Verify**.

> ![A screenshot of a computer error message Description automatically
> generated](./media/image23.png)
>
> Beachten Sie, dass Sie ein Kontrollkästchen aktivieren können, um 30
> Tage lang keine erneute Bestätigung anzufordern.

18. Da **die Microsoft Authenticator App** für mehr Sicherheit und
    reibungslose Erfahrung sorgt, werden Sie aufgefordert, diese zu
    konfigurieren, klicken Sie vorerst auf **Skip for now**

> ![A screenshot of a computer error Description automatically
> generated](./media/image24.png)

19. Wählen Sie in der Nachricht Stay signed in die Option **No**.
    Outlook im Web öffnet sich in Alex Wilbers Posteingang.

> ![A screenshot of a computer error Description automatically
> generated](./media/image25.png)

20. Wählen Sie in der oberen rechten Ecke das Symbol **Account manager
    for Alex Wilber** und wählen Sie dann **Sign out**.

> ![A computer screen shot of a computer screen Description
> automatically generated](./media/image26.png)

21. Schließen Sie Microsoft Edge.

Aufgabe 3: Entfernen der benutzerspezifischen MFA

1.  Wechseln Sie zu[**SEA-SVR1**](urn:gd:lg:a:select-vm). Melden [Sie
    sich auf **SEA-SVR1**](urn:gd:lg:a:select-vm) bei Bedarf als
    [**Contoso\Administrator**](urn:gd:lg:a:send-vm-keys) mit dem
    Kennwort !! [**Pa55w.rd**](urn:gd:lg:a:send-vm-keys)!! an und
    schließen den **Server Manager**.

2.  Wählen Sie in der Taskleiste **Microsoft Edge** aus, navigieren Sie
    zu **Microsoft Entra Admin Center**
    !!**https://Entra.Microsoft.com**!!

3.  Melden Sie sich mit den Anmeldeinformationen des **Office
    365-Mandantenadministrators** an.

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)
>
> Das **Microsoft Entra Admin Center** wird geöffnet.

4.  Erweitern Sie im **Microsoft Entra Admin Center** im
    Navigationsbereich **Identity**, und wählen Sie dann **Users**.

5.  Wählen Sie **All Users** und dann oben im Ergebnisbereich **Per-user
    MFA**. Möglicherweise müssen Sie zuerst die Auslassungspunkte
    auswählen, um die Option **Per-user MFA** anzuzeigen.

> ![A screenshot of a computer Description automatically
> generated](./media/image3.png)

6.  Oben auf der Seite unter **multi-factor authentication**, wählen
    Sie **users** aus.

7.  Aktivieren Sie in der Benutzerliste das Kontrollkästchen neben
    **Alex Wilber**.

> Beachten Sie, dass der **Multi-Factor Auth Status** für Alex Wilber
> jetzt auf **Enforced** festgelegt ist (zuvor auf "Aktiviert"). Dies
> liegt daran, dass Alex sich registriert hat und MFA verwendet.
>
> ![A screenshot of a computer Description automatically
> generated](./media/image27.png)

8.  Wählen Sie auf der Seite "Alex Wilber" die Option **Manage user
    settings.**

> ![A screenshot of a computer Description automatically
> generated](./media/image28.png)

9.  Aktivieren Sie im Feld Benutzereinstellungen verwalten das
    Kontrollkästchen neben allen drei Optionen, wählen Sie **Save** und
    dann **Close** aus.

> ![A screenshot of a computer Description automatically
> generated](./media/image29.png)
>
> Mit diesen Optionen werden alle gespeicherten MFA-Einstellungen für
> Alex entfernt.
>
> ![A white rectangular frame with black border Description
> automatically generated](./media/image30.png)

10. Aktivieren Sie in der Benutzerliste das Kontrollkästchen neben
    **Alex Wilber**.

11. Wählen Sie auf der Seite "Alex Wilber" die Option **Disable**.

> ![A screenshot of a computer Description automatically
> generated](./media/image31.png)

12. Wählen Sie in der **Disable multi-factor authentication** die Option
    **yes**.

> ![](./media/image32.png)

13. Wählen Sie in der Meldung **Updates successful** aus **close**.

> ![A white screen with black text Description automatically
> generated](./media/image33.png)
>
> Beachten Sie, dass der **Multi-Factor Auth Status** für Alex Wilber
> jetzt **Disabled**.
>
> ![A screenshot of a computer Description automatically
> generated](./media/image34.png)

14. Schließen Sie Microsoft Edge.

**Ergebnisse**: Nach Abschluss dieser Übung haben Sie die mehrstufige
Authentifizierung pro Benutzer erfolgreich konfiguriert.

Übung 2: Konfigurieren der mehrstufigen Authentifizierung mit bedingtem
Zugriff

**Szenario**

Um zusätzliche Sicherheit für Benutzeranmeldeereignisse zu
gewährleisten, müssen Sie die mehrstufige Authentifizierung (MFA)
konfigurieren und testen. Sie entscheiden, dass die Verwendung einer
Richtlinie für bedingten Zugriff eine größere Flexibilität für Ihre
MFA-Anforderungen bietet. Alex Wilber hat sich bereit erklärt, die
Einstellungen für Sie zu validieren.

Aufgabe 1: Überprüfen der Anmeldung vor dem Aktivieren des bedingten
Zugriffs mit MFA

1.  Wechseln Sie und melden Sie sich bei
    [**SEA-WS3**](urn:gd:lg:a:select-vm) an als
    !\![**Admin**](urn:gd:lg:a:send-vm-keys)!! mit dem Passwort
    !\![**Pa55w.rd**](urn:gd:lg:a:send-vm-keys)!!an.

2.  Wählen Sie auf der Taskleiste **Microsoft Edge** aus. Geben Sie in
    der Adressleiste
    !\![**outlook.office.com**](urn:gd:lg:a:send-vm-keys)!! und drücken
    Sie Enter.

3.  Geben Sie auf der **Sign In**
    Seite!!**AlexW@M365xXXXXXXX.onmicrosoft.com**!! an und wählen Sie
    dann **Next**.

4.  Geben Sie auf der Seite **Enter password** !!**P@55w.rd1234**!! und
    wählen Sie **Sign In** aus. Wählen Sie an der Eingabeaufforderung
    Edge zum Speichern des Kennworts die Option **Save**.

> Outlook im Web wird geöffnet. Beachten Sie, dass nur das Kennwort für
> die Anmeldung bei Outlook im Web erforderlich war.

5.  Wählen Sie in der oberen rechten Ecke den **Account Manager for Alex
    Wilber** und dann **Sign out**.

> ![A screenshot of a computer Description automatically
> generated](./media/image1.png)

6.  Schließen Sie Microsoft Edge.

Aufgabe 2: Konfigurieren des bedingten Zugriffs mit MFA

1.  Wechseln Sie zu [**SEA-SVR1**](urn:gd:lg:a:select-vm). Melden [Sie
    sich auf **SEA-SVR1**](urn:gd:lg:a:select-vm) bei Bedarf als
    [**Contoso\Administrator**](urn:gd:lg:a:send-vm-keys) mit dem
    Kennwort !\![**Pa55w.rd**](urn:gd:lg:a:send-vm-keys)!! an und
    schließen Sie den **Server Manager**.

2.  Wählen Sie in der Taskleiste **Microsoft Edge aus**, navigieren Sie
    zu **Microsoft Entra Admin Center**
    !!**https://Entra.Microsoft.com**!!

3.  Melden Sie sich mit **den Anmeldeinformationen** des Office
    365-Mandantenadministrators an.

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)
>
> Das **Microsoft Entra Admin Center** wird geöffnet.

4.  Erweitern Sie im **Microsoft Entra Admin Center** im
    Navigationsbereich **Identity**, dann Protection und dann
    **Conditional Access.**

> ![A screenshot of a computer Description automatically
> generated](./media/image35.png)

5.  Auf der Seite **Conditional Access**, wählen Sie **Policies**, und
    dann wählen Sie **+ New policy** aus.

> ![A screenshot of a computer Description automatically
> generated](./media/image36.png)

6.  Auf der Seite **New Conditional access policy**, in der
    **Name** Box, geben Sie !\![**Contoso MFA
    Policy**](urn:gd:lg:a:send-vm-keys)!! ein.

7.  Unter **Assignments**, wählen Sie **0 users or workload identities
    selected** aus.

> ![A screenshot of a computer Description automatically
> generated](./media/image37.png)

8.  Wählen Sie im Bereich Benutzer und Gruppen die Option neben **Select
    users and groups** aus, und aktivieren Sie dann das Kontrollkästchen
    neben **Users and groups**.

9.  Auf der Seite **Select**, wählen Sie **Alex Wilber** und klicken Sie
    dann auf **Select**.

> ![A screenshot of a computer Description automatically
> generated](./media/image38.png)
>
> Beachten Sie, dass Sie normalerweise eine Gruppe angeben, aber für
> diese Übung werden wir nur die Einstellung auf Alex Wilber testen.

10. Wählen Sie unter Zielressourcen die Option **No target resources
    selected** aus, und klicken Sie dann auf **Select apps**.

> ![A screenshot of a computer Description automatically
> generated](./media/image39.png)

11. Aktivieren Sie auf der Seite **Select** das Kontrollkästchen neben
    **Office 365,** und klicken Sie dann auf **Select**.

> ![A screenshot of a computer Description automatically
> generated](./media/image40.png)

12. Unter **Access controls**, im Bereich **Grant**, wählen Sie **0
    controls selected** aus.

> ![A screenshot of a computer Description automatically
> generated](./media/image41.png)

13. Auf der Seite **Grant**, wählen Sie **Grant access**, aktivieren Sie
    das Kontrollkästchen neben **Require multi-factor authentication**,
    und klicken Sie dann auf **Select**.

> ![A screenshot of a computer Description automatically
> generated](./media/image42.png)

14. Unter **Enable policy**, wählen Sie **On**.

15. Wählen Sie **Create** aus, um die MFA-Richtlinie von Contoso zu
    erstellen. Beachten Sie, dass die Richtlinie mit dem Status **On**
    aufgeführt ist.

> ![A screenshot of a computer Description automatically
> generated](./media/image43.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image44.png)

16. Wählen Sie im **Microsoft Entra Admin Center** die Option **Users**
    aus. Wählen Sie in der Liste Users die Option **Alex Wilber**.

> ![A screenshot of a computer Description automatically
> generated](./media/image45.png)

17. Wählen Sie auf der Seite Alex Wilber die Option **Authentication
    methods**.

> ![](./media/image46.png)
>
> Beachten Sie, dass bereits eine Telefonnummer für Alex konfiguriert
> wurde.

18. Schließen Sie Microsoft Edge.

Aufgabe 3: Überprüfen der MFA für bedingten Zugriff

1.  Wechseln Sie zu [**SEA-WS3**](urn:gd:lg:a:select-vm). Wählen Sie in
    der Taskleiste **Microsoft Edge** aus.

2.  Geben Sie in der Adressleiste
    !\![**outlook.office.com**](urn:gd:lg:a:send-vm-keys)!! ein und
    drücken Sie Enter.

3.  Wählen Sie auf der Seite **Pick an account** die Option
    !!**AlexW@M365xXXXXXXX.onmicrosoft.com**!!

> ![A screenshot of a computer Description automatically
> generated](./media/image12.png)

4.  Geben Sie auf der Seite **Enter password** !!**P@55w.rd1234**!! ein
    und wählen Sie **Sign in**.

5.  Wählen Sie in der Eingabeaufforderung **Verify your identity** Ihre
    SMS-Telefonnummer aus.

> ![A screenshot of a computer error Description automatically
> generated](./media/image22.png)

6.  Geben Sie auf der Seite **Enter code** den Code ein, der an Ihr
    Mobiltelefon gesendet wurde, und wählen Sie dann **Verify**.

> ![A screenshot of a computer error message Description automatically
> generated](./media/image23.png)
>
> Beachten Sie, dass Sie ein Kontrollkästchen aktivieren können, um 30
> Tage lang keine erneute Bestätigung anzufordern.

7.  Wählen Sie in der Nachricht Stay signed die Option **No**. Outlook
    im Web öffnet sich in Alex Wilbers Posteingang.

> ![A screenshot of a computer error Description automatically
> generated](./media/image25.png)

8.  Wählen Sie in der oberen rechten Ecke den **Account Manager for Alex
    Wilber** und dann **Abmelden aus**.

> ![A computer screen shot of a computer screen Description
> automatically generated](./media/image26.png)

9.  Schließen Sie Microsoft Edge.

Aufgabe 4: Entfernen der MFA mit bedingtem Zugriff

1.  Wechseln Sie zu [**SEA-SVR1**](urn:gd:lg:a:select-vm). Melden [Sie
    sich auf **SEA-SVR1**](urn:gd:lg:a:select-vm) bei Bedarf als
    [**Contoso\Administrator**](urn:gd:lg:a:send-vm-keys) mit dem
    Kennwort !! [**Pa55w.rd**](urn:gd:lg:a:send-vm-keys)!! an und
    schließen Sie den **Server Manager**.

2.  Wählen Sie in der Taskleiste **Microsoft Edge aus**, navigieren Sie
    zu **Microsoft Entra Admin Center**
    !!**https://Entra.Microsoft.com**!!

3.  Melden Sie sich mit den Anmeldeinformationen des **Office
    365-Mandantenadministrators** an.

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)
>
> Das **Microsoft Entra Admin Center** wird geöffnet.

4.  Erweitern Sie im **Microsoft Entra Admin Center** im
    Navigationsbereich **Identity**, dann **Protection** und dann
    **Conditional Access.**

> ![A screenshot of a computer Description automatically
> generated](./media/image35.png)

5.  Auf der Seite **Conditional Access** wählen Sie **Policies** und
    wählen Sie dann **Contoso MFA Policy**.

6.  Auf der Seite **Contoso MFA Policy**, wählen Sie **Delete** und
    wählen Sie dann **Delete**.

> ![A screenshot of a computer Description automatically
> generated](./media/image47.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image48.png)

7.  Klicken Sie zur **Delete Confirmation** auf die Schaltfläche
    **Delete**.

> ![A screenshot of a computer error Description automatically
> generated](./media/image49.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image50.png)

8.  Schließen Sie Microsoft Edge.

**Ergebnisse**: Nach Abschluss dieser Übung haben Sie die mehrstufige
Authentifizierung mithilfe einer Richtlinie für bedingten Zugriff
erfolgreich konfiguriert.
