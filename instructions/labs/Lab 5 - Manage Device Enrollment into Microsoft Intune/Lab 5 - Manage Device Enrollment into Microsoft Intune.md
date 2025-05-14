**Lab 5 - Gestire la registrazione dei dispositivi in Microsoft Intune**

**Summary**

In questo lab ci si prepara per la gestione dei dispositivi con
Microsoft Intune esaminando e assegnando licenze, configurando la
registrazione automatica di Windows e configurando le restrizioni di
registrazione.

**Prerequisites**

I seguenti laboratori devono essere completati prima di questo
laboratorio:

- Lab \#1- Gestione delle identità nell'ID Microsoft Entra

- Lab \#2- Sincronizzazione delle identità tramite Microsoft Entra
  Connect

**Note**: Avrai anche bisogno di un telefono cellulare in grado di
ricevere messaggi di testo utilizzati per proteggere l'autenticazione di
accesso a Windows Hello per Entra ID.

**Scenario**

È necessario prepararsi per la gestione dei dispositivi con Microsoft
Intune. Prima di tutto, è necessario assicurarsi che agli utenti vengano
assegnate licenze appropriate per la gestione dei dispositivi. Come test
di verifica, assegnerai ad Aaron Nicholls le licenze richieste. È
inoltre necessario assicurarsi che qualsiasi dispositivo Windows
aggiunto o registrato nell'ID Microsoft Entra venga registrato
automaticamente in Intune. È stato anche chiesto di assicurarsi che i
membri del gruppo Sales non possano registrare dispositivi Android e iOS
personali in Intune e che il limite di dispositivi di registrazione sia
aumentato a 10 dispositivi. Infine, è necessario configurare Allan
Deyoung come responsabile della registrazione dei dispositivi per
consentirgli di registrare 1000 dispositivi.

**Task 1: Rivedere e assegnare le licenze per la gestione dei
dispositivi**

1.  In SEA-SVR1 passare alla finestra dell'interfaccia di
    amministrazione di Microsoft 365.

![](./media/image1.png)

2.  Naviga e seleziona **Fatturazione**, quindi fai clic su **Licenze**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image2.png)

3.  Nella pagina **Licenze** prendere nota delle licenze disponibili nel
    tenant.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image3.png)

4.  Selezionare e fare clic su **Enterprise Mobility + Security E5**.
    Notare tutti gli utenti a cui è stata assegnata questa licenza. È
    possibile assegnare e rimuovere licenze da questa posizione.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image4.png)

![](./media/image5.png)

5.  Selezionare un utente per visualizzare le licenze assegnate
    all'utente. Prendi nota dei servizi

incluso nella licenza Enterprise Mobility + Security E5. Microsoft
Intune è uno dei servizi supportati per questa licenza.

![](./media/image6.png)

6.  Nel riquadro di **spostamento dell'interfaccia di amministrazione**
    di Microsoft 365 selezionare **Utenti attivi.**

![](./media/image7.png)

7.  Ricerca e selezione!!**Cindy White**!!

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image8.png)

8.  **Nella pagina utente** di Cindy White, fai clic su **Licenze e
    app**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image9.png)

9.  In Impostazioni, nel campo **Luogo di utilizzo**, selezionare Stati
    Uniti e fare clic sulla casella di controllo **Enterprise
    Mobility** + **Security E5** e **Office 365 E5** (senza team),
    quindi fare clic su **Salva modifiche.**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image10.png)

*Nota: prima di poter assegnare una licenza a un utente, è necessario
che l'utente disponga di una posizione di utilizzo impostata.*

![](./media/image11.png)

**Task 2: Impostazione della password dell'utente tramite PowerShell**

1.  In SEA-SVR1 fare clic con il **pulsante** destro del mouse sul
    pulsante Start, quindi **selezionare Windows PowerShell (Admin)**.

![](./media/image12.png)

2.  Nella finestra di dialogo **Controllo account utente** selezionare
    **Sì**.

![](./media/image13.png)

3.  Nella finestra di **Windows PowerShell** digitare il comando
    seguente e quindi premere **INVIO**:

!!**Connect-MsolService**!!

![A computer screen with white text Description automatically
generated](./media/image14.png)

