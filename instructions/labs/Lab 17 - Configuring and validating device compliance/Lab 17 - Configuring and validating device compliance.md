Laboratório 17 - Configurando e validando a conformidade do dispositivo

**Resumo**

Neste laboratório, você valida a conformidade do dispositivo
configurando uma política de conformidade e uma regra de acesso
condicional associada usada para determinar o status de um dispositivo
gerenciado.

**Pré-requisitos**

Os seguintes laboratórios devem ser concluídos antes deste laboratório:

- Laboratório nº 1 - **Gerenciando Identidades no Microsoft Entra ID**

- Laboratório nº 2 - **Sincronizando Identidades usando o Microsoft
  Entra Connect**

- Laboratório nº 5 - **Gerenciar registro de dispositivos no Microsoft
  Intune**

- Laboratório nº 6 - **Registro de dispositivos no Microsoft Intune**

- Laboratório nº 7 - **Criação e implementação de perfis de
  configuração**

Exercício 1: Configurando políticas de conformidade.

**Cenário**

A Contoso gostaria de garantir que os dispositivos Windows registrados
no Microsoft Intune atendam a uma especificação mínima de configuração.
As seguintes especificações são necessárias:

- Versão mínima do sistema operacional Windows: 10.0.19041.329

- É necessário o Microsoft Defender Antimalware.

Se um dispositivo atender a esses requisitos, ele será marcado como
compatível. Se não atender, deverá ser marcado como não compatível.

Tarefa 1: Criar e atribuir uma política de conformidade

1.  Entre no [***SEA-SVR1***](urn:gd:lg:a:select-vm) como
    !!**[Contoso\Administrator](urn:gd:lg:a:send-vm-keys)!!** com a
    senha !!**[Pa55w.rd](urn:gd:lg:a:send-vm-keys)!!** 

2.  Na barra de tarefas, selecione **Microsoft Edge**. No Microsoft
    Edge, digite !!**https://Intune.microsoft.com!!** na barra de
    endereços e pressione **Enter.**

3.  Entre com **Office 365 Tenant Admin credentials**.

> ![A screenshot of a computer Description automatically
> generated](./media/image1.png)

4.  No painel de navegação, selecione **Devices** e, em seguida,
    **Compliance** em Gerenciar dispositivos.

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)

5.  No painel **Compliance | Policies**, no painel de detalhes,
    selecione **+ Create Policy**.

> ![A screenshot of a computer Description automatically
> generated](./media/image3.png)

6.  No painel **Create a policy**, forneça o seguinte valor e selecione
    **Create**:

    - Plataforma: **Windows 10 and later**

> ![A screenshot of a computer Description automatically
> generated](./media/image4.png)

7.  Na aba **Basics**, forneça o seguinte valor e selecione **Next**:

    - Nome: !!**[Compliance1](urn:gd:lg:a:send-vm-keys)!!**

> ![](./media/image5.png)

8.  Na aba **Compliance settings**, expanda **Device Health** e revise
    as configurações disponíveis.

> ![A screenshot of a computer Description automatically
> generated](./media/image6.png)

9.  Na aba **Compliance settings**, expanda **Device Properties**. No
    campo **Minimum OS version**, digite
    !!**[10.0.19041.329](urn:gd:lg:a:send-vm-keys)!!**

> ![A screenshot of a computer Description automatically
> generated](./media/image7.png)

10. Na aba **Compliance settings**, expanda **System Security**. Defina
    a configuração **Microsoft Defender Antimalware** e selecione
    **Next**.

> ![](./media/image8.png)

11. Na guia **Actions for noncompliance**, observe que a ação para
    **Mark device noncompliant** como não compatível é definida como
    **immediately**.

> ![A screenshot of a computer Description automatically
> generated](./media/image9.png)
>
> Veja como você pode configurar o número de dias após os quais o
> dispositivo será marcado como não compatível e configurar ações
> adicionais.

12. Selecione **Next**. Na aba **Assignments**, selecione **Add
    groups**. Selecione **Windows Devices**, escolha **Select** e, em
    seguida, **Next**.

> ![A screenshot of a computer Description automatically
> generated](./media/image10.png)
>
> **Observação**: O grupo **Windows Devices** foi criado em Criação e
> implantação de perfis de configuração - Laboratório.

13. Selecione **Create**.

> ![A screenshot of a computer Description automatically
> generated](./media/image11.png)

14. No menu de navegação, selecione **Devices** e, em seguida, no painel
    de navegação Dispositivos, selecione **Compliance**.

> ![A screenshot of a computer Description automatically
> generated](./media/image12.png)

15. Na página **Compliance**, selecione **Compliance settings**.

> ![A screenshot of a computer Description automatically
> generated](./media/image13.png)

16. Na página **Compliance policy settings**, ao lado de **Mark devices
    with no compliance policy assigned as**, selecione **Not Compliant**
    e, em seguida, selecione **Save**.

> ![A screenshot of a computer Description automatically
> generated](./media/image14.png)
>
> Esta configuração garantirá que qualquer dispositivo que não tenha uma
> política de conformidade atribuída seja definido como **Not
> compliant**.

**Resultados:** Após concluir este exercício, você terá configurado com
sucesso uma política de conformidade.

Exercício 2: Criando uma política de acesso condicional para impor
conformidade.

**Cenário**

Quando um usuário utiliza um dispositivo marcado como não compatível,
ele não deve conseguir acessar seu e-mail. Foi solicitado que você
configure uma política de acesso condicional que imponha essa regra e
verifique se ela funciona conforme o esperado.

Tarefa 1: Criar uma política de acesso condicional

1.  Em [***SEA-SVR1***](urn:gd:lg:a:select-vm), no **Microsoft Intune
    admin center,** selecione **Devices** e, em seguida, **Conditional
    access**.

