Hello World

//2014_0319_1439
    Thanks for your sharing!
//2014_0321_1037
    读，仿，写，查
//2014_0325_1105
    
//2014_0327_1005
    程序（硬盘）——加载> [（操作系统代码——>代码）内存]——>{[堆（动态分配alloc出来的），栈（局部变量），数据区（静态变量和字符串常量），代码区（存放代码）]内存管理}
    
    按声明分类：
    局部变量：方法块 语句块  {int i = 100; ......}
    实例变量(不能初始化)：@Interface Person {
                int age;
                int sex;
            }
            
    数据类型->基本数据类型->数值类型->整数类型
                                ->浮点型
                       ->字符类型（char）
                       ->布尔类型
                       ->空类型（void）
           ->指针数据类型->类（class）
                       ->id
    
    OC里 Boolean 允许取值TRUE或FALSE，也可以0或非0的整数
    Java里 Boolean 值允许TRUE或FALSE
    
    容量小的默认转换为容量大得数据类型
    数据类型按容量大小排练 Byte,short,char->int->long->float->double
    Byte,short,char之间不会互相转换，三者在计算转换时首先转换成int类型
    容量大的数据类型转换成容量小的数据类型,要加上强制转换符,但可能会造成精度的降低或溢出
    
    位运算符
    
//2014_0330_1102
    类与对象
    
    
    
    方法调用 [类名或对象名 方法名]
    
    消息嵌套 [[ClassOrinstance method:arg1] otherMethod]
    
    对象必须先创建，然后初始化，才能使用
    
    在init方法中,若要父类完成所需的一次性初始化，需要调用[super init]，init方法返回的值（id数据类型），描述了被初始化的对象
    
    OC判断方法重名只按照函数名来，与参数类型和返回值无关
    
    self指的时类对象本身，super是父类对象本身，self用来调用对象方法，super调用父类的方法
    
//2014_0331_0941
    @property和@synthesize
    
    @property()括号中，可填写的属性
    readwrite:默认
    readonly :只读，意味着没有set方法
    assign   :默认，引用计数不增加
    retain   :引用计数增加1
    原则性    :actomic默认
    非原子性  :nonatomic
    
    actomic是OC中的一种线程保护技术，是防止在未完成的时候，被另外一个线程使用，造成数据错误。

    static
    
    类的继承
    @interface 子类:父类
    
    权限控制:
        private protected public
        
    OC中只继承单继承
    
    动态类型:OC在运行时才确定对象的时间类型
    动态绑定:程序在执行时才确定对象的调用的时间方法
    
    多态是一种事物的多种状态。不同类的对象可以定义共享系统名称的方法->相同名称方法，不同类
    多态的条件:继承关系，方法重写，父类的声明变量指向子类对象
    
    select 调用动作
    SEL action
    action = @select(run);
    [car performSelector:action];

    [car performSelector:@select(run)];
    
    
    Cocoa Foundation框架
    NSNumber

    NSString
    
    NSArray
    
//2014_0401
    NSDictionary
    键--值对组成的数据集合
    通过key（键），查找对应value值，key通常是字符串对象，也可以是其他任意类型对象
    在一个字典对象中，key值必须是唯一的
    字典对象的键和值不可以为空（nil），如果需要在一个字典对象中表示一个空值，可以使用NSNull对象

    //字典创建
    NSDictionary *dic1 = [NSDictionary dictionaryWithObject:@"value" forKey:@"k1"];
    NSDictionary *dic2 = [NSDictionary dictionaryWithObjectsAndKeys:@"vi", @"k1", @"vi", @"k1", @"vi", @"k1", nil];
    NSDictionary *dic3 = [NSDictionary dictionaryWithDictionary:dict1];

    快速枚举

    NSSet
    它是一组‘单值’对象的集合，且NSSet实例中元素是’无序‘，同一个对象只能保存一个，并且它也分位可变和不可变的集合对象（NSMutableSet）
    
    
