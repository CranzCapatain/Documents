# Documents
分享一些技术上的知识

> iOS知识点
##### 应用内跳转到系统内app特定设置的方法

```Objective-C

NSURL *url;
if ([UIDevice currentDevice].systemVersion.floatValue >= 10.0) {
    url = [NSURL URLWithString:[NSString stringWithFormat:@"APP-Prefs:root=%@",[[NSBundle mainBundle] objectForInfoDictionaryKey:@"CFBundleIdentifier"]]];
    if ([[UIApplication sharedApplication] canOpenURL:url]) {
        [[UIApplication sharedApplication] openURL:url options:@{} completionHandler:nil];
    }
} else {
    url = [NSURL URLWithString:[NSString stringWithFormat:@"prefs:root=%@",[[NSBundle mainBundle] objectForInfoDictionaryKey:@"CFBundleIdentifier"]]];
    if ([[UIApplication sharedApplication] canOpenURL:url]) {
        [[UIApplication sharedApplication] openURL:url];
    }
}
            
```
