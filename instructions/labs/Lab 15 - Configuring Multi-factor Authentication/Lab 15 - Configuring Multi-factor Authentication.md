Lab 15 - Configurazione dell'autenticazione a più fattori

**Sommario**

In questo lab si configurerà l'autenticazione a più fattori (MFA) per
utente e si applicherà l'autenticazione a più fattori usando un criterio
di accesso condizionale.

Esercizio 1: Configurare l'autenticazione a più fattori per utente.

**Scenario**

Per fornire una sicurezza aggiuntiva per gli eventi di accesso utente, è
necessario configurare e testare l'autenticazione a più fattori (MFA).
Si decide di testare prima l'autenticazione a più fattori per utente.
Alex Wilber ha accettato di convalidare le impostazioni per te.

Task 1: Convalidare l'accesso prima di abilitare l'autenticazione a più
fattori

1.  Cambia e accedi a SEA-WS3 come !! Admin!! con la
    password!\![**Pa55w.rd**](urn:gd:lg:a:send-vm-keys)!!

2.  Sulla barra delle applicazioni, seleziona **Microsoft Edge**. Nella
    barra degli indirizzi, inserisci !! outlook.office.com!! e premere
    Invio.

3.  Nella pagina di **accesso**, inserisci !!
    AlexW@M365xXXXXXXX.onmicrosoft.com!! , quindi seleziona **Avanti**.

4.  Nella pagina **Inserisci password**, inserisci !! P@55w.rd1234!! e
    seleziona **Accedi**. Al prompt della password di salvataggio di
    Edge, **selezionare Salva.**

> Verrà aperto Outlook sul Web. Tieni presente che per accedere a
> Outlook sul Web è stata richiesta solo la password.

5.  Nell'angolo in alto a destra, seleziona **Account manager per Alex
    Wilber**, **quindi seleziona Esci.**

> ![](./media/image1.png)

6.  Chiudi Microsoft Edge.

Task 2: Abilitare l'autenticazione a più fattori per un utente

1.  Passare a SEA-SVR1. In SEA-SVR1, se necessario, accedere come
    Contoso\Administrator con la password di !! Pa55w.rd!! e chiudi
    **Server Manager**.

2.  Sulla barra delle applicazioni selezionare **Microsoft Edge**,
    passare all'interfaccia di **amministrazione di Microsoft
    Entra**!!**https://Entra.Microsoft.com**!!

3.  Accedere con le credenziali di amministratore **tenant di Office
    365.**

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)
>
> Verrà visualizzata l'interfaccia di amministrazione di Microsoft
> Entra.

4.  Nell'interfaccia di **amministrazione di Microsoft Entra**, nel
    riquadro di spostamento, espandere Identità, quindi selezionare
    **Utenti**.

5.  Selezionare **Tutti gli utenti** e quindi nella parte superiore del
    riquadro dei risultati selezionare **MFA per utente**. Potrebbe
    essere necessario selezionare prima i puntini di sospensione per
    visualizzare l'opzione **MFA per utente.**

> ![A screenshot of a computer Description automatically
> generated](./media/image3.png)

6.  Nella pagina di autenticazione a più fattori selezionare le
    **impostazioni del servizio.**

> ![A screenshot of a computer Description automatically
> generated](./media/image4.png)

7.  Scorri verso il basso fino alla sezione delle **opzioni di
    verifica**.

> Prendi nota dei vari metodi che possono essere configurati per la
> verifica dell'utente.

8.  Nella sezione **Memorizza autenticazione a più fattori su
    dispositivo attendibile selezionare** la casella di controllo
    accanto a **Consenti agli utenti di ricordare l'autenticazione a più
    fattori sui dispositivi attendibili**.

> Accanto a **Numero di giorni per i quali gli utenti** possono
> considerare attendibili i dispositivi, inserisci **30** e quindi
> seleziona **Salva**. Selezionare **Chiudi** quando
> richiesto.![](./media/image5.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image6.png)

9.  Nella parte superiore della pagina, in **Autenticazione a più
    fattori,** selezionare **utenti**.

> ![A screenshot of a computer Description automatically
> generated](./media/image7.png)

10. Nell'elenco degli utenti selezionare la casella di controllo accanto
    a **Alex Wilber**.

11. Nella pagina Alex Wilber selezionare **Abilita**.

> ![A screenshot of a computer Description automatically
> generated](./media/image8.png)

12. Nel messaggio Informazioni **sull'abilitazione dell'autenticazione a
    più fattori,** selezionare **Abilita autenticazione a più fattori**.

