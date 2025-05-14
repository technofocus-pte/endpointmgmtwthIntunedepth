Lab01 - Gestione delle identità nell'ID Microsoft Entra

**Summary**

In questo lab si userà l'interfaccia di amministrazione di Microsoft
Entra per creare e modificare utenti, assegnare ruoli amministrativi,
creare e modificare gruppi e gestire le assegnazioni di licenze nell'ID
Microsoft Entra.

**Esercizio 1: Creazione di utenti nell'ID Microsoft Entra Scenario**

È necessario creare account utente nell'ID Microsoft Entra per alcuni
nuovi dipendenti che inizieranno la prossima settimana. I nuovi utenti
sono elencati nella tabella seguente:

[TABLE]

Nota: per la posizione, utilizza la tua regione locale o gli Stati
Uniti.

Ti è stato anche detto che nei prossimi due mesi verranno assunti molti
altri dipendenti. Si è deciso che lo scripting sarebbe un metodo molto
più efficiente per aggiungere un gran numero di nuovi utenti. Si è
deciso di creare uno script di PowerShell e di testarlo quando si crea
l'account di Cody Godinez.

Attività 1: Creare utenti usando l'interfaccia di amministrazione di
Microsoft Entra

1.  On [***SEA-SVR1***](urn:gd:lg:a:select-vm), accedere come
    Contoso\Administrator con la password
    di!\![**Pa55w.rd**](urn:gd:lg:a:send-vm-keys)!!.

> ![Screenshot](./media/image1.png)
>
> Apri il browser Microsoft Edge e vai a
>
> !\![**https://entra.microsoft.com/#view/Microsoft_AAD_UsersAndTenants/UserManagementMenuBlade/~/AllUsers/menuId/**](https://entra.microsoft.com/#view/Microsoft_AAD_UsersAndTenants/UserManagementMenuBlade/~/AllUsers/menuId/)!!
>
> Alla richiesta di accesso, immettere le credenziali del tenant di
> Office 365 dalla scheda Home dell'interfaccia del lab.
>
> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)

Nota: se promosso per l'autenticazione a più fattori, completare il
processo di accesso all'autenticazione a più fattori.

> Nell'interfaccia di amministrazione di Microsoft Entra espandere
> Identità e nel riquadro di spostamento selezionare Utenti.
>
> ![A screenshot of a computer Description automatically
> generated](./media/image3.png)
>
> Prendere nota degli utenti già esistenti come membri del dominio ID
> Microsoft Entra. Ogni utente è abilitato come indicato nella colonna
> Account abilitato. La colonna Sincronizzato locale abilitato indica No
> per tutti gli utenti correnti. Ciò indica che ogni utente è stato
> creato direttamente nell'ID Microsoft Entra e non è stato
> sincronizzato da un servizio directory locale.
>
> ![A screenshot of a computer Description automatically
> generated](./media/image4.png)

2.  Sulla sezione Utenti | Pagina Tutti gli utenti, selezionare Nuovo
    utente, quindi selezionare Crea nuovo utente.

> ![](./media/image5.png)

3.  Nella pagina Nuovo utente, verificare che l'opzione Crea utente sia
    selezionata, immettere quanto segue:

    - Nome utente
      principale: !\![**ereeve**](urn:gd:lg:a:send-vm-keys)!!

    - nome visualizzato: !\![**Edmund
      Reeve**](urn:gd:lg:a:send-vm-keys)!!

    - **Deseleziona Genera automaticamente password.**

    - Password **–** !!**P@55w.rd1234**!!

> ![A screenshot of a computer Description automatically
> generated](./media/image6.png)

4.  Nella scheda **Proprietà**, fornisci le informazioni seguenti e
    quindi fai clic su **Assegnazioni successive.**

    - **Titolo del lavoro**, entrare!\![**HR
      Rep**](urn:gd:lg:a:send-vm-keys)!!

    - **Dipartimento**, entrare !!**H[R](urn:gd:lg:a:send-vm-keys)**!!

    - **Luogo di utilizzo - Stati Uniti**

> ![](./media/image7.png)

5.  Nella scheda Compiti, fai clic sul **pulsante Rivedi + crea.**

> ![A screenshot of a computer Description automatically
> generated](./media/image8.png)

