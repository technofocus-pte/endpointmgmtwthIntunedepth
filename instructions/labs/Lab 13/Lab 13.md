Atelier 13 : Configurer les politiques de protection des applications
pour les appareils mobiles

**Résumé**

Dans cet Atelier , vous configurerez une politique de protection des
applications pour un appareil mobile.

**Scénario**

Tous les développeurs de Contoso disposent d'iPhones et d'iPads
exécutant les dernières versions d'iOS/iPadOS. Le service de sécurité
est préoccupé par les fuites de données et souhaite éviter que les
données de l'e-mail de l'entreprise ne soient copiées vers d'autres
applications sur les appareils mobiles. Vous devez fournir une solution
qui répond aux préoccupations du service de sécurité. Vous devez vous
assurer de ce qui suit :

- Les données Outlook doivent être limitées pour la sauvegarde sur
  iTunes ou iCloud.

- Seules les applications gérées par une stratégie peuvent envoyer et
  recevoir des données à partir d'Outlook.

- Seules les applications gérées par une stratégie peuvent couper,
  copier ou coller avec Outlook.

- Les utilisateurs doivent fournir leurs informations d'identification
  de compte professionnel ou scolaire pour accéder à Outlook.

Tâche 1 : Créer une politique de protection des applications pour les
appareils iOS/iPadOS

1.  Sur [***SEA-SVR1***](urn:gd:lg:a:select-vm), si nécessaire,
    connectez-vous en tant que
    [**Contoso\Administrator**](urn:gd:lg:a:send-vm-keys) avec le mot de
    passe !\![**Pa55w.rd**](urn:gd:lg:a:send-vm-keys) !!

2.  Dans la barre des tâches, sélectionnez **Microsoft Edge** et accédez
    au **Microsoft Intune admin
    center** !!**https://intune.microsoft.com** !! dans la barre
    d'adresse, puis appuyez sur **Enter**.

3.  Connectez-vous avec les informations d'identification de
    l'administrateur du Office 365 Tenant à partir de l'onglet Accueil.

4.  Dans la page **Microsoft Intune admin center** , sélectionnez
    **Apps**.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image1.png)

5.  Sur le panneau **Apps | Overview** , sous **Policy**, sélectionnez
    **App protection policies**.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image2.png)

6.  Dans le volet d'informations, sélectionnez **+ Create policy**  puis
    iOS**/iPadOS.**

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image3.png)

7.  Sous l' onglet **Basics** , configurez les options suivantes et
    sélectionnez **Next** :

    - Nom : !\![**Outlook – Developers**](urn:gd:lg:a:send-vm-keys)!!

    - La description : !\![**Policy to prevent cut/copy and paste from
      Outlook**](urn:gd:lg:a:send-vm-keys)!!

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image4.png)

8.  Dans l' onglet **Apps**, cliquez sur + **Select public apps**.

9.  Dans le panneau **Sélectionner les applications à cibler**, dans la
    zone de texte, tapez !!**Outlook** !! Sélectionnez **Microsoft
    Outlook**, puis cliquez sur le bouton **Select**, puis sélectionnez
    **Next**.

> ![Captures d'écran d'un ordinateur Description générée
> automatiquement](./media/image5.png)

10. Sous l' onglet **Data protection** , configurez les options
    suivantes et sélectionnez **Next** :

    - Sauvegarder les données de l'organisation dans les sauvegardes
      ITunes et iCloud : **Block**

    - Envoyer les données de l'organisation à d'autres applications :
      **Policy managed apps**

    - Recevoir des données d'autres applications : **Policy managed
      apps**

    - Restreindre le couper, le copier et le coller entre d'autres
      applications : **Policy managed apps**

> Laisser tous les autres paramètres par défaut
>
> ![](./media/image6.png)

11. Sous l' onglet **Access requirements** , configurez les options
    suivantes et sélectionnez **Next** :

    - NIP pour l'accès : **Non requis**

    - Informations d'identification de compte professionnel ou scolaire
      pour l'accès : **Requis**

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image7.png)

12. Dans l' onglet **Conditional launch**, passez en revue les
    paramètres. Sélectionnez **Next**.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image8.png)
>
> **Remarque** : Ici, vous pouvez définir les exigences de sécurité de
> connexion pour votre politique de protection d'accès. Vous pouvez
> sélectionner un paramètre et entrer la valeur que les utilisateurs
> doivent respecter pour se connecter à votre application d'entreprise.
> Prenez note des différents paramètres mais ne changez rien.

13. Sous l' onglet **Assignments**, sélectionnez **Next**.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image9.png)

14. Sous l' onglet **Review + create** vérifiez les paramètres et
    sélectionnez **Create**.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image10.png)

15. Sur le panneau **Apps | App protection policies**  dans le volet
    d'informations, vérifie que **Outlook - Développers** est
    répertorié.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image11.png)

16. Fermez Microsoft Edge.

**Résultats** : Une fois cet exercice terminé, vous avez configuré une
politique de protection des applications pour un appareil mobile.
