Lab 16 - Konfigurieren der Self-Service-Kennwortzurücksetzung für
Benutzerkonten in Microsoft Entra

**Zusammenfassung**

In dieser Übung konfigurieren und validieren Sie die
Self-Service-Kennwortzurücksetzung (Self-Service Password Reset, SSPR)
für Benutzerkonten in **Microsoft Entra ID**.

**Voraussetzungen**

Die folgenden Übungen müssen vor diesem Lab abgeschlossen werden:

1.  Lab \#2 - Synchronisieren von Identitäten mit Microsoft Entra
    Connect

2.  Lab \#5 - Verwalten der Geräteregistrierung bei Microsoft Intune

**Szenario**

Der Helpdesk hat darauf hingewiesen, dass eine große Anzahl von
Support-Tickets mit dem Zurücksetzen von Passwörtern zusammenhängt. Sie
wurden gebeten, eine Lösung vorzuschlagen, mit der Benutzer ihr eigenes
Passwort zurücksetzen können. Bei Konten, die von AD DS synchronisiert
werden, sollte der Prozess sowohl das Microsoft Entra als auch das AD
DS-Kennwort zurücksetzen.

Aufgabe 1: Konfigurieren des Kennwortrückschreibens

1.  Melden Sie sich bei [***SEA-SVR1***](urn:gd:lg:a:select-vm) an als
    !!**[Contoso\Administrator](urn:gd:lg:a:send-vm-keys)!!** mit dem
    Passwort !!**[Pa55w.rd](urn:gd:lg:a:send-vm-keys)!!** an und
    schließen Sie den **Server Manager**.

2.  Doppelklicken Sie auf dem Desktop auf **Azure AD Connect**.

> ![A screenshot of a computer Description automatically
> generated](./media/image1.png)

3.  Wählen Sie auf der Seite **Welcome to Azure AD Connect** die Option
    **Configure**.

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)

4.  Auf der Seite **Additional tasks**, wählen Sie **Customize
    synchronization options**, und wählen Sie dann **Next**.

> ![A screenshot of a computer Description automatically
> generated](./media/image3.png)

5.  Geben Sie auf der Seite **Connect to Azure AD** bei Bedarf
    [!!**admin@M365xXXXXXXX.onmicrosoft.com**](mailto:!!admin@M365xXXXXXXX.onmicrosoft.com)**!!**
    ein und geben Sie im Textfeld **USERNAME** das **PASSWORD** ein, und
    wählen Sie dann **Next**.

> ![A screenshot of a computer Description automatically
> generated](./media/image4.png)

6.  Auf der Seite **Connect to your directories**, wählen Sie **Next**.

7.  Auf der Seite **Domain and OU filtering**, wählen Sie **Next**.

8.  Auf der Seite **Optional features**, wählen Sie **Password
    writeback**, und wählen Sie dann **Next**.

> ![A screenshot of a computer Description automatically
> generated](./media/image5.png)

9.  Auf der Seite **Ready to configure**, wählen Sie **Configure**.

> ![A screenshot of a computer Description automatically
> generated](./media/image6.png)
>
> ![A computer screen shot of a computer Description automatically
> generated](./media/image7.png)
>
> **Hinweis**: Die Konfiguration kann einige Minuten dauern.

10. Auf der Seite **Configuration complete**, wählen Sie **Exit**.

> ![A screenshot of a computer Description automatically
> generated](./media/image8.png)

Aufgabe 2: Aktivieren der Self-Service-Kennwortzurücksetzung.

1.  Wählen Sie auf der Taskleiste **Microsoft Edge** aus, navigieren Sie
    zum **Microsoft Entra Admin Center https://Entra.Microsoft.com**.

2.  Melden Sie sich mit den Anmeldeinformationen des **Office
    365-Mandantenadministrators** an.

> ![A screenshot of a computer Description automatically
> generated](./media/image9.png)
>
> Das **Microsoft Entra Admin Center** wird geöffnet.

3.  Erweitern Sie im **Microsoft Entra Admin Center** im
    Navigationsbereich **Identity**, und wählen Sie dann **Users**.

4.  Wählen Sie im Navigationsbereich **Users** die Option **Password
    reset**.

> ![A screenshot of a computer Description automatically
> generated](./media/image10.png)

5.  Im Fenster **Password reset | Properties**, wählen Sie **All**, um
    die Self-Service-Kennwortzurücksetzung für alle Benutzer zu
    aktivieren. Wählen Sie **Save** aus.

