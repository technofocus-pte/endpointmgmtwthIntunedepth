Lab 03: Configurazione e gestione dell'aggiunta all'ID Microsoft Entra

**Summary**

In questo lab verranno configurate le impostazioni di join ID di
Microsoft Entra ed eseguiranno scenari di join standard e ibrido di
Microsoft Entra per i dispositivi Windows.

**Prerequisites**

I seguenti laboratori devono essere completati prima di questo
laboratorio:

- Lab \#2: Sincronizzazione delle identità tramite Microsoft Entra
  Connect

**Note**: Avrai anche bisogno di un telefono cellulare in grado di
ricevere messaggi di testo utilizzati per proteggere l'autenticazione di
accesso a Windows Hello per Entra ID.

**Esercizio 1: Configurazione del join a Microsoft Entra**

**Scenario**

È necessario configurare le impostazioni del dispositivo Entra ID per
assicurarsi che tutti gli utenti siano autorizzati ad aggiungere
dispositivi a Entra ID. È inoltre necessario assicurarsi che gli utenti
possano partecipare a un massimo di 20 dispositivi e che Allan Deyoung
venga aggiunto come amministratore locale in tutti i dispositivi
aggiunti a Microsoft Entra. Infine, si verificherà che l'aggiunta a
Microsoft Entra funzioni come previsto facendo in modo che Joni Sherman
si unisca a SEA-WS1 al tenant.

## Task 0: Enable TLS 1.2 using PowerShell script.

1.  In SEA-WS1 accedere come Contoso\Administrator con la password
    Pa55w.rd

2.  Nel menu di avvio digita **PowerShell,** fai clic con il pulsante
    destro del mouse su PowerShell e seleziona Esegui come
    amministratore.

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

## Task 1: Configure Microsoft Entra ID join Device settings

1.  **Passare a SEA-SVR1**. Nella barra degli indirizzi del browser
    **Microsoft Edge**, digita il seguente URL: !!
    https://entra.microsoft.com!! e premere il pulsante **Invio**.

2.  Accedi con il tuo ID inquilino O365: !!
    admin@M365xXXXXXXXX.onmicrosoft.com!!, e utilizzare la password
    dell'amministratore del tenant.

![A screenshot of a computer Description automatically
generated](./media/image4.png)

![A screenshot of a login box Description automatically
generated](./media/image5.png)

3.  **Se rimani connesso**? , selezionare il pulsante **Sì**.

![A screenshot of a computer Description automatically
generated](./media/image6.png)

4.  Nella finestra dell'interfaccia di amministrazione di **Microsoft
    Entra**, naviga e fai clic su **Identità**.

![A screenshot of a computer Description automatically
generated](./media/image7.png)

5.  Nella sezione **Identità**, seleziona Dispositivi, quindi naviga e
    fai clic su Tutti i dispositivi come mostrato nell'immagine
    sottostante.

![A screenshot of a computer Description automatically
generated](./media/image8.png)

Si noti che non sono stati trovati dispositivi, poiché non è stato
ancora aggiunto alcun dispositivo.

![](./media/image9.png)

6.  Sui dispositivi | Pagina Tutti i **dispositivi**, selezionare
    **Impostazioni dispositivo**.

![A screenshot of a computer Description automatically
generated](./media/image10.png)

7.  **Sui dispositivi | Pagina Impostazioni dispositivo,** nel riquadro
    dei dettagli, in **Gli utenti possono aggiungere dispositivi** a
    Entra, verificare che l'opzione Tutti sia **selezionata.**

Ciò indica che tutti gli utenti Entra sono autorizzati ad aggiungere
dispositivi Windows 10 o versioni successive a Microsoft Entra. Si noti
che questa impostazione non si applica ai dispositivi aggiunti
all'ambiente ibrido Entra o ai dispositivi aggiunti tramite la modalità
di distribuzione automatica di Windows Autopilot.

