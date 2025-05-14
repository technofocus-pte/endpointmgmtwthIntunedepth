**Laboratório 9 - Usando um perfil de configuração para definir as
configurações de Wi-Fi do iOS e iPadOS**

**Resumo**

Neste laboratório, usaremos o Microsoft Intune para criar e aplicar um
perfil de configuração para executar as configurações de Wi-Fi para
dispositivos iOS e iPadOS.

**Exercício 1: Criando um perfil de configuração.**

**Cenário**

Foi solicitado que você crie um perfil de configuração para configurar
automaticamente as configurações de Wi-Fi dos dispositivos iOS e iPadOS
registrados. Você precisa garantir que as configurações de Wi-Fi estejam
configuradas da seguinte forma:

- Nome da rede: **Contoso Wi-Fi**

- SSID: **MainOffice**

- Conectar automaticamente: **Habilitar**

- Tipo de segurança: **WPA/WPA2-Personal**

- Chave pré-compartilhada: **ContosoWiFi123**

- Atribuído a: **Um novo grupo de segurança chamado Dispositivos
  iOS_iPadOS**

**Tarefa 1: Criar o grupo de dispositivos iOS_iPadOS**

1.  Altere para
    *[SEA-SVR1](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10).*
    Na janela do **Microsoft Entra admin center**, navegue e selecione
    **Groups** e clique em **All groups**.

> ![A screenshot of a computer Description automatically
> generated](./media/image1.png)

2.  No painel **Groups | All groups**, selecione **New group**.

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)

3.  No painel **New Group**, insira as seguintes informações e clique no
    botão **Create**, conforme mostrado na imagem abaixo:

    - Group type: **Security**

    - Group name: !!**iOS_iPadOS Devices**!!

    - Group description: !!**All iOS and iPadOS devices**!!

    - Membership type: **Assigned**

> ![A screenshot of a group Description automatically
> generated](./media/image3.png)

4.  No painel **Groups | All groups**, atualize a página e verifique se
    o grupo **iOS_iPadOS Devices** é exibido.

> ![A screenshot of a computer Description automatically
> generated](./media/image4.png)

**Tarefa 2: Criar um perfil de configuração com base nos requisitos do
cenário**

1.  Mude para a aba do **Microsoft Intune admin center** e selecione
    **Devices** na barra de navegação.

> ![A screenshot of a computer Description automatically
> generated](./media/image5.png)

2.  Na página **Devices | Overview**, selecione **iOS/iPadOS,** conforme
    mostrado na imagem abaixo.

> ![A screenshot of a computer Description automatically
> generated](./media/image6.png)

3.  Na página **iOS/iPadOS,** navegue e clique em **Configuration
    profiles**.

4.  Na página **iOS/iPadOS | Configuration profiles**, na aba
    **Policies**, clique em **+ Create** e selecione **+ New Policy**.

> ![](./media/image7.png)

5.  No painel **Create a profile**, selecione as seguintes opções e, em
    seguida, selecione **Create**:

    - Platform: **iOS/iPadOS**

    - Profile type: **Templates**

    - Template name: **Wi-Fi**

> ![A screenshot of a computer Description automatically
> generated](./media/image8.png)

6.  No painel **Basics**, insira as seguintes informações e selecione
    **Next**:

    - Name: !!**iOS/iPadOS Wi-Fi Policy**!!

    - Description: !!**Wi-Fi settings for iOS/iPadOS Devices**!!

> ![A screenshot of a computer Description automatically
> generated](./media/image9.png)

7.  No painel **Configuration settings**, ao lado de **Wi-Fi type**,
    selecione **Basic**.

> Opções adicionais são exibidas com base no tipo selecionado.

8.  No painel **Configuration settings**, selecione as seguintes opções
    e, em seguida, selecione **Next**:

    - Network name: !!**Contoso Wi-Fi**!!

    - SSID: !! **MainOffice**!!

    - Connect automatically: **Enable**

    - Security type: **WPA/WPA2-Personal**

    - Pre-Shared key: !!**ContosoWiFi123**!!

> ![A screenshot of a computer Description automatically
> generated](./media/image10.png)

9.  No painel **Assignments**, em **Included groups**, selecione **Add
    groups**.

> ![A screenshot of a computer Description automatically
> generated](./media/image11.png)

10. Na janela **Select groups to include**, selecione **iOS_iPadOS
    Devices** e clique em **Select**.

> ![](./media/image12.png)

11. Na aba **Assignments**, clique no botão **Next**.

> ![A screenshot of a computer Description automatically
> generated](./media/image13.png)

12. Na aba **Review + create**, clique no botão **Create**.

> ![A screenshot of a computer Description automatically
> generated](./media/image14.png)

13. Verifique se a **Política de iOS/iPadOS Wi-Fi** está listada.

> ![A screenshot of a computer Description automatically
> generated](./media/image15.png)
>
> **Resultados:** Após concluir este exercício, você terá criado e
> atribuído com sucesso um perfil de configuração para definir as
> configurações de Wi-Fi para dispositivos iOS e iPadOS.
