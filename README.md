# CFCodeTexting

github排名 https://github.com/trending

python学习
https://github.com/521xueweihan/HelloGitHub


MVVM框架
https://github.com/LPD-iOS/LPDMvvmKit


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

##### 3.
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
