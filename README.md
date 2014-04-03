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
    
    对象是类的一个实例，是一个具体的事物。
    类与对象是抽象与具体的关系
    
    万事万物皆对象
    
    类可以看成静态属性（实例变量）和动态（方法）属性的结合体
    
    方法是用来完成特定功能的代码片段
    
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
    
//    0401
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
        





