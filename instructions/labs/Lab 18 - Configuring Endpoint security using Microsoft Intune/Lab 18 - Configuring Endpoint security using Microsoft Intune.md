Laboratório 18 - Configurando a segurança de endpoint usando o Microsoft
Intune

**Resumo**

Neste laboratório, você criará uma política para configurar o Microsoft
Defender para dispositivos gerenciados no Microsoft Intune.

**Pré-requisitos**

Os seguintes laboratórios devem ser concluídos antes deste laboratório:

- Laboratório nº 5 - Gerenciar registro de dispositivos no Microsoft
  Intune

- Laboratório nº 6 - Registro de dispositivos no Microsoft Intune

- Laboratório nº 7 - Criação e implementação de perfis de configuração

**Cenário**

Você foi solicitado a garantir que o Grupo de Desenvolvedores da Contoso
tenha o Microsoft Defender configurado corretamente. Foi solicitado que:

- A proteção contra violações deve ser impedida.

- As áreas Proteção da conta, Controle de aplicativos e navegador,
  Segurança do dispositivo, Desempenho e integridade do dispositivo e
  Opções de família no aplicativo Segurança do Windows devem ser
  ocultadas

- O nome da empresa e o número de telefone devem ser adicionados.

- As configurações de proteção em tempo real, correção e verificação
  também devem ser definidas.

As configurações serão verificadas por meio de testes em um dispositivo
registrado, SEA-WS1, e em um dispositivo não registrado, SEA-CL1.

Tarefa 1: Configurar a experiência de segurança do Windows no Intune

1.  Altere e faça login no [***SEA-SVR1***](urn:gd:lg:a:select-vm) como
    !!**[Contoso\Administrator](urn:gd:lg:a:send-vm-keys)!!** com a
    senha !!**[Pa55w.rd](urn:gd:lg:a:send-vm-keys)!!**

2.  Na barra de tarefas, selecione **Microsoft Edge.**

3.  No Microsoft Edge, digite !!**https://Intune.microsoft.com!!** na
    barra de endereço e pressione **Enter.**

4.  Entre como administrador de locatário do Office 365.

> ![A screenshot of a computer Description automatically
> generated](./media/image1.png)

5.  No painel de navegação, selecione **Endpoint security** e, em
    seguida, selecione **Antivirus**.

> ![](./media/image2.png)

6.  No painel **Endpoint security |Antivirus**, selecione **+ Create
    Policy**.

> ![A screenshot of a computer Description automatically
> generated](./media/image3.png)

7.  No painel **Create a profile**, para **Platform**, selecione
    **Windows 10, Windows 11 and Windows Server.**

8.  Na lista **Profile**, selecione **Windows Security experience**. Em
    seguida, selecione **Create**.

> ![A screenshot of a computer Description automatically
> generated](./media/image4.png)

9.  Na aba Basics, no campo **Name**, digite !!**[Windows Security
    Settings](urn:gd:lg:a:send-vm-keys)!!**. Selecione **Next**.

> ![A screenshot of a computer Description automatically
> generated](./media/image5.png)

10. Em **Defender**, configure as seguintes configurações:

    - TamperProtection (Device): **On**

> ![A screenshot of a computer Description automatically
> generated](./media/image6.png)

11. No **Windows Defender Security Center**, configure as seguintes
    configurações:

    - Disable Account Protection UI: **Enable**

    - Disable App Browser UI: **Enable**

    - Disable Device Security UI: **Enable**

    - Disable Family UI: **Enable**

    - Disable Health UI: **Enable**

> ![A screenshot of a computer Description automatically
> generated](./media/image7.png)

12. Ao lado de **Enable Customized Toasts,** selecione **Enable**.

13. No campo **Company name**, selecione **Configured** e digite
    !!**[Contoso IT](urn:gd:lg:a:send-vm-keys)!!**

14. Para **Phone**, selecione **Configured** e digite
    !!**[555-1234](urn:gd:lg:a:send-vm-keys)!!** e selecione **Next**.

> ![A screenshot of a computer Description automatically
> generated](./media/image8.png)

15. Na página **Scope tags**, selecione **Next**.

> ![A screenshot of a computer Description automatically
> generated](./media/image9.png)

16. Na aba **Assignments**, em **Included groups,** selecione **Add
    groups**. Escolha o grupo **Contoso Developer Devices**, clique em
    **Select** e, em seguida, selecione **Next**.

> ![A screenshot of a computer Description automatically
> generated](./media/image10.png)

17. Na aba **Review + create**, revise as informações e selecione
    **Save**.

> ![A screenshot of a computer Description automatically
> generated](./media/image11.png)

Tarefa 2: Configurar a política do Microsoft Defender Antivirus no
Intune

1.  No painel **Endpoint security |Antivirus**, selecione **Create
    Policy**.

