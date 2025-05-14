Laboratório 23: Gerenciando atualizações de qualidade e de recursos do
Windows

**Resumo**

Neste laboratório, você configurará as definições de atualizações de
qualidade e de recursos do Windows usando o Intune.

**Pré-requisitos**

Os seguintes laboratórios devem ser concluídos antes deste laboratório:

- Laboratório 01 - Gerenciando Identidades no Microsoft Entra ID

- Laboratório 06 - Registro de dispositivos no Microsoft Intune

- Laboratório 07 - Criação e implementação de perfis de configuração

**Observação:** você também precisará de um celular que possa receber
mensagens de texto usadas para proteger a autenticação de entrada do
Windows Hello no Azure AD.

**Cenário**

Você foi solicitado a configurar um anel de atualização para afetar
apenas os dispositivos que são membros do grupo Contoso Developer
Devices. Esse grupo deve atender aos seguintes requisitos:

- Período de adiamento da atualização de qualidade (dias): **15**

- Período de adiamento da atualização de recursos (dias): **45**

- Opção para pausar atualizações do Windows: **Desativar**

- Opção para verificar atualizações do Windows: **Habilitar**

- Otimização de entrega: Modo de download: **somente HTTP, sem
  pareamento (0)**

Tarefa 1: verificar as configurações de atualização atuais para um único
dispositivo

1.  Altere para [***SEA-WS1***](urn:gd:lg:a:select-vm), faça login como
    **Cindy White** com o PIN [**102938**](urn:gd:lg:a:select-vm).

2.  Selecione **Start** e depois selecione o ícone **Settings.**

> ![](./media/image1.png)

3.  Em **Settings**, selecione **Windows Update.**

> Observe que você tem a opção de pausar as atualizações por um período
> específico.

4.  Na página do **Windows Update**, selecione **Advanced options**.

> ![](./media/image2.png)

5.  Na página **Advanced options,** selecione **Delivery Optimization**.

> ![A screenshot of a computer Description automatically
> generated](./media/image3.png)

6.  Na página **Delivery Optimization**, verifique se a opção **Allow
    downloads from other PCs** está habilitada.

7.  Selecione **Devices on the internet and my local network**.

> ![A screenshot of a computer Description automatically
> generated](./media/image4.png)

8.  Em **Settings**, selecione **Windows Update.**

> ![A screenshot of a computer Description automatically
> generated](./media/image5.png)

9.  Selecione **Advanced options** e, em seguida, **Configured update
    policies**.

> ![A screenshot of a computer Description automatically
> generated](./media/image6.png)
>
> Observe que nenhuma política de atualização está definida no
> dispositivo.
>
> ![A screenshot of a computer Description automatically
> generated](./media/image7.png)

10. No painel de navegação, selecione **Windows Update**.

Tarefa 2: Review applied settings

1.  Na página do **Windows Update**, selecione **Update history**.

> ![A screenshot of a computer update Description automatically
> generated](./media/image8.png)

2.  Revise as atualizações listadas e selecione **Uninstall updates**.

> ![A screenshot of a computer update Description automatically
> generated](./media/image9.png)

3.  Revise as atualizações listadas em **Installed Updates**. Feche as
    Atualizações Instaladas.

> ![A screenshot of a computer Description automatically
> generated](./media/image10.png)

4.  Feche o aplicativo **Settings.**

Tarefa 3: Configurar as definições de atualização usando o Intune

1.  Altere para [***SEA-SVR1***](urn:gd:lg:a:send-vm-keys) e faça login
    como
    [**[Contoso\Administrator](urn:gd:lg:a:send-vm-keys)**](urn:gd:lg:a:send-vm-keys)
    com a senha [**Pa55w.rd**](urn:gd:lg:a:send-vm-keys) .

2.  Na barra de tarefas, selecione **Microsoft Edge**.

