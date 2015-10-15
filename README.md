KakaoTalk Cordova Plugin
========================

A plugman compatible Cordova plugin for the KakaoTalk(https://developers.kakao.com) Cordova Plugin.


Cordova Install Note:
========================

__Android

nothing to do ;-)


__iOS

1. Install Kakao SDK (https://developers.kakao.com/docs/ios)
2. Add following code to appDelegate

// IMPORT!!!
__import <KakaoOpenSDK/KakaoOpenSDK.h>
- (BOOL)application:(UIApplication *)application openURL:(NSURL *)url
                                       sourceApplication:(NSString *)sourceApplication
                                              annotation:(id)annotation {
    ...
    
	
    __if ([KOSession isKakaoAccountLoginCallback:url]) {
        __return [KOSession handleOpenURL:url];
    __}
    
    ...
}

// Complete METHOD!!!

__- (void)applicationDidBecomeActive:(UIApplication *)application{
    __[KOSession handleDidBecomeActive];
__}


cordova plugin add https://github.com/lihak/KakaoTalkCordovaPlugin --variable KAKAO_APP_KEY=<KAKAO_APP_KEY>


How to use the plugin
========================

### Usage

This plugin adds an object to the window. Right now, you can only login and logout.

##### Login

Login using the `.login` method:
```
KakaoTalk.login({
    success: function (result) {
        console.log('Successful login!');
		console.log(result);
    },
    error: function (message) {
        console.log('Error logging in');
		console.log(error);
    }
});

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
  },
  function() {
    console.log('Error logging out');
  }
);
```
