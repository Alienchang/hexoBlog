title: dispath_group
date: 2015-07-07 14:08:48
tags:
---


NSMutableArray *mutableArray = [@[] mutableCopy];
dispatch_group_t serviceGroup = dispatch_group_create();


dispatch_group_enter(serviceGroup);
[[WTAPIClient sharedClient] fetchCommentsByBlogID:_blog.blogID
start:startIndex.integerValue
count:20
success:^(WTObjectArray *array) {
[mutableArray insertObject:array atIndex:0];
dispatch_group_leave(serviceGroup);
}
failure:^(NSError *error) {
[weakSelf handleError:error];
[mutableArray insertObject:[WTObjectArray new] atIndex:0];
dispatch_group_leave(serviceGroup);
}];


dispatch_group_enter(serviceGroup);
[[WTAPIClient sharedClient] fetchLoversWithBlogId:_blog.blogID
start:startIndex.integerValue
limit:20
success:^(WTObjectArray *array) {
[mutableArray addObject:array];
dispatch_group_leave(serviceGroup);
} failure:^(NSError *error) {
[weakSelf handleError:error];
[mutableArray addObject:[WTObjectArray new]];
dispatch_group_leave(serviceGroup);
}];


dispatch_group_notify(serviceGroup,dispatch_get_main_queue(),^{
// Assess any errors
NSError *overallError = nil;

successBlock(mutableArray);
// Now call the final completion block
});