8.  **Nella sezione** Richiedi autenticazione a più fattori per
    registrare o aggiungere dispositivi con Entra**,** verifica che
    l'impostazione sia impostata su **No**.

![A screenshot of a computer Description automatically
generated](./media/image11.png)

9.  **Nella sezione Numero massimo di dispositivi per utente,
    selezionare 20 (scelta consigliata).**

10. Fare clic sul **collegamento Gestisci amministratori locali
    aggiuntivi in tutti i dispositivi aggiunti a Microsoft Entra.**
    Viene visualizzata la pagina Amministratori **dispositivi.**

![A screenshot of a computer Description automatically
generated](./media/image12.png)

11. **Nella finestra** di dialogo Amministratori dispositivi **|**
    Pagina Assegnazioni**,** selezionare **Aggiungi assegnazioni.**

![A screenshot of a computer Description automatically
generated](./media/image13.png)

12. Nella casella di ricerca, inserisci !! **Allan Deyoung**!,
    selezionare l'oggetto utente Allan Deyoung, quindi selezionare
    **Aggiungi.**

![A screenshot of a computer Description automatically
generated](./media/image14.png)

13. Allan Deyoung verrà ora aggiunto come amministratore del dispositivo
    in tutti i dispositivi aggiunti a Microsoft Entra.

![A screenshot of a computer screen Description automatically
generated](./media/image15.png)

14. Fare clic su **Dispositivi | Collegamento alle impostazioni** del
    dispositivo sotto la barra di ricerca del portale di Azure per
    tornare alla pagina **Impostazioni dispositivo**.

![A screenshot of a computer Description automatically
generated](./media/image16.png)

15. **Nella pagina** Impostazioni dispositivo, seleziona **Salva.**

![A screenshot of a computer Description automatically
generated](./media/image17.png)

**Task 2: Eseguire l'aggiunta all'ID di Microsoft Entra**

Passa a SEA-WS1 e accedi come **amministratore** con la password di !!
Pa55w.rd!.

![](./media/image18.png)

1.  Sulla barra delle applicazioni, seleziona l'icona del **pulsante
    Start di Windows,** quindi seleziona **Impostazioni**.

![](./media/image19.png)

2.  Nella finestra **Impostazioni**, seleziona **Account**.

![A screenshot of a computer Description automatically
generated](./media/image20.png)

3.  Nella pagina **Account** selezionare Accedi all'azienda o
    **all'istituto di istruzione.**

![A screenshot of a computer Description automatically
generated](./media/image21.png)

4.  Nella pagina **Accedi all'azienda o all'istituto** di istruzione
    selezionare **Connetti**.

![A screenshot of a computer Description automatically
generated](./media/image22.png)

5.  **Nella finestra** dell'account Microsoft, **seleziona Aggiungi
    questo dispositivo** all'ID **Microsoft Entra.**

![A screenshot of a computer screen Description automatically
generated](./media/image23.png)

6.  Nella pagina di **accesso**, digita !!
    JoniS@M365xXXXXXXX.onmicrosoft.com!! , quindi seleziona **Avanti**.

![Graphical user interface, application, Teams Description automatically
generated](./media/image24.png)

7.  Nella pagina **Inserisci password** immettere la password del
    tenant: !! P@55w.rd1234!! e quindi seleziona **Accedi**.

![Graphical user interface, application Description automatically
generated](./media/image25.png)

8.  Nella finestra di dialogo **Assicurati che si tratti
    dell'organizzazione** selezionare **Partecipa**.

![A screenshot of a computer error Description automatically
generated](./media/image26.png)

9.  Sul pulsante **È tutto pronto**! , selezionare **Fine**.

![A screenshot of a computer Description automatically
generated](./media/image27.png)

10. Nella pagina **Accedi all'azienda** o all'istituto di istruzione
    verificare che sia visualizzato **Connesso ad Azure AD di Contoso**.

