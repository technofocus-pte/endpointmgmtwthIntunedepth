Lab 16 - Configurazione della reimpostazione della password self-service
per gli account utente in Microsoft Entra

**Sommario**

In questo lab si configurerà e si convaliderà la reimpostazione della
password self-service per gli account utente **nell'ID Microsoft
Entra**.

**prerequisiti**

To following lab(s) must be completed before this lab:

- Lab \#2- Sincronizzazione delle identità tramite Microsoft Entra
  Connect

- Lab \#5- Gestire la registrazione dei dispositivi in Microsoft Intune

**Scenario**

L'Help Desk ha indicato che un gran numero di ticket di supporto sono
correlati alla reimpostazione della password. Ti è stato chiesto di
proporre una soluzione per consentire agli utenti di reimpostare la
propria password. Per gli account sincronizzati da Servizi di dominio
Active Directory, il processo deve reimpostare sia la password di
Microsoft Entra che quella di Servizi di dominio Active Directory.

Task 1: Configurare password writeback

1.  Accedi a
    [***SEA-SVR1***](urn:gd:lg:a:select-vm) come !!**[Contoso\Administrator](urn:gd:lg:a:send-vm-keys)!!** Con
    la password !!**[Pa55w.rd](urn:gd:lg:a:send-vm-keys)!!** e
    chiudi **Server Manager**.

2.  Sul desktop, fare doppio clic **Azure AD Connect**.

> ![A screenshot of a computer Description automatically
> generated](./media/image1.png)

3.  Nella pagina **Benvenuto in Azure AD Connect** selezionare
    **Configura**.

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)
>
> Nella pagina **Attività aggiuntive** selezionare **Personalizza
> opzioni di sincronizzazione** e quindi selezionare **Avanti**.
>
> ![A screenshot of a computer Description automatically
> generated](./media/image3.png)

4.  Nella pagina **Connetti ad Azure AD,** se necessario,
    digitare!!**admin@M365xXXXXXXX.onmicrosoft.com!!** nella casella di
    testo **NOME UTENTE** digitare la **PASSWORD** e quindi selezionare
    **Avanti**.

> ![A screenshot of a computer Description automatically
> generated](./media/image4.png)

5.  Nella pagina **Connetti alle directory selezionare** Avanti. Nella
    pagina Filtro **dominio e unità organizzativa** selezionare
    **Avanti**.

> Nella pagina **Funzionalità facoltative** selezionare Writeback
> **password** e quindi selezionare **Avanti**.
>
> ![A screenshot of a computer Description automatically
> generated](./media/image5.png)

6.  Nella pagina **Pronto per la configurazione** selezionare
    **Configura**.

> ![A screenshot of a computer Description automatically
> generated](./media/image6.png)
>
> ![A computer screen shot of a computer Description automatically
> generated](./media/image7.png)
>
> **Note**: la configurazione può richiedere alcuni minuti.
>
> Nella pagina **Configurazione completata** selezionare **Esci**.
>
> ![A screenshot of a computer Description automatically
> generated](./media/image8.png)

Attività 2: Abilitare la reimpostazione della password self-service.

1.  Sulla barra delle applicazioni seleziona **Microsoft Edge,** vai a
    **Amministratore di Microsoft Entra center**

