Laboratório 20: Implementando o Windows 11 com o Autopilot

**Resumo**

Neste laboratório, você aprenderá como provisionar um dispositivo
Windows 11 com o Autopilot usando o modo controlado pelo usuário.

**Pré-requisitos**

Os seguintes laboratórios devem ser concluídos antes deste laboratório:

- Laboratório 01 - Gerenciando Identidades no Microsoft Entra ID

- Laboratório 02 - Sincronizando Identidades usando o Microsoft Entra
  Connect

- Laboratório 11 - Monitorar a atividade do dispositivo e do usuário no
  Intune

**Cenário**

A equipe de TI da Contoso está planejando implementar novos dispositivos
com Windows 11 usando o Autopilot. Os dispositivos têm uma instalação
padrão do Windows 11. Os usuários devem conseguir conectar o
dispositivo, ligá-lo e responder a um número mínimo de perguntas durante
o OOBE, usando suas credenciais do Microsoft Entra ID para fazer login.
O processo deve registrar e ingressar automaticamente no domínio do
Entra ID. Você foi solicitado a configurar e testar a experiência usando
o SEA-WS4, que você instalou e configurou recentemente usando o Hyper-V.

Tarefa 1: Crie um grupo no Centro de Administração do Microsoft Entra.

1.  Altere e faça login no [***SEA-SVR1***](urn:gd:lg:a:select-vm) como
    !!   with the password [**Pa55w.rd**](urn:gd:lg:a:send-vm-keys) and
    close **Server Manager**.**Contoso\Administrator**!! com a senha
    !!!! e feche o **Server Manager**.

2.  Na barra de tarefas, selecione **Microsoft Edge** .

3.  Em Microsoft Edge, na barra de endereços, digite !!﷟﷟HYPERLINK
    "https://entra.microsoft.com"**ttps://entra.microsoft.com**!! e
    pressione **Enter** . Se solicitado, entre com
    [**admin@M365xXXXXXXXX.onmicrosoft.com**](mailto:admin@M365xXXXXXXXX.onmicrosoft.com)!!
    e a senha.

![](./media/image1.png)

4.  No painel de navegação, selecione **Identity.**

5.  Em **Identity**, selecione **Groups**.

> ![](./media/image2.png)

6.  No painel **Groups | All groups**, selecione **New group**.

> ![](./media/image3.png)

7.  No painel **New Group**, na lista **Group type**, selecione
    **Security**.

8.  Na caixa **Group name**, digite !!﷟HYPERLINK
    "http://urn:gd:lg:a:send-vm-keys"**IT Devices**!!.

9.  Na caixa **Group description**, digite !!﷟HYPERLINK
    "http://urn:gd:lg:a:send-vm-keys"**IT Department Devices**!!.

10. Na lista **Membership type**, selecione **Dynamic Device**.

11. Selecione **Add dynamic query**.

> ![](./media/image4.png)

12. No painel **Dynamic membership rules,** selecione **Edit** acima da
    caixa **Rule syntax**.

> ![](./media/image5.png)

13. Na caixa de texto Edit rule syntax, adicione a seguinte regra de
    associação simples e selecione **OK** .

14. !!(device.devicePhysicalIDs -any (\_ -contains "\[ZTDId\]"))!!

> ![](./media/image6.png)

15. Selecione **Save** para fechar as **Dynamic membership rules** e, em
    seguida, selecione **Create** para criar o grupo.

> ![A screenshot of a computer Description automatically
> generated](./media/image7.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image8.png)
>
> ![](./media/image9.png)

Tarefa 2: Gerar um arquivo de comma-separated value (CSV) específico
para o dispositivo

1.  Altere para [***SEA-SVR2***](urn:gd:lg:a:select-vm) e faça login
    como
    [**[Contoso\Administrator](urn:gd:lg:a:send-vm-keys)**](urn:gd:lg:a:send-vm-keys)
    com a senha !!﷟HYPERLINK
    "http://urn:gd:lg:a:send-vm-keys"**Pa55w.rd**!!.

