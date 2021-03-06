---
pagename: Interface and Class Definitions
redirect_from:
  - android-interface-and-class-definitions.html
Keywords:
sitesection: Documents
categoryname: "Messaging Channels"
documentname: Mobile App Messaging SDK for Android
subfoldername: SDK APIs

order: 110
permalink: mobile-app-messaging-sdk-for-android-sdk-apis-interface-and-class-definitions.html

indicator: messaging
---

### ICallback

```java
public interface ICallback<T, E extends Throwable> {
  void onSuccess(T value);
  void onError(E exception);
}
```

### AgentData

```java
public class AgentData {
  public String mFirstName;
  public String mLastName;
  public String mAvatarURL;
  public String mEmployeeId;
  public String mNickName;
}
```



### InitLivePersonProperties

```java
public class InitLivePersonProperties{
  private String brandId;
  private String appId;
  private MonitoringInitParams mMonitoringInitParams;
  private InitLivePersonCallBack initCallBack;
}
```


### ConsumerProfile

```java
public class ConsumerProfile {
  private String mFirstName;
  private String mLastName;
  private String mPhoneNumber;
  private String mNickName;
  private String mAvatarUrl;
}
```

### PushMessage

```java
public class PushMessage {
  private String mBrandId;
  private String mMessage;
  private String mFrom;
  private String mConversationId;
  private String mBackendService;
  private String mCollapseKey;
  private int mCurrentUnreadMessagesCounter = -1;
  //if we get unread messages counter from push message this value will contain it.
}
```

### LPConversationData


```java
public class LPConversationData{
  private CloseReason closeReason;
  private String conversationId;
}
```  

### PermissionType


```java
public enum PermissionType {
  PHOTO_SHARING
}  
```

### LPAuthenticationParams

```java
public class LPAuthenticationParams{
  private LPAuthenticationType mType;
    private String mAuthKey;
    private String mHostAppJWT;
    private String mHostAppRedirectUri;
    private List<String> mCertificatePinningKeys;

    public enum LPAuthenticationType {SIGN_UP, UN_AUTH, AUTH }
}
```

### ConversationViewParams

```javascript

public class ConversationViewParams{
  boolean viewOnlyMode = false;
  CampaignInfo mCampaignInfo;
  LPConversationsHistoryStateToDisplay mHistoryConversationsStateToDisplay = LPConversationsHistoryStateToDisplay.ALL;
  LPConversationHistoryMaxDaysDateType mHistoryConversationMaxDaysType = LPConversationHistoryMaxDaysDateType.startConversationDate;
  int mHistoryConversationsMaxDays = -1; //no limit
}
```

### LPConversationsHistoryStateToDisplay

```java
public enum LPConversationsHistoryStateToDisplay {
  OPEN, CLOSE , ALL
}

```


### LPConversationHistoryMaxDaysDateType

```java
public enum LPConversationHistoryMaxDaysDateType {
  startConversationDate, endConversationDate
}
```

**Monitoring API Related Classes**


### MonitoringInitParams

```java
public class MonitoringInitParams {
  private String mAppInstallId;
}
```

### MonitoringParams

```java
public class MonitoringParams {
  private String pageId;
  private JSONArray entryPoints;
  private JSONArray engagementAttributes;
}
```

### EngagementCallback

```java
public interface EngagementCallback {
  void onSuccess(LPEngagementResponse engagementResponse);
  void onError(MonitoringErrorType errorType, Exception e);
}
```

### SdeCallback

```java
public interface SdeCallback {
  void onSuccess(LPSdeResponse sdeResponse);
  void onError(MonitoringErrorType errorType, Exception e);
}
```

### LPEngagementResponse

```java

public final class LPEngagementResponse {
  @NotNull
  private String pageId;
  @Nullable
  private String sessionId;
  @Nullable
  private String visitorId;
  @Nullable
  private List<EngagementDetails> engagementDetailsList;
}
```

### LPSdeResponse

```java
public class LPSdeResponse {
  @NotNull
  private String pageId;
  @Nullable
  private final String sessionId;
  @Nullable
  private final String visitorId;
}
```

### EngagementDetails

```java
public final class EngagementDetails {
  @NotNull
  private  String campaignId;
  @NotNull
  private  String engagementId;
  @NotNull
  private  String engagementRevision;
  @NotNull
  private  String contextId;
  @Nullable
  private String conversationId;
  @Nullable
  private String status;
}
```

### MonitoringErrorType

```java
enum class MonitoringErrorType {
  NOT_INITIALIZED,
  INITIALIZATION_ERROR,
  LOGOUT_ERROR,
  PARAMETER_MISSING,
  NO_NETWORK,
  REQUEST_ERROR,
  CSDS_ERROR
}
```

### LPMonitoringIdentity (Kotlin syntax)

A class that contains data on the consumer identity.

consumerId - unique and non-guessable identifier of the consumer (email and phone number are not good candidates since they can be guessed by an attacker, and might be recycled and move between consumers).

issuer - Issuer, who identified the consumer - usually the brand.

```java
class LPMonitoringIdentity(val consumerId: String? = "", val issuer: String? = ""){
}
```
