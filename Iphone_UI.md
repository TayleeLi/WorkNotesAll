Hello World

//2014_0423_1956
    Thanks for your sharing!

//Iphone开发入门

//-IOS系统的概述与架构
    架构
        IOS扮演底层硬件和应用程序的中介
        创建的应用程序不能直接访问硬件，而需要和系统接口进行交互
        系统接口转而又去和适当的驱动打交道
        |---------Cocoa Touch---------|
        |------------Media------------|
        |--------Core Services--------|
        |-----------Core OS-----------|
        
        IOS实现可以看作是多个层的集合，底层为所有应用程序提供基础服务，高层则包含一些复杂巧妙的服务和技术
        
    Cocoa Touch层
        提供基本的系统行为支持，将你的工作量降到最低，当你想要实现更为复杂的行为和界面时，才考虑向下层探寻技术支持
        UIKit框架：UIKit提供了一些程序运行所必须得关键对象，使得App能够捕获用户输入在屏幕上显示内容
        MapKit框架：IOS 3.0引入该框架，该框架提供一个可被嵌入到应用程序的地图界面，该界面包含一个可以滚动的地图视图
        Address Book UI框架：IOS 3.0引入该框架，可以利用该框架撰写电子邮件，并将其放入到用户的发件箱排队等候发送
        Message UI框架：显示创建或者编辑联系人的标准系统界面

    Media层
        包含图形，音频，视频等技术
        Quartz Core框架：包含Core Animation接口。Core Animation是高级动画制作和混合技术，它使用经过优化的渲染路径实现复杂的动画和视觉效果
        Media Player框架：应用程序播放视频和音频内容
        AV Foundation框架：该框架包含Objective-C类可用于播放音频内容
        Core Graphics框架：(CoreGraphics.framework)包含Quartz 2D绘图API接口。该框架基于C接口，提供绘图功能
        
    Core Services
        提供基础系统服务。可能应用程序并不直接使用这些服务，但它们是系统很多部分依赖以建构的基础
        Foundation框架：为Core Foundation框架的许多功能提供Objective-C封装
        Core Foundation框架：是一组C语言接口，它们为IOS应用程序提供基本数据管理和服务功能
        Core Location框架：可用于定位某个设备当前经纬度
        其他框架：CFNetwork框架，Core Data框架，Core Media框架，Core Telephony框架，Event Kit框架，Mobile Core Services框架，Quick Look框架，Store Kit框架，System Configuration框架

//-IOS平台限制
    平台间的差异
    屏幕大小限制
    内存限制
    窗口限制
    电量限制
    简短的用户帮助
    IOS多任务
    IOS开发的三种方式

//-集成环境的介绍
    Xcode
    Interface
    Instruments
    iPhone Simulator
    IOS SDK

//-我们的第一个程序————HelloWorld
    Interface Builder构建我们的程序
    NSArray *views = [[NSBundle mainBundle] loadNibNamed:@"View" owner:self options:nil];
    NSBundle类
    使用NSBundle可以访问程序包里的资源，xib存储在程序包中，所以可以使用NSBundle加载xib文件

//-应用程序的文件组织
    项目文件组织
    项目文件释义
        supporting Files
            plist文件：应用程序相关设置(属性)的文件
            strings文件：设置应用程序本地化的文件
            main.m：程序入口
            pch文件：程序的预处理文件
        frameworks
            存放框架位置
        products
            应用程序执行文件
    常用属性说明
        CFBundleDevelopmentRegion       //本地化相关，如果用户所在地没有相应的语言资源
        CFBundleDisplayName             //应用程序下显示的程序名
        CFBundleIdentifier              //该app的唯一标识
        CFBundleInfoDictionaryVersion   //Info.plist格式的版本
        CFBundleVersion                 //应用程序版本号
        UIStatusBarStyle                //状态栏类型
        UIRequiresPerssistentWifi       //在程序中弹出wifi选择的key(系统设置中需要将wifi提示打开)
        CFBundleIconFile                //该app图标文件名，不填默认是icon.png
        UILanchImageFile                //该app启动图片，不填默认是Default.png

//-模拟器常用操作
    选取设备
    旋转设备
    返回首页
    锁定
    模拟内存警告
    呼叫状态栏目
    拷贝屏幕以及屏幕快照
    常用快捷键

