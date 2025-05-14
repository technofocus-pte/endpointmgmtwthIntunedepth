Atelier 21 : Actualisation de Windows avec la réinitialisation du pilote
automatique et le mode de déploiement automatique.

**Résumé**

Dans cet atelier, vous allez apprendre à effectuer une réinitialisation
à distance de l'Autopilot.

**Conditions préalables**

Le(s) Ateliers suivant(s) doit(vent) être complété(s) avant cet atelier:

- Atelier 01-Gestion des identités dans Microsoft Entra ID

- Atelier 02 : synchronisation des identités à l'aide d'Azure AD Connect

- Atelier 21 : Déploiement de Windows 11 à l'aide de Microsoft
  Deployment Toolkit

- Atelier 20 - Déploiement de Windows 11 avec Autopilot

**Scénario**

SEA-WS4 a été déployé à l'aide de Windows Autopilot. Vous devez tester
un autre scénario de provisionnement qui implique la réinitialisation
d'Autopilot. Vous allez créer un profil de déploiement configuré avec le
mode de déploiement automatique de Windows Autopilot.

Tâche 1 : Configurer un profil de déploiement Windows Autopilot à
déploiement automatique

1.  Passez à [***SEA-SVR1***](urn:gd:lg:a:select-vm).

> ![](./media/image1.png)

2.  Dans **Microsoft Edge**, ouvrez un nouvel onglet et accédez à
    [**https://intune.microsoft.com**](https://intune.microsoft.com). Si
    vous y êtes invité, connectez-vous à l'aide [**de
    admin@M365xXXXXXXXX.onmicrosoft.com**](mailto:admin@M365xXXXXXXXX.onmicrosoft.com)
    et de paswword.

3.  Dans le **Microsoft Intune admin center** sélectionnez **Devices**.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image2.png)

4.  Dans la section **Device onboarding** , sélectionnez
    **Inscription**.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image3.png)

5.  Dans le panneau Inscription Windows, dans le volet d'informations,
    sélectionnez select **Deployment Profiles**.

> ![](./media/image4.png)

6.  Dans le panneau **Windows AutoPilot deployment profiles** ,
    sélectionnez **Contoso profile 1** puis **Properties.**

> ![](./media/image5.png)
>
> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image6.png)
>
> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image7.png)

7.  Faites défiler jusqu'à **Assignments**  puis sélectionnez **Edit**.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image8.png)

8.  À côté de **IT Devices**, sélectionnez **Remove**.

> ![](./media/image9.png)

9.  Sélectionnez **Review and save** , puis Sélectionnez **Save**.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image10.png)

10. Fermer le **Contoso Profile 1|Properties** .

11. Dans le panneau **Windows AutoPilot deployment profiles** ,
    sélectionnez **Createprofile**, puis **Windows PC**.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image11.png)

12. Sous l' onglet **Basics**, dans la zone de texte **Name**, tapez
    [**le profil Contoso 2**](urn:gd:lg:a:send-vm-keys).

13. Pour **Convert all targeted devices to Autopilot**, sélectionnez
    **No**, puis sélectionnez **Next**.

> ![](./media/image12.png)

14. Dans l' onglet **Out-of-box experience (OOBE)** **assurez-vous** que
    le **Deployment mode**  est défini sur **Self-Deploying**.

> ![](./media/image13.png)

15. Assurez-vous que les options suivantes sont définies :

    - Langue (région) : **Operating system default**

    - Configurer automatiquement le clavier : **Yes**

    - Appliquer le modèle de nom de périphérique :Y**es**

    - Entrez un nom :
      [**Contoso- %RAND :2 %**](urn:gd:lg:a:send-vm-keys)

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image14.png)

16. Sélectionnez **Next**.

17. Sous l' onglet **Assignments**, sous **included Groups**,
    sélectionnez **Add groups**.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image15.png)

18. Sélectionnez le groupe **IT Devices** et cliquez sur **Select**.
    Sélectionnez **Next**.

> ![](./media/image16.png)
>
> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image17.png)

19. Dans le panneau **Review + create** , passez en revue les
    informations, puis sélectionnez **Create**.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image18.png)

Tâche 2 : Effectuer une réinitialisation de l'Autopilot

1.  Dans le **Microsoft Intune admin center**, sélectionnez **Devices**,
    puis sélectionnez **All devices**

2.  Sélectionnez l'Autopilot PC (commence par le nom DESKTOP).

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image19.png)

3.  Dans la barre de menus, sélectionnez l'ellipse, puis sélectionnez
    **Autopilot Reset**.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image20.png)

4.  À l'invite du message, sélectionnez **Yes**.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image21.png)

5.  Passez à [***SEA-SVR2***](urn:gd:lg:a:select-vm) et agrandissez la
    fenêtre **SEA-WS4**.

> **Remarque** : SEA-WS4 doit toujours être en cours d'exécution à
> partir du laboratoire précédent
>
> **Remarque** : Mettez à jour l'appareil vers la dernière version, puis
> cliquez sur redémarrer.

6.  Redémarrez **SEA-WS4**.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image22.png)
>
> **Remarque** : Ce processus peut prendre 30 minutes et redémarrera
> plusieurs fois au cours du processus. Votre instructeur peut passer au
> module suivant pendant que cette tâche est terminée. Assurez-vous de
> revenir pour terminer la tâche 3 lors de votre prochaine séance de
> laboratoire.

Tâche 3 : Vérifier le déploiement d'Autopilot

1.  Sur la page de connexion, saisissez
    [**Cindy@M365x19242953.onmicrosoft.com**](mailto:Cindy@M365x19242953.onmicrosoft.com)
    avec le mot de passe [**P@55w.rd1234**](mailto:P@55w.rd1234).

2.  Dans **Utiliser Windows Hello avec votre compte**, sélectionnez
    **OK.**

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image23.png)

3.  Sur la page **Verify your identity**, sélectionnez la méthode de
    vérification par texte.

4.  Sur la page **Enter** **code**, entrez le code qui a été envoyé par
    SMS à votre appareil mobile, puis sélectionnez **Verify**.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image24.png)

5.  Dans la boîte de **Setup up a PIN** , dans les champs **New PIN** et
    **Confirm PIN**, entrez [**102938**](urn:gd:lg:a:send-vm-keys), puis
    sélectionnez **OK**.

> ![](./media/image25.png)

6.  Sur la page **Tout est prêt ! !** , sélectionnez **OK.**

7.  Sélectionnez **Start**, puis Sélectionnez **Settings**.

> ![](./media/image26.png)

8.  Sélectionnez **Accounts**, puis **Access work or school**. Vérifiez
    que l'appareil est connecté à Azure AD de Contoso.

> ![](./media/image27.png)

9.  Sélectionnez **Connected to Contoso's Azure AD** , puis I
    Sélectionnez **info.**

> ![](./media/image28.png)

10. Dans la page **Managed by contoso** , faites défiler l'écran vers le
    bas, puis sélectionnez **Sync**.

> ![](./media/image29.png)

11. Sur **SEA-WS4**, fermez la fenêtre **Settings**.

12. Arrêtez **SEA-WS4** et fermez la fenêtre **SEA-WS4**.

13. Sur [***SEA-SVR2***](urn:gd:lg:a:select-vm), fermez le Gestionnaire
    Hyper-V.

**Résultats** : Une fois cet exercice terminé, vous aurez configuré un
appareil Windows 11 avec la réinitialisation Autopilot à l'aide du mode
de déploiement automatique.
