**실습 9 - 구성 프로필을 사용하여 iOS 및 iPadOS Wi-Fi 설정 구성**

**요약**

이 실습에서는 Microsoft Intune을 사용하여 구성 프로필을 만들고 적용하여
iOS 및 iPadOS 기기의 Wi-Fi 설정을 구성합니다.

**연습 1: 구성 프로필 만들기**

**시나리오**

등록된 iOS 및 iPadOS 기기의 Wi-Fi 설정을 자동으로 구성하는 데 사용할
구성 프로필을 생성하라는 요청을 받았습니다. Wi-Fi 설정이 다음과 같이
구성되어 있는지 확인해야 합니다.

- Network name: **Contoso Wi-Fi**

- SSID: **MainOffice**

- Connect automatically: **Enable**

- Security type: **WPA/WPA2-Personal**

- Pre-Shared key: **ContosoWiFi123**

- Assigned to: **A new security group named iOS_iPadOS Devices**

**작업 1: iOS_iPadOS 장치 그룹 만들기**

1.  [*SEA-SVR1*](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10)로
    전환합니다. **Microsoft Entra admin center** 창에서 **Groups를**
    찾아 선택한 다음 **All groups**을 클릭합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image1.png)

2.  **Groups | All groups**  블레이드에서 **New group**을 선택합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)

3.  **New Group** 블레이드에서 다음 정보를 입력하고 아래 이미지에 표시된
    대로 **Create** 버튼을 클릭합니다:

    - Group type: **Security**

    - Group name: !!**iOS_iPadOS Devices**!!

    - Group description: !!**All iOS and iPadOS devices**!!

    - Membership type: **Assigned**

> ![A screenshot of a group Description automatically
> generated](./media/image3.png)

4.  **Groups | All groups** 블레이드에서 페이지를 새로 고치고
    **iOS_iPadOS Devices** 그룹이 표시되는지 확인합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image4.png)

**작업 2: 시나리오 요구 사항을 기반으로 구성 프로필 만들기**

1.  **Microsoft Intune admin center** 탭으로 전환하고 탐색 모음에서
    **Devices**를 선택합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image5.png)

2.  **Devices | Overview** 페이지에서 아래 이미지와 같이
    **iOS/iPadOS**를 선택합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image6.png)

3.  **iOS/iPadOS** 페이지에서 **Configuration profiles**를 찾아
    클릭합니다.

4.  **iOS/iPadOS | 구성 프로필** 페이지의 **Policies** 탭에서 +
    **Create**를 클릭하고 + **New Policy**를 선택합니다.

> ![](./media/image7.png)

5.  **Create a profile** 블레이드에서 다음 옵션을 선택한 다음
    **Create**를 선택합니다:

    - Platform: **iOS/iPadOS**

    - Profile type: **Templates**

    - Template name: **Wi-Fi**

> ![A screenshot of a computer Description automatically
> generated](./media/image8.png)

6.  **Basics**블레이드에서 다음 정보를 입력한 후 **Next**를 선택합니다.:

    - Name: !!**iOS/iPadOS Wi-Fi Policy**!!

    - Description: !!**Wi-Fi settings for iOS/iPadOS Devices**!!

> ![A screenshot of a computer Description automatically
> generated](./media/image9.png)

7.  **Configuration settings**블레이드에서 **Wi-Fi type** 옆에 있는
    **Basic**을 선택합니다.

> 선택한 유형에 따라 추가 옵션이 표시됩니다.

8.  **Configuration settings** 블레이드에서 다음 옵션을 선택한 후
    **Next**를 선택합니다:

    - Network name: !!**Contoso Wi-Fi**!!

    - SSID: !! **MainOffice**!!

    - Connect automatically: **Enable**

    - Security type: **WPA/WPA2-Personal**

    - Pre-Shared key: !!**ContosoWiFi123**!!

> ![A screenshot of a computer Description automatically
> generated](./media/image10.png)

9.  **Assignments** 블레이드의 **Included groups**에서 **Add groups를**
    선택합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image11.png)

10. **Select groups to include** 창에서 **iOS_iPadOS Devices**를 선택한
    다음 **Select**를 클릭합니다.

> ![](./media/image12.png)

11. **Assignments**탭에서 **Next** 버튼을 클릭합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image13.png)

12. **Review + create** 탭에서 **Create** 버튼을 클릭합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image14.png)

13. **iOS/iPadOS Wi-Fi Policy**가 나열되어 있는지 확인합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image15.png)
>
> **결과**: 이 연습을 완료하면 iOS 및 iPadOS 기기의 Wi-Fi 설정을
> 구성하는 구성 프로필을 성공적으로 만들고 할당하게 됩니다.
