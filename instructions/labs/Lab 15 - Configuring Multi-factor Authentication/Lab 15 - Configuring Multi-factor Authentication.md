Laboratório 15 - Configurando a Multi-factor Authentication

**Resumo**

Neste laboratório, você configurará a multi-factor authentication (MFA)
por usuário e aplicará a MFA usando uma política de acesso condicional.

Exercício 1: Configurar Multi-factor Authentication por usuário.

**Cenário**

Para fornecer segurança adicional aos eventos de login do usuário, você
precisa configurar e testar a multi-factor authentication (MFA). Você
decide testar primeiro a MFA por usuário. Alex Wilber concordou em
validar as configurações para você.

Tarefa 1: validar o login antes de habilitar o MFA

1.  Altere e faça login no [**SEA-WS3**](urn:gd:lg:a:select-vm) como
    !\![**Admin**](urn:gd:lg:a:send-vm-keys)!! com a senha
    !\![**Pa55w.rd**](urn:gd:lg:a:send-vm-keys)!!

2.  Na barra de tarefas, selecione **Microsoft Edge**. Na barra de
    endereços, digite
    !\![**outlook.office.com**](urn:gd:lg:a:send-vm-keys)!! e pressione
    Enter.

3.  Na página **Sign in**, digite
    !!**AlexW@M365xXXXXXXX.onmicrosoft.com**!! e então selecione
    **Next**.

4.  Na página **Enter password**, digite !!**P@55w.rd1234**!! e
    selecione **Sign in**. No prompt Salvar senha do Edge, selecione
    **Save**.

> O Outlook na Web é aberto. Observe que apenas a senha foi necessária
> para entrar no Outlook na Web.

5.  No canto superior direito, selecione **Account manager for Alex
    Wilber** e depois selecione **Sign out**.

> ![](./media/image1.png)

6.  Feche o Microsoft Edge.

Tarefa 2: Habilitar MFA para um usuário

1.  Altere para [**SEA-SVR1**](urn:gd:lg:a:select-vm). Em
    [**SEA-SVR1**](urn:gd:lg:a:select-vm), se necessário, faça login
    como **[Contoso\Administrator](urn:gd:lg:a:send-vm-keys)** com a
    senha !! [**Pa55w.rd**](urn:gd:lg:a:send-vm-keys) !! e feche o
    **Server Manager**.

2.  Na barra de tarefas, selecione **Microsoft Edge** e navegue até o
    **Microsoft Entra admin center** !!**https://Entra.Microsoft.com**!!

3.  Entre com credenciais de **Office 365 Tenant admin.**

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)
>
> O **Microsoft Entra admin center** é aberto.

4.  Em **Microsoft Entra admin center**, no painel de navegação, expanda
    **Identity** e selecione **Users**.

5.  Selecione **All users** e, na parte superior do painel de
    resultados, selecione **Per-user MFA**. Talvez seja necessário
    selecionar a reticência primeiro para visualizar a opção **Per-user
    MFA**.

> ![A screenshot of a computer Description automatically
> generated](./media/image3.png)

6.  Na página de Multi-factor Authentication, selecione **service
    settings**.

> ![A screenshot of a computer Description automatically
> generated](./media/image4.png)

7.  Role para baixo até a seção de **verification options**.

> Observe os vários métodos que podem ser configurados para verificação
> do usuário.

8.  Na seção **remember multi-factor authentication on trusted device**,
    marque a caixa de seleção ao lado de **Allow users to remember
    multi-factor authentication on devices they trust**.

9.  Ao lado de **Number of days users can trust devices for**, insira
    **30** e selecione **Save**. Selecione **Close** quando solicitado.

> ![](./media/image5.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image6.png)

10. No topo da página, em **multi-factor authentication**, selecione
    **users**.

> ![A screenshot of a computer Description automatically
> generated](./media/image7.png)

11. Na lista de usuários, marque a caixa de seleção ao lado de **Alex
    Wilber.**

12. Na página Alex Wilber, selecione **Enable**.

> ![A screenshot of a computer Description automatically
> generated](./media/image8.png)

