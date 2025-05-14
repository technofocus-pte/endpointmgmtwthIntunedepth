Laboratório 21: Atualizando o Windows com Redefinição do Autopilot e
modo Self-Deploying

**Resumo**

Neste laboratório, você aprenderá como executar uma redefinição remota
do Autopilot.

**Pré-requisitos**

Os seguintes laboratórios devem ser concluídos antes deste laboratório:

- Laboratório 01 - Gerenciando Identidades no Microsoft Entra ID

- Laboratório 02 - Sincronizando Identidades usando o Microsoft Entra
  Connect

- Laboratório 19 - Implementação do Windows 11 usando o Microsoft
  Deployment Toolkit

- Laboratório 20 - Implementando o Windows 11 com o Autopilot

**Cenário**

O SEA-WS4 foi implementado usando o Windows Autopilot. Você precisa
testar outro cenário de provisionamento que envolva a redefinição do
Autopilot. Você criará um novo perfil de implementação configurado com o
modo de Self-Deploying do Windows Autopilot.

Tarefa 1: Configurar um perfil de implementação do Windows Autopilot
Self-Deploying

1.  Altere para [***SEA-SVR1***](urn:gd:lg:a:select-vm).

> ![](./media/image1.png)

2.  No **Microsoft Edge**, abra uma nova aba e navegue até
    [**https://intune.microsoft.com**](https://intune.microsoft.com). Se
    solicitado, entre com
    [**<admin@M365xXXXXXXXX.onmicrosoft.com>**](mailto:admin@M365xXXXXXXXX.onmicrosoft.com)
    e senha.

3.  No **Microsoft Intune admin center**, selecione **Devices**.

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)

4.  Na seção **Device onboarding**, selecione **Enrollment**.

> ![A screenshot of a computer Description automatically
> generated](./media/image3.png)

5.  No painel de registro do Windows, em detalhes, selecione
    **Deployment Profiles**.

> ![](./media/image4.png)

6.  No painel **Windows AutoPilot deployment profiles**, selecione
    **Contoso Profile 1** e, em seguida, selecione **Properties**.

> ![](./media/image5.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image6.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image7.png)

7.  Role para baixo até **Assignments** e selecione **Edit**.

> ![A screenshot of a computer Description automatically
> generated](./media/image8.png)

8.  Ao lado de **IT Devices**, selecione **Remove**.

> ![](./media/image9.png)

9.  Selecione **Review and save** e depois selecione **Save**.

> ![A screenshot of a computer Description automatically
> generated](./media/image10.png)

10. Feche a página **Contoso Profile 1|Properties**.

11. No painel **Windows AutoPilot deployment profiles**, selecione
    **Create profile** e, em seguida, selecione **Windows PC**.

> ![A screenshot of a computer Description automatically
> generated](./media/image11.png)

12. Na aba **Basics**, na caixa de texto **Name**, digite [**Contoso
    profile 2**](urn:gd:lg:a:send-vm-keys) .

13. Para **Convert all targeted devices to Autopilot,** selecione **no**
    e depois **Next**.

> ![](./media/image12.png)

14. Na aba **Out-of-box experience (OOBE)**, certifique-se de que o
    **Deployment mode** esteja definido como **Self-Deploying**.

> ![](./media/image13.png)

15. Certifique-se de que as seguintes opções estejam definidas:

    - Language (Region): **Operating system default**

    - Automatically configure keyboard: **Yes**

    - Apply device name template: **Yes**

    - Enter a name: [**Contoso-%RAND:2%**](urn:gd:lg:a:send-vm-keys)

> ![A screenshot of a computer Description automatically
> generated](./media/image14.png)

16. Selecione **Next**.

17. Na aba **Assignments**, em **Included groups,** selecione **Add
    groups**.

> ![A screenshot of a computer Description automatically
> generated](./media/image15.png)

18. Selecione o grupo **IT Devices** e clique em **Select**. Selecione
    **Next**.

> ![](./media/image16.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image17.png)

19. No painel **Review + create**, revise as informações e selecione
    **Create**.

> ![A screenshot of a computer Description automatically
> generated](./media/image18.png)

Tarefa 2: Executar uma redefinição do Autopilot

1.  No **Microsoft Intune admin center**, selecione **Devices** e depois
    **All devices**.

2.  Selecione o PC do Autopilot (começa com o nome DESKTOP).

> ![A screenshot of a computer Description automatically
> generated](./media/image19.png)

3.  Na barra de menu, selecione a elipse e depois selecione **Autopilot
    Reset**.

> ![A screenshot of a computer Description automatically
> generated](./media/image20.png)

4.  No prompt da mensagem, selecione **Yes**.

> ![A screenshot of a computer Description automatically
> generated](./media/image21.png)

5.  Altere para [***SEA-SVR2***](urn:gd:lg:a:select-vm) e maximize a
    janela **SEA-WS4.**

> **Observação**: O SEA-WS4 ainda deve estar em execução no laboratório
> anterior
>
> **Observação**: Atualize o dispositivo para a versão mais recente e
> clique em reiniciar.

6.  Reinicie o **SEA-WS4.**

> ![A screenshot of a computer Description automatically
> generated](./media/image22.png)
>
> **Observação:** Este processo pode levar 30 minutos e será reiniciado
> várias vezes durante o processo. Seu instrutor pode continuar com o
> próximo módulo enquanto esta tarefa é concluída. Não se esqueça de
> retornar para concluir a Tarefa 3 durante sua próxima sessão de
> laboratório.

Tarefa 3: Verificar a implementação do Autopilot

1.  Na página de login, digite **Cindy@M365x19242953.onmicrosoft.com**
    com a senha [**P@55w.rd1234**](mailto:P@55w.rd1234).

2.  Em **Use Windows Hello with your account**, selecione **OK.**

> ![A screenshot of a computer Description automatically
> generated](./media/image23.png)

3.  Na página **Verify your identity**, selecione o método de
    verificação de texto.

4.  Na página **Enter code**, insira o código que foi enviado por
    mensagem de texto para seu dispositivo móvel e selecione **Verify**.

> ![A screenshot of a computer Description automatically
> generated](./media/image24.png)

5.  Na caixa de diálogo **Setup up a PIN**, nos campos **New PIN** e
    **Confirm PIN**, digite [**102938**](urn:gd:lg:a:send-vm-keys) e
    selecione **OK.**

> ![](./media/image25.png)

6.  Na página **All set!,** selecione **OK.**

7.  Selecione **Start** e **Settings**.

> ![](./media/image26.png)

8.  Selecione **Contas** e, em seguida, **Access work or school**.
    Verifique se o dispositivo está conectado ao Azure AD da Contoso.

> ![](./media/image27.png)

9.  Selecione **Connected to Contoso's Azure AD** e selecione **Info**.

> ![](./media/image28.png)

10. Na página **Managed by Contoso**, role para baixo e selecione
    **Sync**.

> ![](./media/image29.png)

11. No **SEA-WS4**, feche a janela **Settings**.

12. Desligue o **SEA-WS4** e feche a janela do **SEA-WS4**.

13. No [***SEA-SVR2***](urn:gd:lg:a:select-vm), feche o Gerenciador do
    Hyper-V.

**Resultados:** Após concluir este exercício, você terá provisionado um
dispositivo Windows 11 utilizando a Redefinição do Autopilot no modo
Self-Deploying.
