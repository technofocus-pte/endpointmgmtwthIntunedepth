Laboratório 13: Configurar políticas de proteção de aplicativos para
dispositivos móveis

**Resumo**

Neste laboratório, você configurará uma política de proteção de
aplicativo para um dispositivo móvel.

**Cenário**

Todos os desenvolvedores da Contoso possuem iPhones e iPads com as
versões mais recentes do iOS/iPadOS. O departamento de segurança está
preocupado com vazamentos de dados e quer evitar que os dados do e-mail
corporativo sejam copiados para outros aplicativos nos dispositivos
móveis. Você deve fornecer uma solução que atenda às preocupações do
departamento de segurança. Garantindo o seguinte:

- Os dados do Outlook devem ser restritos para backup no iTunes ou
  iCloud.

- Somente aplicativos gerenciados por políticas podem enviar e receber
  dados do Outlook.

- Somente aplicativos gerenciados por políticas podem recortar, copiar
  ou colar com o Outlook.

- Os usuários devem fornecer suas credenciais de conta corporativa ou
  escolar para acessar o Outlook.

Tarefa 1: Criar uma política de proteção de aplicativos para
dispositivos iOS/iPadOS

1.  Em [***SEA-SVR1***](urn:gd:lg:a:select-vm), se necessário, faça
    login como
    [**[Contoso\Administrator](urn:gd:lg:a:send-vm-keys)**](urn:gd:lg:a:send-vm-keys)
    com a senha !\![**Pa55w.rd**](urn:gd:lg:a:send-vm-keys)!!

2.  Na barra de tarefas, selecione **Microsoft Edge** e navegue até o
    **Microsoft Intune admin
    center** !!**https://intune.microsoft.com**!! na barra de endereço e
    pressione **Enter.**

3.  Entre com as credenciais de administrador de locatário do Office 365
    na aba Home.

4.  Na página do **Microsoft Intune admin center**, selecione **Apps**.

> ![A screenshot of a computer Description automatically
> generated](./media/image1.png)

5.  No painel **Apps | Overview**, em **Policy**, selecione **App
    protection policies**.

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)

6.  No painel de detalhes, selecione **+ Create policy** e depois
    selecione **iOS/iPadOS.**

> ![A screenshot of a computer Description automatically
> generated](./media/image3.png)

7.  Na aba **Basics**, configure as seguintes opções e selecione
    **Next**:

    - Name: !\![**Outlook – Developers**](urn:gd:lg:a:send-vm-keys)!!

    - Description: !\![**Policy to prevent cut/copy and paste from
      Outlook**](urn:gd:lg:a:send-vm-keys)!!

> ![A screenshot of a computer Description automatically
> generated](./media/image4.png)

8.  Na aba **Apps**, clique em + **Select public apps**.

9.  No painel **Select apps to target**, na caixa de texto, digite
    !!**Outlook**!! Selecione **Microsoft Outlook**, clique no botão
    **Select** e, em seguida, selecione **Next**.

> ![Screens screenshot of a computer Description automatically
> generated](./media/image5.png)

10. Na aba **Data protection**, configure as seguintes opções e
    selecione **Next**:

    - Backup Org data to ITunes and iCloud backups: **Block**

    - Send Org data to other apps: **Policy managed apps**

    - Receive data from other apps: **Policy managed apps**

    - Restrict cut, copy, and paste between other apps: **Policy managed
      apps**

> Deixe todas as outras configurações como padrão
>
> ![](./media/image6.png)

11. Na aba **Access requirements**, configure as seguintes opções e
    selecione **Next**:

    - PIN for access: **Not required**

    - Work or school account credentials for access: **Require**

> ![A screenshot of a computer Description automatically
> generated](./media/image7.png)

12. Na aba **Conditional launch**, revise as configurações. Selecione
    **Next**.

> ![A screenshot of a computer Description automatically
> generated](./media/image8.png)
>
> **Observação:** aqui você pode definir os requisitos de segurança de
> login para sua política de proteção de acesso. Você pode selecionar
> uma configuração e inserir o valor que os usuários devem atender para
> fazer login no aplicativo da sua empresa. Observe as diversas
> configurações, mas não altere nada.

13. Na aba **Assignments**, selecione **Next**.

> ![A screenshot of a computer Description automatically
> generated](./media/image9.png)

14. Na aba **Review + create**, revise as configurações e selecione
    **Create**.

> ![A screenshot of a computer Description automatically
> generated](./media/image10.png)

15. No painel **Apps | App protection policies**, no painel de detalhes,
    verifique se **Outlook - Developers** está listado.

> ![A screenshot of a computer Description automatically
> generated](./media/image11.png)

16. Feche o Microsoft Edge.

**Resultados:** Após concluir este exercício, você terá configurado com
sucesso uma política de proteção de aplicativo para um dispositivo
móvel.