> ![A screenshot of a computer Description automatically
> generated](./media/image10.png)

2.  Selecione **Hyper-V Manager** na barra de tarefas.

> ![A screenshot of a computer Description automatically
> generated](./media/image11.png)

3.  Em Máquinas Virtuais, clique com o botão direito do mouse em
    **SEA-WS4** e selecione **Connect**.

> ![](./media/image12.png)

4.  Na janela do **SEA-WS4**, selecione **Start**. Quando o computador
    iniciar, maximize a janela.

> ![A screenshot of a computer Description automatically
> generated](./media/image13.png)

5.  Entre no **SEA-WS4** como
    [**[Administrator](urn:gd:lg:a:send-vm-keys)**](urn:gd:lg:a:send-vm-keys)
    com a senha !!﷟HYPERLINK
    "http://urn:gd:lg:a:send-vm-keys"**Pa55w.rd**!!.

> ![A screenshot of a computer Description automatically
> generated](./media/image14.png)

6.  Clique com o botão direito do mouse em **Start**, selecione
    **Windows Terminal (Admin)** e selecione **Yes** no prompt do **User
    Account Control**.

> ![](./media/image15.png)
>
> ![A screenshot of a computer error Description automatically
> generated](./media/image16.png)

7.  No prompt de linha de comando do Windows PowerShell, digite o
    seguinte cmdlet e pressione **Enter** :

> !! Install-Script -Name Get-WindowsAutoPilotInfo!!

![A screenshot of a computer Description automatically
generated](./media/image17.png)

8.  Você receberá três prompts. Em cada um deles, digite
    [**Y**](urn:gd:lg:a:send-vm-keys) e pressione **Enter**.

> ![](./media/image18.png)

9.  No prompt de linha de comando do Windows PowerShell, digite o
    seguinte cmdlet e pressione **Enter** :

> !!**Set**-ExecutionPolicy *RemoteSigned*!!

10. Quando solicitado, digite [**Y**](urn:gd:lg:a:send-vm-keys) e
    pressione Enter.

11. No prompt de linha de comando do Windows PowerShell, digite o
    seguinte cmdlet e pressione **Enter** :

> !!Get-WindowsAutoPilotInfo.ps1 -OutputFile C:\Computer.csv!!
>
> ![](./media/image19.png)

12. No prompt de linha de comando do Windows PowerShell, digite o
    seguinte comando, pressione **Enter** e revise o conteúdo do
    arquivo:

13. **type** !!C:\Computer.csv!!

> ![](./media/image20.png)

14. No prompt de comando do Windows PowerShell, digite o seguinte
    comando e pressione **Enter** . Isso copiará o arquivo para
    **SEA-SVR2** :

15. copy !!c:\computer.csv \\sea-svr2\labfiles!!

> ![A screenshot of a computer screen Description automatically
> generated](./media/image21.png)

16. Feche o prompt de comando do Windows PowerShell.

Tarefa 3: Trabalhar com um perfil de implementação do Windows Autopilot

1.  Altere para [***SEA-SVR1***](urn:gd:lg:a:select-vm).

> ![](./media/image22.png)

2.  No **Microsoft Edge** , abra uma nova aba e navegue até !!﷟HYPERLINK
    "https://intune.microsoft.com"**https://intune.microsoft.com**!! Se
    solicitado, entre com
    [**admin@M365xXXXXXXX.onmicrosoft.com**](mailto:admin@M365xXXXXXXX.onmicrosoft.com)!!
    e a senha.

3.  Em **Microsoft Intune admin center**, selecione **Devices**.

4.  Na seção **Device enrollment**, selecione **Enroll devices**.

5.  No painel de detalhes, role para baixo até **Windows Autopilot
    Deployment Program** e selecione **Devices**.

> ![A screenshot of a computer Description automatically
> generated](./media/image23.png)