//-应用程序的生命周期
    应用程序的生命周期是由发生在程序启动到终止期间的一序列事件构成的。
    _________________________________________________    _____________________________________________
    |                     UIKit                     |    |                 Your code                 |
    |-----------------------------------------------|    |-------------------------------------------|
    |           ----------------------------        |    |                                           |
    |           |User taps application icon|        |    |                                           |
    |           ----------------------------        |    |                                           |
    |                       |                       |    |                                           |
    |                       Ⅴ                       |    |                                           |
    |           ----------------------------        |    |                                           |
    |           |         main()           |        |    |                                           |
    |           ----------------------------        |    |                                           |
    |                       |                       |    |                                           |
    |                       Ⅴ                       |    |                                           |
    |           ----------------------------        |    |      --------------------------------     |
    |           |   UIApplicationMain()    | <------|----|----> |ApplicationDidFinishLaunching:|     |
    |           ----------------------------        |    |      --------------------------------     |
    |                       |                       |    |                                           |
    |                       Ⅴ                       |    |                                           |
    |                | <-----------<                |    |      --------------------------------     |
    |                | Event Loop  | <--------------|----|----> |         Handle event         |     |
    |                V -----—----> |                |    |      --------------------------------     |
    |                       |                       |    |                                           |
    |                       Ⅴ                       |    |                                           |
    |    ---------------------------------------    |    |      --------------------------------     |
    |    |System asks applications to terminate| <--|----|----> |   ApplicationWillTerminate:  |     |
    |    ---------------------------------------    |    |      --------------------------------     |
    |                       |                       |    |                                           |
    |                       Ⅴ                       |    |                                           |
    |    ---------------------------------------    |    |                                           |
    |    |   Application exeution terminates   |    |    |                                           |
    |    ---------------------------------------    |    |                                           |
    —————————————————————————————————————————————————    —————————————————————————————————————————————
    
    主函数
    在iPhone的应用程序中，main函数仅在最小程度上被使用，应用程序运行所需的大多数实际工作由UIApplicationMain函数来处理.
    main例程只做三件事：创建--一个自动释放池，调用UIApplicationMain函数，以及释放自动释放池。
    
//2014_0423
//窗口与视图基本概念和用法
    UIKit是一个提供了在IOS上实现图形，事件驱动程序的框架
        UIView是视图的基类
        UIViewController视图控制器的基类
        UIResponder表示一个可以接受触摸事件的对象
        窗口是视图的一个子类。窗口的主要功能：一是提供一个区域来显示视图，二是将事件(event)分发给视图，一个应用通常只有一个窗口，但也有列外。
//-UIWindow与UIView的关系
    在IOS中，使用窗口与视图在屏幕上显示应用程序的内容。窗口本身不具有任何内容，但它对于应用程序的视图提供一个基本的容器。视图定义你想要用的一些内容填充的窗口的以部分。例如，可能显示图形，文本，形状或某种组合的视图。还可以使用视图来组织和管理其他视图。
    通常窗口用UIWindow类的实例来表示。注意UIWindow继承自UIView
    window对象有以下职责
        它包含了应用程序的可视化的内容
        它为视图和其他应用程序对象在触摸中提供了关键性的作用
        它与视图控制器一起协作来呈现数据
    大多数IOS应用程序在其生命周期内只有一个UIWindow。并且在应用程序的生命周期中，窗口跨越整个设备的主屏幕和从应用程序的主nib文件被加载(或以编程方法创建)。但是，如果应用程序支持的外部显示器使用的视频输出，它可以创建额外的窗口，以显示该外部显示器上的内容。所有其他的窗口通常由系统创建，并且通常在响应特定的时间的时候创建的，如传入的电话呼叫。
    //0426
    *手动创建
    *通过Xib来创建，通过mainWindow.xib文件加载进行实例化
        self.window = [[[UIWindow alloc] initWithFrame:[[UIScreen mainScreen] bounds]] autorelease];
        self.wondow.rootViewController = self.viewController;
        [self.window makeKeyAndVisible];
    UIScreen
        UIScreen对象可以充当IOS设备物理屏幕的代替者，[[UIScreen mainScreen] bounds]获取设备屏幕大小，如iPhone和iPad的尺寸不一样，如果要做的比较通用应该使用UIScreen类来获取尺寸。
        虽然IOS支持将一个窗口叠放在其他窗口的上方，但是你的应用程序永远不会创建多个窗口，因为会影响事件的传递。
    手机屏幕的几个概念
        Screen size：屏幕尺寸，指具体的屏幕物理长度，以屏幕对角线的长度作为标示。
        Resolution：屏幕分辨率，指屏幕上总共的物理像素点。
        Density：密度，标示每英寸有多少个显示点。density是以分辨率为基础，即指在固定分配率上散开的像素点，也就是说屏幕的density越大。
        ASPECT RATIO：屏幕宽高比例。也就是平时我们说的宽高比为4:3
        Device-independent pixe：dip，设备无关像素。dip是一种虚拟的像素单位，专门用来给程序定义UI用
        色阶：也就是我们平时说的65536色，26万色，1600万色并没有数字看起来差别那么大，这实际上只是表示相邻的三个色阶而已，当然，1600万色显示效果是最好的。
    iPhone屏幕尺寸
        iPhone4前的设备屏幕：320*480
        iPhone4，4s设备屏幕：640*960
        iPhone5设备屏幕：640*1136
        iPad，iPad2：1024*768
        iPad3，iPad4：2048*1535
        iPad mini：1024*768
    获取当前UIWindow和级别
        通过UIApplication获取当前keyWindow
        keyWindow是用来管理键盘以及非触摸类的消息，并且只能有一个window是keyWindow。
        UIWindow *keyWindow = [UIApplication sharedApplication].keyWindow;
        每个UIWindow对象配置windowLevel属性，大部分时候不应该去改变windowLevel。
        UIWindow有3个级别，对应了3种显示优先级。通过windowLevel设置，优先级为：UIWIndowLevelAlert>UIWindowStatusBar>UIWindowLevelNormal
    UIView
        视图，大家在iPhone上看到的控件大部分都是UIView的子类。
        视图，通常是UIView的一个对象，表示屏幕上的一块矩形区域，同时处理该区域的绘制和触屏事件。
        一个视图也可以作为其他视图的父视图，同时决定着这些子视图的位置和大小。
        UIView类做了大量的工作去管理这些内部视图的关系
        视图同时也是App中MVC模式中得View成分。

