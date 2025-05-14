**Laboratório 11 - Monitorar a atividade do dispositivo e do usuário no
Intune**

**Resumo**

Neste laboratório, você monitorará a atividade de login do usuário, logs
de auditoria e atividade do dispositivo.

**Pré-requisitos**

Os seguintes laboratórios devem ser concluídos antes deste laboratório:

- Laboratório nº 1 - Gerenciando Identidades no Microsoft Entra ID

- Laboratório nº 2 - Sincronizando Identidades usando o Microsoft Entra
  Connect

- Laboratório nº 5 - Gerenciar registro de dispositivos no Microsoft
  Intune

- Laboratório nº 6 - Registro de dispositivos no Microsoft Intune

- Laboratório nº 7 - Criação e implementação de perfis de configuração

**Observação:** você também precisará de um telefone celular que possa
receber mensagens de texto usadas para proteger a autenticação de login
do Windows Hello no Microsoft Entra ID.

**Cenário**

Você precisa revisar a atividade de login da Cindy White e as
informações gerais fornecidas pelos logs de auditoria. Você também
precisa verificar o hardware no
[*SEA-WS1*](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10)
e confirmar se o perfil de configuração atribuído a este dispositivo foi
aplicado com sucesso.

**Tarefa 1: Monitorar a atividade do usuário**

1.  Altere para
    *[SEA-SVR1](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10)*
    e faça login com as credenciais fornecidas, se necessário.

2.  Na página do **Microsoft Entra admin center**, navegue e selecione
    **Users** e clique em **All users**.

> ![](./media/image1.png)

3.  Na página **Users**, navegue e selecione **Allan Deyoung**.

> ![](./media/image2.png)

4.  Na página do usuário **Allan Deyoung**, navegue e clique em
    **Sign-in logs**.

> ![A screenshot of a computer Description automatically
> generated](./media/image3.png)

5.  Na página **Allan Deyoung | Sign-in logs**, clique na primeira
    entrada na aba **User sign-ins (interactive)**.

> ![A screenshot of a computer Description automatically
> generated](./media/image4.png)

6.  Selecione cada uma das páginas principais, incluindo **Basic
    info**, **Location**, **Device info**, **Authentication Details** e
    **Conditional Access**. Role para baixo e examine as informações em
    cada página. Após revisar cuidadosamente as informações fornecidas
    em cada página, feche o painel.

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

7.  No painel de Users navigation, selecione **Audit logs**.

8.  No painel de detalhes, são exibidas informações de auditoria sobre
    alterações administrativas para usuários. Examine as informações
    selecionando as diversas entradas.

> ![A screenshot of a computer Description automatically
> generated](./media/image10.png)
>
> ![](./media/image11.png)

**Tarefa 2: Monitorar a atividade do dispositivo**

1.  Altere para a janela do **Microsoft Intune admin center**, navegue e
    clique em **Devices**.

![](./media/image12.png)

2.  No painel de navegação Dispositivos, selecione **Overview**.

> ![A screenshot of a computer Description automatically
> generated](./media/image13.png)

3.  Role para baixo e revise o seguinte:

- Configuration policy assignment failures

- Noncompliant devices.

- Deployment status per Windows update ring.

> ![](./media/image14.png)

4.  Role para baixo até a seção **Manage devices** e clique em
    **Configuration**. Revise os detalhes da configuração.

> ![](./media/image15.png)

5.  Role para cima e selecione **All devices**. Na página **Devices |
    All devices,** são exibidas informações sobre os dispositivos, como
    Device name, Managed by, Ownership, Compliance, OS e OS version.
    Clique em **SEA-WS1**.

> ![](./media/image16.png)

6.  No painel de navegação SEA-WS1, selecione **Hardware** e examine o
    inventário de hardware.

> ![A screenshot of a computer Description automatically
> generated](./media/image17.png)

7.  No painel de navegação SEA-WS1, selecione **Discovered apps** e
    examine o inventário de aplicativos.

> ![A screenshot of a computer Description automatically
> generated](./media/image18.png)

8.  No painel de navegação do SEA-WS1, selecione **Device
    configuration** e, no painel de detalhes, anote os perfis de
    configuração atribuídos ao dispositivo. A coluna **State** deve
    exibir **Succeeded**, o que significa que os perfis foram aplicados
    com sucesso ao dispositivo.

> ![](./media/image19.png)

9.  Na página **SEA-WS1 | Device configuration**, clique em **Contoso
    Developer – standard**.

> ![](./media/image20.png)

10. No painel **Contoso Developer – standard**, anote cada configuração
    que você configurou no perfil.

> O **State** deve exibir **Succeeded** ao lado de todos eles.
>
> ![](./media/image21.png)

**Resultados:** Após concluir este exercício, você terá monitorado com
sucesso a atividade de login do usuário, os registros de auditoria e a
atividade do dispositivo.