6.  No painel de **Windows Autopilot devices** na barra de menus,
    selecione **Import**, selecione o **ícone folder** e navegue até !!
    HYPERLINK "http://urn:gd:lg:a:send-vm-keys" **\\SEA-SVR2\Labfiles**
    !!!!﷟HYPERLINK
    "http://urn:gd:lg:a:send-vm-keys"**\\SEA-SVR2\Labfiles**!! ,
    selecione **Computer.csv** , selecione **Open** e, em seguida,
    selecione **Import**.

> ![](./media/image24.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image25.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image26.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image27.png)
>
> **Observação** : o processo de importação pode levar até 15 minutos,
> mas normalmente leva cerca de 5 minutos.
>
> **Importante** : Após a conclusão do processo, o dispositivo pode não
> ser exibido. Nesse caso, selecione o botão **Sync**, aguarde alguns
> minutos e selecione **Refresh**.

7.  Selecione **X** para fechar o painel **de dispositivos do Windows
    Autopilot** .

> ![](./media/image28.png)

8.  No painel de registro do Windows, no painel de detalhes, selecione
    **Deployment Profiles**.

> ![](./media/image29.png)

9.  No painel **Windows AutoPilot deployment profiles**, selecione
    **Create profile** e, em seguida, selecione **Windows PC**.

> ![](./media/image30.png)

10. Na aba **Basics**, na caixa de texto **Name**, type !!﷟HYPERLINK
    "http://urn:gd:lg:a:send-vm-keys"**Contoso profile1**!!

11. Para **Convert all targeted devices to Autopilot,** selecione **No**
    e depois **Next**.

> ![A screenshot of a computer Description automatically
> generated](./media/image31.png)

12. Na aba **Out-of-box experience (OOBE)**, certifique-se de que o
    **Deployment mode** esteja definido como **User-Driven**.

13. Certifique-se de que a **Join to Microsoft Entra ID as** esteja
    definida como **Microsoft Entra Joined** .

14. Certifique-se de que as seguintes opções estejam definidas:

    - Microsoft Software License Terms: **Hide**

    - Privacy Settings: **Hide**

    - Hide change account options: **Hide**

    - User account type: **Administrator**.

    - Allow pre-provisioned deployment: **No**

    - Language (Region): **Operating system default**

    - Automatically configure keyboard: **Yes**

    - Apply device name template: **No**

15. Selecione **Next**.

> ![](./media/image32.png)

16. Na aba **Assignments**, em **Included groups,** selecione **Add
    groups**.

17. Selecione o grupo **IT Devices** e clique em **Select**. Selecione
    **Next**.

> ![](./media/image33.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image34.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image35.png)

18. No painel **Review + create**, revise as informações e selecione
    **Create**.

> ![A screenshot of a computer Description automatically
> generated](./media/image36.png)
>
> ![](./media/image37.png)

Tarefa 4: Redefinir o PC

1.  Altere para [***SEA-SVR2***](urn:gd:lg:a:select-vm). O computador
    **SEA-WS4** ainda deve estar maximizado.

> ![](./media/image38.png)

2.  Em **SEA-WS4**, selecione **Start**, type !!﷟HYPERLINK
    "http://urn:gd:lg:a:send-vm-keys"**reset**!! e selecione **Reset
    this PC**.

> ![](./media/image39.png)

3.  Na seção **Reset this PC**, selecione **Reset PC**.

> ![A screenshot of a computer Description automatically
> generated](./media/image40.png)

4.  Selecione **Remove everything** e depois **Local reinstall**.

> ![A blue screen with white text Description automatically
> generated](./media/image41.png)
>
> ![A blue screen with white text Description automatically
> generated](./media/image42.png)

5.  Selecione **Next** e depois **Reset**.