> ![A screenshot of a computer Description automatically
> generated](./media/image9.png)

13. Nel messaggio **Aggiornamenti riusciti**, selezionare **Chiudi**. Si
    noti che lo stato di autenticazione a più fattori per Alex Wilber è
    ora abilitato.

14. ![A screenshot of a computer Description automatically
    generated](./media/image10.png)

> ![A screenshot of a computer Description automatically
> generated](./media/image11.png)

15. Chiudi Microsoft Edge.

Task 3: Registrazione e convalida MFA

1.  Passare a SEA-WS3. Sulla barra delle applicazioni, seleziona
    **Microsoft Edge.**

2.  Nella barra degli indirizzi, inserisci !! outlook.office.com!! e
    premere Enter.

3.  Nella pagina **Scegli un account**,
    seleziona!\![**AlexW@M365xXXXXXXX.onmicrosoft.com**](mailto:AlexW@M365xXXXXXXX.onmicrosoft.com)!!

> ![A screenshot of a computer Description automatically
> generated](./media/image12.png)

4.  Nella pagina **Inserisci password**, inserisci!!**P@55w.rd1234**!! e
    selezionare **Accedi.**

5.  Nella pagina **Altre informazioni richieste** selezionare
    **Avanti**. Viene visualizzata la pagina Proteggi il tuo account.

> ![A screenshot of a computer Description automatically
> generated](./media/image13.png)
>
> In genere, è consigliabile usare l'app Microsoft Authenticator per
> gestire l'autenticazione a più fattori. Tuttavia, per questo scenario
> di laboratorio, si useranno i messaggi di testo.

6.  Nella **pagina Mantieni sicuro il tuo account**, seleziona **Voglio
    configurare un metodo diverso**.

> ![A screenshot of a computer Description automatically
> generated](./media/image14.png)

7.  Nella finestra di dialogo **Scegli un metodo diverso,** seleziona
    **Telefono**, quindi seleziona **Conferma**.

> ![A screenshot of a computer Description automatically
> generated](./media/image15.png)

8.  Nella pagina **Telefono** immettere il numero di cellulare a cui è
    possibile ricevere messaggi di testo, quindi selezionare **Avanti**.

> ![A screenshot of a computer screen Description automatically
> generated](./media/image16.png)
>
> Dopo aver ricevuto il codice di verifica come SMS, immettere il codice
> dove indicato nella pagina **Telefono** e quindi selezionare
> **Avanti**.![](./media/image17.png)

9.  Nel messaggio SMS verificato, seleziona **Avanti**, quindi seleziona
    **Fine**.

> ![A screenshot of a computer screen Description automatically
> generated](./media/image18.png)
>
> ![](./media/image19.png)

10. Nel messaggio Rimani connesso, seleziona **No**.

> ![A screenshot of a computer error Description automatically
> generated](./media/image20.png)
>
> Outlook sul Web si apre nella casella di posta di Alex Wilber.

11. Nell'angolo in alto a destra, seleziona **Account manager per Alex
    Wilber**, quindi seleziona **Esci**.

> ![](./media/image21.png)
>
> **Nota**: gli utenti devono registrarsi solo la prima volta che
> utilizzano l'autenticazione a più fattori. Gli accessi successivi
> richiedono solo di fornire il codice di convalida inviato tramite SMS
> al numero di telefono inserito durante la registrazione.

12. Nella barra degli indirizzi,
    inserire!\![**outlook.office.com**](urn:gd:lg:a:send-vm-keys)!!  e
    premere Invio.

13. Nella pagina **Scegli un account**,
    seleziona!!**AlexW@M365xXXXXXXXX.onmicrosoft.com**!!

14. Nella pagina **Inserisci password**, digita!!**P@55w.rd1234**!!
    Nella barra degli indirizzi, **inserire**

> ![A screenshot of a computer error Description automatically
> generated](./media/image22.png)
>
> Viene visualizzata **la richiesta Verifica identità.** Nota che
> contiene le ultime due cifre del tuo numero di telefono.

15. Alla richiesta **Verifica la tua identità**, seleziona il tuo numero
    di telefono SMS.

16. Nella pagina **Inserisci codice**, inserisci il codice inviato al
    tuo cellulare, quindi seleziona **Verifica**.

> ![A screenshot of a computer error message Description automatically
> generated](./media/image23.png)
>
> Si noti che è possibile selezionare una casella di controllo per non
> richiedere nuovamente la verifica per 30 giorni.
>
> Poiché **l'app Microsoft Authenticator** garantisce una maggiore
> sicurezza e un'esperienza fluida, ti verrà chiesto di configurare lo
> stesso, per ora fai clic su **Salta per ora**
>
> ![A screenshot of a computer error Description automatically
> generated](./media/image24.png)

