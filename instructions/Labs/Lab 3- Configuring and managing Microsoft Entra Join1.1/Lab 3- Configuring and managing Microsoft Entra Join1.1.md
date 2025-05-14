**Lab 03: Konfigurieren und Verwalten von Microsoft Entra ID Join**

**Zusammenfassung**

In dieser Übung konfigurieren Sie die Microsoft Entra ID
Join-Einstellungen und führen sowohl Standard- als auch Microsoft Entra
Hybridjoin-Szenarien für Windows-Geräte durch.

**Voraussetzungen**

Die folgenden Übungen müssen vor diesem Lab abgeschlossen werden:

- Lab \#2: Synchronisieren von Identitäten mithilfe von Microsoft Entra
  Connect

**Hinweis**: Sie benötigen außerdem ein Mobiltelefon, das
Textnachrichten empfangen kann, die zum Sichern der Windows
Hello-Anmeldeauthentifizierung bei der Entra ID verwendet werden.

**Übung 1: Konfigurieren von Microsoft Entra Join**

**Szenario**

Sie müssen die Entra ID-Geräteeinstellungen konfigurieren, um
sicherzustellen, dass alle Benutzer Geräte mit Entra ID verknüpfen
dürfen. Sie müssen auch sicherstellen, dass Benutzer nur maximal 20
Geräten beitreten können und dass Allan Deyoung als lokaler
Administrator auf allen Microsoft Entra Joined-Geräten hinzugefügt wird.
Abschließend überprüfen Sie, ob Microsoft Entra Join wie erwartet
funktioniert, indem Sie Joni Sherman SEA-WS1 mit dem Mandanten
verknüpfen lassen.

## Aufgabe 0: Aktivieren von TLS 1.2 mithilfe des PowerShell-Skripts.

1.  Melden Sie sich auf SEA-WS1 als Contoso\Administrator mit dem
    Kennwort Pa55w.rd an.

2.  Geben Sie im Startmenü [**PowerShell
    ein**](urn:gd:lg:a:send-vm-keys) , klicken Sie mit der rechten
    Maustaste auf PowerShell und wählen Sie Als Administrator ausführen
    aus.

![](./media/image1.png)

3.  Führen Sie das folgende Skript in der PowerShell aus.

**If** (-Not (Test-Path
'HKLM:\SOFTWARE\WOW6432Node\Microsoft\\NETFramework\v4.0.30319'))

{

New-Item 'HKLM:\SOFTWARE\WOW6432Node\Microsoft\\NETFramework\v4.0.30319'
-Force | Out-Null

}

New-ItemProperty -Path
'HKLM:\SOFTWARE\WOW6432Node\Microsoft\\NETFramework\v4.0.30319' -Name
'SystemDefaultTlsVersions' -Value '1' -PropertyType 'DWord' -Force |
Out-Null

New-ItemProperty -Path
'HKLM:\SOFTWARE\WOW6432Node\Microsoft\\NETFramework\v4.0.30319' -Name
'SchUseStrongCrypto' -Value '1' -PropertyType 'DWord' -Force | Out-Null

**If** (-Not (Test-Path
'HKLM:\SOFTWARE\Microsoft\\NETFramework\v4.0.30319'))

{

New-Item 'HKLM:\SOFTWARE\Microsoft\\NETFramework\v4.0.30319' -Force |
Out-Null

}

New-ItemProperty -Path
'HKLM:\SOFTWARE\Microsoft\\NETFramework\v4.0.30319' -Name
'SystemDefaultTlsVersions' -Value '1' -PropertyType 'DWord' -Force |
Out-Null

New-ItemProperty -Path
'HKLM:\SOFTWARE\Microsoft\\NETFramework\v4.0.30319' -Name
'SchUseStrongCrypto' -Value '1' -PropertyType 'DWord' -Force | Out-Null