13. Na mensagem **About enabling multi-factor auth**, selecione **enable
    multi-factor auth**.

> ![A screenshot of a computer Description automatically
> generated](./media/image9.png)

14. Na mensagem **Updates successful**, selecione **close**. Observe que
    o **Multi-Factor Auth Status** para Alex Wilber agora está
    **Enabled**.

> ![A screenshot of a computer Description automatically
> generated](./media/image10.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image11.png)

15. Feche o Microsoft Edge.

Tarefa 3: Registrar e validar o MFA

1.  Altere para [**SEA-WS3**](urn:gd:lg:a:select-vm). Na barra de
    tarefas, selecione **Microsoft Edge.**

2.  Na barra de endereço, digite
    !\![**outlook.office.com**](urn:gd:lg:a:send-vm-keys)!! e pressione
    Enter.

3.  Na página **Pick an account**, selecione
    !\![**AlexW@M365xXXXXXXX.onmicrosoft.com**](mailto:AlexW@M365xXXXXXXX.onmicrosoft.com)!!

> ![A screenshot of a computer Description automatically
> generated](./media/image12.png)

4.  Na página **Enter password**, digite !!**P@55w.rd1234**!! e
    selecione **Sign in**.

5.  Na página **More information required**, selecione **Next**. A
    página Manter sua conta segura será aberta.

> ![A screenshot of a computer Description automatically
> generated](./media/image13.png)
>
> Normalmente, você usará o aplicativo Microsoft Authenticator para
> gerenciar a Multi-factor Authentication. No entanto, para este cenário
> de laboratório, você usará mensagens de texto.

6.  Na página **Keep your account secure**, selecione **I want to set up
    a different method**.

> ![A screenshot of a computer Description automatically
> generated](./media/image14.png)

7.  Na caixa de diálogo **Choose a different method**, selecione
    **Phone** e, em seguida, selecione **Confirm**.

> ![A screenshot of a computer Description automatically
> generated](./media/image15.png)

8.  Na página **Phone,** insira seu número de celular pelo qual você
    pode receber mensagens de texto e selecione **Next**.

> ![A screenshot of a computer screen Description automatically
> generated](./media/image16.png)

9.  Após receber o código de verificação como mensagem de texto, insira
    o código no local indicado na página **Phone** e selecione **Next**.

> ![](./media/image17.png)

10. Na mensagem de verificação de SMS, selecione **Next** e, em seguida,
    **Done**.

> ![A screenshot of a computer screen Description automatically
> generated](./media/image18.png)
>
> ![](./media/image19.png)

11. Na mensagem Permanecer conectado, selecione **No**.

> ![A screenshot of a computer error Description automatically
> generated](./media/image20.png)
>
> O Outlook na Web abre na caixa de entrada de Alex Wilber.

12. No canto superior direito, selecione **Account manager for Alex
    Wilber** e depois selecione **Sign out**.

> ![](./media/image21.png)
>
> **Observação:** os usuários só precisam se cadastrar na primeira vez
> que usarem o MFA. Os logins subsequentes exigem apenas o fornecimento
> do código de validação enviado por mensagem de texto para o número de
> telefone informado durante o cadastro.

13. Na barra de endereço, digite
    !\![**outlook.office.com**](urn:gd:lg:a:send-vm-keys)!! e pressione
    Enter.

14. Na página **Pick an account**, selecione
    !!**AlexW@M365xXXXXXXXX.onmicrosoft.com**!!

15. Na página **Enter password**, digite !!**P@55w.rd1234**!! e
    selecione **Sign in**.

> ![A screenshot of a computer error Description automatically
> generated](./media/image22.png)
>
> O prompt **Verify your identity** será aberto. Observe que contém os
> dois últimos dígitos do seu número de telefone.

16. No prompt **Verify your identity**, selecione seu número de telefone
    de texto.

17. Na página **Inserir código**, insira o código enviado para seu
    celular e selecione **Verify**.

> ![A screenshot of a computer error message Description automatically
> generated](./media/image23.png)
>
> Observe que você pode marcar uma caixa de seleção para não solicitar
> verificação novamente por 30 dias.