![A screenshot of a computer Description automatically
generated](./media/image28.png)

11. Chiudi la pagina **Impostazioni**.

**Task 3: Convalidare l'aggiunta a Microsoft Entra**

1.  Su SEA-WS1, fare clic con **il pulsante destro** del mouse
    sull'icona del **pulsante Start di Windows**, quindi selezionare
    Terminale Windows (amministratore) come mostrato **nell'immagine
    seguente.**

![](./media/image29.png)

2.  Nella finestra di **dialogo Controllo** account utente selezionare
    **Sì**.

![](./media/image30.png)

3.  Nella console di PowerShell digitare il comando seguente e premere
    il pulsante **Invio**:

!!**dsregcmd /status**!!

4.  Nell'output, in **Stato dispositivo, verificare** che sia
    visualizzato AzureAdJoined: **YES**.

Ciò indica che il dispositivo è aggiunto a Microsoft Entra.

![](./media/image31.png)

5.  Close PowerShell.

6.  Fare nuovamente clic con il **pulsante destro del mouse** sull'icona
    del pulsante Start di Windows, quindi selezionare **Gestione
    computer.**

![A screenshot of a computer Description automatically
generated](./media/image32.png)

7.  Nella finestra **Gestione computer** espandere Utenti e **gruppi
    locali e quindi** selezionare Gruppi.

![](./media/image33.png)

![A screenshot of a computer Description automatically
generated](./media/image34.png)

8.  Fare doppio clic sul gruppo **Amministratori**.

![A screenshot of a computer Description automatically
generated](./media/image35.png)

Si noti che Joni Sherman è stata aggiunta come amministratore locale su
SEA-WS1. Si noti anche due entità di sicurezza rappresentate dai
relativi identificatori di sicurezza (SID). Questi due SID rappresentano
il ruolo di amministratore globale Entra e il ruolo di amministratore
del dispositivo aggiunto a Microsoft Entra.

![](./media/image36.png)

9.  Chiudi tutte le finestre aperte e disconnettiti da SEA-WS1 facendo
    clic sull'icona del pulsante Start di **Windows \> Amministratore \>
    Esci.**

![](./media/image37.png)

10. Passare a **SEA-SVR1** ed eseguire l'accesso con le credenziali
    Contoso\Administrator e la password!!**Pa55w.rd**!!

![A screenshot of a computer Description automatically
generated](./media/image38.png)

11. **Nell'interfaccia di amministrazione di Microsoft Entra**, naviga e
    fai clic su **Identità**.

12. Naviga e seleziona **Dispositivi**, quindi fai clic su Tutti i
    **dispositivi**.Nella sezione Dispositivi | Tutti i **dispositivi**,
    si noti che **SEA-WS1 è elencato**.![](./media/image39.png)

13. Verificare che il tipo di **join** sia elencato come **Microsoft
    Entra Joined** e che il **proprietario sia Joni Sherman.**

![](./media/image40.png)

14. Si noti inoltre che la colonna MDM mostra **Nessuno**. Ciò indica
    che il dispositivo non è ancora gestito da Microsoft Intune.

![A screenshot of a computer Description automatically
generated](./media/image41.png)

**Task 4: Accedere a Windows come utente Microsoft Entra**

1.  Passare a **SEA-WS1** e fare clic su **Altro utente.**

![](./media/image42.png)

2.  **Accedi come** !!**JoniS@M365xXXXXXXX.onmicrosoft.com**!!  con la
    password del tenant: !!**P@55w.rd1234**!!

**Nota: attendere la creazione del profilo.**

![](./media/image43.png)

Nota: se viene richiesto Windows Hello, **completare il processo** di
accesso di conseguenza e nella pagina Imposta un PIN, nelle caselle
**Nuovo PIN** e Conferma **PIN**, digitare !! 102938!! e quindi
selezionare **OK**.

![](./media/image44.png)

**Task 5: Rimuovere un dispositivo Windows da Entra**

