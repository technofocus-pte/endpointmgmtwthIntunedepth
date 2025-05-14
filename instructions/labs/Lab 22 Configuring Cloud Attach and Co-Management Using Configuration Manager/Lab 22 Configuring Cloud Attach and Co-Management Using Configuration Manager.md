Lab 22: Configurazione del collegamento cloud e della co-gestione
tramite Configuration Manager

**Sommario**

In questo lab si abiliterà Cloud Attach e si configurerà la co-gestione
usando Microsoft Endpoint Configuration Manager e Microsoft Intune.

**Prerequisiti**

To following lab(s) must be completed before this lab:

- Lab 01- Gestione delle identità nell'ID Microsoft Entra

- Lab 02- Sincronizzazione delle identità tramite Azure AD Connect

- Lab 03- Configurazione e gestione dell'aggiunta all'ID Microsoft Entra

- Lab 05- Gestire la registrazione dei dispositivi in Intune

**Scenario**

Contoso dispone sia di un'implementazione di Microsoft Endpoint
Configuration Manager che di Microsoft Intune. È necessario configurare
l'integrazione tra i due servizi e abilitare la co-gestione per i
dispositivi Windows gestiti. Abiliterai Cloud Attach, configurerai la
co-gestione e quindi convaliderai le impostazioni utilizzando SEA-CL1.

Task 1: Preparare l'ambiente

1.  Passare a  [***SEA-SVR1***](urn:gd:lg:a:select-vm) e accedi come
    [**Contoso\Administrator**](urn:gd:lg:a:send-vm-keys) con la
    password di !\![**Pa55w.rd**](urn:gd:lg:a:send-vm-keys)!! .

2.  In Server Manager selezionare **Strumenti**, quindi selezionare
    **Utenti e computer di Active Directory.**

> ![](./media/image1.png)

3.  Nel riquadro di spostamento selezionare **Seattle Clients.**

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)

4.  Fare clic con il pulsante destro del mouse su **SEA-CL1** e quindi
    selezionare **Sposta**.

> ![A computer screen shot of a computer Description automatically
> generated](./media/image3.png)

5.  Nella finestra di dialogo **Sposta** selezionare **Entra client** e
    quindi selezionare **OK**.

> ![A screenshot of a computer Description automatically
> generated](./media/image4.png)

6.  Chiudere **Utenti e computer di Active Directory.**

7.  Sulla barra delle applicazioni, fare clic con il pulsante destro del
    mouse su **Start** e selezionare **Windows Powershell (Admin)**.

> ![A screenshot of a computer Description automatically
> generated](./media/image5.png)

8.  Nella finestra di **Windows PowerShell** digitare il comando
    seguente e quindi premere **INVIO**:

> !!**Start**-ADSyncSyncCycle -PolicyType **Initial**!!
>
> ![A screenshot of a computer screen Description automatically
> generated](./media/image6.png)

9.  Chiudere la finestra di PowerShell.

10. Passare a [***SEA-CL1***](urn:gd:lg:a:select-vm).

11. Sulla barra delle applicazioni, fai clic con il pulsante destro del
    mouse su **Start**, **seleziona Arresta o disconnetti**, quindi
    seleziona **Riavvia**.

> ![](./media/image7.png)
>
> **Nota**: il riavvio attiverà l'aggiunta ad Azure AD ibrido su
> SEA-CL1.

12. Dopo [***SEA-CL1***](urn:gd:lg:a:select-vm) è stato riavviato,
    accedi come
    [**Contoso\Administrator**](urn:gd:lg:a:send-vm-keys) con la
    password di [**Pa55w.rd**](urn:gd:lg:a:send-vm-keys).

13. Sulla barra delle applicazioni, fai clic con il pulsante destro del
    mouse **su Start** e seleziona **Terminale Windows
    (Amministratore)**.

> ![](./media/image8.png)

14. Nella finestra di **Windows PowerShell** digitare il comando
    seguente e quindi premere **INVIO**:

