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