18. Como o **Microsoft Authenticator App** garante mais segurança e uma
    experiência tranquila, você será solicitado a configurá-lo, por
    enquanto clique em **Skip for now**

> ![A screenshot of a computer error Description automatically
> generated](./media/image24.png)

19. Na mensagem Permanecer conectado, selecione **No**. O Outlook na Web
    abre na caixa de entrada de Alex Wilber.

> ![A screenshot of a computer error Description automatically
> generated](./media/image25.png)

20. No canto superior direito, selecione **Account manager for Alex
    Wilber** e depois selecione **Sign out**.

> ![A computer screen shot of a computer screen Description
> automatically generated](./media/image26.png)

21. Feche o Microsoft Edge.

Tarefa 3: Remover MFA por usuário

1.  Altere para [**SEA-SVR1**](urn:gd:lg:a:select-vm). No
    [**SEA-SVR1**](urn:gd:lg:a:select-vm), se necessário, faça login
    como
    [**[Contoso\Administrator](urn:gd:lg:a:send-vm-keys)**](urn:gd:lg:a:send-vm-keys)
    com a senha !\![**Pa55w.rd**](urn:gd:lg:a:send-vm-keys)!! e feche o
    **Server Manager**.

2.  Na barra de tarefas, selecione **Microsoft Edge** e navegue até o
    **Microsoft Entra admin center** !!**https://Entra.Microsoft.com**!!

3.  Entre com credenciais de **Office 365 Tenant admin.**

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)
>
> O **Microsoft Entra admin center** é aberto.

4.  Em **Microsoft Entra admin center**, no painel de navegação, expanda
    **Identity** e selecione **Users**.

5.  Selecione **Todos os usuários** e, na parte superior do painel de
    resultados, selecione **Per-user MFA**. Talvez seja necessário
    selecionar a reticência primeiro para visualizar a opção **Per-user
    MFA**.

> ![A screenshot of a computer Description automatically
> generated](./media/image3.png)

6.  No topo da página, em **multi-factor authentication**, selecione
    **users**.

7.  Na lista de usuários, marque a caixa de seleção ao lado de **Alex
    Wilber**.

> Observe que o **Multi-Factor Auth Status** de Alex Wilber agora está
> definido como **Enforced** (anteriormente, estava definido como
> Habilitado). Isso ocorre porque Alex se registrou e está usando a MFA.
>
> ![A screenshot of a computer Description automatically
> generated](./media/image27.png)

8.  Na página Alex Wilber, selecione **Manage user settings.**

> ![A screenshot of a computer Description automatically
> generated](./media/image28.png)

9.  Na caixa Gerenciar configurações do usuário, marque a caixa de
    seleção ao lado de todas as três opções, selecione **save** e, em
    seguida, selecione **close**.

> ![A screenshot of a computer Description automatically
> generated](./media/image29.png)
>
> Essas opções removerão todas as configurações de MFA salvas para Alex.
>
> ![A white rectangular frame with black border Description
> automatically generated](./media/image30.png)

10. Na lista de usuários, marque a caixa de seleção ao lado de **Alex
    Wilber.**

11. Na página Alex Wilber, selecione **Disable**.

> ![A screenshot of a computer Description automatically
> generated](./media/image31.png)

12. Na mensagem **Disable multi-factor authentication**, selecione
    **yes**.

> ![](./media/image32.png)

13. Na mensagem **Updates successful**, selecione **close**.

> ![A white screen with black text Description automatically
> generated](./media/image33.png)
>
> Observe que o **Multi-Factor Auth Status** para Alex Wilber agora está
> **Disabled**.
>
> ![A screenshot of a computer Description automatically
> generated](./media/image34.png)

14. Feche o Microsoft Edge.

**Resultados:** Após concluir este exercício, você terá configurado com
sucesso a Multi-factor Authentication por usuário.

Exercício 2: Configurar Multi-factor Authentication usando acesso
condicional

**Cenário**

Para fornecer segurança adicional aos eventos de login do usuário, você
precisa configurar e testar a multi-factor authentication (MFA). Você
decide usar uma política de acesso condicional que oferece maior
flexibilidade para seus requisitos de MFA. Alex Wilber concordou em
validar as configurações para você.