6.  Verifica i dettagli e poi clicca sul pulsante **Crea**.

> ![](./media/image9.png)
>
> ![A close-up of a computer screen Description automatically
> generated](./media/image10.png)

7.  Allo stesso modo, crea l'account utente per Miranda Snider con i
    dettagli seguenti.

    - Nome utente principale: 
      !\![**msnider**](urn:gd:lg:a:send-vm-keys)!!

    - Nome visualizzato: !! [**Miranda
      Snider**](urn:gd:lg:a:send-vm-keys)!!

    - Deseleziona **Genera automaticamente la password.**

    - Password **–** !!**P@55w.rd1234**!!

    - Titolo del lavoro - !!**Helpdesk Manager**!!

    - Dipartimento **-** !!**Operations**!!

    - Luogo di utilizzo - Stati Uniti

8.  Seleziona l'account utente di **Allan Deyoung** e fai clic su
    **Modifica proprietà** e aggiorna le informazioni sul lavoro con i
    dettagli seguenti, quindi fai **clic** sul pulsante Salva.

    - Titolo di lovaro- !\![**IT Admin**](urn:gd:lg:a:send-vm-keys)!!

    -  Dipartmento - !\![**IT**](urn:gd:lg:a:send-vm-keys)!!

> ![A screenshot of a computer Description automatically
> generated](./media/image11.png)

12. Seleziona l'account utente di **Joni Sherman** e fai clic su
    **Modifica proprietà** e aggiorna le informazioni sul lavoro con i
    dettagli seguenti, quindi fai clic sul pulsante **Salva**.

    - Titolo di lavoro- !!**ParaLegal**!!

    -  Dipartmento - !!**Legal**!!

> ![A screenshot of a computer Description automatically
> generated](./media/image12.png)

13. Seleziona l'account utente di **Alex Wilber** e fai clic su
    **Modifica proprietà** e aggiorna le informazioni sul lavoro con i
    dettagli seguenti, quindi fai clic sul pulsante **Salva.**

    - Titolo di lavoro - !!**Marketing Assistant**!!

    -  Dipartimento – !\![**Marketing**](urn:gd:lg:a:send-vm-keys)!!

> ![](./media/image13.png)

1.  Attività 2: Creare utenti tramite PowerShell

> In SEA-SVR1, sulla barra delle applicazioni, fare clic con il pulsante
> destro del mouse su **Start**, quindi selezionare **Windows PowerShell
> (Admin).**
>
> ![](./media/image14.png)

2.  Nella finestra di **Windows PowerShell** digitare il comando
    seguente e quindi premere **INVIO**. Se richiesto, inserisci !! Y!!
    nei messaggi NuGet e del repository:

> !!**Install-Module MSOnline**!!
>
> ![](./media/image15.png)

3.  Nella finestra di **Windows PowerShell** digitare il comando
    seguente e quindi premere **INVIO**:

> !!**Connect-MsolService**!!
>
> ![A screenshot of a computer Description automatically
> generated](./media/image16.png)

4.  Nella finestra di **dialogo Accedi al tuo account** accedi
    utilizzando le credenziali del tenant di Office 365 dalla scheda
    Home.

> **Nota: se è stato richiesto di modificare la password delle
> credenziali di amministratore del tenant, assicurarsi di fornire la
> password aggiornata.**

5.  Nella finestra di **Windows PowerShell** digitare il codice seguente
    per creare un nuovo utente e quindi premere **INVIO**.

> Nota: incolla il comando seguente nel blocco note e sostituisci i
> dettagli del tenant, quindi copia e incolla il comando in Windows
> PowerShell, se necessario per garantire che le informazioni sul tenant
> siano corrette
>
> !!**New-MsolUser -UserPrincipalName
> cgodinez@M365xXXXXXXXX.onmicrosoft.com -DisplayName "Cody Godinez"
> -FirstName "Cody" -LastName "Godinez" -Password ‘P@55w.rd1234’
> -ForceChangePassword $false -UsageLocation "US" -Title "Sales Rep"
> -Department "Sales"**!!
>
> ![A screenshot of a computer screen Description automatically
> generated](./media/image17.png)
>
> Nella finestra di **Windows PowerShell** digitare il comando seguente
> per reimpostare le password di Alew Wilber, Allan Deyoung e Joni
> Sherman
>
> !!**Get-MsolUser | Where-Object DisplayName -EQ "Alex Wilber" |
> Set-MsolUserPassword -NewPassword P@55w.rd1234 -ForceChangePassword
> $false**!!
>
> !!**Get-MsolUser | Where-Object DisplayName -EQ “Allan Deyoung” |
> Set-MsolUserPassword -NewPassword P@55w.rd1234 -ForceChangePassword
> $false**!!
>
> !!**Get-MsolUser | Where-Object DisplayName -EQ "Joni Sherman" |
> Set-MsolUserPassword -NewPassword P@55w.rd1234 -ForceChangePassword
> $false**!!
>
> ![A computer screen shot of a program Description automatically
> generated](./media/image18.png)