3.  No Microsoft Edge, digite
    [**https://intune.microsoft.com**](urn:gd:lg:a:send-vm-keys) na
    barra de endereço e pressione **Enter.**

4.  Entre como
    [**admin@M365x19242953.onmicrosoft.com**](urn:gd:lg:a:send-vm-keys)
    com a senha.

5.  No painel de navegação, selecione **Devices** e depois selecione
    **Windows 10 and later Updates**.

> ![](./media/image11.png)

6.  No painel **Devices | Update rings for Windows 10 and later,**
    selecione **Create profile**.

> ![](./media/image12.png)

7.  No painel **Basics**, insira as seguintes informações e selecione
    **Next**:

    - Name: !\![**Contoso Updates -
      standard**](urn:gd:lg:a:send-vm-keys)!!

    - Description: !\![**Standard Windows updates
      configuration**](urn:gd:lg:a:select-vm)!!

> ![](./media/image13.png)

8.  No painel **Update ring settings**, insira as seguintes informações
    e selecione **Next**:

    - Quality update deferral period
      (days): [**15**](urn:gd:lg:a:send-vm-keys)

    - Feature update deferral period
      (days): [**45**](urn:gd:lg:a:send-vm-keys)

    - Option to pause Windows updates: **Disable**

    - Option to check for Windows updates: **Enable**

> ![](./media/image14.png)

9.  No painel **Assignments**, em **Included groups,** selecione **Add
    groups**.

10. No painel **Select groups to include**, na caixa **Search**,
    selecione **Contoso Developer devices** e, em seguida, selecione
    **Select**.

> ![A screenshot of a computer Description automatically
> generated](./media/image15.png)
>
> ![](./media/image16.png)

11. Selecione **Next** e no painel **Review + create** selecione
    **Create**.

12. Na barra de navegação, selecione **Configuration profiles**.

13. No painel **Devices | Configuration,** no painel de detalhes,
    selecione **Create policy**.

> ![](./media/image17.png)

14. No painel **Create a profile**, selecione as seguintes opções e, em
    seguida, selecione **Create**:

    - Platform: **Windows 10 and later**

    - Profile type: **Templates**

    - Template name: **Delivery Optimization**

> ![](./media/image18.png)

15. No painel **Basics**, insira as seguintes informações e selecione
    **Next**:

    - Name: !\![**Contoso Developer - Delivery
      optimization**](urn:gd:lg:a:send-vm-keys)!!

    - Description: !\![**Delivery optimization for
      Developer**](urn:gd:lg:a:send-vm-keys)!!

> ![](./media/image19.png)

16. No painel **Configuration settings**, insira as seguintes
    informações e selecione **Next**:

    - Modo de download: **HTTP only, no peering (0)**

> ![A screenshot of a computer Description automatically
> generated](./media/image20.png)

17. No painel **Assignments**, em **Included groups,** selecione **Add
    groups**.

18. No painel **Select groups to include**, selecione **Contoso
    Developer devices** e, em seguida, selecione **Select**.

> ![A screenshot of a computer Description automatically
> generated](./media/image21.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image22.png)

19. Selecione **Next** duas vezes e, no painel **Review + create,**
    selecione **Create**.

> ![Screenshot](./media/image23.png)

Tarefa 4: Verifique se as definições de atualização do dispositivo são
gerenciadas centralmente

1.  Altere para [***SEA-WS1***](https://intune.microsoft.com) .

2.  Selecione **Start** e depois selecione o ícone **Settings.**

> ![](./media/image24.png)

3.  No aplicativo **Settings**, selecione **Accounts** e depois
    selecione **Access work or school**.

> ![A screenshot of a computer Description automatically
> generated](./media/image25.png)

4.  Na seção **Access work or school**, selecione o link **Connected to
    Contoso's Azure AD** e, em seguida, selecione **Info**.

> ![A screenshot of a computer Description automatically
> generated](./media/image26.png)

5.  Na caixa de diálogo **Areas Managed by Contoso**, selecione
    **Sync**. Aguarde a conclusão da sincronização.

> ![A screenshot of a computer Description automatically
> generated](./media/image27.png)

6.  No aplicativo **Settings**, selecione **Windows Update**.

> Observe que você não pode pausar atualizações.

7.  Selecione **Advanced options**.

> ![](./media/image28.png)

8.  Selecione **Delivery Optimization**.

> ![A screenshot of a computer Description automatically
> generated](./media/image29.png)
>
> Observe que **Allow downloads from other PCs** não está disponível.

9.  No aplicativo **Settings**, selecione **Windows Update,** selecione
    **Advanced options** e, em seguida, selecione **Configured update
    policies**.

> ![](./media/image30.png)
>
> Anote todas as políticas definidas no dispositivo.

10. Feche todos os aplicativos e janelas que foram abertos.

> **Observação:** O ambiente de laboratório é configurado para impedir
> que as atualizações do Windows sejam aplicadas para evitar atrasos e
> impactos não intencionais durante os laboratórios.