17. Nel messaggio Rimani connesso, seleziona **No**. Outlook sul Web si
    apre nella casella di posta di Alex Wilber.

> ![A screenshot of a computer error Description automatically
> generated](./media/image25.png)

18. Nell'angolo in alto a destra, seleziona **Account manager per Alex
    Wilber**, **quindi seleziona Esci.**

> ![A computer screen shot of a computer screen Description
> automatically generated](./media/image26.png)

19. Chiudi Microsoft Edge.

Task 3: Rimuovere MFA per utente

1.  Passare a [**SEA-SVR1**](urn:gd:lg:a:select-vm).
    Su [**SEA-SVR1**](urn:gd:lg:a:select-vm), se necessario, accedere
    come [**Contoso\Administrator**](urn:gd:lg:a:send-vm-keys) con la
    password di  !\![**Pa55w.rd**](urn:gd:lg:a:send-vm-keys)!! e
    chiudere **Server Manager**.

2.  Nella barra delle applicazioni selezionare **Microsoft Edge**,
    passare al centro di amministrazione di **Microsoft
    Entra** !!**https://Entra.Microsoft.com**!!

3.  Accedere con le credenziali di **amministratore tenant di Office
    365.**

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)
>
> Verrà visualizzata l'interfaccia di **amministrazione di Microsoft
> Entra**.

4.  Nell'interfaccia di **amministrazione di Microsoft Entra**, nel
    riquadro di spostamento, espandere **Identità**, quindi selezionare
    **Utenti**.

5.  Selezionare **Tutti gli utenti** e quindi nella parte superiore del
    riquadro dei risultati selezionare **MFA per utente**. Potrebbe
    essere necessario selezionare prima i puntini di sospensione per
    visualizzare l'opzione **MFA per utente.**

> ![A screenshot of a computer Description automatically
> generated](./media/image3.png)

6.  Nella parte superiore della pagina, in **Autenticazione a più
    fattori,** selezionare **utenti**.

7.  Nell'elenco degli utenti selezionare la casella di controllo accanto
    a **Alex Wilber**.

> Si noti che lo stato di **autenticazione a più fattori** per Alex
> Wilber è ora impostato su Applicato (in precedenza era **impostato**
> su Abilitato). Ciò è dovuto al fatto che Alex si è registrato e
> utilizza l'autenticazione a più fattori.
>
> ![A screenshot of a computer Description automatically
> generated](./media/image27.png)

8.  Nella pagina Alex Wilber selezionare **Gestisci impostazioni
    utente.**

> ![A screenshot of a computer Description automatically
> generated](./media/image28.png)

9.  Nella casella Gestisci impostazioni utente selezionare la casella di
    controllo accanto a tutte e tre le opzioni, selezionare **Salva** e
    quindi selezionare **Chiudi**.

> ![A screenshot of a computer Description automatically
> generated](./media/image29.png)
>
> Queste opzioni rimuoveranno tutte le impostazioni MFA salvate per
> Alex.
>
> ![A white rectangular frame with black border Description
> automatically generated](./media/image30.png)

10. Nell'elenco degli utenti selezionare la casella di controllo accanto
    a **Alex Wilber**.

11. Nella pagina Alex Wilber, seleziona **Disabilita**.

> ![A screenshot of a computer Description automatically
> generated](./media/image31.png)

12. Nel messaggio **Disabilita autenticazione a più fattori**
    selezionare **Sì**.

> ![](./media/image32.png)

13. Nel messaggio **Aggiornamenti riusciti**, selezionare **Chiudi**.

> ![A white screen with black text Description automatically
> generated](./media/image33.png)
>
> Tieni presente che lo stato di **autenticazione a più fattori** per
> Alex Wilber è ora **disabilitato**.
>
> ![A screenshot of a computer Description automatically
> generated](./media/image34.png)

14. Chiudi Microsoft Edge.

**Risultati**: dopo aver completato questo esercizio, l'autenticazione a
più fattori per utente sarà stata configurata correttamente.

**Esercizio 2: Configurare l'autenticazione a più fattori tramite
l'accesso condizionale**

**Scenario**

Per fornire una sicurezza aggiuntiva per gli eventi di accesso utente, è
necessario configurare e testare l'autenticazione a più fattori (MFA).
Si decide che l'uso di un criterio di accesso condizionale offre una
maggiore flessibilità per i requisiti dell'autenticazione a più fattori.
Alex Wilber ha accettato di convalidare le impostazioni per te.

