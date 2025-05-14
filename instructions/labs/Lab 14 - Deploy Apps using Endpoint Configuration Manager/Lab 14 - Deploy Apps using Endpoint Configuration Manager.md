Lab14 - Distribuire app con Endpoint Configuration Manager

**Sommario**

In questo lab si userà Microsoft Endpoint Configuration Manager per
distribuire applicazioni alle workstation client desktop.

**Scenario**

Contoso usa Microsoft Endpoint Configuration Manager per gestire le
workstation desktop all'interno dell'ambiente di rete Active Directory
locale. È necessario distribuire una nuova applicazione denominata
Microsoft Power BI desktop nei client di Windows 11 Configuration
Manager. L'amministratore di Endpoint Configuration Manager ha già
creato automaticamente l'oggetto applicazione. Le attività includono la
creazione di una raccolta per i dispositivi di destinazione, la
distribuzione del contenuto dell'applicazione ai punti di distribuzione
e quindi la creazione della distribuzione assegnata alla raccolta di
destinazione. Il processo verrà verificato assicurandosi che
l'applicazione sia visualizzata nel Software Center su SEA-CL1.

Task 1: Creare una raccolta di dispositivi

1.  Passa a SEA-CFG1, accedi come Contoso\Administrator con la password
    !! Pa55w.rd!. Sulla barra delle applicazioni selezionare **Console
    di Configuration Manager**. Verrà visualizzata la console di
    Microsoft Endpoint Configuration Manager.

> ![](./media/image1.png)

2.  Nell'area di lavoro **Asset e conformità** selezionare **Raccolte
    dispositivi.**

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)

3.  Fare clic con il pulsante destro del mouse su **Raccolte
    dispositivi**, quindi scegliere Crea raccolta dispositivi. Verrà
    visualizzata la procedura guidata di **creazione della raccolta
    dispositivi.**

> ![A screenshot of a computer Description automatically
> generated](./media/image3.png)

4.  Nella pagina **Generale** configurare quanto segue, quindi
    selezionare **Avanti**:

    - Nome: !! Potenza BI App Distribuzione

    - Commento: !! Dispositivi mirati per installare Power BI Desktop!!

> Limitazione della raccolta: tutte le stazioni di **lavoro di Windows
> 11**
>
> ![A screenshot of a computer Description automatically
> generated](./media/image4.png)

5.  Nella pagina **Regole di appartenenza** selezionare **Avanti**. In
    corrispondenza dell'avviso di Configuration Manager selezionare
    **OK**. Aggiungerai un membro diretto in un passaggio successivo.

> ![A screenshot of a computer Description automatically
> generated](./media/image5.png)
>
> ![A screenshot of a computer error Description automatically
> generated](./media/image6.png)

6.  Nella pagina **Riepilogo** selezionare Avanti, quindi nella pagina
    Completamento **selezionare** **Chiudi**.

> ![A screenshot of a computer Description automatically
> generated](./media/image7.png)
>
> La raccolta Distribuzione **app Power BI viene visualizzata**
> nell'elenco Raccolte dispositivi.
>
> ![A screenshot of a computer Description automatically
> generated](./media/image8.png)

Task 2: Assegnazione di un dispositivo a una raccolta esistente

1.  Nell'area di **lavoro Asset e conformità** selezionare
    **Dispositivi**.

> Prendere nota dei dispositivi elencati. Tutti i dispositivi che hanno
> un cerchio verde con un segno di spunta bianco sono attualmente
> attivi.
>
> ![](./media/image9.png)

2.  Nel riquadro dei dettagli selezionare **SEA-CL1**.

3.  Fare clic con il pulsante destro del mouse su **SEA-CL1**, scegliere
    **Aggiungi elementi selezionati,** quindi selezionare **Aggiungi
    elementi selezionati** **alla raccolta di dispositivi esistente.**

> ![](./media/image10.png)

4.  Nella finestra di dialogo **Seleziona** raccolta selezionare
    **Distribuzione app Power BI** e quindi selezionare **OK**.

> ![A screenshot of a computer Description automatically
> generated](./media/image11.png)

5.  Per verificare, nell'area di lavoro **Asset e conformità**
    selezionare Raccolte dispositivi e quindi fare doppio clic su
    **Distribuzione app Power BI**.

> ![A screenshot of a computer Description automatically
> generated](./media/image12.png)
>
> [***SEA-CL1***](urn:gd:lg:a:select-vm) dovrebbe essere elencato come
> membro di questa collezione.
>
> ![A screenshot of a computer Description automatically
> generated](./media/image13.png)

Task 3: Configurare un tipo di distribuzione

1.  Nella console di Microsoft Endpoint Configuration Manager
    selezionare l'area di lavoro **Libreria software**.

> ![A screenshot of a software library Description automatically
> generated](./media/image14.png)

2.  Nell'area di lavoro Raccolta **software espandere** **Gestione
    applicazioni** e quindi **selezionare Applicazioni.**