> ![A screenshot of a computer Description automatically
> generated](./media/image11.png)
>
> ![A screenshot of a computer screen Description automatically
> generated](./media/image12.png)

6.  Klicken Sie auf die Seite **Password reset | Properties**, wählen
    Sie **Authentication methods**.

> ![A screenshot of a computer Description automatically
> generated](./media/image13.png)

7.  Stellen Sie für die Methoden, die Benutzern zur Verfügung stehen,
    sicher, dass **Mobil phone** und **Email** ausgewählt sind, und
    wählen Sie dann **Security Questions**.

8.  Für **Number of questions required to register**, wählen Sie **3**.

9.  Für **Number of questions required to reset**, wählen Sie **3**.

> ![A screenshot of a computer Description automatically
> generated](./media/image14.png)

10. Im Abschnitt **Select security questions**, wählen Sie **No security
    questions configured**, dann wählen Sie **Predefined**. Wählen Sie
    drei Fragen Ihrer Wahl aus, und wählen Sie dann zweimal **OK** aus.

> ![A screenshot of a computer Description automatically
> generated](./media/image15.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image16.png)

11. Wählen Sie **Save** aus.

> ![A screenshot of a computer Description automatically
> generated](./media/image17.png)

12. Wählen Sie **Registrierung** aus. Wählen Sie **Yes** für **Require
    users to register when signing in**, und **Number of days before
    users are asked to re-confirm their authentication information**,
    legen Sie den Wert auf **90** fest**,** und wählen Sie dann **Save**
    aus.

> ![A screenshot of a computer Description automatically
> generated](./media/image18.png)

13. Wählen Sie im Navigationsbereich **On-premises integration**.

14. Stellen Sie sicher, dass Ihr lokaler Rückschreibeclient ausgeführt
    wird, und stellen Sie sicher, dass das Kontrollkästchen für **Enable
    password write back for synced users**. Wählen Sie bei Bedarf
    **Save**.

> ![A screenshot of a computer Description automatically
> generated](./media/image19.png)

15. Schließen Sie Microsoft Edge.

Aufgabe 3: Überprüfen der Self-Service-Kennwortzurücksetzung

1.  Wechseln Sie zu [***SEA-WS3***](urn:gd:lg:a:select-vm). Melden Sie
    sich bei Bedarf an als !!**[Admin](urn:gd:lg:a:send-vm-keys)!!** mit
    dem Passwort !!**[Pa55w.rd](urn:gd:lg:a:send-vm-keys)!!**an.

2.  Wählen Sie auf der Taskleiste **Microsoft Edge aus**. Navigieren Sie
    zu !!**https://mysignins.microsoft.com/!!**

3.  Wählen Sie auf der Seite **Pick an account** die Option **Use
    another account**.

> ![A screenshot of a computer Description automatically
> generated](./media/image20.png)

4.  Geben Sie auf der **Sign in** Seite
    [!!**Cindy@M365xXXXXXX.onmicrosoft.com**](mailto:!!Cindy@M365xXXXXXX.onmicrosoft.com)**!!**
    an und wählen Sie dann **Next**.

5.  Geben Sie auf der Seite **Enter password** **!! P@55w.rd1234!!** ein
    und wählen Sie dann **Sign i** aus. Wenn Microsoft Edge Sie
    auffordert, das Kennwort zu speichern, wählen Sie **Save**.

> ![A screenshot of a computer error Description automatically
> generated](./media/image21.png)

6.  Sie werden aufgefordert **More information required** auszuwählen,
    klicken Sie auf **Next.**

> ![A screenshot of a computer error Description automatically
> generated](./media/image22.png)

7.  Geben Sie die Details ein und klicken Sie auf **Next.**

> ![A screenshot of a computer Description automatically
> generated](./media/image23.png)

8.  Geben Sie den 6-stelligen Code ein und klicken Sie auf **Next**

> ![](./media/image24.png)

9.  Klicken Sie erneut auf **Next**.

> ![A screenshot of a computer Description automatically
> generated](./media/image25.png)

10. Klicken Sie auf **Done**.

> ![](./media/image26.png)

11. Sie sollten in der Lage sein, auf die Seite **My Account** zu
    klicken.

> ![](./media/image27.png)

12. Um das **Passwort** zu ändern**,** besuchen Sie den Link - **!!
    https://mysignins.microsoft.com/security-info!!**

