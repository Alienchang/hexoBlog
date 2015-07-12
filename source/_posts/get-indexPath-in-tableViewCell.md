title: 'get indexPath in tableViewCell'
date: 2015-07-09 11:33:11
tags:
---
- (UITableView*)tableView {
    if (tableView == nil) {
        tableView = (UITableView*)self.superview;
        while (tableView && ![tableView isKindOfClass:[UITableView class]]) {
            tableView = (UITableView*)tableView.superview;
    }
}
    return tableView;
}


NSIndexPath *p = [self.tableView indexPathForCell:self];