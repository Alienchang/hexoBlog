title: 'HTML source code of a loaded UIWebView'
date: 2015-07-08 11:59:20
tags:
---

NSString *yourHTMLSourceCodeString = [webView stringByEvaluatingJavaScriptFromString:@"document.documentElement.outerHTML"]