13. Schließen Sie die Verifizierung ab, indem Sie auf den Text
    +XXXXXXXXXXXXXX

> ![A screenshot of a computer error Description automatically
> generated](./media/image28.png)

14. Geben Sie den 6-stelligen Code ein und klicken Sie dann auf
    Überprüfen.

> ![A screenshot of a computer error Description automatically
> generated](./media/image29.png)

15. Klicken Sie auf **Skip for now.**

> ![A screenshot of a computer error Description automatically
> generated](./media/image30.png)

16. Klicken Sie auf der Seite **Security Info** auf **Change** um das
    Passwort zu ändern.

> ![A screenshot of a login page Description automatically
> generated](./media/image31.png)

17. Geben Sie auf der Seite **Change your password** die folgenden
    Informationen ein, und wählen Sie dann **Submit**:

    - Create new password: **!!P@55w.rd12345!!**

    - Confirm new password: **!!P@55w.rd12345!!**

> ![A screenshot of a login box Description automatically
> generated](./media/image32.png)

18. Klicken Sie auf die Schaltfläche **Done**.

> ![](./media/image33.png)

19. Schließen Sie Microsoft Edge, und melden Sie sich bei
    [***SEA-WS3***](urn:gd:lg:a:select-vm) ab.

Aufgabe 4: Ausführen der Azure AD Connect-Synchronisierung

Beachten Sie, dass dieser Schritt normalerweise nicht für das
Kennwortrückschreiben erforderlich ist, aber empfohlen wird, um Probleme
in Laborumgebungen zu beheben und sicherzustellen, dass AD DS mit
Microsoft Entra synchronisiert wird.

1.  Wechseln Sie zu [***SEA-SVR1,***](urn:gd:lg:a:select-vm) klicken Sie
    mit der rechten Maustaste auf **Start** und wählen Sie dann
    **Windows PowerShell (Admin)**.

> ![A screenshot of a computer Description automatically
> generated](./media/image34.png)

2.  Geben Sie an der **Windows PowerShell-Eingabeaufforderung** den
    folgenden Befehl ein, und drücken Sie dann **Enter**:

> **!!Start-ADSyncSyncCycle -PolicyType Delta!!**
>
> ![A screenshot of a computer Description automatically
> generated](./media/image35.png)

3.  Schließen Sie Windows PowerShell, und warten Sie dann ca. 3 bis 4
    Minuten.

Aufgabe 5: Überprüfen des Kennwortrückschreibens

1.  Wechseln Sie zu [***SEA-CL1***](urn:gd:lg:a:select-vm) und melden
    Sie sich ggf. ab. Wählen Sie auf
    [***SEA-CL1***](urn:gd:lg:a:select-vm) Other Users aus**,** und
    versuchen Sie dann, sich als !!**Contoso\Cindy!!** mit dem Passwort
    von !!**P@55w.rd1234!!** an**.**

> ![A screenshot of a computer Description automatically
> generated](./media/image36.png)

2.  Stellen Sie sicher, dass Sie die Meldung erhalten, dass der
    Benutzername oder das Kennwort falsch ist.

> ![A screenshot of a computer screen Description automatically
> generated](./media/image37.png)

3.  Melden Sie sich jetzt an als !!**Contoso\Cindy!!** mit dem Passwort
    [!!**P@55w.rd12345**](mailto:!!P@55w.rd12345)**!!** an, dem
    Kennwort, das mit der SSPR-Funktion festgelegt wurde.

4.  Sie sollten dieses Mal erfolgreich angemeldet sein mit dem **new
    password**.

Dadurch wird bestätigt, dass das Kennwort, das Sie im Portal My Sign in
geändert haben, in das lokale Active Directory Domain Services (AD DS)
-Konto zurückgeschrieben wird.

![A screenshot of a computer error Description automatically
generated](./media/image38.png)

> Hinweis – Wenn Sie die obige Meldung während der Anmeldung erhalten,
> wird bestätigt, dass ***authentication was successful***, das Konto
> jedoch aufgrund eines Problems mit der Gruppenmitgliedschaft keine
> Berechtigung zur Anmeldung auf dem SEA-CL1 hatte.

**Ergebnisse**: Nach Abschluss dieser Übung haben Sie die
Self-Service-Kennwortzurücksetzung erfolgreich konfiguriert und
validiert.