2.   [**https://Entra.Microsoft.com**](https://Entra.Microsoft.com).

3.  Accedere con le credenziali di **amministratore tenant di Office
    365.**

> ![A screenshot of a computer Description automatically
> generated](./media/image9.png)
>
> Verrà visualizzata l'interfaccia di **amministrazione di Microsoft
> Entra**.

4.  Nell'interfaccia di amministrazione di **Microsoft Entra**, nel
    riquadro di spostamento, espandere **Identità**, quindi
    **selezionare Utenti.**

5.  Nel riquadro di navigazione **Utenti**, seleziona **Reimpostazione
    password**.

> ![A screenshot of a computer Description automatically
> generated](./media/image10.png)

6.  Nella sezione **Reimpostazione password | Proprietà,** selezionare
    **Tutto** per abilitare la reimpostazione della **password**
    self-service per tutti gli utenti. Seleziona **Salva**.

> ![A screenshot of a computer Description automatically
> generated](./media/image11.png)
>
> ![A screenshot of a computer screen Description automatically
> generated](./media/image12.png)

7.  Nella sezione **Reimpostazione della password** | Pannello
    Proprietà, selezionare **Metodi di autenticazione.**

> ![A screenshot of a computer Description automatically
> generated](./media/image13.png)

8.  Per i metodi disponibili per gli utenti, assicurarsi che sia
    selezionata l'opzione **Telefono cellulare** ed **E-mail**, quindi
    selezionare **Domande di sicurezza**.

9.  Per il **numero di domande necessarie per la registrazione**,
    selezionare **3.**

10. Per il **numero di domande necessarie per la reimpostazione**,
    selezionare **3**.

> ![A screenshot of a computer Description automatically
> generated](./media/image14.png)

11. Nella **sezione Seleziona domande** di sicurezza **selezionare
    Nessuna domanda di sicurezza** configurata, quindi selezionare
    **Predefinito**. Seleziona tre domande a tua scelta, quindi
    seleziona **OK** due volte.

> ![A screenshot of a computer Description automatically
> generated](./media/image15.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image16.png)Selezionare **Salva**
>
> ![A screenshot of a computer Description automatically
> generated](./media/image17.png)

12. Selezionare **Registrazione** Selezionare **Sì** per **Richiedi agli
    utenti di registrarsi all'accesso,** e **Numero di giorni prima che
    agli utenti venga chiesto di riconfermare le informazioni di
    autenticazione**, impostare il valore su **90**, quindi selezionare
    **Salva**.

> ![A screenshot of a computer Description automatically
> generated](./media/image18.png)

13. Nel riquadro di spostamento **selezionare Integrazione locale**.

14. Verificare che il client di writeback locale sia in esecuzione e
    assicurarsi che la casella di controllo sia selezionata per
    **Abilita write back password per gli utenti sincronizzati**. Se
    necessario, selezionare **Salva**.

> ![A screenshot of a computer Description automatically
> generated](./media/image19.png)

15. Chiudi Microsoft Edge.

Task 3: Convalidare la reimpostazione della password self-service

1.  Passare a [***SEA-WS3***](urn:gd:lg:a:select-vm). Se necessario,
    accedere come!!**[Admin](urn:gd:lg:a:send-vm-keys)!!** con la
    password di!!**[Pa55w.rd](urn:gd:lg:a:send-vm-keys)!!**

2.  Sulla barra delle applicazioni, seleziona Microsoft Edge. Sfogliare
    to !!**https://mysignins.microsoft.com/!!**

3.  Nella pagina **Scegli un account** selezionare **Usa un altro
    account**.

> ![A screenshot of a computer Description automatically
> generated](./media/image20.png)

4.  Nella pagina di **accesso**,
    inserisci!!**Cindy@M365xXXXXXX.onmicrosoft.com!!** , quindi
    seleziona **Avanti**.

5.  Nella pagina **Inserisci password**, digita**!!P@55w.rd1234!!** e
    quindi selezionare **Accedi**. Se Microsoft Edge chiede di salvare
    la password, selezionare **Salva**.

> ![A screenshot of a computer error Description automatically
> generated](./media/image21.png)
>
> Ti verrà chiesto di **fornire ulteriori informazioni**, fare clic su
> **Avanti**
>
> ![A screenshot of a computer error Description automatically
> generated](./media/image22.png)
>
> Fornisci i dettagli e fai clic su **Avanti**.
>
> ![A screenshot of a computer Description automatically
> generated](./media/image23.png)
>
> Inserisci il codice a 6 cifre e clicca su **Avanti**
>
> ![](./media/image24.png)

6.  Fare nuovamente clic su Avanti.

> ![A screenshot of a computer Description automatically
> generated](./media/image25.png)

7.  Fare clic su **Fatto**.

> ![](./media/image26.png)
>
> Si dovrebbe essere in grado di la pagina **Il mio account**
>
> ![](./media/image27.png)

8.  Per modificare la **Password**, visita il link -
    **!!https://mysignins.microsoft.com/security-info!!**

9.  Completa la Verifica, cliccando sul Testo +XXXXXXXXXXXXXX

> ![A screenshot of a computer error Description automatically
> generated](./media/image28.png)
>
> Fornisci il codice a 6 cifre e quindi fai clic su Verifica.
>
> ![A screenshot of a computer error Description automatically
> generated](./media/image29.png)

10. Clicca su **Salta per ora.**

> ![A screenshot of a computer error Description automatically
> generated](./media/image30.png)

11. Nella pagina Informazioni di sicurezza, fai clic su **Modifica** per
    la password.

> ![A screenshot of a login page Description automatically
> generated](./media/image31.png)

12. Nella **pagina Modifica password** immettere le informazioni
    seguenti e quindi selezionare **Invia**:

    - Crea nuova password: **!!P@55w.rd12345!!**

    - Conferma nuova password: **!!P@55w.rd12345!!**

> ![A screenshot of a login box Description automatically
> generated](./media/image32.png)

13. Fare clic sul pulsante Fine.

> ![](./media/image33.png)

14. Chiudi Microsoft Edge ed esci da
    [***SEA-WS3***](urn:gd:lg:a:select-vm).

Task 4: Eseguire il servizio di sincronizzazione Azure AD Connect

Si noti che questo passaggio non è in genere necessario per il writeback
delle password, ma è consigliato per risolvere i problemi inerenti agli
ambienti lab e assicurarsi che Active Directory Domain Services sia
sincronizzato con Microsoft Entra.

1.  Passare a **[*SEA-SVR1*](urn:gd:lg:a:select-vm)** e fare clic con il
    pulsante destro del mouse su **Start,** quindi selezionare **Windows
    PowerShell (Admin)**.

> ![A screenshot of a computer Description automatically
> generated](./media/image34.png)

2.  Al prompt dei comandi di **Windows PowerShell**, digitare il comando
    seguente e quindi premere **INVIO**:

> **!!Start-ADSyncSyncCycle -PolicyType Delta!!**
>
> ![A screenshot of a computer Description automatically
> generated](./media/image35.png)

Chiudere Windows PowerShell e attendere circa 3-4 minuti.

Task 5: Verificare la password riscrittoback

1.  passare a [***SEA-CL1***](urn:gd:lg:a:select-vm) e disconnettersi se
    necessario. Su [***SEA-CL1***](urn:gd:lg:a:select-vm), selezionare
    **Altro utente**, quindi tentare di accedere
    come !!**Contoso\Cindy!!** Con la password di !!**P@55w.rd1234!!**

> ![A screenshot of a computer Description automatically
> generated](./media/image36.png)

2.  Assicurati di ricevere il messaggio che indica che il nome utente o
    la password non sono corretti.

> ![A screenshot of a computer screen Description automatically
> generated](./media/image37.png)

3.  Ora accedi come!!**Contoso\Cindy!!** Con la password
    di !!**P@55w.rd12345!!** la password impostata con la funzione SSPR.

4.  Questa volta l'accesso dovrebbe essere stato eseguito correttamente
    con la **nuova password**.

In questo modo si conferma che la password modificata nel portale di
accesso personale viene riscritta nell'account locale di Servizi di
dominio Active Directory.

![A screenshot of a computer error Description automatically
generated](./media/image38.png)

> Nota: se durante l'accesso viene visualizzato il messaggio precedente,
> viene confermato che **l'autenticazione è riuscita**, ma che l'account
> non disponeva dell'autorizzazione per l'accesso al SEA-CL1 a causa di
> un problema di appartenenza al gruppo.

**Risultati:** dopo aver completato questo esercizio, la reimpostazione
della password self-service sarà stata configurata e convalidata
correttamente.
