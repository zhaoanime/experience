```php
<?php
    namespace app\index\controller;
    
    use\app\index\controller\Index1 as aIndex1 ;
    class Index1{
        public function index1(){
             echo "我是index模块下的index1控制器中的index1方法";
             /*$u = new\app\index\controller\User;
             $u-> index();*/
         }

         public function test(){
        //使用命名空间调用相同模块下的控制器
          $u = new \app\index\controller\index1;
          $u-> index1();
          echo "<hr>";
          //调用相同模块下的控制器
          $u = new User();
          $u->index();
          echo "<hr>";
          $u = controller('User');
          $u->index();
          echo "<hr>";
          //调用不同模块下的控制器
          $u = controller('admin/Index');
          $u->index();
          echo "<hr>";
        //使用面向对象
        $u = new aIndex1;
        $u->index1();
         }
        public function getFunc(){
            //使用相同控制器下的方法
            $this->index1();
            echo "<hr>";
            self::index1();
            echo "<hr>";
            Index1::index1();
            echo "<hr>";
            action('index1');
            echo "<hr>";
            //调用相同模块下不同控制器的方法
            action('User/index');
            echo "<hr>";
            $u = new User;
            $u->index();
            echo "<hr>";
            //调用不同模块下不同控制器下的方法
            action('admin/Index/index');
            echo "<hr>";
            $u = new \app\admin\controller\Index;
            $u->index();
        }
     }
?>
```