**Lab 11- Monitorare l'attività del dispositivo e dell'utente in
Intune**

**Sommario**

**In questo lab verranno monitorati l'attività di accesso degli utenti,
i log di controllo e l'attività del dispositivo.Prerequisites**

I seguenti laboratori devono essere completati prima di questo
laboratorio:

- Lab \#1- Gestione delle identità nell'ID Microsoft Entra

- Lab \#2- Sincronizzazione delle identità tramite Microsoft Entra
  Connect

- Lab \#5- Gestire la registrazione dei dispositivi in Microsoft Intune

- Lab \#6- Registrazione dei dispositivi in Microsoft Intune

- Lab \#7- Creazione e distribuzione dei profili di configurazione

**Nota**: avrai anche bisogno di un telefono cellulare in grado di
ricevere messaggi di testo utilizzati per proteggere l'autenticazione di
accesso a Windows Hello per l'ID Microsoft Entra.

**Scenario**

È necessario esaminare l'attività di accesso di Cindy White e le
informazioni generali fornite dai registri di controllo. È inoltre
necessario verificare l'hardware su SEA-WS1 e confermare che il profilo
di configurazione assegnato a questo dispositivo sia stato applicato
correttamente.

**Task 1: Monitorare l'attività degli utenti**

1.  Passare a SEA-SVR1 e accedere con le credenziali fornite, se
    necessario.

2.  Nella pagina dell'interfaccia di **amministrazione di Microsoft
    Entra**, naviga e seleziona Utenti, quindi fai **clic** su Tutti gli
    **utenti**.

> ![](./media/image1.png)

3.  Nella pagina **Utenti**, naviga e seleziona **Allan Deyoung**.

> ![](./media/image2.png)

4.  Nella **Allan Deyoung** Pagina utente, navigare e cliccare su
    **Sign-in logs**.

> ![A screenshot of a computer Description automatically
> generated](./media/image3.png)

5.  In **Allan Deyoung |** Pagina dei **log di accesso**, fare clic
    sulla prima voce nella **scheda Accessi utente (interattivi**).

> ![A screenshot of a computer Description automatically
> generated](./media/image4.png)

6.  Selezionare ognuna delle pagine principali, tra cui **Informazioni
    di base**, **Posizione, Informazioni sul dispositivo**, **Dettagli
    autenticazione** e **Accesso** condizionale. Scorri verso il basso
    ed esamina le informazioni su ogni pagina. Dopo aver esaminato
    attentamente le informazioni fornite in ogni pagina, chiudere il
    riquadro.

> ![](./media/image5.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image6.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image7.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image8.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image9.png)

7.  Nel riquadro di spostamento Utenti selezionare **Log di controllo**.

8.  Nel riquadro dei dettagli vengono visualizzate le informazioni di
    controllo relative alle modifiche amministrative apportate agli
    utenti. Esamina le informazioni selezionando le varie voci.

> ![A screenshot of a computer Description automatically
> generated](./media/image10.png)
>
> ![](./media/image11.png)

**Task 2: Monitorare l'attività del dispositivo**

1.  Passare alla finestra dell'interfaccia di **amministrazione di
    Microsoft Intune**, spostarsi e fare clic su **Dispositivi**.

![](./media/image12.png)

2.  Nel riquadro di navigazione Dispositivi, seleziona **Panoramica**.

> ![A screenshot of a computer Description automatically
> generated](./media/image13.png)

3.  Scroll down and review the following:

- Errori di assegnazione dei criteri di configurazione

- Dispositivi non conformi.

- Stato della distribuzione per anello di aggiornamento di Windows.

> ![](./media/image14.png)

4.  Scorri verso il basso fino alla sezione **Gestisci dispositivi** e
    fai clic su Configurazione. Esaminare i dettagli della
    **configurazione**.

> ![](./media/image15.png)

5.  Scorri verso l'alto e seleziona **Tutti i dispositivi**. Nella
    sezione **Dispositivi** | Vengono visualizzate le informazioni sui
    **dispositivi**, ad esempio il nome del dispositivo, Gestito da, la
    proprietà, la conformità, il sistema operativo e la versione del
    sistema operativo. Fare clic su **SEA-WS1**.

> ![](./media/image16.png)

6.  Nel riquadro di navigazione SEA-WS1, selezionare **Hardware** ed
    esaminare l'inventario hardware.

> ![A screenshot of a computer Description automatically
> generated](./media/image17.png)

7.  Nel riquadro di navigazione SEA-WS1, **selezionare App** individuate
    ed esaminare l'inventario delle app.

> ![A screenshot of a computer Description automatically
> generated](./media/image18.png)

8.  Nel riquadro di navigazione SEA-WS1, selezionare **Configurazione
    dispositivo** e nel riquadro dei dettagli prendere nota dei profili
    di configurazione del dispositivo assegnati al dispositivo. Nella
    colonna Stato dovrebbe essere visualizzato **Succeeded**, il che
    significa che i profili sono stati applicati correttamente al
    dispositivo.

> ![](./media/image19.png)

9.  Nel **SEA-WS1 | Pagina di configurazione del dispositivo,** fare
    clic su **Contoso Developer - standard.**

> ![](./media/image20.png)

10. Nel pannello **Contoso Developer - Standard** prendere nota di ogni
    impostazione configurata nel profilo.

> **Lo stato** dovrebbe visualizzare **Completato** accanto a tutti.
>
> ![](./media/image21.png)

**Risultati**: dopo aver completato questo esercizio, l'attività di
accesso dell'utente, i log di controllo e l'attività del dispositivo
saranno stati monitorati correttamente.