4.  Nella finestra di dialogo **Accedi al tuo account** accedi
    utilizzando le credenziali del tenant di Office 365 dalla scheda
    Home.

**Nota: se è stato richiesto di modificare la password delle credenziali
di amministratore del tenant, assicurarsi di fornire la password
aggiornata.**

![A screenshot of a computer Description automatically
generated](./media/image15.png)

![A screenshot of a computer screen Description automatically
generated](./media/image16.png)

5.  Nella finestra di **Windows PowerShell** digitare il comando
    seguente per reimpostare le password del **Cindy White**

!!**Get-MsolUser | Where-Object DisplayName -EQ "Cindy White" |
Set-MsolUserPassword -NewPassword P@55w.rd1234 -ForceChangePassword
$false**!!

![A computer screen shot of a program Description automatically
generated](./media/image17.png)

**Task 3: Abilita la registrazione automatica di Windows in Microsoft
Intune**

1.  In **SEA-SVR1**, apri una nuova scheda in **Microsoft Edge**, quindi
    nella barra degli indirizzi digita !!
    https://Endpoint.microsoft.com!! e quindi premere **INVIO**. Se
    viene richiesto di accedere, fornire le credenziali
    dell'amministratore **tenant di Office 365.**

2.  Nell'interfaccia di amministrazione di Microsoft Intune selezionare
    **Dispositivi**.

![A screenshot of a computer Description automatically
generated](./media/image18.png)

3.  Naviga e fai clic su Iscrizione. **Assicurati** che la scheda
    Windows sia selezionata, quindi vai alla sezione Opzioni di
    **registrazione** e fai clic su **Registrazione automatica.**

![](./media/image19.png)

4.  Nella riga dell'ambito utente **MDM** selezionare il pulsante di
    opzione Tutti e quindi selezionare **Salva**.

![](./media/image20.png)

5.  Fare clic su **Dispositivi** | **Link di iscrizione** come mostrato
    nell'immagine sottostante.

![](./media/image21.png)

**Nota:** eseguendo questo passaggio, è stata abilitata la registrazione
automatica in Intune per qualsiasi utente che esegue un'aggiunta ad
Azure AD con un dispositivo Windows.

**Task 4: Configurare le restrizioni di registrazione**

1.  Passare alla sezione **Onboarding dei dispositivi** e fare clic su
    **Registrazione**. Quindi, fai clic sulla scheda Android come
    mostrato nell'immagine **sottostante**.

![](./media/image22.png)

2.  Scorri verso il basso fino alla sezione **Opzioni di registrazione**
    e fai clic su **Restrizione** della **piattaforma del dispositivo.**

![](./media/image23.png)

Seleziona la scheda **Restrizioni Android,** quindi seleziona +**Crea
restrizione.**![](./media/image24.png)

![](./media/image25.png)

3.  Nella casella Nome della pagina **Crea restrizione** immettere !!
    **Limitazione del dispositivo** personale Android!! **Seleziona
    Avanti.**

![](./media/image26.png)

4.  Nella pagina delle impostazioni della piattaforma, in Di **proprietà
    personale,** seleziona **Blocca** per i seguenti tipi di dispositivi
    e fai clic sul pulsante **Avanti**:

    - Android Enterprise (profilo di lavoro)

    - Amministratore del dispositivo Android

![](./media/image27.png)

5.  Nella pagina dei **tag di ambito**, selezionare **Avanti**.

![A screenshot of a computer Description automatically
generated](./media/image28.png)

6.  Nella pagina **Assegnazioni**, in **Gruppi inclusi**, selezionare
    **Aggiungi gruppi.**

![A screenshot of a computer Description automatically
generated](./media/image29.png)

7.  Nella barra di ricerca del riquadro **Seleziona gruppi** da
    **includere**, digita e seleziona Vendite, quindi fai clic sul
    pulsante **Seleziona**.

![A screenshot of a computer Description automatically
generated](./media/image30.png)

8.  Nella scheda **Assegnazioni**, fai clic sul pulsante **Avanti**.

![A screenshot of a computer Description automatically
generated](./media/image31.png)

9.  Nella pagina **Rivedi** + **crea** selezionare **Crea**.

