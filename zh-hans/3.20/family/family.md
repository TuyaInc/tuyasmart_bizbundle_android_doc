# 家庭业务包

## 功能介绍

家庭业务包囊括了家庭、成员、房间等业务，这些是对配网后设备进行管理的基础条件。设备在进行配网后可设置家庭的对应房间位置，该家庭下不同权限的家庭成员对应不同的操作权限(成员管理、设备操作、房间管理)，同时家庭是场景智能执行的最大单位。

## 家庭业务包集成

### 创建工程

在 Android Studio 中建立你的工程,接入公版 SDK 并完成业务包[框架接入](../access.md)

### module 的 build.gradle 配置

``` groovy
dependencies {
  implementation 'com.tuya.smart:tuyasmart-bizbundle-family:3.20.0-7'
}
```



## 功能使用

### 进入家庭管理页面

家庭管理页面支持通过以下**路由**方式跳转：

```java
UrlRouter.execute(UrlRouter.makeBuilder(FamilyManageActivity.this, "family_manage"));
```

### 接受或拒绝家庭邀请

目前家庭接受邀请的业务并不在业务包处理范围内，你可以在自己的应用首页或者其他希望接收家庭邀请的地方来处理这部分逻辑。

**接口说明**

```java
void processInvitation(long homeId, boolean action, IResultCallback callBack)
```

**参数说明**

| 参数   | 说明      |
| ------ | --------- |
| homeId | 家庭 ID   |
| action | 接受/拒绝 |

**示例代码**

处理方式如下：

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