> ![A screenshot of a computer Description automatically
> generated](./media/image12.png)

2.  No painel **Create a profile**, para **Platform**, selecione
    **Windows 10, Windows 11, and Windows Server**.

3.  Na lista **Profile**, selecione **Microsoft Defender Antivirus** e,
    em seguida, selecione **Create**.

> ![A screenshot of a computer Description automatically
> generated](./media/image13.png)

4.  Na aba **Basics**, no campo **Name**, digite !!**[Microsoft Defender
    Antivirus Settings](urn:gd:lg:a:send-vm-keys)!!**. Selecione
    **Next**.

> ![A screenshot of a computer Description automatically
> generated](./media/image14.png)

5.  Na aba **Configuration settings**, defina as seguintes
    configurações:

    - Allow Intrusion Prevention System: **Allowed**

    - Allow scanning of all downloaded files and
      attachments: **Allowed**

    - Allow Realtime Monitoring: **Allowed**

> ![](./media/image15.png)

- Check For Signatures Before Running Scan: **Enabled**

- Days to Retain Cleaned Malware: !!**[60](urn:gd:lg:a:send-vm-keys)!!**

> ![A screenshot of a computer Description automatically
> generated](./media/image16.png)

- Schedule Quick Scan Time: !!**[60](urn:gd:lg:a:send-vm-keys)!!**
  (representa 1:00 da manhã)

> ![A screenshot of a computer Description automatically
> generated](./media/image17.png)

- Submit samples consent: **Send safe samples automatically**

> ![A screenshot of a computer Description automatically
> generated](./media/image18.png)

6.  Na aba **Configuration settings**, selecione **Next**.

7.  Na página **Scope tags**, selecione **Next**.

> ![A screenshot of a computer Description automatically
> generated](./media/image19.png)

8.  Na aba **Assignments**, em **Assignments,** selecione **Add
    groups**.

9.  Escolha o grupo **Contoso Developer Devices**, depois selecione
    **Select** e, em seguida, **Next**.

> ![A screenshot of a computer Description automatically
> generated](./media/image20.png)

10. Na aba **Review + create**, revise as informações e selecione
    **Save**.

> ![A screenshot of a computer Description automatically
> generated](./media/image21.png)

Tarefa 3: Sincronizar os dispositivos gerenciados

1.  No **Microsoft Intune admin center**, selecione **Devices** e depois
    **All devices**.

2.  No painel **Devices | All devices**, selecione **SEA-WS1** e, no
    portal **SEA-WS1**,selecione **Sync** na barra de ferramentas e, em
    seguida, selecione **Yes**.

> ![](./media/image22.png)
>
> Aguarde de 3 a 4 minutos para que a sincronização seja concluída.

3.  Feche o Microsoft Edge.

Tarefa 4: Verificar a configuração

1.  Altere para [***SEA-CL1***](urn:gd:lg:a:select-vm). Se necessário,
    faça login como
    !!**[Contoso\Administrator](urn:gd:lg:a:send-vm-keys)!!** com a
    senha !!**[Pa55w.rd](urn:gd:lg:a:send-vm-keys)!!**.

2.  Em [***SEA-CL1***](urn:gd:lg:a:select-vm), selecione **Start**,
    digite !!**[Windows Security](urn:gd:lg:a:send-vm-keys)!!** e, em
    seguida, no ícone Windows Security, selecione **Open**.

> ![](./media/image23.png)
>
> Observe que todas as opções de segurança são exibidas. Isso ocorre
> porque o SEA-CL1 não está registrado no Intune.
>
> ![A screenshot of a computer security system Description automatically
> generated](./media/image24.png)

3.  Feche a **Windows Security** e saia do
    [***SEA-CL1***](urn:gd:lg:a:select-vm) .

4.  Altere para [***SEA-WS1***](urn:gd:lg:a:select-vm) e faça login como
    **!!Cindy@M365x27131290.onmicrosoft.com!!** com a senha
    **!!P@55w.rd12345!!**.

5.  Selecione **Start**, digite !!**[Windows
    Security](urn:gd:lg:a:send-vm-keys)!!** e, em seguida, no ícone
    Segurança do Windows, selecione **Open**.

> ![](./media/image25.png)
>
> Observe que todas as áreas restritas configuradas na política do
> Intune não são exibidas. O [***SEA-WS1***](urn:gd:lg:a:select-vm) está
> registrado no Intune, que aplicou as configurações de segurança.
>
> ![A screenshot of a computer Description automatically
> generated](./media/image26.png)

6.  Feche o **Windows Security** e saia do
    [***SEA-WS1***](urn:gd:lg:a:select-vm).

**Resultados:** Após concluir este exercício, você terá criado e
aplicado com sucesso uma política para configurar o Microsoft Defender
para dispositivos gerenciados no Intune.