//2014_0402
    类目Category 对现有类的扩展
    
    类目命名规则：类名+扩展方法，如 “NSString+Revert”
    类目不继承父类
    //.h
    @interface NSString (Revert)
    
    - (void)test;
    @end
    
    //.m
    @interface Revert : NSObject

    - (void)test;
    @end

    
    延展
    类的延展就是如同是“匿名”的类目，延展中声明的方法在类本身
    
    通过延展的方式定义类的私有方法
    
    协议
    
    协议没有父类也不能定义实例变量
    协议是一种特殊的程序设计结构，用于声明专门被别的类实现的方法
    适用场合
        需要由别的类实现的方法
        声明未知类的接口
        两个类之间的通讯
    基本特点
        协议可以被任何类实现的方法
        协议本身不是类，它是定义了一个其他类可实现的接口
        类目也可以采用协议
        
    @required  表示必须强制实现的方法
    @optional  表示可以有选择性的实现方法
    
    （代理）委托设计模式
    代理是指一个对象提供机会对另一个对象中的行为发生变化时做的反应
    代理设计模式的基本思想---两个对象协同解决问题，通常用于对象之间的通讯
    
    基本特点
        简化了对象的行为，最小化了对象之间的耦合度
        使用代理，一般来说无需子类化
        简化了我们应用程序开发，既容易实现，有灵活
    
    定时器NSTimer
        它按照一定时间间隔，将指定信息发送到目标对象，并更新某个对象行为，你可以选择在未来的某个时候将它“开启”，或者将它停止乃至销毁
    
    NSRunloop基本概念
        一个runloop就是一个事件处理的循环，用来不停的调度工作及处理输入事件。使用run loop的目的是让你的线程在有工作的时候忙于工作，而没工作的时候处于休眠状态
        
        在我们应用程序中，你不需要创建NSRunloop对象。因为，在我们的主线程中(包含其他子线程)系统会自动创建NSRunloop对象。如果你需要访问当前线程中得runloop，你可以通过类方法“currentRunloop”
        
        
//2014_0408
    内存管理-引用计数
        每个对象都有拥有一个引用计数 retain coount
        当对象被创建的时候，引用计数值是1
        当发生retain消息release消息时，该对象的引用计数加1，该对象的引用计数为2
        当向对象发送release消息时，该对象的引用计数减1
        当一个对象的引用计数为0时，系统自动调用dealoc方法，销毁该对象
    
    对象所有权的基本概念
        当一个所有者(owner，其本身可以是任何一个Objective-C对象)做了以下某个动作时，它就拥有了一个对象所有权(ownership).
        如果创建或者复制某个对象时，则拥有该对象的所有权
            alloc, allocWithZone, copy, copyWithZone, mutableCopy, mutableCopyWithZone
        如果没有创建对象，而是将对象保留，同样拥有该对象的所有权
            retain
        如果你拥有了某个对象的所有权，在不需要某个对象时，需要释放它们
            release，autorelease
    //0409
    我们该如何持有对象
        初始化方法
            直接向对象发送retain消息。持有对象所有权。并在dealloc方法释放该对象
        设置方法
            直接赋值，不保留对象；
            直接保留对象，在dealloc方法中释放对象；
            释放旧对象，保留新对象，在dealloc方法中释放对象；

    详解dealloc方法
        当对象的引用计数为0，系统会自动调用dealloc方法，回收内存。
            - (void)dealloc
            {
                [_cup release];
                [super dealloc];
            }
        
        子类的某些实例是继承自父类的。因此，我们需要调用父类的dealloc方法，来释放父类拥有的这些对象。
        一般来说调用的顺序是，是当之类的对象释放完时，然后再释放父类的所拥有的实例。这一个与调用初始化方法正好相反。

    点语法的内存管理
            赋值 assign：直接赋值，默认
                retain：保留对象
                copy：拷贝对象
            读写性
                readwrite：生成getter，setter方法，默认
                readonly：生成Getter方法
            原子性
                atomic：多线程环境下，存在线程保护，默认
                nonatomic：多线程环境下，不存在线程保护

    自动释放池的基本概念
        在自动释放池中得对象，是能被自动释放的
        
    ARC和垃圾回收机制的基本概念
        automatic reference counting 当你在编译程序时提供自动管理内存的功能，它会为自动加入内存的控制代码，控制对象的生命周期。
    
    内存管理总结
        当你使用new，alloc或copy方法创建一个对象时，该对象的引用计数为1.当不再使用该对象时，你要负责向该对象发送一条release或者autorelease消息，这样，该对象将在其使用寿命结束时被销毁
        你通过任何其他方法获得一个对象时，则假设该对象的引用计数为1，而且已经被设置为自动释放，你不需要执行任何方法来释放该方法。如果你打算在一段时间内拥有该对象，则需要保留它并确保在操作完成时释放它。
        如果你保留了某个对象，你需要释放或者自动释放该对象，必须保持retain方法和release方法使用次数相等

    除了alloc，new或copy之外的方法创建的对象都被声明了autorelease。谁retain，谁release。
    




    





