## 对象的创建与销毁
### 1、用静态工厂方法代替构造器
- 静态工厂方法与构造器不同的第一大优势在于，它们有名称
- 静态工厂方法与构造器不同的第二大优势在于，不必在每次调用它们的时候都创建一个新对象。
- 静态工厂方法与构造器不同的第三大优势在于，它们可以返回原返回类型的任何子类型的对象。
- 静态工厂的第四大优势在于，所返回的对象的类可以随着每次调用而发生变化，这取决于静态工厂方法的参数值。只要是已声明的返回类型的子类型，都是允许的。
- 静态工厂的第五大优势在于，方法返回的对象所属的类，在编写包含该静态工厂方法的类时可以不存在。
- 静态工厂方法的主要缺点在于，类如果不含公有的或者受保护的构造器，就不能被子类化。
- 静态工厂方法的第二个缺点在于，程序员很难发现它们。
#### 静态工厂方法的一些惯用名称：
- from一一类型转换方法，它只有单个参数，返回该类型的一个相对应的实例，例如：
  Date d= Date.from(instant) ;
- of 聚合方法，带有多个参数，返回该类型的一个实例，把它们合并起来，例如：
  Set<Rank> faceCards = EnumSet.of(JACK , QUEEN, KING);
- valueOf一一比from 和of 更烦琐的一种替代方法，例如：
  BigInteger  primer = BigInteger.valueOf(Integer.MAX_VALUE);
- instance 或者getInstance一－返回的实例是通过方法的（如有）参数来描述的，但是不能说与参数具有同样的值，例如：
  StackWalke 「luke = StackWalke 「.getinstance(options);
- create 或者newInstance一一像instance 或者getInstance 一样，但create或者newInstance 能够确保每次调用都返回一个新的实例，例如：
  Object newArray = Aarray.newInstance(classObject, arraylen);
- getType-一像getInstance 一样，但是在工厂方法处于不同的类中的时－候使用。Type 表示工厂方法所返回的对象类型，例如：
  FileStore fs = Files.getFileStore(path];
- newType一像Instance 一样，但是在工厂方法处于不同的类中的时候使用。。
- Type 表示工厂方法所返回的对象类型，例如：
  BufferedReader br＝ Files.newBufferedReader(path);
- type-一－getType 和newType 的简版，例如：
  List<Complaint> litany ＝ Collections.list(legacylitany 〕；
### 2、遇到多个构造器参数时要考虑使用构建器（builder模式）
- 常规builder模式，每个类定义一个static Builder类
- lombok 注解@builder模式
- jdk8 builder模式
### 3、用私有构造器或者枚举类型强化Singleton 属性
### 4、通过私有构造器强化不可实例化的能力
  企图通过将类做成抽象类来强制该类不可被实例化是行不通的。让这个类包含一个私有构造器，它就不能被实例化
### 5、优先考虑依赖注入来引用资源
- 当创建一个新的实例时， 就将该资源传到构造器中。
- 将资源工厂（ factory ）传给构造器，在Java 8 中增加的接口Supplier<T>，最适合用于表示工厂.
### 6、避免创建不必要的对象
- 对于同时提供了静态工厂方法（ static factory method) （详见第l 条）和构造器的不可变类，通常优先使用静态工厂方法而不是构造器，以避免创建不必要的对象。
- 要优先使用基本类型而不是装箱基本类型，要当心无意识的自动装箱。
- 通过维护自己的对象池（ object pool ）来避免创建对象并不是一种好的做法，除非池中的对象是非常重量级的（比如数据库连接池）
- 在提倡使用保护性拷贝的时候，因重用对象而付出的代价要远远大于因创建重复对象而付出的代价
### 7、消除过期的对象引用
- 一般来说， 只要类是自己管理内存，程序员就应该警惕内存泄漏问题。一旦元素被释放掉，则该元素中包含的任何对象引用都应该被清空。
- 内存泄漏的另一个常见来源是缓存。一旦你把对象引用放到缓存中，它就很容易被遗忘掉，从而使得它不再有用之后很长一段时间内仍然留在缓存中。
- 内存泄漏的第三个常见来源是监昕器和其他回调