Tarefa 1: validar o login antes de habilitar o acesso condicional com
MFA

1.  Altere e faça login no [**SEA-WS3**](urn:gd:lg:a:select-vm) como
    !\![**Admin**](urn:gd:lg:a:send-vm-keys)!! com a senha
    !\![**Pa55w.rd**](urn:gd:lg:a:send-vm-keys)!!

2.  Na barra de tarefas, selecione **Microsoft Edge.** Na barra de
    endereços, digite
    !\![**outlook.office.com**](urn:gd:lg:a:send-vm-keys)!! e pressione
    Enter.

3.  Na página **Sign in**, digite
    !!**AlexW@M365xXXXXXXX.onmicrosoft.com**!! e então selecione
    **Next**.

4.  Na página **Enter password**, digite !!**P@55w.rd1234**!! e
    selecione **Sign in**. No prompt Salvar senha do Edge, selecione
    **Save**.

> O Outlook na Web é aberto. Observe que apenas a senha foi necessária
> para entrar no Outlook na Web.

5.  No canto superior direito, selecione **Account manager for Alex
    Wilber** e depois selecione **Sign out**.

> ![A screenshot of a computer Description automatically
> generated](./media/image1.png)

6.  Feche o Microsoft Edge.

Tarefa 2: Configurar acesso condicional com MFA

1.  Altere para [**SEA-SVR1**](urn:gd:lg:a:select-vm). No
    [**SEA-SVR1**](urn:gd:lg:a:select-vm), se necessário, faça login
    como
    [**[Contoso\Administrator](urn:gd:lg:a:send-vm-keys)**](urn:gd:lg:a:send-vm-keys)
    com a senha !\![**Pa55w.rd**](urn:gd:lg:a:send-vm-keys)!! e feche o
    **Server Manager**.

2.  Na barra de tarefas, selecione **Microsoft Edge** e navegue até o
    **Microsoft Entra admin center** !!**https://Entra.Microsoft.com**!!

3.  Entre com as credenciais **Office 365 Tenant admin.**

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)
>
> O **Microsoft Entra admin center** é aberto.

4.  No **Microsoft Entra admin center**, no painel de navegação, expanda
    **Identity**, depois **Protection** e, por fim, **Conditional
    Access.**

> ![A screenshot of a computer Description automatically
> generated](./media/image35.png)

5.  Na página **Conditional Access**, selecione **Policies** e, em
    seguida, **+ New policy**.

> ![A screenshot of a computer Description automatically
> generated](./media/image36.png)

6.  Na página **New Conditional access policy**, na caixa **Name**,
    digite !\![**Contoso MFA Policy**](urn:gd:lg:a:send-vm-keys)!!.

7.  Em **Assignments**, selecione **0 users or workload identities
    selected**.

> ![A screenshot of a computer Description automatically
> generated](./media/image37.png)

8.  No painel Usuários e grupos, selecione a opção ao lado de **Select
    users and groups** e marque a caixa de seleção ao lado de **Users
    and groups**.

9.  Na página **Select**, selecione **Alex Wilber** e clique em
    **Select**.

> ![A screenshot of a computer Description automatically
> generated](./media/image38.png)
>
> Observe que normalmente você especificaria um grupo, no entanto, para
> este exercício, testaremos apenas a configuração em Alex Wilber.

10. Selecione **No target resources selected** em Recursos de destino e
    clique em **Select apps**.

> ![A screenshot of a computer Description automatically
> generated](./media/image39.png)

11. Na página **Select**, marque a caixa de seleção ao lado de **Office
    365** e clique em **Select**.

> ![A screenshot of a computer Description automatically
> generated](./media/image40.png)

12. Em **Access controls**, na seção **Grant**, selecione **0 controls
    selected**.

> ![A screenshot of a computer Description automatically
> generated](./media/image41.png)

13. Na página **Grant**, selecione **Grant access**, marque a caixa de
    seleção ao lado de **Require multi-factor authentication** e clique
    em **Select**.

