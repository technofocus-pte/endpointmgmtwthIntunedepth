# Lab 25: Monitoraggio delle prestazioni dei dispositivi e dell'esperienza utente con l'analisi degli endpoint

**Sommario**

In questo lab si abilita l'analisi degli endpoint per monitorare le
prestazioni dei dispositivi e i punteggi e le informazioni dettagliate
dell'esperienza utente.

**Prerequisiti**

I seguenti laboratori devono essere completati prima di questo
laboratorio:

- Lab 05- Gestire la registrazione dei dispositivi in Intune

- Lab 06- Registrazione dei dispositivi in Intune

- Lab 07- Creazione e distribuzione dei profili di configurazione

**Scenario**

È stato chiesto di monitorare le prestazioni di avvio, l'affidabilità
delle applicazioni e l'esperienza utente con cui gli utenti riavviano i
dispositivi. Per acquisire queste informazioni è necessario abilitare
l'analisi degli endpoint.

### Task 1: Attivare l'analisi degli endpoint

1.  Su [**SEA-SVR1**](urn:gd:lg:a:select-vm), se necessario, accedere
    come [**Contoso\Administrator**](urn:gd:lg:a:send-vm-keys) con la
    password !\![**Pa55w.rd**](urn:gd:lg:a:send-vm-keys)!! and
    close **Server Manager**.

2.  Sulla barra delle applicazioni, seleziona **Microsoft Edge**.

3.  In Microsoft Edge
    digitare!\![**https://intune.microsoft.com**](https://intune.microsoft.com)!! nella
    barra degli indirizzi, quindi premere **INVIO**.

4.  Accedi come
    [**admin@M365x19242953.onmicrosoft.com**](urn:gd:lg:a:send-vm-keys) con
    la password.

5.  Nella pagina dell'interfaccia di **amministrazione di Microsoft
    Intune** selezionare **Report**.

6.  Nel pannello **Report**, in **Analisi**, selezionare Analisi degli
    **endpoint**.

> ![](./media/image1.png)

7.  Nella pagina **Analisi degli endpoint,** assicurarsi che **Raccogli
    i dati del dispositivo da** è impostato su **Tutti i dispositivi
    gestiti dal cloud**, quindi selezionare **Avvia**.

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)
>
> Prendi nota del messaggio nella parte superiore della pagina
> Panoramica. Potrebbero essere necessarie fino a 24 ore prima che i
> punteggi e le informazioni dettagliate vengano visualizzati sulla
> pagina.
>
> ![A screenshot of a computer Description automatically
> generated](./media/image3.png)

8.  Passare a **SEA-WS1** e riavviare il dispositivo.

9.  Accedi come **Cindy White** con la
    password: [**102938**](urn:gd:lg:a:send-vm-keys).

10. Passare a[**SEA-SVR1**](urn:gd:lg:a:select-vm).

11. Nella pagina **dell'interfaccia di amministrazione di Microsoft
    Intune**, selezionare **Dispositivi**, quindi selezionare **Tutti i
    dispositivi.**

12. Selezionare **SEA-WS1**.

> ![](./media/image4.png)

13. Nella pagina **SEA-WS1**, selezionare **Sincronizza**, quindi
    selezionare **Sì**.

> ![A screenshot of a computer Description automatically
> generated](./media/image5.png)

14. Nella pagina **SEA-WS1**, in **Monitor**, selezionare **Esperienza
    utente.** ![A screenshot of a computer Description automatically
    generated](./media/image6.png)

15. Esaminare le schede **Analisi degli endpoint**, Prestazioni di avvio
    e **Affidabilità delle applicazioni.**

> ![A screenshot of a computer Description automatically
> generated](./media/image7.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image8.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image9.png)
>
> Potrebbe non essere riportata alcuna informazione a causa del ritardo,
> tuttavia leggi i dettagli su ciò che sarà visibile su ogni scheda.

16. Nella pagina **dell'interfaccia di amministrazione di Microsoft**
    Intune selezionare **Report**.

17. Nel pannello **Report**, in **Analisi**, selezionare **Analisi degli
    endpoint**.

> ![](./media/image10.png)
>
> Si noti che lo stesso tipo di informazioni è disponibile in Endpoint
> Analytics, tuttavia queste informazioni si basano su tutti i
> dispositivi registrati.
>
> ![A screenshot of a computer Description automatically
> generated](./media/image11.png)

18. Sfogliare i report disponibili nella pagina Analisi endpoint.

19. Chiudi Microsoft Edge.

**Risultati:** dopo aver completato questo esercizio, avrai abilitato
correttamente l'analisi degli endpoint per monitorare le prestazioni del
dispositivo e i punteggi e le informazioni dettagliate dell'esperienza
utente.
