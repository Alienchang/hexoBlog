title: 压缩解压Zip
date: 2014-08-26 13:39:45
tags: [ios]
categories: 技术
---
1、首先引入libz.dylib框架

2、需要ZipArchive   pod 'ZipArchive', '~> 1.3.0'

3、解压缩ZIP文件代码如下：

ZipArchive\* zip = [[ZipArchive alloc] init];
NSArray \*paths = NSSearchPathForDirectoriesInDomains(NSDocumentDirectory, NSUserDomainMask, YES);
NSString \*dcoumentpath = ([paths count] > 0) ? [paths objectAtIndex:0] : nil;
NSString\* l_zipfile = [dcoumentpath stringByAppendingString:@"/test.zip"] ;
 
NSString\* image1 = [dcoumentpath stringByAppendingString:@"/2.png"] ;
NSString\* image2 = [dcoumentpath stringByAppendingString:@"/3.png"] ;
 
BOOL ret = [zip CreateZipFile2:l_zipfile];  
ret = [zip addFileToZip:image1 newname:@"2.png"];  
ret = [zip addFileToZip:image2 newname:@"3.png"];  
if( ![zip CloseZipFile2] )  
{  
    l_zipfile = @"";  
}  
[zip release]; 
4、解压缩ZIP文件代码如下：

ZipArchive\* zip = [[ZipArchive alloc] init];
NSArray \*paths = NSSearchPathForDirectoriesInDomains(NSDocumentDirectory, NSUserDomainMask, YES);
NSString \*dcoumentpath = ([paths count] > 0) ? [paths objectAtIndex:0] : nil;
NSString\* l_zipfile = [dcoumentpath stringByAppendingString:@"/test.zip"] ;
NSString\* unzipto = [dcoumentpath stringByAppendingString:@"/test"] ;
if( [zip UnzipOpenFile:l_zipfile] ) {  
    BOOL ret = [zip UnzipFileTo:unzipto overWrite:YES];  
    if( NO==ret ) { }  
    [zip UnzipCloseFile];  
}  
[zip release];