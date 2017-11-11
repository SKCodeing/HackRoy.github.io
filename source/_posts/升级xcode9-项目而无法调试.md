---
title: '升级xcode9,项目而无法调试'
date: 2017-11-11 16:39:35
tags: Xcode调试
---
之前xcode版本调试都是ok的


```objc
p.p1 {margin: 0.0px 0.0px 0.0px 12.0px; text-indent: -12.0px; font: 11.0px Menlo}p.p2 {margin: 0.0px 0.0px 0.0px 12.0px; text-indent: -12.0px; font: 11.0px Menlo; min-height: 13.0px}span.s1 {font: 11.0px 'PingFang SC'}
PhaseScriptExecution [CP]\ Copy\ Pods\ Resources /Users/lx/Library/Developer/Xcode/DerivedData/MyLibrary-ddrsgsrjpfocjoayxgljcmunezzw/Build/Intermediates.noindex/MyLibrary.build/Debug-iphoneos/MyLibrary.build/Script-788668C26D171DEEC02CAE5E.sh
cd /Users/lx/Desktop/MyLibrary/iphone/MyLibrary
/bin/sh -c /Users/lx/Library/Developer/Xcode/DerivedData/MyLibrary-ddrsgsrjpfocjoayxgljcmunezzw/Build/Intermediates.noindex/MyLibrary.build/Debug-iphoneos/MyLibrary.build/Script-788668C26D171DEEC02CAE5E.sh


/Users/lx/Desktop/MyLibrary/iphone/MyLibrary/Pods/MJRefresh/MJRefresh/MJRefresh.bundle
/Users/lx/Desktop/MyLibrary/iphone/MyLibrary/Pods/SVProgressHUD/SVProgressHUD/SVProgressHUD.bundle
/Users/lx/Desktop/MyLibrary/iphone/MyLibrary/Pods/UMengSocialCOM/Umeng_SDK_Social_iOS_ARM64_5.2.1/UMSocial_Sdk_5.2.1/UMSocialSDKResourcesNew.bundle
/Users/lx/Desktop/MyLibrary/iphone/MyLibrary/Pods/UMengSocialCOM/Umeng_SDK_Social_iOS_ARM64_5.2.1/UMSocial_Sdk_Extra_Frameworks/TencentOpenAPI/TencentOpenApi_IOS_Bundle.bundle
/Users/lx/Desktop/MyLibrary/iphone/MyLibrary/Pods/UMengSocialCOM/Umeng_SDK_Social_iOS_ARM64_5.2.1/UMSocial_Sdk_Extra_Frameworks/SinaSSO/WeiboSDK.bundle
ibtool --reference-external-strings-file --errors --warnings --notices --minimum-deployment-target 8.0 --output-format human-readable-text --compile /Users/lx/Library/Developer/Xcode/DerivedData/iLUXDAYEC-ddrsgsrjpfocjoayxgljcmunezzw/Build/Products/Debug-iphoneos/iLUXDAYEC.app/UMSCommentDetailController.nib /Users/lx/Desktop/MyLibrary/iphone/MyLibrary/Pods/UMengSocialCOM/Umeng_SDK_Social_iOS_ARM64_5.2.1/UMSocial_Sdk_5.2.1/SocialSDKXib/UMSCommentDetailController.xib --sdk /Users/lx/Desktop/个人/安装包/Xcode.app/Contents/Developer/Platforms/iPhoneOS.platform/Developer/SDKs/iPhoneOS11.0.sdk --target-device iphone
2017-09-22 11:22:24.608 ibtoold[28644:1474589] WARNING: Unhandled destination metrics: (null)
2017-09-22 11:22:24.608 ibtoold[28644:1474589] WARNING: Unhandled destination metrics: (null)
/* com.apple.ibtool.document.warnings */
/Users/lx/Desktop/MyLibrary/iphone/MyLibrary/Pods/UMengSocialCOM/Umeng_SDK_Social_iOS_ARM64_5.2.1/UMSocial_Sdk_5.2.1/SocialSDKXib/UMSCommentDetailController.xib:global: warning: This file is set to build for a version older than the deployment target. Functionality may be limited. [9]
/* com.apple.ibtool.document.errors */
/Users/lx/Desktop/MyLibrary/iphone/MyLibrary/Pods/UMengSocialCOM/Umeng_SDK_Social_iOS_ARM64_5.2.1/UMSocial_Sdk_5.2.1/SocialSDKXib/UMSCommentDetailController.xib:global: error: Compiling IB documents for earlier than iOS 7 is no longer supported. [12]
/* com.apple.ibtool.warnings */
/Users/lx/Desktop/MyLibrary/iphone/MyLibrary/Pods/UMengSocialCOM/Umeng_SDK_Social_iOS_ARM64_5.2.1/UMSocial_Sdk_5.2.1/SocialSDKXib/UMSCommentDetailController.xib: warning: Internationalization is not available when compiling for targets before iOS 6.0
Command /bin/sh failed with exit code 1
```

解决办法：点击Pods-->找到友盟的文件夹 然后找到Resources 找到那一堆XIB 点击右侧展开属性栏 找到interface Builder Document 吧Builds For 换成7.0以后 
