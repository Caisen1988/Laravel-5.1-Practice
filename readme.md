# Laravel-5.1-Practice

## 一.开发环境

#### 0. [开发工具](https://pan.baidu.com/s/1mh94q9a#list/path=%2F)
> 编辑器：atom 虚拟机：vartualBox vagrant

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
    
#### 8.运行yarn install 报错是因为虚拟机OS的原因
    yarn --no-bin-links
    
#### 9.0 运行gulp报错 重新编译    
    npm rebuild node-sass --no-bin-links


    
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

#### 7.前端工作流
    gulp 
    gulp watch
    
#### 8.数据库
* 8.1 Homestead 虚拟机里的 MySQL 数据库服务器连接方式为：
    Host: 127.0.0.1
    Port: 33060
    User: homestead
    Pass: secret

* 8.2 配置文件在根目录下面 .env

* 8.3 数据库迁移

```
php artisan migrate
``` 

 > migrations 表。这种表是在我们在第一次执行 artisan migrate 命令时生成的，其作用是用来做迁移版本的记录。
    
* 8.4 数据库回滚 
```
    $ php artisan migrate:rollback
``` 

* 8.5 数据库重置
```    
    $ php artisan migrate:refresh
```    

#### 9.Tinker 操作环境
```
php artisan tinker //进入tinker环境

>>> App\Models\User::create(['name'=> 'Aufree', 'email'=>'aufree@estgroupe.com','password'=>bcrypt('password')])

User::first()   //进行数据库操作
$user->name = 'Summer'
$user->save()   //保存后生效
$user->update(['name'=>'Aufree'])
```

#### 10.用户资源路由(RESTful 架构)

    Route::resource('users', 'UsersController');
上面代码将等同于：
```
Route::get('/users', 'UsersController@index')->name('users.index');
Route::get('/users/{user}', 'UsersController@show')->name('users.show');
Route::get('/users/create', 'UsersController@create')->name('users.create');
Route::post('/users', 'UsersController@store')->name('users.store');
Route::get('/users/{user}/edit', 'UsersController@edit')->name('users.edit');
Route::patch('/users/{user}', 'UsersController@update')->name('users.update');
Route::delete('/users/{user}', 'UsersController@destroy')->name('users.destroy');
```

#### 11.Gravatar 头像
> Gravatar 为 “全球通用头像”，当你在 Gravatar 的服务器上放置了自己的头像后，可通过将自己的 Gravatar 登录邮箱进行 MD5 转码，并与 Gravatar 的 URL 进行拼接来获取到自己的 Gravatar 头像。

#### 12. CSRF
 * 使用 POST 方法提交表单时，Laravel 为了安全考虑，会让我们提供一个 token（令牌）来防止我们的应用受到 CSRF（跨站请求伪造）的攻击
```   
    {{ csrf_field() }}
```
    
#### 14.session

```
session()->flash('success', '欢迎，您将在这里开启一段新的旅程~');
```