**If** (-Not (Test-Path
'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS
1.2\Server'))

{

New-Item
'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS
1.2\Server' -Force | Out-Null

}

New-ItemProperty -Path
'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS
1.2\Server' -Name 'Enabled' -Value '1' -PropertyType 'DWord' -Force |
Out-Null

New-ItemProperty -Path
'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS
1.2\Server' -Name 'DisabledByDefault' -Value '0' -PropertyType 'DWord'
-Force | Out-Null

**If** (-Not (Test-Path
'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS
1.2\Client'))

{

New-Item
'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS
1.2\Client' -Force | Out-Null

}

New-ItemProperty -Path
'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS
1.2\Client' -Name 'Enabled' -Value '1' -PropertyType 'DWord' -Force |
Out-Null

New-ItemProperty -Path
'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS
1.2\Client' -Name 'DisabledByDefault' -Value '0' -PropertyType 'DWord'
-Force | Out-Null

Write-Host 'TLS 1.2 has been enabled. You must restart the Windows
Server for the changes to take affect.' -ForegroundColor Cyan

![](./media/image2.png)

4.  Starten Sie die Windows Server-VM neu.

![](./media/image3.png)

## Task 1: Configure Microsoft Entra ID join Device settings

1.  Wechseln Sie zu **SEA-SVR1**. Geben Sie in der Adressleiste des
    **Microsoft Edge-Browsers** die folgende URL ein**: !!**
    [**https://entra.microsoft.com**](https://entra.microsoft.com)!! und
    drücken Sie dann **Enter**.

2.  Melden Sie sich mit Ihrer O365-Mandanten-ID an:
    !!**admin@M365xXXXXXXXX.onmicrosoft.com**!!und verwenden Sie das
    Admin-Kennwort des Mandanten.

![A screenshot of a computer Description automatically
generated](./media/image4.png)

![A screenshot of a login box Description automatically
generated](./media/image5.png)

3.  In der Dialogbox **Stay signed in?** Wählen Sie die Schaltfläche
    **Yes** aus.

![A screenshot of a computer Description automatically
generated](./media/image6.png)

4.  Navigieren Sie im **Microsoft Entra admin center** -Fenster und
    klicken Sie auf **Identity**.

![A screenshot of a computer Description automatically
generated](./media/image7.png)

5.  Wählen Sie im Abschnitt **Identity** die Option **Devices** aus,
    navigieren Sie dann und klicken Sie auf **All Devices,** wie in der
    Abbildung unten gezeigt.

![A screenshot of a computer Description automatically
generated](./media/image8.png)

Beachten Sie, dass keine Geräte gefunden wurden, da Sie noch keinem
Gerät beigetreten sind.

![](./media/image9.png)

6.  Auf den **Devices | All devices** und wählen Sie **Device
    settings**.

![A screenshot of a computer Description automatically
generated](./media/image10.png)

7.  Auf den **Devices | Device settings** im Detailbereich unter **Users
    may join devices to Entra**, Vergewissern Sie sich, dass **All**
    ausgewählt ist.

Dies bedeutet, dass alle Entra-Benutzer berechtigt sind, Windows 10 oder
neuere Geräte mit Microsoft Entra zu verbinden. Beachten Sie, dass diese
Einstellung nicht für in Entra hybrid eingebundene Geräte oder für
Geräte gilt, die über den Selbstbereitstellungsmodus von Windows
Autopilot eingebunden wurden.

8.  Im Bereich **Require Multi-factor Authentication to register or join
    devices with Entra**, stellen Sie sicher, dass die Einstellung auf
    **No**.

![A screenshot of a computer Description automatically
generated](./media/image11.png)

9.  Wählen Sie im Abschnitt **Maximum number of devices per user** die
    Option **20 (Recommended)**.

10. Klicken Sie auf den Link **Manage** **Additional local
    administrators on all Microsoft Entra Joined devices**. Die **Device
    Administrators** Seite öffnet sich.

![A screenshot of a computer Description automatically
generated](./media/image12.png)

11. Klicken Sie in der Menüleiste **Device Administrators |
    Assignments**, wählen Sie **Add assignments**.

![A screenshot of a computer Description automatically
generated](./media/image13.png)

12. Geben Sie im Suchfeld !! ein. **Allan Deyoung**!!, wählen Sie das
    Benutzerobjekt **Allan Deyoung** aus, und wählen Sie dann **Add**.

![A screenshot of a computer Description automatically
generated](./media/image14.png)

13. Allan Deyoung wird jetzt als Geräteadministrator auf allen Microsoft
    Entra Joined-Geräten hinzugefügt.

![A screenshot of a computer screen Description automatically
generated](./media/image15.png)

14. Klicken Sie auf **Devices | Device settings** unter der Suchleiste
    des Azure-Portals, um zur Seite **Device settings** zurückzukehren.

![A screenshot of a computer Description automatically
generated](./media/image16.png)

15. Wählen Sie auf der Seite **Device settings** die Option **Save**.

![A screenshot of a computer Description automatically
generated](./media/image17.png)

**Aufgabe 2: Ausführen der Microsoft Entra ID-Verknüpfung**

1.  Wechseln Sie zu
    [SEA-WS1](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10)
    und melden Sie sich als **Admin** mit dem Passwort!! **Pa55w.rd**!!.

![](./media/image18.png)

2.  Wählen Sie auf der Taskleiste das **Symbol für die
    Windows-Startschaltfläche** aus, und wählen Sie dann **Settings**.

![](./media/image19.png)

3.  Wählen Sie im Fenster **Settings** die Option **Accounts**.

![A screenshot of a computer Description automatically
generated](./media/image20.png)

4.  Wählen Sie auf der Seite **Accounts** die Option **Access work or
    school**.

![A screenshot of a computer Description automatically
generated](./media/image21.png)

5.  Wählen Sie auf der Seite **Access work or school** die Option
    **Connect**.

![A screenshot of a computer Description automatically
generated](./media/image22.png)

6.  Wählen Sie im **Microsoft account** \> **Join this device to
    Microsoft Entra ID**.

![A screenshot of a computer screen Description automatically
generated](./media/image23.png)

7.  Geben Sie auf der **Sign In** !!
    ein.JoniS@M365xXXXXXXX.onmicrosoft.com!! und wählen Sie dann
    **Next** aus.

![Graphical user interface, application, Teams Description automatically
generated](./media/image24.png)

8.  Geben Sie auf der Seite **Enter password** das Mandantenkennwort
    ein: !\![**P@55w.rd1234**](mailto:P@55w.rd1234)!! und wählen Sie
    dann **Anmelden** aus.

![Graphical user interface, application Description automatically
generated](./media/image25.png)

9.  Wählen Sie im Dialogfeld **Make sure this is your organization** die
    Option **Join**.

![A screenshot of a computer error Description automatically
generated](./media/image26.png)

10. Auf der Seite **You're all set!** Seite, wählen Sie **Done**.

![A screenshot of a computer Description automatically
generated](./media/image27.png)

11. Vergewissern Sie sich auf der Seite **Access work or school**
    zugreifen**, Connected to Contoso's Azure AD** angezeigt wird.

![A screenshot of a computer Description automatically
generated](./media/image28.png)

12. Schließen Sie die Seite **Settings**.

**Aufgabe 3: Überprüfen von Microsoft Entra Join**

1.  Klicken Sie auf
    [SEA-WS1](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10)
    mit der rechten Maustaste auf das Symbol für die **Windows** **Start
    button** und wählen Sie dann **Windows Terminal (Admin)** aus, wie
    in der folgenden Abbildung gezeigt.

![](./media/image29.png)

2.  Wählen Sie im Dialogfeld **User Account Control** die Option
    **Yes**.

![](./media/image30.png)

3.  Geben Sie in der PowerShell-Konsole den folgenden Befehl ein, und
    drücken Sie die **Enter:**

!!**dsregcmd /status**!!

4.  Überprüfen Sie in der Ausgabe unter **Device Status**, ob
    **AzureAdJoined: YES** angezeigt wird.

Dies bedeutet, dass das Gerät Microsoft Entra Joined ist.

![](./media/image31.png)

5.  Schließen Sie PowerShell.

6.  Klicken Sie erneut mit der rechten Maustaste auf das Symbol der
    **Windows-Startschaltfläche** und wählen Sie dann **Computer
    Management**.

![A screenshot of a computer Description automatically
generated](./media/image32.png)

7.  Erweitern Sie im Fenster **Computer Management** die Option **Local
    Users and Groups**, und wählen Sie dann **Groups**.

![](./media/image33.png)

![A screenshot of a computer Description automatically
generated](./media/image34.png)

8.  Doppelklicken Sie auf die Gruppe **Administrators**.

![A screenshot of a computer Description automatically
generated](./media/image35.png)

Beachten Sie, dass Joni Sherman als lokale Administratorin auf [SEA-WS1
hinzugefügt
wurde](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10).
Beachten Sie auch zwei Sicherheitsprinzipale, die durch ihre
Sicherheits-IDs (Security Identifier, SID) dargestellt werden. Diese
beiden SIDs stellen die globale Administratorrolle Entra und die Rolle
des Microsoft Entra Joined-Geräteadministrators dar.

![](./media/image36.png)

9.  Schließen Sie alle geöffneten Fenster und melden Sie sich von
    SEA-WS1 ab, indem Sie auf **Windows Start button icon \> Admin \>
    Sign out**.

![](./media/image37.png)

10. Wechseln Sie zu **SEA-SVR1** und melden Sie sich mit den
    Anmeldeinformationen **Contoso\Administrator** und Passwort an
    !!**Pa55w.rd**!!

![A screenshot of a computer Description automatically
generated](./media/image38.png)

11. Navigieren Sie im **Microsoft Entra Admin Center** und klicken Sie
    auf **Identity**.

12. Navigieren Sie und wählen Sie **Devices**, dann klicken Sie auf
    **All devices**.

13. Klicken Sie in der Menüleiste **Devices | All devices**, beachten
    Sie, dass **SEA-WS1** aufgeführt ist.

![](./media/image39.png)

14. Stellen Sie sicher, dass der **Join-Typ** als **Microsoft Entra
    Joined** aufgeführt ist und dass der Besitzer **Joni Sherman** ist.

![](./media/image40.png)

15. Beachten Sie auch, dass in der Spalte MDM **None**. Dies weist
    darauf hin, dass dieses Gerät noch nicht von Microsoft Intune
    verwaltet wird.

![A screenshot of a computer Description automatically
generated](./media/image41.png)

**Aufgabe 4: Anmelden bei Windows als Microsoft Entra User**

1.  Wechseln Sie zu **SEA-WS1** und klicken Sie auf **Other user.**

![](./media/image42.png)

2.  **Melden** Sie sich als !!**JoniS@M365xXXXXXXX.onmicrosoft.com**!!
     mit dem Mieterpasswort: !!**P@55w.rd1234**!!

**Hinweis: Warten Sie, bis das Profil erstellt wurde.**

![](./media/image43.png)

**Hinweis** – Wenn Sie zu **Windows Hello** aufgefordert werden,
schließen Sie den Anmeldevorgang entsprechend ab und geben Sie auf der
Seite **Set up a PIN** in den Feldern **New PIN** und **Confirm Pin** !!
**ein.102938**!! und wählen Sie dann **OK** aus.

![](./media/image44.png)

**Aufgabe 5: Entfernen eines Windows-Geräts aus Entra**

1.  Melden [Sie sich auf
    SEA-WS1](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10)
    mit Joni Sherman an, wenn Sie dazu aufgefordert werden und wenn die
    Option zur Eingabe der PIN verfügbar ist, geben Sie die PIN ein:
    !!**102938**!! oder geben Sie das Passwort als !!**P@55w.rd1234**!!

![A screenshot of a computer Description automatically
generated](./media/image45.png)

2.  Wählen Sie im Fenster **Settings** die Option **Accounts**.

![A screenshot of a computer Description automatically
generated](./media/image46.png)

3.  Navigieren Sie im linken Navigationsbereich und klicken Sie auf
    **Accounts**. Wählen Sie auf der Seite **Accounts** die Option
    **Access work or school** aus.

![A screenshot of a computer Description automatically
generated](./media/image47.png)

4.  Wählen Sie auf der Seite **Access work or school** die Dropdownliste
    neben **Connected to Contoso's Azure AD** aus**,** wie in der
    folgenden Abbildung dargestellt. Klicken Sie auf **Disconnect** und
    wählen Sie dann **Yes**.

![](./media/image48.png)

![A screenshot of a computer Description automatically
generated](./media/image49.png)

![A screenshot of a computer Description automatically
generated](./media/image50.png)

5.  Wählen Sie auf der Seite **Disconnect from the organization** die
    Option **Disconnect**.

![A blue box with white text Description automatically
generated](./media/image51.png)

6.  Geben Sie im Dialogfeld **Windows Security** im Feld
    **E-Mail-Adresse** den Wert!!. Admin!! ein und geben Sie in das Feld
    **Password**!! Pa55w.rd!! ein. Wählen Sie **OK**.

![Graphical user interface Description automatically
generated](./media/image52.png)

7.  Wählen Sie im Dialogfeld **Restart your PC** die Option **Restart
    now**. **SEA-WS1** und starten Sie neu.

![A blue box with white text Description automatically
generated](./media/image53.png)

**Ergebnisse**: Nach Abschluss dieser Übung haben Sie die Microsoft
Entra Geräteeinstellungen konfiguriert, ein Gerät mit Entra verknüpft
und ein Gerät aus Entra entfernt.

**Übung 2: Konfigurieren der Microsoft Entra Hybrideinbindung**

**Szenario**

Einige Contoso Windows-Geräte sind derzeit mit den lokalen Active
Directory-Domänendiensten verbunden. Damit diese Geräte nahtlos auf
Clouddienste zugreifen können, planen Sie, Microsoft Entra Hybrid Join
zu aktivieren. Sie testen Microsoft Entra Hybrid Join, indem Sie Azure
AD Connect neu konfigurieren und den Prozess auf SEA-CL2 testen.

**Aufgabe 1: Vorbereiten der Umgebung**

1.  Wechseln Sie zu
    [SEA-SVR1](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10).

![A picture containing text Description automatically
generated](./media/image54.png)

2.  Wählen Sie die **Windows** **Start icon** aus**,** erweitern Sie
    **Windows Administrative Tools,** und wählen Sie dann **Active
    Directory Users and Computers** aus.

![](./media/image55.png)

3.  Klicken Sie in **Active Directory Users and Computers** mit der
    rechten Maustaste auf **Contoso.com**, zeigen Sie auf **Neu**, und
    wählen Sie dann **Organizational Unit** aus.

![](./media/image56.png)

4.  In der Dialogbox **New-Object - Organizational Unit**, geben Sie
    !!**Entra clients**!! ein und wählen Sie dann **OK**.

![A screenshot of a computer Description automatically
generated](./media/image57.png)

5.  Wählen Sie im Navigationsbereich **Seattle Clients**. Klicken Sie
    mit der rechten Maustaste auf **SEA-CL2** und wählen Sie dann
    **Move**.

![](./media/image58.png)

6.  Wählen Sie im Dialogfeld **Move** die Option **Entra clients** und
    dann **OK** aus.

![A screenshot of a computer Description automatically
generated](./media/image59.png)

7.  Schließen Sie **Active Directory Users and Computers**.

![A screenshot of a computer Description automatically
generated](./media/image60.png)

**Aufgabe 2: Neukonfiguration von Entra Connect**

1.  Doppelklicken Sie auf [dem Desktop auf
    SEA-SVR1](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10)
    auf Azure AD Connect

![A black rectangle with blue lines Description automatically
generated](./media/image61.png)

1.  Wählen Sie im **Microsoft Azure Active Directory** Connect-Fenster
    **Configure**.

![](./media/image62.png)

2.  Wählen Sie auf der Seite **Additional tasks** die Option **Customize
    synchronization options** aus, und wählen Sie **Next**.

![A screenshot of a computer Description automatically
generated](./media/image63.png)

3.  Geben Sie auf der Seite **Connect to Entra** in den Feldern
    **USERNAME** und **PASSWORD** Ihre Anmeldeinformationen für den
    Office 365-Mandanten **ein,** und wählen Sie dann **Next** aus.

![A screenshot of a computer Description automatically
generated](./media/image64.png)

4.  Klicken Sie auf der Seite **Connect your directories** auf die
    Schaltfläche **Next.**

![A screenshot of a computer Description automatically
generated](./media/image65.png)

5.  Stellen Sie auf der Seite **Domain and OU filtering** sicher, dass
    **Sync selected domains and Ous** ausgewählt ist.

6.  Erweitern Sie **Contoso.com**, wählen Sie **Entra Clients** aus und
    klicken Sie dann auf **Next**.

![A screenshot of a computer Description automatically
generated](./media/image66.png)

7.  Stellen Sie auf der Seite **Optional features** sicher, dass
    **Password hash synchronization** ausgewählt ist, und wählen Sie
    dann **Next**.

8.  Auf der Seite **Ready to configure**, stellen Sie sicher das **Start
    the synchronization process when configuration
    completes** ausgewählt ist, und wählen Sie dann **Configure**.

![A screenshot of a computer Description automatically
generated](./media/image67.png)

9.  Wenn die Konfiguration abgeschlossen ist, wählen Sie **Exit** aus.

![](./media/image68.png)

Hinweis: Warten Sie ca. 5 Minuten, bis die Synchronisierung
abgeschlossen ist.

**Aufgabe 3: Konfigurieren der Microsoft Entra Hybrideinbindung mit
Azure AD Connect**

1.  Doppelklicken Sie
    [auf](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10)
    dem SEA-SVR1 VM **Desktop** auf **Azure AD Connect**.

![Text Description automatically generated with medium
confidence](./media/image69.png)

2.  Wählen Sie im **Fenster Microsoft Azure Active Directory Connect**
    die Option **Configure**.

![](./media/image70.png)

3.  Wählen Sie auf der Seite **Additional tasks** die Option **Configure
    device options** und wählen Sie **Next**.

![](./media/image71.png)

4.  Wählen Sie auf der Seite **Overview** die Option **Next**.

![A screenshot of a computer Description automatically
generated](./media/image72.png)

5.  Geben Sie auf der Seite **Connect to Entra** (Mit Entra verbinden)
    das Kennwort des Administratormandanten in das Feld **PASSWORD**
    ein, und wählen Sie dann **Next**.

![](./media/image73.png)

6.  Wählen Sie auf der Seite **Device Options** die Option **Configure
    Hybrid Azure AD Join** aus, und wählen Sie dann **Next**.

![A screenshot of a computer Description automatically
generated](./media/image74.png)

7.  Wählen Sie auf der Seite **Device operating systems** die Option
    **Windows 10 or later domain-joined devices**, und wählen Sie dann
    **Next**.

![A screenshot of a computer Description automatically
generated](./media/image75.png)

8.  Aktivieren Sie auf der **SCP-Konfigurationsseite** das
    Kontrollkästchen neben **Contoso.com**. Wählen Sie **Azure Active
    Directory** vom **Authentication Service** Dropdown und wählen Sie
    **Add**.

![](./media/image76.png)

9.  Geben Sie im Fenster **Enterprise Admin Credentials** window
    **Contoso\Administrator** als **USername** und !!**Pa55w.rd**!! als
    **Password**. Wählen Sie **OK** und dann **Next** aus.

![A screenshot of a computer security Description automatically
generated](./media/image77.png)

![](./media/image78.png)

10. Wählen Sie auf der Seite **Ready to configure** die Option
    **Configure** aus, um die Konfiguration auszuführen.

![A screenshot of a computer Description automatically
generated](./media/image79.png)

11. Wenn die Konfiguration abgeschlossen ist, wählen Sie **Exit**.

![A screenshot of a computer Description automatically
generated](./media/image80.png)

12. Klicken Sie in der Taskleiste mit der rechten Maustaste auf das
    Symbol für die **Windows Start button icon** und wählen Sie
    **Windows Powershell (Admin)**.

![A screenshot of a computer Description automatically
generated](./media/image81.png)

13. Geben Sie im **Windows PowerShell-Fenster** den folgenden Befehl
    ein, und drücken Sie dann **Enter**:

!!**Start-ADSyncSyncCycle -PolicyType Initial**!!

![A screenshot of a computer Description automatically
generated](./media/image82.png)

14. Schließen des PowerShell-Fensters.

Hinweis: Warten Sie ca. 5 Minuten, bis die Synchronisierung
abgeschlossen ist.

**Task 4: Verify the Entra registration**

1.  Wechseln Sie zu
    [SEA-CL2](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10).

2.  Wählen Sie auf der Anmeldeseite die Power Taste aus, und wählen Sie
    dann **Restart**.

![Graphical user interface, application Description automatically
generated](./media/image83.png)

***Hinweis**: Der Neustart löst die hybride Microsoft Entra Join On aus
[SEA-CL2](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10).*

3.  Melden Sie sich nach dem Neustart von **SEA-CL2** als
    **Contoso\Administrator** mit dem Kennwort !!**Pa55w.rd**!!

![Graphical user interface, application Description automatically
generated](./media/image84.png)

4.  Klicken Sie in der Taskleiste mit der rechten Maustaste auf die
    Schaltfläche **Windows Start icon button** und wählen Sie **Windows
    Terminal (Admin)**.

![A screenshot of a computer Description automatically
generated](./media/image81.png)

5.  Geben Sie im **Windows PowerShell-Fenster** den folgenden Befehl
    ein, und drücken Sie dann **Enter**:

!!**dsregcmd /status**!!

6.  Überprüfen Sie in der Ausgabe unter **Device Item**, ob. 

- **AzureAdJoined : YES** 

- **DomainJoined : YES** wird angezeigt.

![](./media/image85.png)

***Hinweis: Wenn das Gerät noch nicht mit Entra verbunden ist, warten
Sie, bis die Entra Connect-Synchronisierung abgeschlossen ist, und
starten Sie SEA-CL2 erneut neu. Es kann 5-10 Minuten dauern, bis der
Status aktualisiert wird.***

Darüber hinaus können Sie sich bei **SEA-SVR1** anmelden und im
**Windows** PowerShell-Fenster den folgenden Befehl eingeben, um die
Synchronisierung zu beschleunigen.

!!**Start-ADSyncSyncCycle -PolicyType Initial**!!

7.  Alle Fenster schließen Auf
    [SEA-CL2](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10)
    und abmelden.

8.  Wechseln Sie zu
    [SEA-SVR1](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10)
    und zum **Microsoft Entra Admin** Center-Fenster, navigieren Sie und
    klicken Sie auf **Identity**.

![A screenshot of a computer Description automatically
generated](./media/image7.png)

9.  Wählen Sie im Abschnitt **Identity** die Option **Devices** aus,
    navigieren Sie dann und klicken Sie auf **All Devices,** wie in der
    Abbildung unten gezeigt.

![A screenshot of a computer Description automatically
generated](./media/image8.png)

10. Stellen Sie sicher, dass **SEA-CL2** **Microsoft Entra** **hybrid
    joined** als Wert für die Zeile **Join-Typ** hat. Klicken Sie auf
    die Schaltfläche **Refresh**, wenn SEA-CL2 nicht aufgeführt ist.

![A screenshot of a computer Description automatically
generated](./media/image86.png)

11. Schließen Sie alle Fenster in
    [SEA-SVR1](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10).

**Ergebnisse**: Nach Abschluss dieser Übung haben Sie die Microsoft
Entra Hybrideinbindung erfolgreich konfiguriert und validiert.
