# Family Biz Bundle

## Features

The family biz bundle includes business such as family, member, room, etc., these are the basic conditions for managing the equipment after device configuration. After the device is activated, the corresponding room location of the family can be set. The family members with different permissions under the family correspond to different operation permissions (member management, device operation, room management), and the family is the largest unit of scene intelligent execution.

## Biz Bundle integration

### Create project

Create your project in Android Studio, connect to the public SDK and configure [Biz Bundle Framework](../access.md).

### Module's build.gradle configuration

``` groovy
dependencies {
  implementation 'com.tuya.smart:tuyasmart-bizbundle-family:3.20.0-7'
}
```



## Function use

### Go to Family Management page

The family management page supports redirection through the following routing method:

```java
UrlRouter.execute(UrlRouter.makeBuilder(FamilyManageActivity.this, "family_manage"));
```

### Accept or Refuse To Join the Family

At present, the business of accepting family invitations is not within the scope of biz bundle processing. You can handle this part of the logic on your application homepage or other places where you want to receive family invitations.

**Declaration**

```java
void processInvitation(long homeId, boolean action, IResultCallback callBack)
```

**Parameters**

| Parameters | Description     |
| ---------- | --------------- |
| homeId     | Family ID       |
| action     | Accept / Reject |

**Example**

```java
TuyaHomeSdk.getMemberInstance().processInvitation(homeId, isAccept, new IResultCallback() {
            @Override
            public void onError(String errorCode, String errorMsg) {
                
            }

            @Override
            public void onSuccess() {
                // Do something like refresh family list
            }
        });
```



