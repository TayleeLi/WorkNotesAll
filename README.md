Hello World

//2014_0319_1439
    Thanks for your sharing!
    category->类目
    extension->扩展
    protocol->协议
    case class->实例

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
    

//2014_0412
       0417
*应用程序沙盒的基本概念
*NSString类路径的处理常用方法
*NSData类基本概念
*NSFileManger——文件管理的常用操作
*数据持久性——属性列表化
*NSFileHandle——文件内容读取

    文件管理
        IOS中的沙盒（sandbox）机制
        每个引用程序都有自己的独立的储存空间（沙盒）
        一般来说应用程序是不可以相互访问
        
        沙盒目录文件的组成以及相关含义
            我们创建应用程序时，在每个沙盒中含有三格文件。分别是Documents，Library和tmp
            Documents 一般我们需要的持久的数据都放在这个目录中，你可以在当中添加子文件夹，尤其需要我们注意的是，iTunes备份和恢复的时候，会包括此目录。
            Library 设置程序的默认设置和其他状态信息
            tmp 创建临时文件目录，当我们的IOS设备重启时，文件会被自动清除
            
            获取程序的根目录 home
            NSString *homePath = NSHomeDirectory();
            获取Document目录
            NSArrau *paths = NSSearchPathForDirectoriesInDomains(NSDocumentDirectory, NSUserDomainMask, YES);
            NSString *docPath = [paths lastObject];
            获取Library目录
            NSArray *paths = NSSearthPathForDirectoriesInDomain(NSLibraryDirectory, NSUserDomainMask, YES);
            NSString *docPath = [paths lastObject];
            获取Library中的Cache
            NSArray *paths = NSSearthPathForDirectoriesInDomain(NSCachesDirectory, NSUserDomainMask, YES);
            NSString *docPath = [paths lastObject];
            获取tmp路径
            NSString *temp = NSTemporaryDirectory();
            
        NSString类路径处理方法
            //对目录做处理：/Users/apple/testfile.text
            NSString *path = @"/Userss/apple/testfile.text";
            
            常用处理方法如下：
            //获得组成此路径的各个组成部分，结果：("/", "Users", "apple", "testfile.text")
            - (NSArray *)pathComponents;
            //提取路径的最后一个组成部分，结果：testfile.text
            - (NSArray *)lastPathComponent;
            //删除路径的最后一个组成部分，结果：/Users/apple
            - (NSString *)stringByDeletingLastPathComponent;
            //将path添加到现有路径的末尾，结果：/Users/apple/testfile.text/app.text
            - (NSString *)stringByAppendingPathComponent:(NSString *)str;
            //取路径最后部分的扩展名，结果：text
            - (NSString *)pathExtension;
            //删除路径最后部分的扩展名，结果：/Users/apple/testfile
            - (NSString *)stringByDeletingPathExtendion;
            //路径最后部分追加扩展名，结果：/Users/apple/testfile.text.jpg
            - (NSString *)stringByAppendingPathExtension:(NSString *)str;

        NSData的基本概念
            NSData是用来包装数据用的
            NSData存数的是二进制数据，这样就屏蔽了数据之间的差异，文本，音频，图像等数据都可以用NSData来存储
            
        文件管理常用类和方法
            NSFileManager类
                创建文件
                读数据
                写数据
                重命名
                移动文件
                复制文件
                删除文件
                测试文件是否存在
        数据持久性--属性列表化
            字符串
            数组
            字典
            
            数组，字典只能将Bool，NSNumber，NSString，NSData，NSDate，NSArray，NSDictionary写入属性列表plist文件
            
        读取文件类和常用方法
            NSFileManager类主要对文件的操作

            NSFileHandle类主要对文件内容进行读取和写入操作
                创建NSFileHandle对象
                对打开文件进行I/O操作
                关闭文件
            NSFileHandle可以做文件断点续传
            NSFileHandle只可以读写文件，不能创建文件，创建文件使用NSFileManager
    
