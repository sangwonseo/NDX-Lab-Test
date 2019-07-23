## Task 1: Cloud Central에 Azure Permission 부여

 1.  NetApp Cloud Central에 로그인합니다. (https://cloud.netapp.com) 
 
 2.   Policy_for_Setup_As_Service_Azure.json 파일을 수정합니다. ([Policy_for_Setup_As_Service_Azure.json](https://mysupport.netapp.com/cloudontap/iampolicies))
       Policy_for_setup_As_Service_Azure.json 파일의 끝부분에 /subscription/ 다음에 각자 본인의 Azure subscription ID값으로 변경하여 수정하고 저장합니다.
       
```"NotActions": [],
    "AssignableScopes": [
	"/subscriptions/subscription id 기입	"
    ],
    "Description": "Azure SetupAsService",
    "IsCustom": "true"
```

 3. 수정한 JSON을 이용해 custom role을 생성하기 위해 azure portal에 접속합니다.

4. Azure portal에서 제공되는 cloud shell에서 해당 JSON 파일을 업로드합니다. 

5. 업로드된 JSON 파일을 통해 custom role을 생성합니다.
  

       az role definition create --role-definition Policy_for_Setup_As_Service_Azure.json

6. Azure에 생성된 Custom Role 확인합니다. 
    - Azure Subscription 을 열고 pay-as-you-go subscription선택
    - pay-as-you-go subscription선택
    - Roles 클릭 
    - Azure SetupAsService Role 확인
    
![Azure SetupAsService Role](https://github.com/sangwonseo/NDX-Lab-Test/blob/master/Cloud%20Central/Azure_setup_service_rol.png)
    
7.  NetApp Cloud Central에서 Cloud Manager를 설치할 user에게 role을 할당합니다.
      - Azure내 Subscription 을 열고 pay-as-you-go subscription선택
      - Access control (IAM) 클릭
      - Add를 클릭 후 ‘add role assignment’ 선택 
      - Role : Azure SetupAsService 선택
      - Assign access to : Azure AD user, group, or application 에 Access 할당 
      - Select : 본인의 account 선택
