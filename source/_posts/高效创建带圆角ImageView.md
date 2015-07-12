title: 高效创建带圆角ImageView
date: 2015-05-05 10:38:37
categories: blog
tags: [小知识 ,ios]
---
// Get your image somehow
UIImage *image = [UIImage imageNamed:@"image.jpg"];

// Begin a new image that will be the new image with the rounded corners 
// (here with the size of an UIImageView)
UIGraphicsBeginImageContextWithOptions(imageView.bounds.size, NO, 1.0);

// Add a clip before drawing anything, in the shape of an rounded rect
[[UIBezierPath bezierPathWithRoundedRect:imageView.bounds 
cornerRadius:10.0] addClip];
// Draw your image
[image drawInRect:imageView.bounds];

// Get the image, here setting the UIImageView image
imageView.image = UIGraphicsGetImageFromCurrentImageContext();

// Lets forget about that we were drawing
UIGraphicsEndImageContext();