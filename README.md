# ColorWonderful
收藏－－颜色值的封装，求rgb值，一个颜色相反的色值，很有意思的库

# Wonderful
一个关于色彩的库
####效果图
_demo展示，提供了随机配色。_<br />
![image](https://github.com/dsxNiubility/Wonderful/raw/master/screenshots/001.png)


_颜色列表_<br />
![image](https://github.com/dsxNiubility/Wonderful/raw/master/screenshots/colorlist.gif)

####一、UIColor+Wonderful

1.这个分类里扩充了更多的颜色扩展，以后随手写个小Demo再也不需要redColor buleColor了。<br />

self.view.backgroundColor = [UIColor khakiColor];
self.view.backgroundColor = [UIColor chocolateColor];

2.平均每个色系有10种颜色，不仅可以使用名称直接敲出，还能使用颜色阶梯的宏敲出，在你想不起词的时候更加方便。 宏从1～10是颜色渐深，可以根据自己的感觉使用浅一级的宏或深一级的宏。<br />

self.view.backgroundColor = Wonderful_YelloeColor4;
self.view.backgroundColor = Wonderful_BrownColor4;

3.提供了颜色微调方案，可以让一个已知颜色的rgb的某值上升或下降若干，可用于不管背景是什么色，边框都比背景深20。 也可以将认可颜色的详细值打印出来。<br />

UIColor *navColor = [[UIColor redColor]up:SXColorTypeBlue num:30]; // 在红色上把蓝色色值提高30
UIColor *barColor = [[UIColor blueColor]up:1 num:140]; // 可以直接用枚举对应的tag
UIColor *bgColor = [[UIColor blackColor]down:SXColorTypeAlpha num:10]; // 取一个比黑色稍微淡的颜色
UIColor *lineColor = [bgColor up:3 num:20]; // 不管背景是什么颜色 线都比背景浅20.

####二、UIColor+Separate
1.提供颜色分离方案，可以将任何颜色的rgb喝alpha的值取出。<br />

UIColor *testC = [UIColor salmonColor];
float r= [testC red];
float g= [testC green];
float b= [testC blue];
float alpha= [testC alpha];
NSLog(@"******  %f,%f,%f,%f",r,g,b,alpha);

2.可以通过一个颜色算出此颜色的反色，使得背景无论被用户设置成什么色，文字颜色都是背景的反色。<br />

self.showLbl1.backgroundColor = [UIColor peachRed];
self.showLbl1.textColor = [[UIColor peachRed]reverseColor];

3.也可以直接打印这个颜色的各项详细数值。<br />

[[UIColor salmonColor]printDetail];
// 打印结果
This Color's Red:250, Green:128, Blue:114, Alpha:1
decimal red:0.9804 green:0.5020 blue:0.4471
Hexadecimal 0xfa8072


####三、SXColorGradientView
1.颜色渐变的view，可以设置任何颜色到透明的过渡。<br />

SXColorGradientView *grv1 = [SXColorGradientView createWithColor:[UIColor paleGreen] frame:CGRectMake(10, 10, 80, 30) visible:YES direction:SXColorGradientToRight];

2.也可以设置两个颜色相互过渡。<br />

SXColorGradientView *grv3 = [SXColorGradientView createWithFromColor:[UIColor peruColor] toColor:[UIColor ghostWhite] frame:CGRectMake(10, 50, 80, 30) direction:SXColorGradientToRight];

3.可以设置向上下左右四个过渡的方向。<br />

typedef NS_ENUM(NSInteger, SXColorGradientDirection) {
SXColorGradientToTop = 1,
SXColorGradientToLeft = 2,
SXColorGradientToBottom = 3,
SXColorGradientToRight = 4,
};
＊4.后续会增加传入一个数组，然后搭建一个多个颜色过渡的view。

####四、SXMarquee
1.实现任何样式的跑马灯。<br />

SXMarquee *mar3 = [[SXMarquee alloc]initWithFrame:CGRectMake(20, 390, 335, 25) speed:2 Msg:@"If you've submitted an update to fix a critical bug in your app on the App Store and you are requesting an expedited review." bgColor:[UIColor goldColor] txtColor:[UIColor goldenrod]];
[mar3 changeMarqueeLabelFont:[UIFont boldSystemFontOfSize:12]]; // 可以用默认也可以配置更多属性
[mar3 start];

2.跑马灯的背景可以设置任何颜色，这个是基于颜色过渡view做的。<br />
3.跑马灯可以实现点击拖动，或者绑定更多点击事件。