1.  Su SEA-WS1, accedi con Joni Sherman se richiesto e se l'opzione per
    inserire il pin è disponibile, inserisci il pin: !! 102938!! oppure
    inserisci la password come!!**P@55w.rd1234**!!

![A screenshot of a computer Description automatically
generated](./media/image45.png)

2.  Nella finestra **Impostazioni**, seleziona **Account**.

![A screenshot of a computer Description automatically
generated](./media/image46.png)

3.  Nel riquadro di navigazione a sinistra, naviga e fai clic su
    **Account**. Nella pagina **Account** selezionare **Accedi
    all'azienda o all'istituto di istruzione**.

![A screenshot of a computer Description automatically
generated](./media/image47.png)

4.  Nella pagina **Accedi all'azienda o all'istituto** di istruzione
    selezionare l'elenco a discesa accanto a **Connesso ad Azure AD di
    Contoso**, come illustrato nell'immagine seguente. Fare clic su
    Disconnetti e quindi selezionare **Sì**.

![](./media/image48.png)

![A screenshot of a computer Description automatically
generated](./media/image49.png)

![A screenshot of a computer Description automatically
generated](./media/image50.png)

5.  Nella pagina **Disconnetti dall'organizzazione** selezionare
    **Disconnetti**.

![A blue box with white text Description automatically
generated](./media/image51.png)

6.  Nella casella **Indirizzo e-mail della finestra** di dialogo
    **Sicurezza di Windows** immettere !! Admin!! e nella casella
    Password, digita !! Pa55w.rd!. Seleziona **OK**.

![Graphical user interface Description automatically
generated](./media/image52.png)

7.  Nella **finestra di dialogo Riavvia** il PC, **seleziona Riavvia
    ora. SEA-WS1** si riavvia.

![A blue box with white text Description automatically
generated](./media/image53.png)

**Risultati**: dopo aver completato questo esercizio, saranno state
configurate le impostazioni del dispositivo Microsoft Entra, aggiunto un
dispositivo a Entra e rimosso un dispositivo da Entra.

**Esercizio 2: Configurazione del join ibrido di Microsoft Entra**

**Scenario**

Alcuni dispositivi Windows Contoso sono attualmente aggiunti ai servizi
di dominio Active Directory locali. Per consentire a tali dispositivi di
accedere senza problemi ai servizi cloud, si prevede di abilitare
l'aggiunta ibrida a Microsoft Entra. Si testerà l'aggiunta ibrida di
Microsoft Entra riconfigurando Azure AD Connect e testando il processo
in SEA-CL2.

**Task 1: Preparare l'ambiente**

1.  Passare a
    [SEA-SVR1](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10).

![A picture containing text Description automatically
generated](./media/image54.png)

2.  **Selezionare il pulsante dell'icona** Start di **Windows,**
    espandere Strumenti di amministrazione di **Windows,** quindi
    selezionare Utenti e computer di **Active Directory**.

![](./media/image55.png)

3.  In Utenti e computer di Active Directory **fare clic con** il
    pulsante destro **del mouse su Contoso.com**, scegliere **Nuovo e
    quindi** selezionare Unità organizzativa.

![](./media/image56.png)

4.  Nella finestra di dialogo **Nuovo-Oggetto - Unità organizzativa**,
    digitare !! Entra i clienti!! e quindi selezionare **OK**.

![A screenshot of a computer Description automatically
generated](./media/image57.png)

5.  Nel riquadro di spostamento selezionare **Seattle Clients**. Fare
    clic con il pulsante destro del mouse su **SEA-CL2,** quindi
    selezionare **Sposta**.

![](./media/image58.png)

6.  Nella finestra di dialogo **Sposta** selezionare **Entra client** e
    quindi selezionare **OK**.

![A screenshot of a computer Description automatically
generated](./media/image59.png)

7.  Chiudere **utenti e computer di Active Directory.**