6.  Nella finestra di **Windows PowerShell** digitare il comando
    seguente e quindi premere **INVIO**:

> !!**Get-MsolUser**!!

7.  Verificare che sia visualizzato l'elenco degli utenti del tenant.
    Prendi nota anche di quali utenti hanno una licenza assegnata. A
    qualsiasi utente con il valore **isLicensed** **False** non è stata
    assegnata una licenza.

> ![A screenshot of a computer Description automatically
> generated](./media/image19.png)

Risultati: dopo aver completato questo esercizio, saranno stati creati
correttamente nuovi account utente in Microsoft Entra ID.

**Esercizio 2: Assegnazione di ruoli amministrativi nell'ID Microsoft
Entra**

**Scenario**

È necessario rivedere e modificare i ruoli amministrativi correnti per
il tenant. È stato fornito un elenco di utenti a cui devono essere
assegnati ruoli amministrativi come indicato nella tabella seguente.

[TABLE]

Task 1: Revisione e assegnazione dei ruoli amministrativi

1.  Su **SEA-SVR1** passare a **Microsoft Edge**.

2.  **Nell'interfaccia di amministrazione di Microsoft Entra,** nel
    riquadro di spostamento, espandere **Ruoli e amministratori.**

3.  Seleziona **Ruoli e amministratore** e cerca !! Amministratore
    globale!! e fare clic sul ruolo **Amministratore globale**.

> ![A screenshot of a computer Description automatically
> generated](./media/image20.png)

4.  Clicca su **Aggiungi compiti.**

> ![A screenshot of a computer Description automatically
> generated](./media/image21.png)

5.  Nella pagina Aggiungi assegnazioni selezionare **Allan Deyoung** e
    quindi selezionare **Aggiungi.**

> ![A screenshot of a computer Description automatically
> generated](./media/image22.png)

6.  Nella parte superiore della pagina, nel collegamento di navigazione,
    **seleziona Ruoli e amministratori.**

> ![A screenshot of a computer Description automatically
> generated](./media/image23.png)

7.  Nella pagina **Ruoli e amministratori**, cerca e seleziona !!
    Amministratore utenti!. Assicurati che l'opzione **Assegnazioni**
    sia selezionata.

> ![A screenshot of a chat Description automatically
> generated](./media/image24.png)
>
> Si noti che non sono presenti utenti attualmente assegnati al ruolo
> Amministratore utenti.

8.  Clicca su + **Aggiungi compiti.**

> ![A screenshot of a computer Description automatically
> generated](./media/image25.png)

9.  Nella pagina Aggiungi assegnazioni selezionare **Edmund Reeve** e
    quindi selezionare **Aggiungi**.

> ![A screenshot of a computer Description automatically
> generated](./media/image26.png)

10. Fare clic sul collegamento **Ruoli e amministratori**, quindi
    cercare e selezionare !! Amministratore dell'helpdesk!!.

> ![A screenshot of a computer Description automatically
> generated](./media/image27.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image28.png)
>
> Si noti che non sono attualmente assegnati utenti al ruolo di
> amministratore del supporto tecnico.

11. Nella finestra di dialogo **Amministratore dell'helpdesk** | Pagina
    Assegnazioni, selezionare **Aggiungi assegnazioni.**

> ![A screenshot of a computer Description automatically
> generated](./media/image29.png)

12. Nella pagina Aggiungi assegnazioni selezionare **Miranda Snider** e
    quindi selezionare **Aggiungi**.

