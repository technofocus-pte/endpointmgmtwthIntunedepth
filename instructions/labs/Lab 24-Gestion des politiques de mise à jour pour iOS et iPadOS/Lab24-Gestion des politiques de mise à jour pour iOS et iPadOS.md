Atelier 26 : Gestion des politiques de mise à jour pour iOS et iPadOS

**Résumé**

Dans cet atelier, vous allez configurer une stratégie de mise à jour à
utiliser pour gérer les mises à jour du système d'exploitation pour iOS
et iPadOS.

**Scénario**

Tous les développeurs de Contoso disposent d'iPhones et d'iPads
exécutant les dernières versions d'iOS/iPadOS. Vous avez inscrit ces
appareils via l'inscription automatisée des appareils d'Apple et vous
devez configurer une politique de mise à jour pour le système
d'exploitation de l'appareil. Vous devez vous assurer de ce qui suit :

- Version à installer : Dernière mise à jour.

- N'autorisez les mises à jour automatiques qu'entre le mercredi à
  Minuit et le jeudi à Minuit.

Tâche 1 : Créer une Politique de mise à jour pour les appareils
iOS/iPadOS

1.  Sur [***SEA-SVR1***](urn:gd:lg:a:select-vm), si nécessaire,
    connectez-vous en tant que
    [**Contoso\Administrator**](urn:gd:lg:a:send-vm-keys) avec le mot de
    passe [**Pa55w.rd**](urn:gd:lg:a:send-vm-keys) et fermez **server
    manager**.

2.  Dans la barre des tâches, sélectionnez **Microsoft Edge**.

3.  Dans Microsoft Edge, tapez
    [**https://intune.microsoft.com**](https://intune.microsoft.com)
    dans la barre d'adresse, puis appuyez sur **Enter**.

4.  Connectez-vous en tant que
    [**admin@M365x19242953.onmicrosoft.com**](urn:gd:lg:a:send-vm-keys)
    avec le mot de passe.

5.  Dans la page **Microsoft Intune admin center**, sélectionnez
    **Devices**.

6.  Sur le panneau **Devices|By platform**  sous **Policies**,
    sélectionnez **iOS/iPadOS.**

> ![](./media/image1.png)

7.  Sélectionnez **Update Policies for iOS/iPadOS**

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image2.png)

8.  Dans le volet d'informations, sélectionnez **Create profile**.

9.  Sous l' onglet **basics**, configurez les options suivantes et
    sélectionnez **Next** :

    - Nom: !\![**iOS/iPadOS update policy**](urn:gd:lg:a:send-vm-keys)!!

    - Description: !\![**Policy to manage system updates for iOS and
      iPadOS**](urn:gd:lg:a:send-vm-keys)!!

> ![](./media/image3.png)

10. Dans l' onglet **Update policy settings** , configurez les options
    suivantes et sélectionnez **Next** :

    - Sélectionnez la version à installer : **Latest update**

    - Type de planification : **Update during scheduled time**

    - Fuseau horaire : **UTC :00**

    - Fenêtre horaire :

    - Jour de début : **Wednesday**

      - Heure de début : **12 AM**

      - Fin de la journée : **thursday**

      - Heure de fin : **12 AM**

> ![](./media/image4.png)

11. Sous l' onglet **Assignments**, sélectionnez **Next**.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image5.png)

12. Sous l' onglet **Review + create** , vérifiez les paramètres et
    sélectionnez **Create**.

13. Sur le panneau **Devices | Update policies for iOS/iPadOS** , dans
    le volet de détails, vérifiez que **iOS/iPadOS update policy**  est
    répertoriée.

> ![Une capture d'écran d'un ordinateur Description générée
> automatiquement](./media/image6.png)

14. Fermez Microsoft Edge.

**Résultats** : une fois cet exercice terminé, vous avez configuré une
politique de mise à jour pour iOS et iPadOS.