> ![A screenshot of a computer Description automatically
> generated](./media/image42.png)

14. Em **Enable policy**, selecione **On**.

15. Selecione **Create** para criar a Política de MFA da Contoso.
    Observe que a política está listada com o Estado **On.**

> ![A screenshot of a computer Description automatically
> generated](./media/image43.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image44.png)

16. Em **Microsoft Entra admin center**, selecione **Users**. Na lista
    Usuários, selecione **Alex Wilber**.

> ![A screenshot of a computer Description automatically
> generated](./media/image45.png)

17. Na página Alex Wilber, selecione **Authentication methods**.

> ![](./media/image46.png)
>
> Observe que um número de telefone já foi configurado para Alex,

18. Feche o Microsoft Edge.

Tarefa 3: Validar o MFA de acesso condicional

1.  Altere para [**SEA-WS3**](urn:gd:lg:a:select-vm). Na barra de
    tarefas, selecione **Microsoft Edge.**

2.  Na barra de endereço, digite
    !\![**outlook.office.com**](urn:gd:lg:a:send-vm-keys)!! e pressione
    Enter.

3.  Na página **Pick an account**, selecione
    !!**AlexW@M365xXXXXXXX.onmicrosoft.com**!!

> ![A screenshot of a computer Description automatically
> generated](./media/image12.png)

4.  Na página **Enter password**, digite !!**P@55w.rd1234**!! e
    selecione **Sign in**.

5.  No prompt **Verify your identity**, selecione seu número de telefone
    para mensagem de texto.

> ![A screenshot of a computer error Description automatically
> generated](./media/image22.png)

6.  Na página **Enter code**, insira o código enviado para seu celular e
    selecione **Verify**.

> ![A screenshot of a computer error message Description automatically
> generated](./media/image23.png)
>
> Observe que você pode marcar uma caixa de seleção para não solicitar
> verificação novamente por 30 dias.

7.  Na mensagem Permanecer conectado, selecione **No**. O Outlook na Web
    será aberto na caixa de entrada de Alex Wilber.

> ![A screenshot of a computer error Description automatically
> generated](./media/image25.png)

8.  No canto superior direito, selecione **Account manager for Alex
    Wilber** e depois selecione **Sign out**.

> ![A computer screen shot of a computer screen Description
> automatically generated](./media/image26.png)

9.  Feche o Microsoft Edge.

Tarefa 4: Remover o MFA de acesso condicional

1.  Altere para [**SEA-SVR1**](urn:gd:lg:a:select-vm). No
    [**SEA-SVR1**](urn:gd:lg:a:select-vm), se necessário, faça login
    como
    [**[Contoso\Administrator](urn:gd:lg:a:send-vm-keys)**](urn:gd:lg:a:send-vm-keys)
    com a senha !\![**Pa55w.rd**](urn:gd:lg:a:send-vm-keys)!! e feche o
    **Server Manager**.

2.  Na barra de tarefas, selecione **Microsoft Edge** e navegue até o
    **Microsoft Entra admin center** !!**https://Entra.Microsoft.com**!!

3.  Entre com credenciais do **Office 365 Tenant admin.**

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)
>
> O **Microsoft Entra admin center** é aberto.

4.  No **Microsoft Entra admin center**, no painel de navegação, expanda
    **Identity**, depois **Protection** e, por fim, **Conditional
    Access.**

> ![A screenshot of a computer Description automatically
> generated](./media/image35.png)

5.  Na página **Conditional Access,** selecione **Policies** e, em
    seguida, selecione **Contoso MFA Policy**.

6.  Na página **Contoso MFA Policy**, selecione **Delete** e, em
    seguida, selecione **Delete**.

> ![A screenshot of a computer Description automatically
> generated](./media/image47.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image48.png)

7.  Para confirmar a exclusão, clique no botão **Delete**.

> ![A screenshot of a computer error Description automatically
> generated](./media/image49.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image50.png)

8.  Feche o Microsoft Edge.

**Resultados:** Após concluir este exercício, você terá configurado com
sucesso a Multi-factor Authentication usando uma política de acesso
condicional.