> ![A screenshot of a software library Description automatically
> generated](./media/image15.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image16.png)
>
> Si notino le applicazioni create dall'amministratore di Endpoint
> Configuration Manager.
>
> Nel riquadro dei dettagli selezionare **Microsoft Power BI Desktop
> (x64**).
>
> ![A screenshot of a computer Description automatically
> generated](./media/image17.png)

3.  Nel riquadro dei risultati selezionare la scheda **Tipi di
    distribuzione**. Si noti che esiste un tipo di distribuzione basato
    su Windows Installer.

> ![A screenshot of a computer Description automatically
> generated](./media/image18.png)

4.  Fare clic con il pulsante destro del mouse sul tipo di
    **distribuzione Microsoft Power BI Desktop (x64) - Window**s
    installer e quindi scegliere Proprietà.

> ![A screenshot of a computer Description automatically
> generated](./media/image19.png)

5.  Nella finestra di dialogo **Proprietà** selezionare la scheda
    **Programmi**. Prendi nota di come è installata l'applicazione.
    Utilizzerà msiexec con l'opzione /q che esegue un'installazione
    silenziosa.

> ![](./media/image20.png)

6.  Nella finestra di dialogo **Proprietà** selezionare la scheda
    **Requisiti**, quindi selezionare **Aggiungi**.

> ![A screenshot of a computer Description automatically
> generated](./media/image21.png)

7.  Nella finestra di dialogo **Proprietà selezionare** la scheda
    Requisiti, quindi selezionare **Aggiungi**:

    - Categoria: **Dispositivo**

    - Condizione: **sistema operative**

    - Tipo di regola: **Valore**

    - Operatore: **Uno di Windows 11 (Selezionare la casella accanto a
      Windows 11)**

> ![A screenshot of a computer program Description automatically
> generated](./media/image22.png)

8.  Nella finestra di dialogo **Proprietà** selezionare **OK**. Questo
    requisito impedirà l'installazione dell'app su qualsiasi sistema
    operativo ad eccezione di Windows 11.

> ![A screenshot of a computer Description automatically
> generated](./media/image23.png)

Task 4: Distribuire il contenuto ai punti di distribuzione

1.  Nell'area di lavoro **Raccolta software** selezionare **Microsoft
    Power BI Desktop (x64).Right-** fare clic su **Microsoft Power BI
    Desktop (x64**) e quindi selezionare Distribuisci **contenuto**.

> ![A screenshot of a computer Description automatically
> generated](./media/image24.png)
>
> Nella pagina **Generale** selezionare **Avanti**.
>
> ![A screenshot of a computer Description automatically
> generated](./media/image25.png)

2.  Nella pagina **Contenuto** selezionare **Avanti**.

> ![A screenshot of a computer Description automatically
> generated](./media/image26.png)

3.  Nella pagina **Destinazione** **contenuto** selezionare Aggiungi e
    quindi selezionare **Punto di distribuzione.**

> ![A screenshot of a computer Description automatically
> generated](./media/image27.png)

4.  Nella finestra di **dialogo Aggiungi punti** di distribuzione
    selezionare la casella di controllo accanto **a
    SEA-CFG1**.CONTOSO.COM e quindi selezionare **OK**.

> ![A screenshot of a computer Description automatically
> generated](./media/image28.png)

5.  Nella pagina **Destinazione contenuto**, selezionare **Avanti**.

> ![A screenshot of a computer Description automatically
> generated](./media/image29.png)

6.  Nella pagina **Riepilogo** selezionare **Avanti** e quindi
    selezionare **Chiudi**.

> ![A screenshot of a computer Description automatically
> generated](./media/image30.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image31.png)
>
> Nella scheda **Riepilogo**, seleziona **Stato contenuto.**
>
> ![A screenshot of a computer Description automatically
> generated](./media/image32.png)
>
> Verrà visualizzata la pagina Stato contenuto per Microsoft Power BI
> Desktop. Nel riquadro dei risultati, verificare che sia visualizzato
> un cerchio verde e che accanto al cerchio venga visualizzato
> Successo:1. Ciò indica che il contenuto è ora distribuito ai punti di
> distribuzione e può ora essere distribuito nei dispositivi. Potrebbe
> essere necessario selezionare il pulsante Aggiorna nella barra
> multifunzione.
>
> ![A screenshot of a computer Description automatically
> generated](./media/image33.png)

7.  Nell'angolo in alto a sinistra, selezionare la freccia **Torna alle
    applicazioni** per tornare al nodo Applicazioni della libreria
    software.

Task 5: Creare una distribuzione

1.  Nell'area di lavoro Raccolta software selezionare **Microsoft Power
    BI Desktop (x64).Right-** fare clic su **Microsoft Power BI Desktop
    (x64)** e quindi selezionare Distribuisci. Viene visualizzata la
    procedura **guidata Distribuisci** software.

> ![A screenshot of a computer Description automatically
> generated](./media/image34.png)

2.  Nella pagina **Generale**, accanto a **Raccolta**, selezionare
    **Sfoglia**.

> ![A screenshot of a computer Description automatically
> generated](./media/image35.png)

3.  Nella pagina **Seleziona raccolta** selezionare **Raccolte utenti e
    quindi selezionare Raccolte dispositivi.**

