# Laboratório 4 - Gerenciar o registro do dispositivo Microsoft Entra

**Resumo**

Neste laboratório, realizaremos o registro do Microsoft Entra usando um
dispositivo Windows.

**Exercício 1: Configurando o registro do dispositivo Microsoft Entra**

**Cenário**

Vários usuários solicitaram usar seus dispositivos iOS, Android e
Windows para acessar os recursos de nuvem da Contoso. Como a Contoso não
é proprietária dos dispositivos, você não quer que os usuários realizem
uma associação ao Entra para o gerenciamento completo dos dispositivos.
Em vez disso, você precisa garantir que os usuários consigam registrar
seus dispositivos no Microsoft Entra, o que ainda permite que você
aplique a política da empresa aos aplicativos conforme necessário e
ainda permite que os usuários acessem os recursos da Contoso. Você
testará o registro de dispositivos do Microsoft Entra usando um
dispositivo Windows 11.

**Tarefa 1: Configurar o registro do dispositivo do Azure AD**

1.  Em
    [*SEA-SVR1*](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10),
    abra uma nova aba no navegador Edge e digite a seguinte URL,
    !!**https://entra.microsoft.com**!! e pressione o botão **Enter**.

2.  Entre com seu ID de locatário do O365
    !!**admin@M365xXXXXXXXX.onmicrosoft.com**!! e use a senha de
    administrador do locatário.

> ![A screenshot of a computer Description automatically
> generated](./media/image1.png)
>
> ![A screenshot of a login box Description automatically
> generated](./media/image2.png)

3.  Na caixa de diálogo **Stay signed in?,** selecione o botão **Yes.**

> ![A screenshot of a computer Description automatically
> generated](./media/image3.png)

4.  Na janela do **Microsoft Entra admin center**, navegue e clique em
    **Identity**.

![A screenshot of a computer Description automatically
generated](./media/image4.png)

5.  Selecione **Devices** e, em seguida, **Device settings** e, no
    painel de detalhes, verifique se a opção **Users may register their
    devices with Microsoft Entra** está definida como **All** e
    acinzentada.

> Esta opção fica acinzentada e definida como **All** por padrão quando
> o Microsoft Intune está habilitado no locatário. Isso garante que
> todos os usuários possam registrar dispositivos pessoais com Windows
> 10 ou superior, iOS, Android e macOS no Azure AD.
>
> ![](./media/image5.png)

**Tarefa 2: Executar o registro do Microsoft Entra**

1.  Altere para
    [*SEA-WS1*](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10)
    e faça login como **Admin** com a senha !!**Pa55w.rd**!!.

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image6.png)

2.  Na barra de tarefas, selecione **Start** e depois **Settings**.

![A screenshot of a computer Description automatically
generated](./media/image7.png)

3.  Na janela **Settings**, selecione **Accounts**.

![A screenshot of a computer Description automatically
generated](./media/image8.png)

4.  Na página **Accounts**, selecione **Access work or school**.

![A screenshot of a computer Description automatically
generated](./media/image9.png)

5.  Na página **Access work or school**, selecione **Connect**.

![A screenshot of a computer Description automatically
generated](./media/image10.png)

6.  Na página de **Sign in**, digite
    !!**JoniS@M365xXXXXXXX.onmicrosoft.com**!! e então selecione
    **Next**.

![](./media/image11.png)

7.  Na página **Enter password**, digite a senha do locatário:
    !\![**P@55w.rd1234**](mailto:P@55w.rd1234)!! e então selecione
    **Sign in**

![A screenshot of a computer Description automatically
generated](./media/image12.png)

8.  Na página **You're all set!,** selecione **Done**.

![A screenshot of a computer Description automatically
generated](./media/image13.png)

9.  Na página **Access work or school,** verifique se a **conta
    corporativa ou escolar** de Joni é exibida.

![A screenshot of a computer Description automatically
generated](./media/image14.png)

10. Feche a página **Settings**.

**Tarefa 3: Validar o registro do Microsoft Entra**

1.  Em
    [*SEA-WS1*](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10),
    clique com o botão direito do mouse no **botão Start** e selecione
    **Terminal do Windows (Admin)** .

> ![A screenshot of a computer Description automatically
> generated](./media/image15.png)

2.  Na caixa de diálogo **User Account Control**, selecione **Yes**.

> ![A screenshot of a computer error Description automatically
> generated](./media/image16.png)

3.  No console do PowerShell, digite o seguinte comando e pressione
    **Enter** :

> !!**dsregcmd /status**!!

4.  Na saída **User State**, verifique se **WorkplaceJoined : YES** é
    exibido. Isso indica que o usuário realizou um registro de
    dispositivo no Microsoft Entra.

> ![A screenshot of a computer Description automatically
> generated](./media/image17.png)

5.  Feche o PowerShell e saia do **SEA-WS1** .

6.  Altere para SEA-SVR1. Acesse a janela do **Microsoft Entra admin
    center**, navegue e clique em **Identity**.

> ![A screenshot of a computer Description automatically
> generated](./media/image18.png)
>
> 7\. Na seção **Identity**, selecione **Devices**, navegue e clique em
> **All devices**, conforme mostrado na imagem abaixo.
>
> ![A screenshot of a computer Description automatically
> generated](./media/image19.png)

8.  Verifique se o **Join Type** está listado como **Microsoft Entra
    registered** e se o proprietário é **Joni Sherman** .

> ![](./media/image20.png)
>
> Observe que o dispositivo é registrado no Microsoft Entra, NÃO
> associado ao Microsoft Entra. Dispositivos registrados no Entra
> geralmente são dispositivos que não podem ser associados ao Entra ou
> dispositivos que são de propriedade pessoal do usuário. O registro de
> um dispositivo fornecerá acesso a recursos baseados na nuvem.

9.  Feche o Microsoft Edge.

**Tarefa 4: Entre no Windows e desconecte-se da organização**

1.  Altere para
    *[SEA-WS1](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10).*
    Na barra de tarefas, selecione o **ícone** **Windows Start** e, em
    seguida, selecione **Settings**.

![A screenshot of a computer Description automatically
generated](./media/image7.png)

2.  Na janela **Settings**, selecione **Accounts**.

> ![A screenshot of a computer Description automatically
> generated](./media/image8.png)

3.  Na página **Accounts**, selecione **Access work or school**.

> ![A screenshot of a computer Description automatically
> generated](./media/image9.png)

4.  Na página **Access work or school**, clique na seta ao lado da conta
    **JoniS@M3654xXXXXXXXX** **Work or school**, conforme mostrado na
    imagem abaixo.

> ![](./media/image21.png)

5.  Clique no botão **Disconnect**.

> ![A screenshot of a computer Description automatically
> generated](./media/image22.png)

6.  Clique no botão **Yes** para confirmar a remoção da conta.

> ![A screenshot of a computer Description automatically
> generated](./media/image23.png)
>
> Observe que você não precisa reiniciar para desconectar um dispositivo
> registrado no Microsoft Entra.

7.  Saia do **SEA-WS1**.

![A screenshot of a computer Description automatically
generated](./media/image24.png)

**Resultados** : Após concluir este exercício, você terá configurado o
registro do dispositivo Microsoft Entra.
