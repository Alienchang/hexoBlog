title: textView改变行间距以及文本域边框距离
date: 2014-08-28 10:48:16
tags: [ios ,小知识]
categories: 技术
---

//改变行间距
NSMutableParagraphStyle \*paragraphStyle = [[NSMutableParagraphStyle alloc]init];
[paragraphStyle setLineSpacing:2.];
NSDictionary \*attributes = @{ NSFontAttributeName:[UIFont systemFontOfSize:14], NSParagraphStyleAttributeName:paragraphStyle};
textview.attributedText = [[NSAttributedString alloc]initWithString:_textview.text attributes:attributes];

//改变文本域位置
[textview setContentInset:UIEdgeInsetsMake(10, 0, 0, 0)];