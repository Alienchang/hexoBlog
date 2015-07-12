title: FMDB
date: 2014-09-22 14:29:46
tags: [ios]
categories: 技术
---
使用资料库的第一件事，就是建立一个资料库。要注意的是，在iOS环境下，只有document directory 是可以进行读写的。在写程式时用的那个Resource资料夹底下的东西都是read-only。因此，建立的资料库要放在document 资料夹下。方法如下： 


NSArray \*paths = NSSearchPathForDirectoriesInDomains(NSDocumentDirectory, NSUserDomainMask, YES);
NSString \*documentDirectory = [paths objectAtIndex:0];
NSString \*dbPath = [documentDirectory stringByAppendingPathComponent:@"MyDatabase.db"];
FMDatabase \*db = [FMDatabase databaseWithPath:dbPath] ;
if (![db open]) {
   NSLog(@“Could not open db.”);
   return ;
}

建立table
如果是新建的资料库档，一开始是没有table的。建立table的方式很简单：

[db executeUpdate:@"CREATE TABLE PersonList (Name text, Age integer, Sex integer, Phone text, Address text, Photo blob)"];
这是FMDB裡很常用的指令，[FMDatabase_object executeUpdate:]后面用NSString塞入SQLite语法，就解决了。因為这篇主要是在讲FMDB，所以SQLite的语法就不多说了，上述程式码建立了一个名為PersonList的table，裡面有姓名、年龄、性别、电话、地址和照片。（嗯….很范例的一个table）
－插入资料
插入资料跟前面一样，用executeUpdate后面加语法就可以了。比较不同的是，因為插入的资料会跟Objective-C的变数有关，所以在string裡使用?号来代表这些变数。
[db executeUpdate:@"INSERT INTO PersonList (Name, Age, Sex, Phone, Address, Photo) VALUES (?,?,?,?,?,?)",

@"Jone", [NSNumber numberWithInt:20], [NSNumber numberWithInt:0], @“091234567”, @“Taiwan, R.O.C”, [NSData dataWithContentsOfFile: filepath]];
其中，在SQLite中的text对应到的是NSString，integer对应NSNumber，blob则是NSData。该做的转换FMDB都做好了，只要了解SQLite语法，应该没有什麼问题才是。
－更新资料
太简单了，不想讲，请看范例：
[db executeUpdate:@"UPDATE PersonList SET Age = ? WHERE Name = ?",[NSNumber numberWithInt:30],@“John”];
－取得资料
取得特定的资料，则需使用FMResultSet物件接收传回的内容：
FMResultSet \*rs = [db executeQuery:@"SELECT Name, Age, FROM PersonList"];

while ([rs next]) {
NSString \*name = [rs stringForColumn:@"Name"];
int age = [rs intForColumn:@"Age"];
}

[rs close];
用[rs next]可以轮询query回来的资料，每一次的next可以得到一个row裡对应的数值，并用[rs stringForColumn:]或[rs intForColumn:]等方法把值转成Object-C的型态。取用完资料后则用[rs close]把结果关闭。
－快速取得资料
在有些时候，只会query某一个row裡特定的一个数值（比方只是要找John的年龄），FMDB提供了几个比较简便的方法。这些方法定义在FMDatabaseAdditions.h，如果要使用，记得先import进来。
view sourceprint
//找地址
NSString \*address = [db stringForQuery:@"SELECT Address FROM PersonList WHERE Name = ?",@"John”];

//找年齡
int age = [db intForQuery:@"SELECT Age FROM PersonList WHERE Name = ?",@"John”];


photos:
<img src="/img/wallpaper-2572384.jpg" style="width: 300px;"/>

