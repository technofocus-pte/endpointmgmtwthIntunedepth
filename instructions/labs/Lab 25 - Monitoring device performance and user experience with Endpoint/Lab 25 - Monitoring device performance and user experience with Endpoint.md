# Laboratório 25: Monitoramento do desempenho do dispositivo e da experiência do usuário com Endpoint analytics

**Resumo**

Neste laboratório, você habilitará o Endpoint Analytics para monitorar o
desempenho do dispositivo, além de pontuações e insights da experiência
do usuário.

**Pré-requisitos**

Os seguintes laboratórios devem ser concluídos antes deste laboratório:

- Laboratório 05 - Gerenciar registro de dispositivos no Microsoft
  Intune

- Laboratório 06 - Registro de dispositivos no Microsoft Intune

- Laboratório 07 - Criação e implementação de perfis de configuração

**Cenário**

Você foi solicitado a monitorar o desempenho de inicialização, a
confiabilidade do aplicativo e a experiência do usuário, com que
frequência os usuários reiniciam seus dispositivos. Para obter essas
informações, você precisa habilitar o Endpoint Analytics.

### Tarefa 1: Habilitar Endpoint analytics

1.  Em [**SEA-SVR1**](urn:gd:lg:a:select-vm), se necessário, faça login
    como
    [**[Contoso\Administrator](urn:gd:lg:a:send-vm-keys)**](urn:gd:lg:a:send-vm-keys)
    com a senha !\![**Pa55w.rd**](urn:gd:lg:a:send-vm-keys)!! e feche o
    **Server Manager**.

2.  Na barra de tarefas, selecione **Microsoft Edge** .

3.  No Microsoft Edge, digite
    !\![**https://intune.microsoft.com**](https://intune.microsoft.com)!!
    na barra de endereço e pressione **Enter**.

4.  Entre como
    [**admin@M365x19242953.onmicrosoft.com**](urn:gd:lg:a:send-vm-keys)
    com a senha.

5.  Na página do **Microsoft Intune admin center**, selecione
    **Reports**.

6.  No painel **Reports**, em **Analytics**, selecione **Endpoint
    analytics** .

> ![](./media/image1.png)

7.  Na página **Endpoint analytics**, certifique-se de que **Collect
    device data from** esteja definido como **All cloud-managed
    devices** e selecione **Start**.

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)
>
> Observe a mensagem no topo da página Visão Geral. Pode levar até 24
> horas para que as pontuações e os insights sejam exibidos na página.
>
> ![A screenshot of a computer Description automatically
> generated](./media/image3.png)

8.  Altere para [**SEA-WS1**](urn:gd:lg:a:select-vm) e reinicie o
    dispositivo.

9.  Entre como **Cindy White** com a senha:
    [**102938**](urn:gd:lg:a:send-vm-keys) .

10. Altere para [**SEA-SVR1**](urn:gd:lg:a:select-vm).

11. Na página do **Microsoft Intune admin center**, selecione
    **Devices** e, em seguida, **All devices**.

12. Selecione **SEA-WS1**.

> ![](./media/image4.png)

13. Na página **SEA-WS1**, selecione **Sync** e depois **Yes**.

> ![A screenshot of a computer Description automatically
> generated](./media/image5.png)

14. Na página **SEA-WS1**, em **Monitor** , selecione **User
    experience**. ![A screenshot of a computer Description automatically
    generated](./media/image6.png)

15. Revise as abas **Endpoint analytics**, **Startup performance** e
    **Application reliability**.

> ![A screenshot of a computer Description automatically
> generated](./media/image7.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image8.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image9.png)
>
> Pode não haver nenhuma informação disponível devido ao atraso, no
> entanto, leia os detalhes sobre o que estará visível em cada aba.

16. Na página do **Microsoft Intune admin center**, selecione
    **Reports**.

17. No painel **Reports**, em **Analytics**, selecione **Endpoint
    analytics**.

> ![](./media/image10.png)
>
> Observe que o mesmo tipo de informação está disponível no Endpoint
> Analytics, no entanto, essas informações são baseadas em todos os
> dispositivos registrados.
>
> ![A screenshot of a computer Description automatically
> generated](./media/image11.png)

18. Navegue pelos relatórios disponíveis na página Endpoint analytics.

19. Feche o Microsoft Edge.

**Resultados**: Após concluir este exercício, você terá habilitado com
sucesso o Endpoint Analytics para monitorar o desempenho do dispositivo,
além de pontuações e insights da experiência do usuário.
