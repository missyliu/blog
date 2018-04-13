#用 hexo 搭建博客

## 安装[hexo](https://hexo.io/)

```
$ npm install hexo-cli -g
$ hexo init blog
$ cd blog
$ npm install
$ hexo server
```

## 安装主题[maupassant](https://www.haomwei.com/technology/maupassant-hexo.html)

```
$ git clone https://github.com/tufu9441/maupassant-hexo.git themes/maupassant
// 注意：建议使用 cnpm
$ npm install hexo-renderer-jade --save
$ npm install hexo-renderer-sass --save
```

## 发布常用命令

```
$ hexo clean
$ hexo generate
$ hexo server
$ hexo deploy

$ hero init <folder> // 如果指定 <folder>，便会在目前的资料夹建立一个名为 <folder> 的新资料夹；否则会在目前资料夹初始化。
$ hexo new “<文件名>” // 创建新博客
```
