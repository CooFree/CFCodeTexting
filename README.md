# CFCodeTexting

git使用  https://blog.csdn.net/qq_32531823/article/details/53259822

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
5.用代码使程序转向设置页面：
```
NSURL *url=[NSURL URLWithString:@"prefs:root=WIFI"];//转向->"设置wifi"页面
[[UIApplication sharedApplication] openURL:url];
```