Task 1: Convalidare l'accesso prima di abilitare l'accesso condizionale
con l'autenticazione a più fattori

1.  Passare e accedere a
    [**SEA-WS3**](urn:gd:lg:a:select-vm) as !\![**Admin**](urn:gd:lg:a:send-vm-keys)!!
     con la password !\![**Pa55w.rd**](urn:gd:lg:a:send-vm-keys)!!

2.  Sulla barra delle applicazioni, seleziona **Microsoft Edge**. Nella
    barra degli indirizzi, inserisci !! outlook.office.com!! e premere
    Invio.

3.  Alla pagina **Accedi**,
    inserisci!!**AlexW@M365xXXXXXXX.onmicrosoft.com**e quindi
    selezionare **Avanti**.

4.  Nella pagina **Inserisci password,** digita!!**P@55w.rd1234**!!  e
    selezionare **Accedi**. Al prompt Edge Salva password, selezionare
    **Salva**

> Verrà aperto Outlook sul Web. Tieni presente che per accedere a
> Outlook sul Web è stata richiesta solo la password.

5.  Nell'angolo in alto a destra, seleziona **Account manager per Alex
    Wilber**, quindi **seleziona Esci.**

> ![A screenshot of a computer Description automatically
> generated](./media/image1.png)

6.  Chiudi Microsoft Edge.

Task 2: Configurare l'accesso condizionale con l'autenticazione a più
fattori

1.  Switch to [**SEA-SVR1**](urn:gd:lg:a:select-vm).
    On [**SEA-SVR1**](urn:gd:lg:a:select-vm), se necessario, accedere
    come [**Contoso\Administrator**](urn:gd:lg:a:send-vm-keys) con la
    password di  !\![**Pa55w.rd**](urn:gd:lg:a:send-vm-keys)!!  e
    chiudere **Server Manager.**

2.  Nella barra delle applicazioni selezionare **Microsoft Edge**,
    accedere al **centro di amministrazione Microsoft
    Entra **!!**https://Entra.Microsoft.com**!!

3.  Accedere con le credenziali di **amministratore tenant di Office
    365.**

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)
>
> Verrà visualizzata l'interfaccia di **amministrazione di Microsoft
> Entra**.

4.  Nell'interfaccia di **amministrazione di Microsoft Entra,** nel
    riquadro di spostamento, espandere **Identità, quindi Protezione,**
    quindi **Accesso condizionale.**

> ![A screenshot of a computer Description automatically
> generated](./media/image35.png)

5.  Nella pagina **Accesso condizionale** selezionare **Criteri**,
    quindi selezionare + **Nuovo criterio**.

> ![A screenshot of a computer Description automatically
> generated](./media/image36.png)

6.  Nella casella **Nome** della pagina **Nuovo criterio di accesso
    condizionale immettere**!\![**Contoso MFA
    Policy**](urn:gd:lg:a:send-vm-keys)!!.

7.  In **Assegnazioni** selezionare 0 **utenti o le identità del carico
    di lavoro selezionate**.

> ![A screenshot of a computer Description automatically
> generated](./media/image37.png)

8.  Nel riquadro Utenti e gruppi selezionare l'opzione accanto a
    **Seleziona utenti e gruppi**, quindi selezionare la casella di
    controllo accanto a **Utenti e gruppi.**

> Nella pagina **Seleziona** selezionare **Alex Wilber** e quindi fare
> clic su **Seleziona**.
>
> ![A screenshot of a computer Description automatically
> generated](./media/image38.png)
>
> Si noti che in genere si specifica un gruppo, tuttavia per questo
> esercizio testeremo solo l'impostazione su Alex Wilber.

9.  Selezionare **Nessuna risorsa di destinazione selezionata** in
    Risorse di destinazione, quindi fare clic su **Seleziona app**.

> ![A screenshot of a computer Description automatically
> generated](./media/image39.png)
>
> Nella pagina **Seleziona** selezionare la casella di controllo accanto
> a **Office 365** e quindi fare clic su **Seleziona**.
>
> ![A screenshot of a computer Description automatically
> generated](./media/image40.png)

10. In Controlli di accesso, **nella sezione Concedi,** selezionare **0
    controlli selezionati**.

> ![A screenshot of a computer Description automatically
> generated](./media/image41.png)

