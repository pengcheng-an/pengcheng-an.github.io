---
title: "How to Write a Hugo post"
# aliases: ["/template"]
date: "2021-12-26"
description: ""
tags: ["template", "xxx"]
cover:
    image: "images/cover.webp" # image path/url
    alt: "" # alt text
    caption: "" # display caption under cover

# Usually no need to modify
author: "Pengcheng"
# show table of content
ShowToc: false
ShowBreadCrumbs: false
draft: false
---
# Header 1
This is a paragraph.
## Header 2
- Bullet point 1
- Bullet point 2
### Header 3
_Italic text_, **Bold text**, ~~Strikethrough~~, `code`
> This is a quote. 
#### Header 4
Some cross-references here. Baidu[^1] and Google [^2] have helped a lot for building up this website.

### Insert codes
{{< highlight c >}}
#include <stdio.h>
int main() {
   // printf() displays the string inside quotation
   printf("Hello, World!");
   return 0;
}

{{< /highlight >}}
#### or 
```C
#include <stdio.h>
int main() {
   // printf() displays the string inside quotation
   printf("Hello, World!");
   return 0;
}
```

### Insert a figure
- set width by `width=[pixels]`
- set figure position by `align=left|center|right`

{{< figure width=600 align=center src="images/cover.webp" caption="Template caption" title="A bold title" >}}

### Insert a video
{{<plyr "videos/light-messenger-demo.m4v" "videos/light-messenger-demo_thumb.webp">}}

This is a custom `hugo shortcode` developed by Sark. See `layouts/shortcodes` for more details.

#### how to use
```
{{plyr "path_to_video" "[path_to_video_cover]"}}
```
N.B: Videos (file formats included in `.gitignore`) will NOT pushed/synced to github (considering repo migration friendly; content acceleration, etc.), but instead they will be pushed to COS with `coscmd`. To do so, you will need to 
1. Configure your `coscmd` on your Mac/PC. `pip install coscmd` See [COSCMD 工具](https://cloud.tencent.com/document/product/436/10976). 
2. Find and sync videos from localhost to cos bucket. via `bash` code below. e.g., 
To find any (*) `.mov` videos in [hugo_root]/content and upload to `cos_root` 
```bash
coscmd upload -rs [path_to_your_hugo_root]/content/ / --include "*.mov"
```


### Hyperlinks
- [Do M1 macbooks support HiDPI for 1440p monitors in Beta2?](https://www.reddit.com/r/MacOSBeta/comments/oafgm7/do_m1_macbooks_support_hidpi_for_1440p_monitors/)
- [QuadHD monitor with HiDPI and Mac Mini M1](https://forums.macrumors.com/threads/solution-quadhd-monitor-with-hidpi-and-mac-mini-m1.2303291/post-30285360)


### Button to link
{{<link-button "https://google.com" "Button to link">}}

### (Optional) Image Conversion
It is suggested to `WebP` image format for better loading speed. The below snippets of code are how-to convert different types of images to WebP.

N.B.: `cwebp` `gif2webp` dependencies are required. 

Convert png tp webp
```
find ./ -type f -name '*.png' -exec sh -c 'cwebp -q 90 -alpha_q 100 -m 6 $1 -o "${1%.png}.webp"' _ {} \;
```
Convert jpg to webp
```
find ./ -type f -name '*.jpg' -exec sh -c 'cwebp $1 -o "${1%.jpg}.webp"' _ {} \;
```
Convert gif to webp
```
find ./ -type f -name '*.gif' -exec sh -c 'gif2webp $1 -o "${1%.gif}.webp"' _ {} \;
```



### References
[^1]: [Link to baidu](https://baidu.com)
[^2]: [Link to google](https://google.com)