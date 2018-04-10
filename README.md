DJPhotoBrowser
==============

DJPhotoBrowser是一个简单的图片浏览器，并制作了九宫格图片展示. <br/>

* 支持图片弹出和隐藏动画。<br/>
-- Support the show and hide animation effects
* 支持双击缩放，手势缩放，可设置缩放比例。<br/>
-- Supports double-click scaling, gestures to zoom in.
* 支持图片存储。<br/>
-- Support photo storage.
* 支持网络加载gif图片，长图滚动浏览。<br/>
-- Support network loading GIF images, scroll through long figure.
* 支持横竖屏显示。<br/>
-- Support for landscape and vertical screen display switch.

## Screenshots
九宫格图片展示 <br/>
![image](/photoBrowser1.gif)

图片缩放移动 <br/>
![image](/photoBrowser2.gif)

## Requirements

- iOS 8.0 or later
- Xcode 8.0 or later

## Installation

1. You should copy all the files in path 'DJPhotoBrowser' to your projects;

2. Add under lines to your class:
``` objective-c
#import "DJPhotoBrowser.h"
#import "DJPhotoGridView.h"
```
3. Need ![SDWebImage](https://github.com/rs/SDWebImage/)

## Licenses

All source code is licensed under the [MIT License](https://github.com/iunion/DJKit/blob/master/LICENSE).


## Architecture

### DJPhotoBrowser

- `DJPhotoBrowser`
- `DJPhotoBrowserView`
- `DJWaitingView`

### DJPhotoGridView

- `DJPhotoGridView`
- `DJPhotoItem`

## Usage

### DJPhotoBrowser
``` objective-c
DJPhotoBrowser *browser = [[DJPhotoBrowser alloc] init];
// 原图的父控件，用于显示隐藏图片动画展示，也可通过dataSource设置
browser.sourceImagesContainerView = self;
browser.dataSource = self;
browser.delegate = self;
[browser showWithImageCount:self.photoItemArray.count imageIndex:button.tag];
```

#### DJPhotoBrowserDataSource
``` objective-c
// 预览图片
- (UIImage *)photoBrowser:(DJPhotoBrowser *)browser placeholderImageForIndex:(NSUInteger)index;

// 原图片控件映射到PhotoBrowser的坐标，需要在delegate中做convertRect
- (CGRect)photoBrowser:(DJPhotoBrowser *)browser containerViewRectAtIndex:(NSUInteger)index;

// 高清图片URL
- (NSURL *)photoBrowser:(DJPhotoBrowser *)browser highQualityImageURLForIndex:(NSUInteger)index;
```

#### DJPhotoBrowserDelegate
``` objective-c
// 图片滚动
- (void)photoBrowser:(DJPhotoBrowser *)browser didScrollToIndex:(NSUInteger)index;
```

### DJPhotoGridView
``` objective-c
DJPhotoGridView *photoGroup = [[DJPhotoGridView alloc] init];
photoGroup.frame = CGRectMake(10, 10, 100, 100);
photoGroup.tag = 100;
[cell.contentView addSubview:photoGroup];

photoGroup.photoItemArray = [self.tableDataArray objectAtIndex:indexPath.row];
```

#### photoGridViewSizeWith
``` objective-c
// DJPhotoGridView高度计算
+ (CGSize)photoGridViewSizeWith:(NSArray<DJPhotoItem *> *)photoItemArray;
```

## Author
- [Dennis Deng](https://github.com/iunion)