> ![A screenshot of a computer Description automatically
> generated](./media/image30.png)

13. Nella parte superiore della pagina, nel collegamento di navigazione,
    seleziona **Ruoli e amministratori.**

> ![A screenshot of a computer Description automatically
> generated](./media/image31.png)

**Risultati**: dopo aver completato questo esercizio, è necessario aver
assegnato correttamente i ruoli amministrativi agli utenti.

Esercizio 3: Creazione e gestione di gruppi e convalida
dell'assegnazione delle licenze.

**Scenario**

È necessario aggiungere i tre nuovi utenti a un gruppo di sicurezza e
assegnare le licenze come indicato nella tabella seguente.

[TABLE]

È stato anche chiesto di modificare il marchio dell'azienda per la
pagina di accesso.

Task 1: Creare gruppi usando l'interfaccia di amministrazione di
Microsoft Entra

1.  In SEA-SVR1, nell'interfaccia di **amministrazione** di Microsoft
    Entra, nel riquadro di spostamento, espandere **Identità** e
    selezionare Gruppi, quindi fare clic su Nuovo **gruppo.**

> ![A screenshot of a computer Description automatically
> generated](./media/image32.png)

2.  Nella pagina **Nuovo gruppo**, inserisci quanto segue:

    - Tipo di gruppo: Sicurezza

    - Nome del
      gruppo: !\![**Contoso_Managers**](urn:gd:lg:a:send-vm-keys)!!

3.  Tipo di adesione: Assegnato

4.  In Membri, fai clic su **Nessun membro selezionato**.

5.  Nella pagina Aggiungi membri aggiungere **Edmund Reeve, Miranda
    Snider,** quindi fare clic su **Seleziona**.

> ![A screenshot of a computer Description automatically
> generated](./media/image33.png)

6.  Select **Create**.

Task 2: Creare gruppi tramite PowerShell

1.  In SEA-SVR1 passare a Windows PowerShell.

2.  Nella finestra di **Windows PowerShell** digitare il codice seguente
    per creare un nuovo gruppo e quindi premere **INVIO**:

> !!**New-MsolGroup -DisplayName "Contoso_Sales" -Description "Contoso
> Sales team users"**!!
>
> ![A screenshot of a computer Description automatically
> generated](./media/image34.png)

3.  Nella finestra di **Windows PowerShell** digitare il comando
    seguente e quindi premere **INVIO**:

> !!**Get-MsolGroup**!!
>
> ![A screenshot of a computer screen Description automatically
> generated](./media/image35.png)

4.  Verificare di ottenere l'elenco dei gruppi nel tenant, incluso il
    gruppo **Contoso_Sales** appena creato.

> ![](./media/image36.png)

5.  Nella finestra di **Windows PowerShell** digitare il codice seguente
    per definire una variabile come gruppo Contoso_Sales e quindi
    premere **INVIO**:

> !!**$group = Get-MsolGroup | Where-Object {$\_.DisplayName -eq
> "Contoso_Sales"}**!!

6.  Nella finestra di **Windows PowerShell** digitare il codice seguente
    per definire un'altra variabile come utente, quindi premere
    **INVIO**:

