## Introduction

This is a tiny single page app that hook up with Dropbox endpoint.

Dropbox `upload` api is used, and developed with es2015.

### folder structure

```
.
├── .babelrc
├── .gitignore
├── README.md
├── client
│   ├── build
│   │   ├── bundle.js
│   │   └── bundle.js.map
│   ├── css
│   │   └── flexboxgrid.min.css
│   ├── index.html
│   └── js
│       ├── components
│       │   ├── Form.js (here ▷ 修改html和styles)
│       │   └── FormValidator.js (here ▷ 修改html和styles)
│       ├── index.js
│       └── utils
│           ├── authenticate.js
│           ├── generateFilename.js
│           └── upload.js
├── gulpfile.js
├── img0.png
├── package.json
├── server.js
├── webpack.config.js
└── yarn.lock

6 directories, 19 files
```

### Implementation

dependencies

* react
* material-ui
* flexbox

toolings

* webpack
* babel
* yarn / npm

deployment

* now.sh

### Objective

> On the scene

Users/parents fill the form on the website to send their children's profile and audio/text files

> Behind the scene

Website runs background script to sync those static assets(children profiles & audio/text files) to my Dropbox


### How to use it

Public hosting URL:

[点击进入](https://dropbox-autoloader-uilxervzfo.now.sh/)

Public Dropbox folder URL:

[点击进入](https://www.dropbox.com/sh/b3gtutjf8io2kec/AABahDmOdmCUKUy2Ivbu4heja?dl=0)

**首先测试功能是否正确**

1. 用第一个网址进行app测试
2. 第二个网址查看Dropbox收到的文件是否满足要求

**然后修改Dropbox的目标Token** （当前是我的dropbox)

登录到Dropbox的开发者网址: https://www.dropbox.com/developers/apps

然后点击屏幕右上方的`Create app`,按照提示步骤创建一个新的app，app名字会自动和Dropbox的一个folder名字绑定。

拿到token即可, 其他浮☁️

![dropbox new app page](img0.png)

**如果功能正确，那就把app的服务集成到自己的网站上面**

推荐两种方法:

1. 推荐使用`iframe`控件.(无需touch任何的source)

  将`<iframe width=600 height=600 frameborder=0 scrolling=auto src="https://dropbox-autoloader-nixgimoaps.now.sh/"/>` 复制粘贴到原先网页的HTML源代码的目标位置（被移除button的那个区域）。

2. 手动编译源代码(利用项目文件里面已经配置好的工具手动编译)

  1. 修改源文件
  2. 手动编译. Terminal中手动输入`npm run build`生成新的`/client/build/bundle.js`文件
  3. 将bundle.js文件上传到自己website的root路径下面
  4. 在自己网站的HTML源代码的</body>标签正上方添加：
  `<script src="./bundle.js" type="text/javascript">`


**手动编译**

1. 下载[安装脚本](https://raw.githubusercontent.com/lxynox/dropbox-syncer/master/install.sh)`install.sh`到桌面, Open your terminal:

  Run:

  `curl -fsSL  "https://raw.githubusercontent.com/lxynox/dropbox-syncer/master/install.sh" > ~/Desktop/install.sh`

2. 安装开发环境

  Run:

  `source ~/Desktop/install.sh`

3. 手动修改`/client/js/components/*`, 每次修改后编译source, 得到目标`bundle.js`, embed bundle.js 到HTML

  Run:

  `npm run build`
