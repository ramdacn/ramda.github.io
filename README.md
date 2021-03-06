# ramda.github.io

## 中文翻译

### 1. 在[ramdacn](https://github.com/ramdacn) github 中，下载 ramda 和 ramda.github.io，将 ramda 工程中的 ramda.js 软连接到 ramda.github.io 中。

```console
$ cd one_directory
$ mkdir ramda_translate && cd ramda_translate
$ git clone git@github.com:ramdacn/ramda.git
$ git clone git://github.com/ramdacn/ramda.github.io.git
$ cd ramda.github.io/docs/dist
$ ln -s ../../../ramda/dist/ramda.js
```

### 2. 在 ramda 工程中进行翻译。对 src 文件夹中的文件变动实时更新到 dist/ramda.js 中。

分支名用自己的名字即可，不要在 master 上开发。

一共分五部分，用下面的命令查看自己负责的部分：（命令中 num=[负责第几部分，以数字表示]，如下所示）
```console
$ num=1 && ls -l |grep "^-"| head -n $(( 48 * $num)) | tail -n 48 | awk '{ print $NF }'
```

```console
$ cd ramda/
$ git checkout -b [wangzengdi]
$ node watchsrc.js
```

打开一个新的 terminal 窗口，并进入 ramda 工程中的 src 目录，对相关 API 进行翻译。

```console
$ cd src
$ vi translate_file.js
```

### 3. 在 ramda.github.io 中查看翻译的结果，进入 ramda.github.io 工程目录中

启动本地服务，（如果端口被占用，可以换一个端口）

```console
$ npm run server
```

刷新网页即可查看最新的翻译结果。

## 原 READMD.md 文档

To generate the various files required by the website, run the following
command (using the actual version number in place of `X.Y.Z`):

```console
$ VERSION=X.Y.Z make
```


## Start local server

This repo contains all the prebuilt files used on the site.
It also contains a static file server (available after `npm i`):

	npm run server

Once this is running, visit [localhost:8080](http://localhost:8080/) to view the docs.
In the event that `:8080` is in use, you can change the port like so:

	npm run server -- -p 8081

For more details on configuring the server, see [http-server docs][http-server].

[http-server]: https://github.com/indexzero/http-server#available-options


## What to do on a new release

1. Update [package.json](./package.json) to latest version of `ramda`.

2. Install packages: `npm i`

3. `npm run make_release`


## Development

### Node version

Node 6 or above is required in order to build jsdoc.

If you are using [nvm](https://github.com/creationix/nvm#nvmrc), simply run:

	nvm install && nvm use

### Building docs

To rebuild the [docs](./docs/index.html) page:

	npm run jsdoc


### Building styles

Styles for the site are written with [Less](http://lesscss.org/), using the
[Bootstrap](https://getbootstrap.com/) package.

To rebuild the main [style.css](./style.css):

	npm run less