> !!dsregcmd /**status**!!

15. **Nell'output in** Stato dispositivo, verificare che **AzureAdJoined
    : YES** e **DomainJoined : YES** vengono visualizzati

> ![](./media/image9.png)
>
> **Nota:** se il dispositivo non è ancora stato aggiunto ad Azure AD,
> attendere il completamento del servizio di sincronizzazione Azure AD
> Connect e riavviare nuovamente SEA-CL1.

16. Chiudi tutte le finestre su [***SEA-CL1***](urn:gd:lg:a:select-vm).

Task 2: Creare una raccolta di dispositivi

1.  Passare a [***SEA-CFG1***](urn:gd:lg:a:select-vm), accedere come
    [**Contoso\Administrator**](urn:gd:lg:a:send-vm-keys) con la
    password [**Pa55w.rd**](urn:gd:lg:a:send-vm-keys).

2.  Sulla barra delle applicazioni selezionare **Console di
    Configuration Manager**. Verrà visualizzata la console di Microsoft
    Endpoint Configuration Manager.

> ![A screenshot of a computer Description automatically
> generated](./media/image10.png)

3.  Nell'area di **lavoro Asset e conformità** selezionare **Raccolte
    dispositivi.**

4.  Fare clic con il pulsante destro del mouse su **Raccolte
    dispositivi,** quindi scegliere **Crea raccolta dispositivi.** Verrà
    visualizzata la Creazione guidata raccolta dispositivi.

> ![](./media/image11.png)

- Nella pagina **Generale** configurare quanto segue e quindi
  selezionare **Avanti**: Name: !\![**Co-managed
  Devices**](urn:gd:lg:a:send-vm-keys)!!

> Limitazione della raccolta: **tutti i client desktop e server**
>
> ![](./media/image12.png)
>
> ![](./media/image13.png)
>
> ![](./media/image14.png)

5.  Nella pagina **Regole di appartenenza** selezionare **Avanti**.

> ![A screenshot of a computer Description automatically
> generated](./media/image15.png)

6.  In corrispondenza dell'avviso di Configuration Manager selezionare
    **OK**. Aggiungerai un membro diretto in un passaggio successivo.

> ![A screenshot of a computer error Description automatically
> generated](./media/image16.png)

7.  Nella pagina **Riepilogo**, selezionare **Avanti**, quindi nella
    pagina **Completamento**, selezionare **Chiudi**

> ![A screenshot of a computer Description automatically
> generated](./media/image17.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image18.png)

Task 3: Assegnazione di un dispositivo a una raccolta esistente

1.  Nell'area di lavoro **Asset e conformità** selezionare
    **Dispositivi**.

> Prendere nota dei dispositivi elencati. Tutti i dispositivi che hanno
> un cerchio verde con un segno di spunta bianco sono attualmente
> attivi.

2.  Nel riquadro dei dettagli selezionare **SEA-CL1**.

3.  Clic con il tasto destro **SEA-CL1**, punta su **Aggiungi elementi
    selezionati**, , quindi selezionare **Aggiungi elementi selezionati
    alla raccolta di dispositivi esistente.**

> ![](./media/image19.png)

4.  Nella finestra di dialogo **Seleziona raccolta**, selezionare
    **Dispositivi co-gestiti** e quindi selezionare **OK**.

> ![](./media/image20.png)

5.  Per verificare, nell'area di lavoro **Asset e conformità,**
    selezionare **Raccolte dispositivi** e quindi fare doppio clic su
    **Dispositivi co-gestiti**.

> ![](./media/image21.png)
>
> ![](./media/image22.png)
>
> **SEA-CL1** dovrebbe essere elencato come membro di questa collezione.

Task 4: Gestione configurazione endpoint con collegamento cloud

1.  Nella console di Microsoft Endpoint Configuration Manager
    selezionare l'area di lavoro **Amministrazione**.

> ![](./media/image23.png)

2.  Nell'area di lavoro **Amministrazione** espandere **Servizi cloud**
    e quindi selezionare Collegamento **cloud**.

> ![A screenshot of a computer Description automatically
> generated](./media/image24.png)

3.  Nella barra multifunzione selezionare **Configura collegamento
    cloud**. Viene visualizzata la **Configurazione guidata Cloud
    Attach.**

4.  ![](./media/image25.png)

> ![](./media/image26.png)

5.  Nella **Configurazione guidata collegamento cloud,** nella pagina
    **Cloud Attach** selezionare **Accedi**.

6.  Accedi come
    [**admin@M365x19242953.onmicrosoft.com**](urn:gd:lg:a:send-vm-keys) con
    la password [**9whL~;H8ke=D1^95%D**](urn:gd:lg:a:send-vm-keys).

7.  Nella pagina **Cloud Attach** selezionare **Personalizza
    impostazioni** e selezionare **Avanti**.

> ![](./media/image27.png)

8.  Nell'avviso **Crea applicazione AAD** selezionare **Sì**.

> ![A screenshot of a computer Description automatically
> generated](./media/image28.png)

9.  Nella pagina **Configura caricamento**, accetta l'impostazione
    predefinita e seleziona **Avanti**.

> ![A screenshot of a computer Description automatically
> generated](./media/image29.png)

10. Nella pagina **Abilitazione**, accanto a **Registrazione automatica
    in Intune,** selezionare **Pilot**.

11. Nella pagina **Abilitazione**, accanto a **Registrazione automatica
    di Intune**, selezionare **Sfoglia**.

> ![](./media/image30.png)

12. Nella finestra di dialogo **Seleziona raccolta**, selezionare
    **Dispositivi co-gestiti** e quindi selezionare **OK**. Selezionare
    **Avanti**.

> ![A screenshot of a computer Description automatically
> generated](./media/image31.png)

13. Nella pagina **Riepilogo**, selezionare **Avanti**, quindi nella
    pagina **Completamento**, selezionare **Chiudi**.

> ![A screenshot of a computer Description automatically
> generated](./media/image32.png)

Task 5: Configurare i carichi di lavoro

1.  Nella console di Microsoft Endpoint Configuration Manager
    selezionare l'area di lavoro **Amministrazione**.

2.  Nell'area di lavoro **Amministrazione**, espandere **Servizi
    cloud**, quindi selezionare **Cloud Attach.**

3.  Nel riquadro dei dettagli selezionare **CoMgmtSettingsProd** e
    quindi dalla barra multifunzione selezionare **Proprietà**.

4.  ![A screenshot of a computer Description automatically
    generated](./media/image33.png)

> Il **CoMgmtSettingsProd Properties** apre la casella.

5.  Selezionare **Carichi di lavoro**. Nella pagina **Carichi di
    lavoro,** trascinare il dispositivo di scorrimento su **Pilot
    Intune** per i carichi di lavoro seguenti:

    - **Politiche di conformità**

    - **Applicazioni client**

    - **Criteri di aggiornamento di Windows**

> ![](./media/image34.png)

6.  Seleziona **la pagina di staging**. Nella pagina Gestione
    **temporanea**, selezionare **Sfoglia** accanto a **Criteri di
    conformità**, **Client Apps**, a nd **Criteri di Windows** Update e
    selezionare i **dispositivi co-gestiti** per ogni carico di lavoro.

7.  Selezionare OK per chiudere la casella **Proprietà**
    CoMgmtSettingsProd.

> ![](./media/image35.png)

Task 6: Verificare che SEA-CL1 sia co-gestito

1.  Passare a  [***SEA-SVR1***](urn:gd:lg:a:select-vm).

2.  Sulla barra delle applicazioni, seleziona **Microsoft Edge**, nella
    barra degli indirizzi,
    digita [**https://entra.microsoft.com**](https://entra.microsoft.com),
    e quindi premere **Invio**.

3.  Accedi come utente
    [**admin@M365x19242953.onmicrosoft.com**](urn:gd:lg:a:send-vm-keys),
    e usa la password.

4.  Se il **soggiorno ha effettuato l'accesso?** viene visualizzato il
    prompt, selezionare **No**.

> Verrà visualizzata l'interfaccia di amministrazione di Microsoft
> Entra.

5.  Nell'interfaccia di amministrazione di Microsoft Entra, nel riquadro
    di spostamento, selezionare **Identità.**

> ![](./media/image36.png)

6.  Nella sezione **Dispositivi|Pagina Tutti i dispositivi**, verificare
    che **SEA-CL1** è elencato e che il **tipo di join** è **Microsoft
    Entr hybrid Join**.

> ![](./media/image37.png)

7.  In Microsoft Edge apri un'altra scheda e digita
    [**https://intune.microsoft.com**](https://intune.microsoft.com) nella
    barra degli indirizzi, quindi premere **Invio**.

8.  Nel riquadro di spostamento selezionare **Dispositivi**, quindi
    selezionare **Tutti i dispositivi.**

> Verificare che **SEA-CL1** sia elencato con l'impostazione **Gestito
> da impostata** su **Co-gestito.**
>
> ![](./media/image38.png)
>
> Potrebbe volerci un po' di tempo prima che appaia. Aggiornare il
> riquadro dei dettagli in base alle esigenze. La macchina potrebbe
> apparire con un nome diverso, fare clic sul dispositivo per confermare
> che indica **SEA-CL1.**

9.  Selezionare **SEA-CL1** e nel riquadro dei dettagli scorrere verso
    il basso per visualizzare le informazioni relative allo stato di
    co-gestione.

10. Chiudi Microsoft Edge.

**Risultati:** dopo aver completato questo esercizio, sarà possibile
abilitare Cloud Attach e configurare la co-gestione usando Microsoft
Endpoint Configuration Manager e Microsoft Intune.