11. Nella pagina **Concedi** selezionare Concedi **accesso**,
    selezionare la casella di **controllo accanto a Richiedi
    autenticazione** a più fattori e quindi **fare clic su Seleziona**.

> ![A screenshot of a computer Description automatically
> generated](./media/image42.png)

12. In Abilita criterio, seleziona **Attivato**.

13. Selezionare **Crea** per creare i criteri MFA di Contoso. Si noti
    che il criterio è elencato con uno stato di **On**.

> ![A screenshot of a computer Description automatically
> generated](./media/image43.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image44.png)

14. Nell'interfaccia di **amministrazione di Microsoft Entra**
    selezionare Utenti. Nell'elenco Utenti, seleziona **Alex Wilber**.

> ![A screenshot of a computer Description automatically
> generated](./media/image45.png)

15. Nella pagina Alex Wilber selezionare **Metodi di autenticazione**.

> ![](./media/image46.png)
>
> Si noti che è già stato configurato un numero di telefono per Alex,

16. Chiudi Microsoft Edge.

Task 3: Convalida MFA di accesso condizionato

1.  Passare a SEA-WS3. Sulla barra delle applicazioni, seleziona
    **Microsoft Edge**.

2.  Nella barra degli indirizzi,
    inserisci!\![**outlook.office.com**](urn:gd:lg:a:send-vm-keys)!!  e
    premere Invio

3.  Nella pagina **Scegli un conto**, seleziona
    !!**AlexW@M365xXXXXXXX.onmicrosoft.com**!!

> ![A screenshot of a computer Description automatically
> generated](./media/image12.png)

4.  Nella pagina **Inserisci password**, inserisci !! P@55w.rd1234!! e
    seleziona **Accedi**.

> Alla richiesta **Verifica la tua identità**, seleziona il tuo numero
> di telefono SMS.
>
> ![A screenshot of a computer error Description automatically
> generated](./media/image22.png)

5.  Nella pagina **Inserisci codice**, inserisci il codice inviato al
    tuo cellulare, quindi seleziona **Verifica**.

> ![A screenshot of a computer error message Description automatically
> generated](./media/image23.png)
>
> Si noti che è possibile selezionare una casella di controllo per non
> richiedere nuovamente la verifica per 30 giorni.

6.  Nel messaggio Rimani connesso, seleziona **No**. Outlook sul Web si
    apre nella casella di posta di Alex Wilber.

> ![A screenshot of a computer error Description automatically
> generated](./media/image25.png)

7.  Nell'angolo in alto a destra, seleziona **Account manager per Alex
    Wilber,** quindi seleziona **Esci**.

> ![A computer screen shot of a computer screen Description
> automatically generated](./media/image26.png)

8.  Chiudi Microsoft Edge.

Task 4: Rimuovere l'accesso condizionato MFA

1.  Passare a [**SEA-SVR1**](urn:gd:lg:a:select-vm).
    On [**SEA-SVR1**](urn:gd:lg:a:select-vm), Se necessario, accedi come
    [**Contoso\Administrator**](urn:gd:lg:a:send-vm-keys) con la
    password di  !\![**Pa55w.rd**](urn:gd:lg:a:send-vm-keys)!! e chiudi
    **Server Manager**.

2.  Sulla barra delle applicazioni selezionare **Microsoft Edge,**
    passare all'interfaccia di **amministrazione di Microsoft Entra** 
    !!**https://Entra.Microsoft.com**!!

3.  Accedere con le credenziali di **amministratore tenant di Office
    365**.

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)
>
> Verrà visualizzata l'interfaccia di **amministrazione di Microsoft
> Entra**.

4.  Nell'interfaccia di **amministrazione di Microsoft Entra**, nel
    riquadro di spostamento**,** espandere Identità, quindi
    **Protezione,** quindi Accesso **condizionale.**

> ![A screenshot of a computer Description automatically
> generated](./media/image35.png)

5.  Nella pagina Accesso condizionale selezionare **Criteri** e quindi
    selezionare **Criteri MFA di Contoso.**

6.  Nella **pagina Criteri MFA di Contoso** selezionare **Elimina** e
    quindi selezionare **Elimina**.

> ![A screenshot of a computer Description automatically
> generated](./media/image47.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image48.png)

7.  Per la conferma dell'eliminazione, fare clic sul pulsante Elimina.

> ![A screenshot of a computer error Description automatically
> generated](./media/image49.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image50.png)

8.  Chiudi Microsoft Edge.

**Risultati**: dopo aver completato questo esercizio, l'autenticazione a
più fattori sarà stata configurata correttamente usando un criterio di
accesso condizionale.
