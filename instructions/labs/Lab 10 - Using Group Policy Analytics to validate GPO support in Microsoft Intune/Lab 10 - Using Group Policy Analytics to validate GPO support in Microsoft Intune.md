**Lab 10 - Uso di Analisi Criteri di gruppo per convalidare il supporto
degli oggetti Criteri di gruppo in Microsoft Intune**

**Sommario**

In questa esercitazione si usa Analisi Criteri di gruppo per importare
un oggetto Criteri di gruppo di Active Directory e identificare le
impostazioni che supportano i criteri MDM equivalenti di Microsoft
Intune.

**Scenario**

Contoso ha tradizionalmente utilizzato gli oggetti Criteri di gruppo di
Active Directory per distribuire le impostazioni dei criteri utente e
del computer in tutto il dominio. Si prevede di spostare tutte le
impostazioni dell'oggetto Criteri di gruppo supportate nei profili di
configurazione di Microsoft Intune. Si dispone di un oggetto Criteri di
gruppo denominato Criteri client di Windows. È necessario usare Analisi
Criteri di gruppo per convalidare le impostazioni nell'oggetto Criteri
di gruppo Criteri client di Windows e identificare le impostazioni di
cui è possibile eseguire correttamente la migrazione in Intune.

**Task 1: Esportare l'oggetto Criteri di gruppo Criteri client di
Windows in un file XML**

1.  Accedi a SEA-SVR1 con la barra di ricerca delle credenziali fornite,
    digita !! Gestore del server!! e quindi selezionalo.

> ![](./media/image1.png)

2.  In **Server Manager - Dashboard selezionare** Strumenti e quindi
    **Gestione Criteri di gruppo.**

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)

3.  Nella console Gestione Criteri di gruppo espandere
    **Forest:Contoso.com**, quindi Domini, **Contoso.com** e quindi
    selezionare Oggetti Criteri di **gruppo**.

> Verificare che siano elencati diversi oggetti Criteri di gruppo.

4.  Nel riquadro dei dettagli selezionare l'oggetto Criteri di gruppo
    Criteri **client di Windows.**

> ![](./media/image3.png)

5.  Fare clic con il pulsante destro del mouse su **Criteri client
    Windows,** quindi selezionare **Salva report**.

> ![](./media/image4.png)

6.  Nella finestra di dialogo **Salva** report oggetto Criteri di gruppo
    selezionare **Documenti**, modificare il tipo Salva con nome in file
    **XML** e quindi selezionare **Salva**.

> ![](./media/image5.png)

7.  Chiudere la console Gestione Criteri di gruppo.

8.  Chiudi Server Manager.

**Task 2: Analizzare l'oggetto Criteri di gruppo del client Windows
utilizzando Analisi Criteri di gruppo**

1.  Apri Microsoft Edge, digita !! https://intune.microsoft.com!! nella
    barra degli indirizzi, quindi premere **Invio**.

2.  Accedere con le credenziali del tenant di Office 365, se richiesto.

3.  Nell'interfaccia di amministrazione di **Microsoft Intune
    spostarsi** e selezionare **Dispositivi**.

> ![](./media/image6.png)

4.  Passare alla sezione **Gestisci dispositivi** e selezionare
    **Analisi Criteri di gruppo**.

> ![](./media/image7.png)

5.  Sui **dispositivi | Pannello Analisi Criteri** di **gruppo**,
    selezionare **Importa**.

> ![A screenshot of a computer Description automatically
> generated](./media/image8.png)

6.  Nella scheda di **caricamento del file GPO**, fare clic sulla
    cartella accanto a Seleziona una barra di **ricerca dei file** come
    mostrato nell'immagine sottostante.

> ![A screenshot of a computer Description automatically
> generated](./media/image9.png)

7.  Nella casella **Apri** selezionare Documenti e quindi selezionare
    **Policy.xml** client **Windows**. Quindi, fai clic sul pulsante
    **Apri**.

> ![A screenshot of a computer Description automatically
> generated](./media/image10.png)

8.  Fare clic sul pulsante **Avanti**.

> ![A screenshot of a computer Description automatically
> generated](./media/image11.png)

9.  Nei **tag Scope**, fare clic sul pulsante **Avanti**.

> ![A screenshot of a computer Description automatically
> generated](./media/image12.png)

10. Nella scheda **Rivedi + crea**, fai clic sul pulsante **Crea**.

> ![A screenshot of a computer Description automatically
> generated](./media/image13.png)

11. L'oggetto Criteri di gruppo dei criteri client di Windows viene
    immediatamente importato e analizzato. Chiudere la pagina **Importa
    file GPO.**

12. Sui **dispositivi** | **Pannello Analisi Criteri di gruppo**,
    esaminare le informazioni accanto a Criteri **client Windows**.

> Si noti che l'89% delle impostazioni supporta MDM.
>
> ![A screenshot of a computer Description automatically
> generated](./media/image14.png)

13. In Supporto MDM, seleziona **89%**.

> Si noti il **nome dell'impostazione**, **il supporto MDM**, **il nome
> CSP** e il **mapping CSP** per ogni impostazione supportata. Prendere
> nota delle impostazioni che non dispongono di un mapping CSP
> equivalente.
>
> ![A screenshot of a computer Description automatically
> generated](./media/image15.png)

14. Chiudere **la finestra Criteri client di Windows**.

**Task 3: Esaminare il report di riepilogo di Analisi Criteri di
gruppo**

1.  Nel menu di spostamento dell'interfaccia di **amministrazione
    Microsoft Intune selezionare Report.**

> ![](./media/image16.png)

2.  Nella sezione Gestione dispositivi della pagina **Report**
    selezionare **Analisi Criteri di gruppo.**

> ![](./media/image17.png)

3.  Nel riquadro dei dettagli, in **Riepilogo**, selezionare
    **Aggiorna**. Potrebbe essere necessario aggiornare un paio di volte

> L'aggiornamento e la creazione del report di riepilogo potrebbero
> richiedere 5-10 minuti.

4.  Esaminare le **informazioni sulla conformità alla migrazione** di
    Criteri di gruppo.

> ![A screenshot of a computer Description automatically
> generated](./media/image18.png)
>
> Dovrebbero essere presenti un certo numero di criteri pronti per la
> migrazione e un numero di criteri non supportati.
>
> Selezionare la scheda **Report** e quindi selezionare **Conformità
> alla migrazione di Criteri di gruppo.**![A screenshot of a group
> policy migration Description automatically
> generated](./media/image19.png)

5.  Selezionare **Genera report.**

> ![A screenshot of a computer Description automatically
> generated](./media/image20.png)

6.  Il rapporto Conformità alla migrazione di Criteri di gruppo fornisce
    informazioni relative a ogni impostazione e al tipo di profilo
    supportato.

> ![A screenshot of a computer Description automatically
> generated](./media/image21.png)

7.  Chiudere la finestra **Conformità alla migrazione di Criteri di
    gruppo.**

**Risultati:** dopo aver completato questo esercizio, sarà stato
esportato correttamente un oggetto Criteri di gruppo e sarà stato usato
Analisi Criteri di gruppo per convalidare le impostazioni dei criteri
equivalenti in Intune.