![A screenshot of a computer Description automatically
generated](./media/image32.png)

Si noti la restrizione del dispositivo personale Android assegnata con
una priorità di 1.

![A screenshot of a computer Description automatically
generated](./media/image33.png)

10. Nella **sezione Dispositivi** | Pagina di registrazione, nella
    scheda **Windows**, vai alla **sezione Opzioni di registrazione** e
    fai clic su **Limitazione limite dispositivi.**

![A screenshot of a computer Description automatically
generated](./media/image34.png)

Si noti che esiste una restrizione del limite di dispositivi predefinita
assegnata a Tutti gli utenti. Questa restrizione predefinita imposta un
limite di registrazione dei dispositivi su 5 dispositivi per utente.

11. Nelle restrizioni del limite dei **dispositivi di registrazione
    selezionare** + **Crea restrizione.**

![A screenshot of a computer Description automatically
generated](./media/image35.png)

12. Nella casella **Nome** della pagina Crea restrizione immettere !!
    Limite di registrazione del dispositivo di vendita!! Seleziona
    **Avanti**.

![A screenshot of a computer Description automatically
generated](./media/image36.png)

13. Nella pagina **Limite dispositivi** selezionare **10** e quindi
    selezionare **Avanti**.

![A screenshot of a computer Description automatically
generated](./media/image37.png)

14. Nella pagina **Tag ambito** selezionare **Avanti**.

![A screenshot of a computer Description automatically
generated](./media/image38.png)

15. Nella pagina **Assegnazioni**, in **Gruppi inclusi**, selezionare
    **Aggiungi gruppi**.

![A screenshot of a computer Description automatically
generated](./media/image39.png)

16. Nella casella di **ricerca Seleziona gruppi** da includere nella
    pagina digitare e **selezionare** Vendite, quindi fare clic sul
    pulsante **Seleziona**.

![](./media/image40.png)

17. Fare clic sul pulsante **Avanti**.

![A screenshot of a computer Description automatically
generated](./media/image41.png)

18. Nella pagina **Rivedi** + **crea** selezionare **Crea**.

![A screenshot of a computer Description automatically
generated](./media/image42.png)

19. Ricarica la pagina. Si noti il limite di registrazione del
    dispositivo di vendita, configurato con un limite di dispositivi
    pari a 10 e assegnato con una priorità pari a 1.

![A screenshot of a computer Description automatically
generated](./media/image43.png)

**Task 5: Configurare un gestore registrazione dispositivi**

1.  **Nell'interfaccia di amministrazione** di Microsoft Intune
    selezionare **Dispositivi**.

![](./media/image44.png)

2.  Passare alla sezione **Onboarding del dispositivo** e fare clic su
    **Registrazione**, quindi fare clic sulla scheda **Responsabili
    registrazione dispositivi.**

![](./media/image45.png)

3.  Nel riquadro **Registra dispositivi** selezionare **Responsabili
    registrazione dispositivi**.

Si noti che, per impostazione predefinita, non sono configurati
strumenti di gestione registrazione dispositivi.

4.  Sul pulsante Registra dispositivi|Pagina Responsabili registrazione
    dispositivi, selezionare **Aggiungi**.

![A screenshot of a computer Description automatically
generated](./media/image46.png)

5.  Nella pagina **Aggiungi utente**, in Nome utente, inserisci
    l'indirizzo email di Allan DeYoung !!
    AllanD@M365xXXXXXXX.onmicrosoft.com!! (sostituisci **XXXXXX** con il
    nome del tuo inquilino) e quindi seleziona **Aggiungi**.

![A screenshot of a computer Description automatically
generated](./media/image47.png)

**Allan è ora autorizzato a registrare fino a 1000 dispositivi.**

6.  Nell'interfaccia di amministrazione di Microsoft Intune, nel
    riquadro di spostamento, selezionare **Home**.

![A screenshot of a computer Description automatically
generated](./media/image48.png)

7.  Chiudi Microsoft Edge.

**Risultati**: dopo aver completato questo esercizio, le licenze saranno
state esaminate e assegnate, la registrazione automatica di Windows, le
restrizioni di registrazione abilitate e assegnate e configurato un
gestore di registrazione dispositivi.