> !!**$user = Get-MsolUser | Where-Object {$\_.DisplayName -eq "Cody
> Godinez"}**!!

7.  Nella finestra di **Windows PowerShell** digitare il codice seguente
    per aggiungere Cody a Contoso_Sales utilizzando le variabili
    impostate, quindi premere **INVIO**:

> !!**Add-MsolGroupMember -GroupObjectId $group.ObjectId
> -GroupMemberType "User" -GroupMemberObjectId $user.ObjectId**!!

8.  Nella finestra di **Windows PowerShell** digitare il codice seguente
    e quindi premere **INVIO**:

> !! **Get-MsolGroupMember -GroupObjectId $group.ObjectId**!!

9.  Verificare che **Cody Godinez** sia visualizzato nel risultato
    dell'output del comando.

> ![A screenshot of a computer program Description automatically
> generated](./media/image37.png)

10. Chiudi Windows PowerShell.

Task 3: Rivedere le licenze e modificare il marchio aziendale

1.  Nell'interfaccia di amministrazione di Microsoft Entra, nel riquadro
    di spostamento, espandere **Identità**, quindi espandere
    Fatturazione e selezionare **Licenze**.

> https://admin.microsoft.com/Adminportal/Home?referrer=entra#/licenses
>
> ![](./media/image38.png)

2.  Nella pagina **Licenze**, in Abbonamenti, verificare la presenza di
    tutte le licenze disponibili.

> ![](./media/image39.png)
>
> Note - Prendi nota delle licenze attualmente disponibili e assegnate
> **per Enterprise Mobility + Security E5 e Office 365 E5 (no Teams)**
>
> ![](./media/image40.png)

3.  Nell'interfaccia di amministrazione di Microsoft 365, nel riquadro
    di spostamento a sinistra selezionare **Utenti** e quindi **Utenti
    attivi.**

> ![](./media/image41.png)

4.  Nell'elenco degli utenti, seleziona **Cody Godinez.**

> ![A screenshot of a computer Description automatically
> generated](./media/image42.png)
>
> Nella pagina Cody Godinez selezionare **Licenze e app** ![A screenshot
> of a computer Description automatically
> generated](./media/image43.png)
>
> Si noti che Cody non ha alcuna assegnazione di licenza corrente.

5.  Nella **pagina Licenze e app, seleziona** la casella di controllo
    **accanto a Enterprise Mobility + Security E5 e Office 365 E5 (no
    Teams) e fai clic su Salva modifiche.**

> ![A screenshot of a login page Description automatically
> generated](./media/image44.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image45.png)

Nota: Ripetere i passaggi da 4 a 8 per l'assegnazione delle licenze
Enterprise Mobility + Security E5 e Office 365 E5 (no Teams) a Joni
Sherman, Alex Wilber e Allan Deyoung nel caso in cui non siano state
assegnate le licenze.

6.  Nell'interfaccia di amministrazione di Microsoft Entra, nel riquadro
    di spostamento, espandi **Identità** e seleziona **Gruppi**.

> ![](./media/image46.png)

7.  Sui **Gruppi** | Tutti i gruppi, seleziona **Contoso_Managers.**

> ![A screenshot of a computer Description automatically
> generated](./media/image47.png)

8.  Nella pagina **Contoso_Managers** selezionare **Licenze**.

> ![](./media/image48.png)
>
> **Si noti che il gruppo Contoso_Managers non dispone di assegnazioni
> di licenze correnti.**

9.  . **Passare all'interfaccia di amministrazione di Microsoft 365 e
    scorrere verso il basso fino a licenze, selezionare Enterprise
    Mobility + Security E5.**

> ![A screenshot of a computer Description automatically
> generated](./media/image49.png)

10. **Fare clic sulla scheda Gruppi e fare clic su Assegna licenze.**

> ![](./media/image50.png)

11. Seleziona Contoso_Mangers dall'elenco e clicca su **Assegna.**

12. Nell'interfaccia di amministrazione di Microsoft Entra, nel riquadro
    di spostamento, espandere **Identità**, quindi espandere
    **Fatturazione** e selezionare **Licenze**.

> ![A screenshot of a computer Description automatically
> generated](./media/image51.png)![A screenshot of a computer
> Description automatically generated](./media/image52.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image53.png)

13. Sulle licenze|Pagina di **panoramica**, in **Gestisci**, seleziona
    **Tutti** i **prodotti**.

> ![A screenshot of a computer Description automatically
> generated](./media/image54.png)
>
> ![](./media/image53.png)

14. Ripetere la stessa procedura e assegnare la licenza di Office 365 E5
    (no Teams) al Contoso_Managers team.

> Prendere nota degli utenti a cui è stata assegnata la licenza di
> Office 365 E5 (no Teams). Si noti la colonna Percorsi di assegnazione
> che indica come viene configurata l'assegnazione delle licenze per
> ogni utente. Edmund e Miranda ricevono entrambi l'assegnazione della
> licenza dalla loro appartenenza al gruppo Contoso_Managers. Potrebbe
> essere necessario selezionare Aggiorna un paio di volte per aggiornare
> la colonna Percorso assegnazione.
>
> ![](./media/image55.png)

15. 15\. Chiudi Microsoft Edge.

**Risultati**: dopo aver completato questo esercizio, è necessario aver
creato e gestito correttamente i gruppi e assegnato le licenze.
