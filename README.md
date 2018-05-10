# CFCodeTexting


###### 关于git使用  
https://blog.csdn.net/qq_32531823/article/details/53259822

https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/0013758392816224cafd33c44b4451887cc941e6716805c000
```
提交代码到服务器后发现git clone下来的有些目录是空的。
查看服务器的目录果然是空的。看本季git add .    后查看git  status 

modified: xxx(modified content, untracked content)
大概意思是xxx目录没有被跟踪。那自然push上去的时候是空的了
解决办法：后来发现这主要是xxx目录下有一个.git 目录(隐藏文件，按shift+common+.可显示)，可能是被人给你这个目录的时候里面有了.git目录。删除.git目录。重新git add .就可
```
github排名 https://github.com/trending

python学习
https://github.com/521xueweihan/HelloGitHub


MVVM框架
https://github.com/LPD-iOS/LPDMvvmKit

打包framework的正确姿势
https://www.jianshu.com/p/ef5a888e57f2?from=timeline&isappinstalled=0

资料合集
https://github.com/onmyway133/fantastic-ios-animation
https://github.com/PoisonousMilk/TimLiu-iOS


图片裁剪、相册浏览<br>
https://github.com/longitachi/ZLPhotoBrowser<br>
https://github.com/yackle/CLImageEditor

### 微信小程序开发
https://www.zhihu.com/question/50907897



# 代码小片段

##### 1.键盘透明
```
textField.keyboardAppearance = UIKeyboardAppearanceAlert;
```

##### 2.状态栏的网络活动风火轮是否旋转
```
[UIApplication sharedApplication].networkActivityIndicatorVisible，默认值是NO。
```

##### 3.NSMutableAttributedString 行间距、段落间距 
```
NSMutableAttributedString *attributedString = [[NSMutableAttributedString alloc] initWithString:dLabelString];  
NSMutableParagraphStyle   *paragraphStyle   = [[NSMutableParagraphStyle alloc] init];  

//行间距  
[paragraphStyle setLineSpacing:5.0];  
//段落间距  
[paragraphStyle setParagraphSpacing:10.0];  
//第一行头缩进  
[paragraphStyle setFirstLineHeadIndent:15.0];  
//头部缩进  
//[paragraphStyle setHeadIndent:15.0];  
//尾部缩进  
//[paragraphStyle setTailIndent:250.0];  
//最小行高  
//[paragraphStyle setMinimumLineHeight:20.0];  
//最大行高  
//[paragraphStyle setMaximumLineHeight:20.0];  
      
[attributedString addAttribute:NSParagraphStyleAttributeName value:paragraphStyle range:NSMakeRange(0, [dLabelString length])];  
[dLabel setAttributedText:attributedString];  
```

##### 4.跳转storyBoard
```
   1.获取第一个视图storyBoard
    /* 加载名为storyboardName的Storyboard */
    UIStoryboard *storyboard = [UIStoryboard storyboardWithName:storyboardName bundle:nil];
    
    /* 获取storyboard的InitialViewController 即根控制器*/
    FirstViewController *vc = [storyboard instantiateInitialViewController];
    其中UIViewController可以根据当前视图进行替换，替换成StoryBoard对应的视图类，然后选择跳转方式
    2.获取第二个视图storyboard的某个视图控制器的时候使用
     SecondViewController *VC= [storyboard instantiateViewControllerWithIdentifier:@"NewVC”];(这个过程需要在StoryBoard中设置目标视图的Custom Class和StoryBoard ID)
    //跳转事件的实现
    在第一个视图添加按钮跳转到第二个视图
    [self.navigationController pushViewController:VC animated:YES];(第一个视图是带有导航栏的)
```
##### 5.用代码使程序转向设置页面：
```
NSURL *url=[NSURL URLWithString:@"prefs:root=WIFI"];//转向->"设置wifi"页面
[[UIApplication sharedApplication] openURL:url];
```
##### 6.系统判断
```
#define isOperatingSystemAtLeastVersion(majorVersion, minorVersion, patchVersion)[[NSProcessInfo processInfo] isOperatingSystemAtLeastVersion: (NSOperatingSystemVersion) {
    majorVersion,
    minorVersion,
    patchVersion
}]

if (isOperatingSystemAtLeastVersion(11, 0, 0)) {
    //using new API
} else {
    //using deprecated API
}

```

##### 7. web Cookies 每次退出应用都被清除解决方法( 用于实现自动登录 )https://www.jianshu.com/p/19a053e37c53
```
NSHTTPCookieStorage* cookieStorage = [NSHTTPCookieStorage sharedHTTPCookieStorage];
    NSArray<NSHTTPCookie *> *cookies = [cookieStorage cookiesForURL:[NSURL URLWithString:baseUrl]];
    NSMutableArray<NSDictionary *> *propertiesList = [[NSMutableArray alloc] init];
    [cookies enumerateObjectsUsingBlock:^(NSHTTPCookie * _Nonnull cookie, NSUInteger idx, BOOL * _Nonnull stop) {
        NSMutableDictionary *properties = [[cookie properties] mutableCopy];
        //将cookie过期时间设置为一年后
        NSDate *expiresDate = [NSDate dateWithTimeIntervalSinceNow:3600*24*30*12];
        properties[NSHTTPCookieExpires] = expiresDate;
        //下面一行是关键,删除Cookies的discard字段，应用退出，会话结束的时候继续保留Cookies
        [properties removeObjectForKey:NSHTTPCookieDiscard];
         //重新设置改动后的Cookies
        [cookieStorage setCookie:[NSHTTPCookie cookieWithProperties:properties]];
    }];
```