//2014_0419
    复制对象，对象归档和单类
    
    复制对象的基本概念
    
    对象具备复制功能，必须实现
        <NSCopying>协议
        <NSMutableCopying>协议
        常用的可复制对象有：NSNumber，NSString，NSArray，NSDictionary，NSMutableDictionary，NSMutableArray，NSMutableString
    0421
        复制对象的种类：
            copy：产生对象的副本是不可变的
            mutableCopy：产生的对象副本是可变的
        copy和mutableCopy的区别
            前者返回一个不可变对象副本，后者返回一个可变对象副本
    
    浅拷贝和深拷贝基本概念和用法
        浅拷贝只复制对象本身，对象里属性，包含对象不做复制
        深拷贝则即复制对象本身，对象的属性也会复制一份
        Foundation框架中支持复制的类，默认是浅拷贝

    对象的自定义拷贝
        对象拥有复制特性，需实现NSCopying，NSMutableCopying协议，实现该协议的方法是copyWithZone和mutableCopyWithZone
        
    对象归档的基本概念和用法
        对象归档是指将对象写入文件保存在硬盘上，当再次重新打开程序时，可以还原这些对象。你也可以称它为对象序列化，对象持久化
        数据持久性的方式
            NSKeyedArchiver——对象归档
            NSUserDefaults
            属性列表化（NSArray，NSDictionary保存文件）
            SQlite数据库，Core Data数据库
        归档形式
            对Foundation库中对象进行归档
            自定义对象进行归档（需要实现归档协议，NSCoding）
        归档后的文件是加密的，属性类别是明文
        
    自定义内容归档
        归档
            使用NSData实例作为归档的存储数据
            添加归档的内容（设置key与value）
            完成归档
            将归档数据存入磁盘中
        解归档
            从磁盘读取文件，生成NSData实例
            根据Data实例创建和初始化解归档实例
            解归档，根据key访问value的值
    
    自定义对象的归档基本概念
        自定义的对象要支持归档，需要实现NSCoding协议
        
        NSCopying协议有两个方法，encodeWithCoder方法对对象的属性数据做编码处理
                               initWithCoder解码归档数据来初始化对象
        实现NSCoding协议后，就能通过NSKeyedArchiver归档

        归档后的文件是加密的
        
    单例设计模式
        设计原理是始终返回一个实例，即一个类始终只有一个实例
        
        创建单例的基本步骤
            声明一个单件对象的静态实例，并初始化为nil
            创建一个类的类工厂方法，生成一个该类的实例，并且仅当这个类的实例为nil时
            覆盖allocWithZone：方法确保用户（程序员）在直接分配和初始化对象时，不会产生另一个对象。
            实现NSCopying协议，覆盖release，autorelease，retain，retainCount方法，以此确保单例的状态
            在多线程的环境中，注意使用@synchronized关键字，确保静态实例被正确的创建和初始化
    
        
//2014_0422
    //KVC，KVO和谓词
    //KVC的基本概念和用法
        基本调用方法 - valueForKey:
                   - setValue: forKey:
        它们已字符串的形式向对象发送消息，字符串是我们关注属性的关键
        是否存在setter，getter方法，如果不存在，它将在内部查找名为_key或者key的实例变量。通过KVC，可以获取不存在getter方法的对象值，无需通过对象指针直接访问
        当我们通过setValue: forKey: 设置对象的值，或通过valueForKey来获取对象的值时，如若对象的实例变量为基本数据类型时（char，int，float，BOOL），我们需要对数据进行封装
        
        KVC的简单运算
            sum, min, max, avg, count
            NSString *count = [book valueForKeyPath:@"relativeBooks.@count"];
            NSString *sum = [book valueForKeyPath:@"relativeBooks.@sum._price"];
            NSString *avg = [book valueForKeyPath:@"relativeBooks.@avg._price"];
            NSString *min = [book valueForKeyPath:@"relativeBooks.@min._price"];
            NSString *max = [book valueForKeyPath:@"relativeBooks.@max._price"];

    //KVO的基本概念和用法
        键-值观察使一种使对象获取其他对象的特定属性变化的通知机制
        
        键-值观察为所有对象提供自动观察兼容性。你可以通过禁用自动观察通知并实现手动通知来筛选通知

    //键值观察设计模式的基本概念 和用法
        键-值编码是一个用于间接访问对象属性的机制，使用该机制不需要调用存取方法和变量实例就可以访问对象属性
        键-值编码方法在Objective—C非正式（类目）NSKeyValueCoding中被声明，默认的实现方法由NSObject提供
        键-值编码支持带有对象值的属性，同时也支持纯数值类型和结构，非对象参数和返回类型会被识别并自动封装/解封

    //谓词的基本概念和用法
        cocoa中提供了NSPredicate类，指定过滤的条件。将符合条件的对象保留下来
        创建谓词
            //设置谓词条件
            NSPredicate *predicate = [NSPredicate predicateWithFormat:@"age <= 28"];
            for (Person *person in array) {
                //表示指定的对象是否满足谓词条件
                if([predicate evaluateWithObject:person]){
                    //NSLog(@"person name : %@", person.name);
                }
            }
            
            //返回一个符合谓词条件的数组
            NSArray *newArray = [array fileredArrayUsingPredicate:predicate];
            
            for (Person *person in newArray){
                //NSLog(@"perosn name : %@", [person valueForKey:@"_name"]);
            }

            格式占位符
            逻辑运算符
                in
            关键字
                以**开始---BEGINSWITH
                以**结束---ENDSWITH
                包含---CONTAINS



