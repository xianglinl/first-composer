# first-composer
第一次尝试写自己的composer

1.在GitHub上创建一个自己的项目，然后拉取到本地

`git clone https://github.com/XianglinLiu/first-composer.git`

2.在对应的项目目录里面执行`composer init`

```
cd first-composer
composer init #一路回车就可
```

然后可看到生成了文件`composer.json`

```json
{
    "name": "xianglin/first-composer",
    "description": "this is a test composer",
    "authors": [
        {
            "name": "xianglin",
            "email": "793101759@qq.com"
        }
    ],
    "require": {}
}

```



3.在根目录新建文件夹`src`

`mkdir src`

4.新建测试文件.`Test.php` 并声明命名空间

```php
<?php
/**
 * Created by YupaoWang
 * User：liubo
 * Date：2020/5/26
 * Time：20:14
 */

namespace firstComposer;

class TestComposer
{
    public function showTime()
    {
        echo '当时北京时间: ' . date('Y-m-d H:i:s');
    }
}
```

5.修改`composer.json` 新增`autoload`

```json
{
  "name": "xianglin/first-composer",
  "description": "this is a test framework",
  "license": "MIT",
  "authors": [
    {
      "name": "xianglin",
      "email": "793101759@qq.com"
    }
  ],
  "autoload": {
    "psr-4": {
      "firstComposer\\": "src/"
    }
  },
  "require": {}
}

```

6.执行`tree` 命令可以看到当前目录结构

```
.
├── README.md
├── composer.json
└── src
    └── TestComposer.php
```



7.执行`composer install` ，然后哦执行`tree`查看当前目录文件

```
.
├── README.md
├── composer.json
├── src
│   └── TestComposer.php
└── vendor
    ├── autoload.php
    └── composer
        ├── ClassLoader.php
        ├── LICENSE
        ├── autoload_classmap.php
        ├── autoload_namespaces.php
        ├── autoload_psr4.php
        ├── autoload_real.php
        ├── autoload_static.php
        └── installed.json
```

8.进行测试，新建测试文件夹`exp` 新建测试文件`index.php`
```php
<?php

require_once(__DIR__ . '../../vendor/autoload.php');

use firstComposer\TestComposer;

(new TestComposer())->showTime();
```

`php exp/index.php`

输出:`当时北京时间: 2020-05-26 12:27:43%`

9.编辑文件`.gitignore`

```
vim .gitignore
#写入以下数据
/vendor/
```

10.提交代码到GitHub

```
git add . && 
git commit -m ':rocket: 这个第一次自己写composer 组件' && 
git pull && git push
```

11.检测compser包 [packagist.org](https://packagist.org/packages/submit)

12.检测正常，点击提交即可,提交成功将会跳转到已发布包的[地址](https://packagist.org/packages/xianglin/composer-lear)

13.打包命令,我是直接在GitHub上打包的。
```bash
    git tag 1.0 
    git push origin --tags
```
14.测试一下 ,随便建一个文件夹执行命令

```bash
composer require xianglin/first-composer
```

15.执行命令 输出时间 (`可能需要修改index.php require_once`)

```
php vendor/xianglin/first-composer/exp/index.php
```