> ![A screenshot of a computer Description automatically
> generated](./media/image43.png)
>
> ![A blue screen with white text Description automatically
> generated](./media/image44.png)
>
> **Observação** : Normalmente, esta tarefa não é necessária para novas
> implementações de dispositivos físicos. As informações do Autopilot do
> dispositivo são fornecidas pelo fabricante ou podem ser obtidas do
> dispositivo antes da OOBE. Para os fins deste laboratório, precisamos
> iniciar uma reinicialização para simular uma nova OOBE do dispositivo.
>
> **Observação** : Este processo pode levar de 45 a 60 minutos e será
> reiniciado várias vezes durante o processo. Seu instrutor pode
> continuar com o próximo módulo enquanto esta tarefa é concluída . Não
> se esqueça de retornar para concluir a Tarefa 5 durante sua próxima
> sessão de laboratório.

Tarefa 5: Verificar a implementação do Autopilot

1.  Na **Contoso Corp. Sign-in Page**, enter  !!﷟HYPERLINK
    "mailto:Cindy@M365x19242953.onmicrosoft.com"**Cindy@M365x19242953.onmicrosoft.com**!!
    e selecione **Next**.

2.  Na página Senha, digite enter !!﷟HYPERLINK
    "mailto:P@55w.rd1234"**P@55w.rd1234**!! e selecione **Sign in**.

3.  Em **Use Windows Hello with your account**, selecione **OK** .

> ![A screenshot of a computer Description automatically
> generated](./media/image45.png)

4.  Na página **Verify your identity**, selecione o método de
    verificação de texto.

> ![A screenshot of a computer Description automatically
> generated](./media/image46.png)

5.  Na página **Enter code**, insira o código que foi enviado por
    mensagem de texto para seu dispositivo móvel e selecione **Verify**.

> ![A screenshot of a computer Description automatically
> generated](./media/image47.png)

6.  Na caixa de diálogo **Setup up a PIN**, nos campos **New PIN** e
    **Confirm PIN**, digite [**102938**](urn:gd:lg:a:send-vm-keys) e
    selecione **OK** .

> ![A screenshot of a computer Description automatically
> generated](./media/image48.png)

7.  Na página **All set!,** selecione **OK** .

8.  Selecione **Start** e **Settings**.

> ![A screenshot of a computer Description automatically
> generated](./media/image49.png)

9.  Selecione **Accounts** e, em seguida, **Access work or school**.
    Verifique se o dispositivo está conectado ao Azure AD da Contoso.

> ![A screenshot of a computer Description automatically
> generated](./media/image50.png)

10. Selecione **Connected to Contoso's Azure AD** e selecione **Info**.

> ![A screenshot of a computer Description automatically
> generated](./media/image51.png)

11. Na página **Managed by Contoso**, role para baixo e selecione
    **Sync**.

> ![A screenshot of a computer Description automatically
> generated](./media/image52.png)
>
> ![](./media/image53.png)

12. Em **SEA-WS4**, feche a janela **Settings**.

13. Altere para [***SEA-SVR1***](urn:gd:lg:a:select-vm) .

14. No centro de administração do Microsoft Entra, selecione
    **Identity**, selecione **Devices** e, em seguida, selecione **All
    devices**.

> ![](./media/image54.png)
>
> Observe que o novo dispositivo é exibido com um nome que começa com
> "**DESKTOP-** ". Observe também que o tipo de associação é o
> **Microsoft Entra ID joined,** com Cindy White como proprietária.

15. Selecione o dispositivo Autopilot. Revise as opções de gerenciamento
    na barra do menu superior.

> Observe que você pode **Retire, Wipe, Sync** e **Restart** o
> dispositivo.

16. Selecione a elipse no final da barra de menu e observe os recursos
    adicionais de gerenciamento.

> ![A screenshot of a computer Description automatically
> generated](./media/image55.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image56.png)
>
> Recursos adicionais incluem Fresh Start, Reinicialização do Autopilot,
> Verificação rápida, Verificação completa, entre outros.

17. Feche o Microsoft Edge.

**Resultados** : Após concluir este exercício, você terá provisionado um
dispositivo Windows 11 com o Autopilot usando o modo orientado pelo
usuário.
