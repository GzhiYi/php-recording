# php-recording
1. forum-time-calc/calc.php
## 主要代码记录：
```
ate_default_timezone_set("Etc/GMT-8");
 ```
 > 由于php默认时间和国内时间相差8小时，所以在时间计算之前应该减去8小时，否则时间总是慢8小时
 ```
  $timestamp = date("Y-m-d H:i:s");
  $righttime = strtotime($timestamp)-strtotime($lasttime);    
  echo  '<div class="alert alert-success">';
      if($righttime > 86400){
          echo  '没人发帖了？都：'.(int)($righttime/86400).'天没人发了...';
      }
      else if($righttime > 3600 && $righttime < 86400){
        echo  '最新帖子更新大概为：'.(int)($righttime/3600).'小时前';
      }
      else if($righttime < 3600 && $righttime > 60){
        echo  '最新帖子更新为：'.(int)($righttime/60).'分钟前';
      }
      else{
        echo  '最新帖子更新为：'.(int)$righttime.'秒前';
      }
  echo  '</div>';
```
> 9行为初始化一个时间，为当时的时间(这么说没错吧)
> 10行调用php函数将时间转为类似 201706242201 然后进行相减。获得最新帖子发布距离现在的秒数。$lasttime为最新评论的unix时间戳
> 11-24行对获得的秒数进行逻辑判断。展示为bootstrap的警告框 alert 组件
## 展示图
![](https://github.com/GzhiYi/php-recording/blob/master/forum-time-calc/img/calc.png)