![A screenshot of a computer Description automatically
generated](./media/image60.png)

**Task 2: Riconfigura Entra Connect**

In SEA-SVR1 fare doppio clic su Azure AD Connect sul desktop ![A black
rectangle with blue lines Description automatically
generated](./media/image61.png)

1.  Nella **finestra Microsoft Azure Active** Directory Connect
    **selezionare Configura**.

![](./media/image62.png)

2.  Nella pagina **Attività aggiuntive, seleziona Personalizza opzioni**
    di **sincronizzazione** e seleziona **Avanti**.

![A screenshot of a computer Description automatically
generated](./media/image63.png)

3.  **Nella pagina Connetti a** Entra, nelle caselle **NOME UTENTE** e
    **PASSWORD**, immettere le credenziali del tenant di Office 365 **e
    quindi selezionare** Avanti.

![A screenshot of a computer Description automatically
generated](./media/image64.png)

Nella pagina **Connetti le tue directory**, fai clic sul pulsante
Avanti.![A screenshot of a computer Description automatically
generated](./media/image65.png)

4.  **Nella pagina Filtro dominio e** unità organizzativa verificare che
    **l'opzione** Sincronizza domini **selezionati** e **unità
    organizzative sia selezionata**.

5.  Espandi **Contoso.com**, seleziona **Entra clients**, quindi fai
    clic su **Avanti**.

![A screenshot of a computer Description automatically
generated](./media/image66.png)

6.  Nella pagina **Funzionalità facoltative** verificare che l'opzione
    **Sincronizzazione hash password** sia selezionata e quindi
    selezionare **Avanti**.

7.  **Nella pagina** Pronto per la configurazione verificare che
    l'opzione Avvia il processo di **sincronizzazione al** termine della
    configurazione sia selezionata e quindi selezionare **Configura.**

![A screenshot of a computer Description automatically
generated](./media/image67.png)

8.  Al termine della configurazione, selezionare **Esci**.

![](./media/image68.png)

Nota: attendere circa 5 minuti per il completamento della
sincronizzazione.

**Task 3: Configurare l'aggiunta ibrida a Microsoft Entra con Azure AD
Connect**

In SEA-SVR1 VM **Desktop** fare doppio clic su **Azure AD
Connect.**![Text Description automatically generated with medium
confidence](./media/image69.png)

1.  **Nella finestra** Microsoft Azure Active Directory Connect
    **selezionare Configura.**

![](./media/image70.png)

2.  **Nella pagina** Attività aggiuntive, seleziona Configura opzioni
    dispositivo e seleziona **Avanti.**

![](./media/image71.png)

3.  Nella pagina **Panoramica** selezionare **Avanti**.

![A screenshot of a computer Description automatically
generated](./media/image72.png)

4.  Nella pagina **Connetti a Entra** immettere la password del tenant
    amministratore nella casella **PASSWORD**, quindi selezionare
    **Avanti**.

![](./media/image73.png)

5.  **Nella pagina Opzioni** dispositivo selezionare **Configura
    aggiunta** ad Azure AD **ibrido** e quindi **selezionare Avanti.**

![A screenshot of a computer Description automatically
generated](./media/image74.png)

6.  **Nella pagina Sistemi** operativi dispositivo selezionare
    Dispositivi Windows 10 o versioni successive aggiunti a un dominio e
    quindi **selezionare Avanti.**

![A screenshot of a computer Description automatically
generated](./media/image75.png)

7.  **Nella pagina** di configurazione SCP selezionare la casella di
    **controllo accanto** a Contoso.com. **Seleziona Azure Active
    Directory** dall'elenco a discesa Servizio di autenticazione e
    **seleziona Aggiungi.**

![](./media/image76.png)

8.  Nella finestra **Credenziali amministratore** dell'organizzazione
    immettere Contoso\Administrator come **nome utente** e !! Pa55w.rd!!
    come Password. **Seleziona OK** e **seleziona Avanti.**