//-IOS的坐标系统
    iPhone的视图坐标系是以左上角为原点
    每一个view的frame所使用的坐标系以它的父视图的左上角为原点
    视图结构和相关函数
        CGPoint point = CGPointMake(x, y); //位置
        CGSize size = CGSizeMake(width, height);  //大小
        CGRect rect = CGRectMake(x, y, width, height); //位置和大小
    ____________________________________________
    |                 iPhone                   |
    |------------------------------------------|
    |  --------------------------------------> |  X
    |  |                                       |
    |  |                                       |
    |  |                                       |
    |  |                                       |
    |  |                                       |
    |  |                                       |
    |  |                                       |
    |  |                                       |
    |  |                                       |
    |  |                                       |
    |  |                                       |
    |  |                                       |
    |  |                                       |
    |  |                                       |
    |  |                                       |
    |  |                                       |
    |  |                                       |
    |  |                                       |
    |  |                                       |
    |  |                                       |
    |  |                                       |
    |  |                                       |
    |  |                                       |
    |  |                                       |
    |  V                                       |
    ————————————————————————————————————————————
       Y

    Frame和Bounds
    Frame以其父视图为起点，得出它自己的位置信息
    Bounds即以IOS系统的坐标原点为起点，坐标是(0,0)
    Center表示视图中心点所在的位置，设置此属性可改变视图的位置
    当你设置了三者中的某一个的时候，其他两个值会相应变化
    
    请注意：缺省情况下，视图的边框并不会被父视图的边框裁剪。如果您希望让一个视图裁剪其子视图，需要将其clipsToBounds属性设置为YES
    
    创建UIView
        创建视图UI有两种方式，xib文件和代码创建
            通过xib的方式来创建视图对象
            NSBundle *bundle = [NSBundle mainBundle];
            NSArray *arr = [bundle loadNibNamed:@"myView" owener:self options:nil];
            UIView *myView = [arr objectAtIndex:0];
            
        代码创建视图对象
            CGRect viewRect = CGRectMake(0,0,100,100);
            UIView *myView = [[UIView alloc] initWithFrame:viewRect];


//-视图的层次结构
    UIView层次结构可以理解为“视图树”
    一个视图就是一个容器，当一个视图包含其他视图的时候，两个视图之间就建立了一个父子关系。包含的视图被称为子视图，包含的视图称为父视图或超视图(superView)
    从视觉上看，子视图隐藏了父视图的内容，设置透明属性可以看到父视图的内容
    每个父视图都有一个有序的数组存储着它的子视图，存储的顺序就好影响到每个子视图的显示效果，比如：两个兄弟视图重叠在一起，后来被加入的视图就出现在另外的上面
    一个视图可以嵌入多个subview，但是只能有一个superview
    
    UIView的常用方法
    当调用addSubview的时候，会对其保留，理解为retain一个对象就可以，当调用removeFraomSuperview的时候，会对释放，也就是release。
        基本的添加和删除子视图
        addSubview：                                 //添加子视图
        insertSubview：atIndex：                     //视图插入到指定索引位置
        insertSubView：aboveSubview：                //视图插入指定视图之上
        insertSubview：belowSubview：                //视图插入指定视图之下
        bringSubviewToFront：                        //把视图移动到最顶层
        sendSubviewToFront：                         //把视图移动到最底层
        exchangeSubviewAtIndex：withSubviewAtIndex   //把两个索引对应的视图调换位置
        removeFrontSuperview                         //把视图从父视图中移除
        
    查找视图
        UIView类中有一个tag属性，通过这个tag属性可以标示一个视图对象(整数)
        获取方法，viewWithTag：方法来检索标示过的子视图

