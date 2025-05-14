Lab 02 - Sincronizzazione delle identità tramite Microsoft Entra Connect

**Summary**

**In questa esercitazione verrà configurata la sincronizzazione da
Servizi di dominio Active Directory all'ID Microsoft Entra**

**Scenario**

Contoso Corporation gestisce attualmente gli utenti sia in Active
Directory Domain Services che in Microsoft Entra ID come processi
separati. Questo richiede molto tempo e ha portato a informazioni
incoerenti. È stato assegnato il compito di risolvere questo problema
connettendo le due directory utilizzando lo strumento di
sincronizzazione Microsoft Entra Connect.

## Task 0: Enable TLS 1.2 using PowerShell script

1.  In SEA-SVR1 accedere come Contoso\Administrator con la password
    Pa55w.rd

2.  Nel menu di avvio digita PowerShell, fai clic con il pulsante destro
    del mouse su PowerShell e seleziona **Esegui come amministratore.**

![](./media/image1.png)

3.  Eseguire lo script seguente in PowerShell.

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

4.  Riavviare la macchina virtuale Windows Server.

![](./media/image3.png)

Task 1: Configurare la sincronizzazione della directory con Microsoft
Entra Connect

1.  In SEA-SVR1, se necessario, accedere come Contoso\Administrator con
    la password di !! Pa55w.rd!! Sulla barra delle applicazioni,
    seleziona Microsoft Edge.

2.  Nella barra degli indirizzi,
    inserisci!\![**http://www.microsoft.com/en-us/download/details.aspx?id=47594**](urn:gd:lg:a:send-vm-keys)!!

3.  Nella pagina Microsoft Entra Connect selezionare Scarica.

> Microsoft Entra Connect automatically downloads to
> the **Downloads** folder on **SEA-SVR1**.
>
> ![A screenshot of a computer Description automatically
> generated](./media/image4.png)
>
> Fare clic su **Apri file** per il file scaricato
> **AzureADConnect.msi.**![A screenshot of a phone Description
> automatically generated](./media/image5.png)
>
> Nella pagina Benvenuto in Azure AD Connect della procedura guidata
> Microsoft Azure Active Directory Connect selezionare la casella di
> controllo Accetto le condizioni di licenza e l'informativa sulla
> privacy e quindi selezionare Continua.
>
> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image6.png)

4.  Nella pagina **Impostazioni rapide,** seleziona **Personalizza**.

> ![](./media/image7.png)
>
> Nella pagina **Installa componenti** necessari selezionare
> **Installa**.
>
> ![](./media/image8.png)

5.  Nella pagina di **accesso** utente verificare che l**'opzione
    Sincronizzazione** hash password sia selezionata e quindi
    selezionare **Avanti**.

> ![](./media/image9.png)

6.  **Nella pagina Connetti ad Azure AD,** nelle caselle **NOME UTENTE**
    e **PASSWORD, immettere le credenziali** del tenant di Office 365 e
    **quindi selezionare Avanti**.

> ![](./media/image10.png)

7.  Nella pagina **Connetti** le directory verificare che Contoso.com
    sia elencato in **FORESTA** e quindi selezionare **Aggiungi
    directory**.

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image11.png)
>
> Nella finestra **dell'account della foresta** di Active Directory
> selezionare l'opzione Crea nuovo account AD e nel campo NOME UTENTE
> AMMINISTRATORE DELL'ORGANIZZAZIONE digitare Contoso\Administrator e
> quindi digitare !! Pa55w.rd!! nel campo **PASSWORD**. Selezionare OK,
> quindi selezionare **Avanti**.
>
> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image12.png)
>
> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image13.png)

8.  Nella pagina di configurazione dell'accesso ad Azure AD assicurarsi
    che nell'elenco a discesa NOME ENTITÀ UTENTE sia selezionato il
    valore userPrincipalName.

> ![](./media/image14.png)

9.  **Selezionare** Continua senza associare tutti i **suffissi UPN** ai
    domini verificati, quindi selezionare **Avanti**.

10. Nella pagina Filtro dominio e unità organizzativa selezionare
    Sincronizza domini e unità organizzative selezionati. Espandere
    Contoso.com, deselezionare la casella di controllo accanto a
    Contoso.com e assicurarsi che siano selezionate solo le caselle di
    controllo seguenti: IT, **Manager, Marketing, Ricerca e Vendite.
    Seleziona Avanti.**

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image15.png)

11. Nella pagina Identificazione univoca degli utenti selezionare
    Avanti.

12. Nella pagina **Filtra utenti** e dispositivi **selezionare Avanti.**

13. Nella pagina **Funzionalità facoltative esaminare** le opzioni
    disponibili, ma non apportare modifiche. Verificare che l'opzione
    **Sincronizzazione** hash password sia selezionata e quindi
    selezionare **Avanti**.

> ![](./media/image16.png)

14. Nella pagina Pronto per la **configurazione verificare che sia
    selezionata l'opzione** Avvia il processo di sincronizzazione al
    **termine della configurazione, quindi selezionare** Installa.

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image17.png)

15. Al termine della configurazione, selezionare **Esci**.

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image18.png)
>
> Nota: A questo punto, inizia la sincronizzazione degli oggetti da
> Servizi di dominio Active Directory locali e dall'ID Microsoft Entra.
> È necessario attendere circa 3-4 minuti per il completamento di questo
> processo.

16. Chiudi tutte le finestre aperte.

Task 2: Verificare la sincronizzazione nell'ID Microsoft Entra

In Microsoft Edge apri una nuova scheda e vai alla pagina degli utenti
dell'interfaccia di amministrazione di **Microsoft Entra**

\-
!\![**https://entra.microsoft.com/#view/Microsoft_AAD_UsersAndTenants/UserManagementMenuBlade/~/AllUsers/menuId/**](https://entra.microsoft.com/#view/Microsoft_AAD_UsersAndTenants/UserManagementMenuBlade/~/AllUsers/menuId/)!!
Se viene richiesto di accedere, usare le credenziali del tenant di
Office 365 dalla scheda Home dell'interfaccia del lab.

> ![A screenshot of a computer Description automatically
> generated](./media/image19.png)

1.  Verificare che vengano visualizzati gli utenti di Active Directory
    Domain Services locale. Assicurarsi che questi utenti abbiano il
    valore Sì nella colonna Sincronizzazione locale abilitata.

> ![](./media/image20.png)

2.  Nel riquadro di spostamento selezionare Espandi **gruppi** e quindi
    selezionare **Tutti i gruppi.**

> ![A screenshot of a computer Description automatically
> generated](./media/image21.png)

3.  Verifica di visualizzare i gruppi della tua zona AD DS ()

> ![A screenshot of a computer Description automatically
> generated](./media/image22.png)

4.  Seleziona il gruppo Gestori.

> ![A screenshot of a computer Description automatically
> generated](./media/image23.png)

5.  Nella pagina del gruppo **Manager** selezionare **Membri** e quindi
    assicurarsi di visualizzare gli utenti.

> ![A screenshot of a computer Description automatically
> generated](./media/image24.png)
>
> ![A screenshot of a group of people Description automatically
> generated](./media/image25.png)
>
> **Si noti che non è possibile aggiungere o rimuovere membri da questo
> gruppo, poiché proviene da Servizi di dominio Active Directory
> locale.**

15. Chiudi Microsoft Edge.

Risultati: dopo aver completato questo esercizio, Microsoft Entra
Connect sarà stato configurato correttamente per sincronizzare
l'identità da Servizi di dominio Active Directory all'ID Microsoft Entra
