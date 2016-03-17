KakaoTalk Cordova Plugin
========================

A plugman compatible Cordova plugin for the KakaoTalk(https://developers.kakao.com)

Make sure you've registered your app with Kakao and to have an KAKAO_APP_KEY

Cordova Install Note:
========================

###Android

1. register kakao app on kakao developers(https://developers.kakao.com/apps)
2. get hash value from your kakao app, native app key
3. clone this project, $git clone https://github.com/lihak/KakaoTalkCordovaPlugin
4. cordova plugin add, $cordova plugin -d add ./KakaoTalkCordovaPlugin --variable KAKAO_APP_KEY=%YOUR_APP_KEY%

Kakao developers for android webpage: https://developers.kakao.com/docs/android#getting-started-launch-sample-app


###iOS

1. Install Kakao SDK (https://developers.kakao.com/docs/ios)
2. Add following code to appDelegate

```
#import <KakaoOpenSDK/KakaoOpenSDK.h>

- (BOOL)application:(UIApplication *)application openURL:(NSURL *)url
                                       sourceApplication:(NSString *)sourceApplication
                                              annotation:(id)annotation {

    ...
    if ([KOSession isKakaoAccountLoginCallback:url]){return [KOSession handleOpenURL:url];}
    ...
    
}

- (void)applicationDidBecomeActive:(UIApplication *)application{[KOSession handleDidBecomeActive];}
```

cordova plugin add https://github.com/lihak/KakaoTalkCordovaPlugin --variable KAKAO_APP_KEY=%KAKAO_APP_KEY%


How to use the plugin
========================

### Usage

This plugin adds an object to the window. Right now, you can only login and logout.

##### Login

Login using the `.login` method:
```
KakaoTalk.login(
    function (result) { // success
        console.log('Successful login!');
		console.log(result);
    },
    function (message) { // error
        console.log('Error logging in');
		console.log(message);
    }
);
```

The login reponse object is defined as:
```
{
  id: '<KakaoTalk User Id>',
  nickname: '<KakaoTalk User Nickname>',
  profile_image: '<KakaoTalk User ProfileImage>'
}
```

##### Logout

Logout using the `.logout` method:
```
Kakaotalk.logout(
	function() {
		console.log('Successful logout!');
	}, function() {
		console.log('Error logging out');
	}
);
```
