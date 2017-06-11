# Laravel-5.1-Practice

## 一.开发环境

#### 1.代码位置：
     win10：C:\Users\caisen\Code
     ubuntu: /home/vagrant/Code/Laravel

#### 2.本地域名：http://homestead.app/

#### 3.开启步骤(git bash)：
    1. cd ~/Homestead && vagrant up
    2. vagrant ssh
    3. exit

#### 4.在windows上面修改代码，在ubuntu中git提交代码

#### 5.homsestead的配置文件在windows里面的，在这个文件里配置相应的站点和数据库
    atom ~/.homestead/Homestead.yaml
每次修改Homestead.yaml文件，都需要重新加载和启动

    cd ~/Homestead && vagrant provision && vagrant reload

* vagrant provision 是命令 Vagrant 重新加载 Homestead.yaml 配置；
* vagrant reload 是重启虚拟机使更改生效。

#### 6.windows gitBash 和ubuntu中都可以免密码gitHub

#### 7.如何设置gitHub免密码登录：参考网上教程，只有git clone SSH才能密码登录，git clone 不可以，需要修改：

    git remote set-url origin

    
## 二.Laravel基础知识

#### 1.创建


```
composer create-project laravel/laravel Laravel --prefer-dist "5.1.*"
```

#### 2.数据库，readis等配置文件
   * 相关配置文件在根目录的.env的文件中
   * 可以通过代码getenv('APP_ENV')，拿到相关配置信息
   
#### 3. 在项目根目录

    yarn install  #安装相关module
    gulp 
    
#### 4. 生成静态页面控制器 --plain更加简洁的控制器
    $ php artisan make:controller StaticPagesController
    $ php artisan make:controller StaticPagesController --plain
    
#### 5.添加静态页面视图（在 resources/views 文件夹下面）
    return view('static_pages/home');
    
#### 6.通用视图

```
<!DOCTYPE html>
<html>
<head>
    <title>@yield('title', 'Sample App') - Laravel 入门教程</title>
</head>
<body>
@yield('content')
</body>
</html>
<!-- ---------------------------!>
<!DOCTYPE html>
<html>
<head>
    <title>@yield('title', 'Sample App') - Laravel 入门教程</title>
</head>
<body>
@yield('content')
</body>
</html>


```

    

    

    