![A screenshot of a computer security Description automatically
generated](./media/image77.png)

![](./media/image78.png)

9.  Nella pagina **Pronto per la configurazione** selezionare
    **Configura** per eseguire la configurazione.

![A screenshot of a computer Description automatically
generated](./media/image79.png)

10. Al termine della configurazione, selezionare **Esci**.

![A screenshot of a computer Description automatically
generated](./media/image80.png)

11. Sulla barra delle applicazioni, **fai clic** con il pulsante destro
    del mouse sull'icona del pulsante Start di Windows e seleziona
    Windows **Powershell (Admin)**.

![A screenshot of a computer Description automatically
generated](./media/image81.png)

Nella finestra di **Windows PowerShell** digitare il comando seguente e
quindi premere **INVIO**:!!**Start-ADSyncSyncCycle -PolicyType
Initial**!!

![A screenshot of a computer Description automatically
generated](./media/image82.png)

12. Chiudere la finestra di PowerShell.

Nota: attendere circa 5 minuti per il completamento della
sincronizzazione.

**Task 4: Verifica l'iscrizione Entra**

1.  Switch
    to [SEA-CL2](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10).

2.  Nella pagina di accesso, seleziona il pulsante di **accensione**,
    quindi seleziona **Riavvia**.

![Graphical user interface, application Description automatically
generated](./media/image83.png)

Nota: il riavvio attiverà l'accesso ibrido a Microsoft Entra
*[SEA-CL2](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10).*

3.  Dopo il riavvio di SEA-CL2, accedere come Contoso\Administrator con
    la password di!!**Pa55w.rd**!!

![Graphical user interface, application Description automatically
generated](./media/image84.png)

4.  **Sulla barra delle applicazioni, fai clic con il pulsante destro
    del mouse sul pulsante dell'icona Start di Windows e seleziona
    Terminale Windows (Admin)**.

![A screenshot of a computer Description automatically
generated](./media/image81.png)

5.  Nella finestra di **Windows PowerShell** digitare il comando
    seguente e quindi premere **INVIO**:

!!**dsregcmd /status**!!

6.  Nell'output in Stato dispositivo, verificare che. 

- **AzureAdJoined : YES** 

- **DomainJoined : YES** are displayed.

![](./media/image85.png)

***Nota: se il dispositivo non è ancora collegato a Entra, attendere il
completamento della sincronizzazione di Entra Connect e riavviare
nuovamente SEA-CL2. L'aggiornamento dello stato potrebbe richiedere 5-10
minuti.***

Inoltre, è possibile accedere a **SEA-SVR1** e nella finestra di
**Windows PowerShell**, digitare il seguente comando per velocizzare la
sincronizzazione.

!!**Start-ADSyncSyncCycle -PolicyType Initial**!!

7.  Chiudi tutte le finestre su SEA-CL2 ed esci.

8.  Passare a SEA-SVR1 e passare alla finestra dell'interfaccia di
    amministrazione di **Microsoft Entra**, navigare e fare clic su
    **Identità**.

![A screenshot of a computer Description automatically
generated](./media/image7.png)

9.  Nella sezione **Identità**, seleziona Dispositivi, quindi naviga e
    fai clic su Tutti i **dispositivi** come mostrato nell'immagine
    sottostante.

![A screenshot of a computer Description automatically
generated](./media/image8.png)

10. Verificare che **SEA-CL2** abbia Microsoft Entra hybrid joined come
    valore per il **tipo di join** di riga. Fare clic sul pulsante
    **Aggiorna** se SEA-CL2 non è elencato.

![A screenshot of a computer Description automatically
generated](./media/image86.png)

11. Chiudi tutte le finestre su
    [SEA-SVR1](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10).

**Risultati:** dopo aver completato questo esercizio, l'aggiunta ibrida
di Microsoft Entra sarà stata configurata e convalidata correttamente.