//-视图坐标(Frame和Bounds区别)
    

//-UIView的常用属性和方法
    alpha       //透明色
    background  //背景颜色
    subViews    //子视图集合
    hidden      //是否隐藏
    tag         //标签值
    superview   //父视图
    multipleTouchEnable     //是否开启多点触摸
    userInteractionEnable   //是否响应触摸事件

    视图对象的清理
        如果手动创建一个视图，分配了任何内存，存储了任何对象的引用，都需要释放资源，必须实现dealloc方法。当某个对象的引用计数为0，系统会调用其dealloc方法，去释放对象资源，切记不要手动调用dealloc方法。

//-坐标系统变换
    坐标系统变换通过transform属性改变
    CGAffineTransformScale          对视图比例缩放
    CGAffineTransformRotate         对视图做变焦旋转
    CGAffineTransformTranslate      对视图
    


//-UIView内容模式
    视图的contentMode属性决定了边界变化和缩放操作

//-UIView动画
    UIView类的很多属性都被设计为动画。动画的属性是指当属性从一个值变为另一个值的时候，可以半自动地支持动画。你必须告诉UIKit希望执行什么类型的动画，但是动画一旦开始，Core Animation就会全权负责。UIView对象中支持动画的属性有如下几个：
    frame - 你可以使用这个来动画的改变视图的尺寸和位置
    bounds - 使用这个可以动画的改变视图的尺寸
    center - 使用这个可以动画的改变视图的位置
    transform - 使用这个可以翻转或缩放视图
    alpha - 使用这个可以改变视图透明度
    backgroundColor - 使用这个可以改变视图的背景颜色
    contentStetch - 使用这个可以改变视图内容如何拉伸
    
    配置动画委托
        可以为动画分配一个委托，并通过该委托接受动画开始和结束的信息。当需要在动画开始前和动画结束后立即执行其他任务时，可能就需要设置委托。
        通过UIView调用setAnimationDelegate：方法来设置委托，并通过setAnimationWillStartSelector：和setAnimationDidStopSelector：方法来接受消息的选择器方法。消息处理方法的形式如下：
        - (void)animationWillStart:(NSString *)animationID context:(void *)contect;
        - (void)animationDidStop:(NSString *)animationID finished:(NSNumber *)finished context:(void *)context;
        上面两个方法的animationID和context参数和动画块开始传给beginAnimation:context:方法的参数相同
            animationID - 应用程序提供的字符串，用于标识一个动画块中的动画。
            context - 也是应用程序提供的对象，用于向委托对象传递额外的信息。
        setAnimationDidStopSelector:选择器方法还有一个参数---即一个布尔值。如果动画顺利完成，没有被其他动画取消或停止，则该值为YES。
        
    配置动画的参数
        setAnimationStartDate：设置动画在commitAnimations方法返回之后的发生日期
        setAnimationDelay：设置时间发生动画和commitAnimations方法返回的时间点之间的间隔
        setAnimationDuration：方法来设置动画持续的秒数
        setAnimationCurve：设置动画过程的相对速度，比如动画可能在启示阶段逐渐加速，而在结束阶段逐渐减速，或者整个过程都保持相同的速度
        setAnimationRepeatCount：设置动画的重复次数
        setAnimationRepeatAutoreverses：来指定动画在到达目标值时是否自动反向播放。你可以结合使用这个方法和setAnimationRepeatCount：方法，使各个属性的初始值和目标值之间平滑切换一段时间。
        缺省情况下，所有支持动画的属性在动画块中发生的变化都会形成动画，如果你希望让动画块中发生的某些变化不产生动画效果，可以通过setAnimationEnabled：方法来暂时禁止动画，在完成修改后才重新激活动画。在调用setAnimationEnabled：方法并传入NO值之后，所有的改变都不会产生动画效果，直到用YES值在调用这个方法或者提交整个动画块时，动画才会恢复。你可以用areAnimationEnabled方法来确定当前是否激活动画。

    