> ![A screenshot of a computer Description automatically
> generated](./media/image15.png)

2.  Clique em **Policies** e selecione **+ New policy**,

> ![A screenshot of a computer Description automatically
> generated](./media/image16.png)

3.  No painel **New**, na caixa de texto **Name**, digite
    !\![**Conditional1!!  **](urn:gd:lg:a:send-vm-keys)e então selecione
    **0 users or workload identities selected**.

> ![A screenshot of a computer Description automatically
> generated](./media/image17.png)

4.  No painel **Users and groups**, selecione o botão de opção **All
    users**.

> ![A screenshot of a computer screen Description automatically
> generated](./media/image18.png)

5.  No painel **New**, selecione **No target resources selected**,
    selecione o botão de opção **Select apps**, selecione !!**Office 365
    Exchange Online!!** e clique em **Select**.

> ![A screenshot of a computer Description automatically
> generated](./media/image19.png)

6.  No painel **New**, na seção **Conditions**, selecione **0 conditions
    selected**.

> ![A screenshot of a computer Description automatically
> generated](./media/image20.png)

7.  Na lista de condições, em **Device platforms**, selecione **Not
    configured**. Na seção **Configure,** selecione **Yes**, marque o
    botão de opção **Select device platforms**, marque a caixa de
    seleção **Windows** e, em seguida, selecione **Done**.

> ![A screenshot of a computer Description automatically
> generated](./media/image21.png)

8.  No painel **New,** em **Access controls**, na seção **Grant**,
    selecione **0 controls selected**.

9.  Marque a caixa de seleção **Require device to be marked as
    compliant** e, em seguida, selecione **Select**.

> ![A screenshot of a computer Description automatically
> generated](./media/image22.png)

10. No painel **New**, selecione **On** para a opção **Enable policy** e
    depois selecione **Create**.

> ![A screenshot of a computer Description automatically
> generated](./media/image23.png)

11. Feche o Microsoft Edge.

Tarefa 2: Verificar se a política de acesso condicional está funcionando

1.  Altere para [***SEA-WS3***](urn:gd:lg:a:select-vm) e faça login como
    !!**[Admin](urn:gd:lg:a:send-vm-keys)!!** com a senha
    !!**[Pa55w.rd](urn:gd:lg:a:send-vm-keys)!!**.

2.  Em [***SEA-WS3***](urn:gd:lg:a:select-vm), na barra de tarefas,
    selecione **Microsoft Edge.** No Microsoft Edge, digite
    [**outlook.office.com**](urn:gd:lg:a:send-vm-keys) e pressione
    Enter.

3.  Na caixa de diálogo Escolher uma conta, selecione
    !!**Cindy@M365xXXXXXXX.onmicrosoft.com!!**

4.  Na página **Enter password**, digite !!**P@55w.rd12345!!** e
    selecione **Sign in**. Se a solicitação Salvar senha do Microsoft
    Edge for exibida, selecione **Update**.

> ![A screenshot of a computer error Description automatically
> generated](./media/image24.png)

5.  Verifique se você recebeu a mensagem **"Sign in with your work
    account"**.

> ![A screenshot of a computer Description automatically
> generated](./media/image25.png)

6.  Selecione **More details**. Você verá mais informações sobre o
    motivo do seu bloqueio.

> ![A screenshot of a computer error Description automatically
> generated](./media/image26.png)
>
> **Observação:** Isso ocorre porque o SEA-WS3 não está associado ao
> Microsoft Entra ID e não é gerenciado pelo Microsoft Intune, portanto,
> não é marcado como compatível.

7.  **Close** a janela do navegador.

8.  Altere para [***SEA-WS1***](urn:gd:lg:a:select-vm) e faça login como
    !!**Cindy@M365xXXXXXXX.onmicrosoft.com!!** para a página
    **password**, digite !!**P@55w.rd12345!!** 

> **Observação:** SEA-WS1 é um dispositivo Windows 11 gerenciado que
> está registrado no Intune.

9.  Na barra de tarefas, selecione **Microsoft Edge**. No Microsoft
    Edge, digite
    [**[Outlook.office.com](urn:gd:lg:a:send-vm-keys)**](urn:gd:lg:a:send-vm-keys)
    e pressione **Enter.**

10. Verifique se você consegue acessar a caixa de correio de Cindy.

> ![A screenshot of a computer Description automatically
> generated](./media/image27.png)
>
> **Observação**: Isso ocorre porque o **SEA-WS1** é um dispositivo
> gerenciado e marcado como compatível.

11. Feche o Microsoft Edge e saia do
    [***SEA-WS1***](urn:gd:lg:a:select-vm).

Tarefa 3: Desabilitar a política de acesso condicional

1.  No [***SEA-SVR1***](urn:gd:lg:a:select-vm), no **Microsoft Intune
    admin center** !\!<https://intune.microsoft.com>!! selecione
    **Devices** e, em seguida, selecione **All devices**.

> ![](./media/image28.png)
>
> Observe que o **SEA-WS1** é compatível, e é por isso que Cindy teve
> permissão para acessar sua caixa de correio.

2.  No painel de navegação, selecione **Devices** e, em seguida,
    **Conditional access**.

> ![](./media/image29.png)

3.  Na página **Conditional Access**, selecione **Policies** e clique em
    **Conditional1**.

> ![A screenshot of a computer Description automatically
> generated](./media/image30.png)

4.  Na página **Conditional1**, na parte inferior da página, selecione
    **Off** e depois **Save**.

> ![A screenshot of a computer Description automatically
> generated](./media/image31.png)

5.  Feche o Microsoft Edge.

**Resultados:** Após concluir este exercício, você terá configurado com
sucesso uma política de acesso condicional para determinar a
conformidade do dispositivo.