> Nell'elenco Raccolte **dispositivi selezionare** **Distribuzione app
> Power BI** e quindi selezionare **OK**.![A screenshot of a computer
> Description automatically generated](./media/image36.png)
>
> Nella pagina **Generale** selezionare **Avanti**.
>
> ![A screenshot of a computer Description automatically
> generated](./media/image37.png)
>
> Nella pagina **Contenuto** selezionare **Avanti**.
>
> ![A screenshot of a computer Description automatically
> generated](./media/image38.png)

4.  Nella pagina **Impostazioni di distribuzione,** verificare che
    **l'azione** sia impostata su **Installa** e che lo scopo sia
    impostato su **Disponibile**. Seleziona **Avanti**.

> ![A screenshot of a computer Description automatically
> generated](./media/image39.png)
>
> Nella pagina **Pianificazione** selezionare **Avanti**. L'applicazione
> sarà disponibile il prima possibile per impostazione predefinita.
>
> ![A screenshot of a computer Description automatically
> generated](./media/image40.png)

5.  Nella pagina **Esperienza utente**, accanto a **Notifiche utente**,
    **selezionare Visualizza in Software Center e mostra tutte le
    notifiche**. Seleziona **Avanti**.

> ![A screenshot of a computer Description automatically
> generated](./media/image41.png)

6.  Nella pagina **Avvisi** selezionare **Avanti**.

> ![A screenshot of a computer Description automatically
> generated](./media/image42.png)

7.  Nella pagina **Riepilogo** selezionare **Avanti** e quindi
    selezionare **Chiudi**.

> ![A screenshot of a computer Description automatically
> generated](./media/image43.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image44.png)

8.  Nel riquadro dei risultati, nella scheda **Distribuzioni**,
    verificare che venga visualizzato il deployment.

> ![A screenshot of a computer Description automatically
> generated](./media/image45.png)

9.  Close the Microsoft Endpoint Configuration Manager console.

10. Esci da SEA-CFG1.

Task 6: Use Software center to install a deployed app

1.  Passare a SEA-CL1 e accedere come Contoso\Administrator con la
    password di !! Pa55w.rd!. Fare clic sul **menu Start,** quindi
    accedere al **Pannello di controllo.**

2.  Nei risultati, seleziona **Pannello di controllo**.

> ![A screenshot of a computer Description automatically
> generated](./media/image46.png)

3.  Nel **Pannello di controllo**, **selezionare Sistema e sicurezza**.

> ![A screenshot of a computer Description automatically
> generated](./media/image47.png)

4.  In **Sistema e sicurezza** selezionare Gestione configurazione.
    Viene visualizzato Proprietà di Configuration Manager.

> ![A screenshot of a computer Description automatically
> generated](./media/image48.png)

5.  Nella finestra di dialogo **Proprietà di Gestione configurazione**
    selezionare la scheda **Azioni**.

> ![A screenshot of a computer program Description automatically
> generated](./media/image49.png)

6.  Nella scheda **Azioni**, selezionare Ciclo di recupero e
    **valutazione dei criteri del computer,** quindi selezionare
    **Esegui** ora. Al prompt dei messaggi, selezionare **OK**.

> ![A screenshot of a computer program Description automatically
> generated](./media/image50.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image51.png)

7.  Selezionare OK per chiudere le **proprietà di Gestione
    configurazione,** quindi chiudere il **Pannello di controllo.**

> ![A screenshot of a computer program Description automatically
> generated](./media/image52.png)

8.  Nell'area di notifica, selezionare **Nuovo software disponibile,**
    quindi selezionare **Apri Software Center**. Potrebbe essere
    necessario espandere la freccia dell'area di notifica per
    visualizzare l'icona.

> ![](./media/image53.png)
>
> Se il Software Center non si avvia, fare clic sul menu **Start e
> scorrere** verso il basso e fare clic su !! **Centro software**!!![A
> screenshot of a computer Description automatically
> generated](./media/image54.png)

9.  Nella pagina **Applicazioni di Software** Center si noti la nuova
    applicazione disponibile denominata **Microsoft Power BI Desktop
    (x64).** Questa applicazione è ora disponibile per tutti i
    dispositivi membri della raccolta Distribuzione **app Power BI**
    creata in precedenza.

> ![A screenshot of a computer Description automatically
> generated](./media/image55.png)

10. Selezionare **Microsoft Power BI Desktop (x64)** e quindi
    selezionare **Installa**.

> ![A screenshot of a computer Description automatically
> generated](./media/image56.png)
>
> ![](./media/image57.png)
>
> L'applicazione viene scaricata e installata senza l'input dell'utente.
> Si saprà che l'installazione è stata eseguita correttamente quando il
> collegamento di **Power BI Desktop** viene visualizzato sul desktop.
>
> ![A screenshot of a computer Description automatically
> generated](./media/image58.png)

11. Chiudere il centro software.

12. Esci dal SEA-CL1.

**Risultati**: dopo aver completato questo esercizio, Microsoft Endpoint
Configuration Manager sarà stato utilizzato correttamente per
distribuire le applicazioni nelle workstation client desktop.
