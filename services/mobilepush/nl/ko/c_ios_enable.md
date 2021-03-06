---

copyright:
 years: 2015, 2016

---

#{{site.data.keyword.mobilepushshort}}을 수신하고 전송하도록 iOS 애플리케이션 설정
{: #enable-push-ios-notifications}
마지막 업데이트 날짜: 2016년 10월 19일
{: .last-updated}

iOS 애플리케이션이 {{site.data.keyword.mobilepushshort}}을 수신하고 사용자 디바이스에 전송하도록 설정할 수 있습니다.


##CocoaPods 설치
{: #enable-push-ios-notifications-install}

기존 Xcode 프로젝트의 경우 CocoaPods 종속 항목 관리 도구를 사용하여 Bluemix Mobile Services Client SDK를 설정할 수 있습니다. 또는 SDK를 수동으로 설치할 수 있습니다. 

Swift 푸시 readme 파일을 보려면 [Readme](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-push/tree/master)로 이동하십시오. 



1. Mac 터미널에서 다음 명령을 사용하여 CocoaPods를 설치하십시오.
```
$ sudo gem install cocoapods
```
	{: codeblock}
2. 터미널에 `pod init` 명령을 입력하여 CocoaPods를 초기화하십시오. Xcode 프로젝트가 있는 디렉토리에서 명령을 실행하십시오. `pod init` 명령에서 Podfile을 작성합니다.  
3. 생성된 Podfile에 필요한 SDK 종속 항목을 추가하십시오. 환경 설정에 따라 다음 Podfile 중 하나를 복사하십시오. 
 
**Objective-C**
   
```
source 'https://github.com/CocoaPods/Specs.git'
	# Copy the following list as is and remove the dependencies you do not need.
	pod 'IMFCore'
	pod 'IMFPush'
```
	{: codeblock}

**Swift**
   
```
source 'https://github.com/CocoaPods/Specs.git'
	# Copy the following list as is and remove the dependencies you do not need.
use_frameworks!
target 'MyApp' do
platform :ios, '9.0'
pod 'BMSCore'
pod 'BMSPush'
pod 'BMSAnalyticsAPI'
end
```
	{: codeblock}

3. 터미널에서 프로젝트 폴더로 이동한 후 `pod update` 명령을 사용하여 종속 항목을 설치하십시오. 

이 명령은 종속 항목을 설치하고 새 Xcode 작업공간을 작성합니다.   
**참고**: 원래 Xcode 프로젝트 파일 대신, 반드시 항상 새 Xcode 작업공간을 여십시오. 
```
$ open App.xcworkspace
	```
	{: codeblock}

작업공간에는 원래 프로젝트 및 종속 항목이 포함된 Pods 프로젝트가 있습니다. Bluemix Mobile Services 소스 폴더를 수정하려는 경우 Pods 프로젝트의 `Pods/yourImportedSourceFolder`에서 이 폴더를 찾을 수 있습니다(예: `Pods/BMSPush`).

##Carthage
{: #carthage}

[Carthage](https://github.com/Carthage/Carthage#if-youre-building-for-ios-tvos-or-watchos)를 사용하여 프로젝트에 프레임워크를 추가하십시오. Xcode8의 Carthage는 지원되지 않습니다. 

1. `BMSPush` 프레임워크를 Cartfile에 추가하십시오. 
```
github "github "ibm-bluemix-mobile-services/bms-clientsdk-swift-push" ~> 1.0"
```
	{: codeblock}
2. `carthage update` 명령을 실행하십시오. 빌드가 완료되면 `BMSPush.framework`, `BMSCore.framework`, `BMSAnalyticsAPI.framework`를 Xcode 프로젝트로 끌어오십시오. 
3. [Carthage](https://github.com/Carthage/Carthage#if-youre-building-for-ios-tvos-or-watchos) 사이트의 지시사항에 따라 통합을 완료하십시오.


##가져온 프레임워크 및 소스 폴더 사용
{: using-imported-frameworks}

코드에서 SDK를 참조하십시오. 환경 설정에 따라 다음 방법 중 하나를 사용하십시오. 

**Objective-C**

관련 헤더에 대해 `#import` 지시문을 작성합니다. 예: 

```
	//Objective-C
 #import <IMFCore/IMFCore.h>
 #import <IMFPush/IMFPush.h>
```
	{: codeblock}

**참고**: CocoaPods 명령 `pod install` 또는 `pod update`를 사용하여 Pods 프로젝트를 업데이트하면 Bluemix Mobile Services 소스 폴더가 대체될 수 있습니다. 원래 파일의 사용자 정의한 버전을 유지하려면, 이러한 명령을 실행하기 전에 해당 버전을 백업해야 합니다. 

**Swift**

다음 전제조건을 충족해야 합니다. 

- iOS 8.0 이상
- Xcode 7


관련 헤더에 대해 `#import` 지시문을 작성합니다. 예: 
```
//swift
import BMSCore
import BMSPush
```
	{: codeblock}
Swift 푸시 readme 파일을 보려면 [Readme](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-push/tree/master)로 이동하십시오.

##빌드 설정
{: build-settings}

**Xcode > 빌드 설정 > 빌드 옵션 및 Bitcode 사용 설정**으로 이동하여 **No**로 설정하십시오.

**주의**: iOS 9의 경우, ATS(App Transport Security) 기능을 변경하면 인증 프로세스의 처리 방식에 영향이 미칠 수 있습니다. 블로그 포스팅 [iOS 9의 ATS 및 Bitcode](https://developer.ibm.com/mobilefirstplatform/2015/09/09/ats-and-bitcode-in-ios9/), [지금 Bluemix에 iOS 9 앱 연결](https://developer.ibm.com/bluemix/2015/09/16/connect-your-ios-9-app-to-bluemix/)에서 이러한 변경에 대해 자세히 설명합니다. 

## iOS 앱을 위한 푸시 SDK 초기화
{: #enable-push-ios-notifications-initialize}

초기화 코드를 배치하는 공통 위치는 iOS 애플리케이션에 대한 애플리케이션 위임자입니다. 푸시 대시보드의 **모바일 옵션** 링크를 클릭하여 애플리케이션 라우트와 GUID를 가져오십시오. 

###Core SDK 초기화
{: Initializing-the-core-sdk}

**Objective-C**

```
// Initialize the SDK for Object-C with IBM Bluemix GUID and route
IMFClient *imfClient = [IMFClient sharedInstance];
[imfClient initializeWithBackendRoute:"add_your_applicationRoute_here" backendGUID:"add_your_appId_here"];
```
	{: codeblock}

**Swift**

```
// Initialize the Core SDK for Swift with IBM Bluemix GUID, route, and region
let myBMSClient = BMSClient.sharedInstance
myBMSClient.initialize(bluemixRegion: "Location where your app is hosted.") 
myBMSClient.defaultRequestTimeout = 10.0 // Timeout in seconds
```
	{: codeblock}

### 라우트, GUID 및 Bluemix 리젼
{: route-guid-bluemix-region}

####appRoute
{: ios-approute}

Bluemix에서 생성한 서버 애플리케이션에 지정된 라우트를 지정합니다.

####GUID
{: ios-guid}

Bluemix에서 생성한 애플리케이션에 지정된 고유 키를 지정합니다. 이 값은 대소문자를 구분합니다. 

####bluemixRegionSuffix
{: ios-bluemixRegionSuffix}

앱이 호스트된 위치를 지정합니다. `bluemixRegion` 매개변수는 사용 중인 Bluemix 배치를 지정합니다. 이 값을 `BMSClient.REGION` 정적 특성으로 설정하고 세 값 중 하나를 사용할 수 있습니다. 

- BMSClient.REGION_US_SOUTH
- BMSClient.REGION_UK
- BMSClient.REGION_SYDNEY

####AppGUID
{: ios-AppGUID}

Bluemix에서 작성한 {{site.data.keyword.mobilepushshort}} 서비스에 지정되는 고유 AppGUID 키를 지정합니다.

###클라이언트 푸시 SDK 초기화
{: initializing-the-client-Push-SDK}

**Objective-C**

```
//Initialize client Push SDK for Objective-C
IMFPushClient *push = [IMFPushClient sharedInstance];
[push initializeWithAppGUID:@"appGUID" clientSecret:@"clientSecret"];
```
	{: codeblock}

**Swift**

```
//Initialize client Push SDK for Swift
let push = BMSPushClient.sharedInstance
push.initializeWithAppGUID("appGUID", clientSecret:"clientSecret")
```
	{: codeblock}


## iOS 애플리케이션 및 디바이스 등록
{: #enable-push-ios-notifications-register}


디바이스에 애플리케이션을 설치한 후 원격 알림을 수신하려면 애플리케이션을 APNs에 등록해야 합니다. APNs에서 생성한 디바이스 토큰을 앱에서 수신한 후에는 {{site.data.keyword.mobilepushshort}} 서비스에 이를 되돌려 보내야 합니다. 

iOS 애플리케이션과 디바이스를 등록하려면 다음을 수행해야 합니다. 

1. 백엔드 애플리케이션을 작성하십시오. 
2. 토큰을 {{site.data.keyword.mobilepushshort}}에 전달하십시오. 


###백엔드 애플리케이션 작성
{: create-a-backend-app}

Boilerplates 섹션 Bluemix® 카탈로그에서 {{site.data.keyword.mobilepushshort}} 서비스를 이 애플리케이션에 자동으로 바인드하는 백엔드 애플리케이션을 작성하십시오. 백엔드 앱을 이미 작성한 경우에는 앱을 {{site.data.keyword.mobilepushshort}} 서비스에 바인드했는지 확인하십시오. 

**Objective-C**

```
//For Objective-C
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
if ([[[UIDevice currentDevice] systemVersion] floatValue] >= 8.0){
         [[UIApplication sharedApplication] registerUserNotificationSettings:[UIUserNotificationSettings settingsForTypes:(UIUserNotificationTypeSound | UIUserNotificationTypeAlert | UIUserNotificationTypeBadge) categories:categories]];
	    [[UIApplication sharedApplication] registerForRemoteNotifications];
	    }
	    else{
	    [[UIApplication sharedApplication] registerForRemoteNotificationTypes:
	    (UIUserNotificationTypeBadge | UIUserNotificationTypeSound | UIUserNotificationTypeAlert)];
	    }
	    return YES;
	}
```
	{: codeblock}

**Swift**

```
//For Swift
func application(application: UIApplication, didFinishLaunchingWithOptions launchOptions: [NSObject: AnyObject]?) -> Bool {
 let settings = UIUserNotificationSettings(forTypes: [.Alert, .Badge, .Sound], categories: nil)
    UIApplication.sharedApplication().registerUserNotificationSettings(settings)
    UIApplication.sharedApplication().registerForRemoteNotifications()
	}
```
	{: codeblock}

###{{site.data.keyword.mobilepushshort}}에 토큰 전달
{: pass-token-push-notifications}

APNs에서 토큰이 수신되면 `registerWithDeviceToken` 메소드의 일부로 {{site.data.keyword.mobilepushshort}}에 토큰을 전달하십시오. 

**Objective-C**

```
//For Objective-C
		-( void) application:( UIApplication *)application didRegisterForRemoteNotificationsWithDeviceToken:( NSData *)deviceToken{
     IMFClient *client = [IMFClient sharedInstance];
	[client initializeWithBackendRoute: @"your-backend-route-here" backendGUID: @"Your-backend-GUID-here"];
	// get Push instance
	IMFPushClient* push = [IMFPushClient sharedInstance];
	[push initializeWithAppGUID:@"appGUID"];
	[push registerWithDeviceToken:deviceToken completionHandler:^(IMFResponse *response,  NSError *error) {
    if (error){
     NSLog(@"%@",error.description);
    }  else
  {
    NSLog(@"%@",response.responseJson.description);
  }
}];
 }
```
	{: codeblock}

**Swift**

APNs로부터 토큰이 수신되면 이 토큰을 `didRegisterForRemoteNotificationsWithDeviceToken` 메소드의 일부로 푸시 알림에 전달하십시오. 

```
func application (application: UIApplication, didRegisterForRemoteNotificationsWithDeviceToken deviceToken: NSData){
   let push =  BMSPushClient.sharedInstance
   push.initializeWithAppGUID("appGUID")
   push.registerWithDeviceToken(deviceToken) { (response, statusCode, error) -> Void in
       if error.isEmpty {
            print( "Response during device registration : \(response)")
            print( "status code during device registration : \(statusCode)")
        }
        else{
            print( "Error during device registration \(error) ")
            print( "Error during device registration \n  - status code: \(statusCode) \n Error :\(error) \n")
        }
    }
	}
```
	{: codeblock}


## iOS 디바이스에서 푸시 알림 수신
{: #enable-push-ios-notifications-receiving}

다음 방법 중 하나를 사용하여 iOS 디바이스에서 푸시 알림을 수신할 수 있습니다. 

**Objective-C**

iOS 디바이스에서 푸시 알림을 수신하려면 애플리케이션의 위임자에 다음 Objective-C 메소드를 추가하십시오.

```
// For Objective-C
-(void)application:(UIApplication *)application didReceiveRemoteNotification:(NSDictionary *)userInfo {
//userInfo dictionary will contain data sent from server.
}
```
	{: codeblock}

**Swift**

iOS 디바이스에서 푸시 알림을 수신하려면 애플리케이션의 위임자에 다음 Swift 메소드를 추가하십시오.
```
// For Swift
func application(application: UIApplication, didReceiveRemoteNotification userInfo: [NSObject : AnyObject], fetchCompletionHandler completionHandler: (UIBackgroundFetchResult) -> Void) {
//UserInfo dictionary will contain data sent from the server
    }
```
	{: codeblock}

## 기본 푸시 알림 전송
{: #send}

애플리케이션을 개발한 후에는 기본 푸시 알림을 전송할 수 있습니다. 

기본 푸시 알림을 전송하려면 다음 단계를 완료하십시오. 

1. **알림 전송**을 선택하고 **받는 사람** 옵션을 선택하여 메시지를 작성하십시오. 지원되는 옵션은 **태그별 디바이스**, **디바이스 ID**, **사용자 ID**, **Android 디바이스**, **iOS 디바이스**, **웹 알림** 및 **모든 디바이스**입니다.
**참고**: **모든 디바이스** 옵션을 선택하는 경우 {{site.data.keyword.mobilepushshort}}을 구독하는 모든 디바이스가 알림을 수신합니다.
![알림 화면](images/tag_notification.jpg)

2. **메시지** 필드에 메시지를 작성하십시오. 필요에 따라 선택적 옵션을 구성하도록 선택하십시오.
3. **전송**을 클릭하십시오. 
3. 디바이스가 알림을 수신했는지 확인하십시오. 

다음 이미지는 iOS 디바이스에서 {{site.data.keyword.mobilepushshort}}을 처리하는 경보 상자를 표시합니다.

![iOS의 포그라운드 푸시 알림](images/iOS_Screenshot.jpg) 

### 알림 전송을 위한 선택적 설정
{: #send_ios_otpional_setting}

iOS 디바이스에 알림을 전송하기 위해 {{site.data.keyword.mobilepushshort}} 설정을 추가로 사용자 정의할 수 있습니다. 다음과 같은 선택적 사용자 정의 옵션이 지원됩니다.

- **배지**: 애플리케이션 배지에 표시되는 숫자를 나타냅니다. 기본값은 영(0)이며, 이 값은 배지를 표시하지 않습니다. 
- **사운드**: 알림을 수신할 때 재생되는 사운드 클립을 표시합니다. 기본값 또는 앱에 번들링된 사운드 리소스의 이름을 지원합니다.
- **추가 페이로드**: 알림에 대한 사용자 정의 페이로드 값을 지정합니다.


## 다음 단계
{: #next_steps_tags}

정상적으로 기본 알림을 설정한 후 태그 기반 알림 및 고급 옵션을 구성할 수 있습니다. 

다음의 푸시 알림 서비스 기능을 사용자의 앱에 추가하십시오.
태그 기반 알림을 사용하려면 [태그 기반 알림](c_tag_basednotifications.html)을 참조하십시오.
고급 알림 옵션을 사용하려면 [고급 푸시 알림 사용](t_advance_badge_sound_payload.html)의 내용을 참조하십시오. 
