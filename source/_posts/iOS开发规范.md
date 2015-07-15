## <div align = center>iOS开发规范</div>
##### 一、文档结构

	1、如果是新功能、模块、或者是独立的library，需要新建folder，然后拖进工程，不要单单只新建group。
    2、小的图片资源直接放到assets中，大一些的比如启动页面放在指定文件夹中。
    3、自己封装的类放在Util中，第三方的工具类放到Librarys中
    4、通用的常量写在AppConst中
    
##### 二、类规范
	1、使用 #pragma mark - 来标记模块，例如tableViewDelegate一定要写成 #pragma mark -UITableView Delegate，不要写成 #pragma mark -tableView Delegate。
    2、属性的初始化尽量在getter方法中完成。
    


##### 三、命名

	1、类命名：
    新建类的命名按照驼峰命名法，不要与现有文件名相似、并且尽量描述类作用，类名如果不多于30个字节不可以使用缩写。严禁使用下划线。对于系统的常用类作实例变量声明时加入后缀。
    例：WTHeaderImageView
    例：WTBaseDataSource
    
    2、变量命名：
    
    	（1）属性：头字母小写，同样驼峰命名，不可以使用下划线，尽量不要使用缩写。属性列表尽量保持对齐美观。
   		 例：
   		 @property (nonatomic, strong) NSDictionary          *rawData;
			@property (nonatomic, strong) NSMutableArray        *dataArray;
			@property (nonatomic, strong) NSNumber              *nextStart;
			@property (nonatomic, assign) BOOL                  hasNextPage;
			@property (nonatomic, weak)   WTBaseViewController  *controller;
    
    	（2）成员变量：以下划线开头，其他同属性，列表也保持对齐。
   		 例：
   			 @interface WTClubContentViewController (){
    				BOOL _canRefresh;
    				BOOL _showNoDataView;
				}
         
         （3）全局静态字符串：以小写的k开头，其余同属性。
            例：
            static NSString *const kRecommendMatchesKey     = @"recommendMatchesKey";
			static NSString *const kRecentWeatherPath       = @"recentWeatherCache";
			static NSString *const kMyYueMatchKey           = @"myYueMatchKey";
            
##### 四、注释
	1、统一使用VVDocument插件
    /**
 	*  <#Description#>
	 *
	 *  @param nibNameOrNil   <#nibNameOrNil description#>
	 *  @param nibBundleOrNil <#nibBundleOrNil description#>
	 *
 	*  @return <#return value description#>
 	*/
    2、类中的功能性方法要有70%以上是有注释的，方法中如果有比较复杂的逻辑判断或者数学计算也要添加注释
    3、多使用//TODO: 、//TOFIX: 、#error <#message#>、#warning <#message#>
    4、.h文件开头处简要介绍类作用
    5、文档导出工具可使用appledoc
   详见 http://www.devtang.com/blog/2012/02/01/use-appledoc-to-generate-xcode-doc/
  
  ##### 五、编码规范
    1、方法中尽量不要使用明文字符串
    2、正常方法中代码不要超过30行，必要可以宽限到50行
    3、测试中的log方法用完即删
    4、不需要暴露的属性和变量尽量写在.m文件中。
    