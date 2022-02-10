---
layout:     post
title:      "关于 Typora 的图片显示问题"
subtitle:   
date:       2022-02-10 06:35:00
author:     "Cooper"
header-img: "img/post-bg-2015.jpg"
catalog: true
typora-root-url: ../
tags:
    - Typora
    
---



在`Typora`中设置 Image 的路径：



![Screen Shot 2022-02-10 at 06.45.22](/img/md-post/2022-02-10-Typora%20image/Screen%20Shot%202022-02-10%20at%2006.45.22.png)



![Screen Shot 2022-02-10 at 06.46.19](/img/md-post/2022-02-10-Typora%20image/Screen%20Shot%202022-02-10%20at%2006.46.19.png)

此后在`Typora`中插入图片后，图片的位置会自动保存在`../img/md-post/${filename}`，这里是指去上一个目录找`img/md-post`文件夹，`${filename}`是图片的文件名。

而后，在写`markdown`的时候，将`typora-root-url`的路径设置为`../`,如下所示：

```
---
layout:     post
title:      "Trinity tutorial"
subtitle:   
date:       2019-02-01 12:00:00
author:     "Cooper"
header-img: "img/post-bg-2015.jpg"
catalog: true
typora-root-url: ../
tags:
    - Bioinformatic tools
    - Ttranscriptome
---    
```

此时，无论在`Typora`或 `Jekyll`中都能正常显示图片啦。