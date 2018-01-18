## 							                   jQuery

- ### 1、jQuery效果

  - #### 1、jQuery隐藏/显示

    - 1、.hide(speed,callback) //参数可选，speed的值有 "slow"、“fast”、毫秒
    - 2、.show();同上
    - 3、toggle();// 切换

  - #### 2、淡入淡出

    - 1、.fadeIn(speed,callback);
    - 2、.fadeOut();
    - 3、.fadeToggle();

  - #### 3、滑动

    - 1、.slideDown();//滑出
    - 2、.slideUp(); // 滑入
    - 3、s.lideToggle();

  - #### 4、动画

    - 1、animate({params},speed,callback)
    - 2、若需对位置进行操作，首先把元素的CSS position属性设置为relative或absolute、fixed

  - #### 5、stop()

    - 1、.stop(); //无参数；停止动画
    - 2、.stop(stopAll);//有一个参数，当参数为true时，停止所有动画
    - 3、.stop(stopAll,gotoEnd); //有两个参数，当参数都为true时，是停止所有动作，但完成所有动作

  - #### 6、Callback

    - 1、由于Javascript语句是逐一执行的，按照次序，动画之后的语句可能会产生错误或页面冲突，因为动画还没执行完成，为了避免这个情况，需要以参数的形式添加callback函数。

  - #### 7、chaining

    - 1、方法链接，即是把所有方法链接在一起；例如：
             $("#p1").css("color","red").slideUp(2000).slideDown(2000);

    - 2、当进行链接时，代码会变得很差。不过jQuery在语法上不是很严格；可以这行和缩进

             $("#p1").css("color","red")
                     .slideUp(2000)
                     .slideDown(2000);

- ### 2、jQuery HTML
    jQuery中最重要的部分，就是DOM操作能力。

    jQuery提供一系列与DOM相关的方法，这使访问和操作元素和属性变得很容易。

  - #### 1、获取

    - 1、.text();  //设置或返回所选元素的文本内容
    - 2、.html();  //设置或返回所选元素的内容（包括标签）
    - 3、.val();   //  设置或返回表单字段的值
    - 4、.attr();  //用于获取属性值

  - #### 2、设置
    - 1、text()、html()、val() 的三个方法拥有回调函数。回调函数有两个参数：被选元素列表中当前元素的下标，以及原始值。
            $("#btn1").click(function(){
              $("#test1").text(function(i,origText){
                 return "Old text: " + origText + " New text: Hello world!
                 (index: " + i + ")";
              });
             });
            $("#btn2").click(function(){
              $("#test2").html(function(i,origText){
                return "Old html: " + origText + " New html: Hello <b>world!</b>
                (index: " + i + ")";
              });
            });

    - 2、attr()方法允许设置多个属性
             $("button").click(function(){
              $("#w3s").attr({
               "href" : "http://www.w3school.com.cn/jquery",
               "title" : "W3School jQuery Tutorial"
              });
             });

    - 3、attr()的回调函数：jQuery 方法 attr()，也提供回调函数。回调函数由两个参数：被选元素列表中当前元素的下标，以及原始（旧的）值。然后以函数新值返回您希望使用的字符串。
             $("button").click(function(){
               $("#w3s").attr("href", function(i,origValue){
                 return origValue + "/jquery";
               });
            });

  - #### 3、添加

    - 1、append() - 在被选元素的结尾插入内容

    - 2、prepend() - 在被选元素的开头插入内容

      - append()和prepend()方法能够通过参数接收无限量的新元素。可以通过jQuery生成文本/HTML元素function appendText()；或者通过Javascript代码和DOM元素。
            {
              var txt1="<p>Text.</p>";               // 以 HTML 创建新元素
              var txt2=$("<p></p>").text("Text.");   // 以 jQuery 创建新元素
              var txt3=document.createElement("p");  // 以 DOM 创建新元素
              txt3.innerHTML="Text.";
              $("p").append(txt1,txt2,txt3);         // 追加新元素
            }

    - 3、after() - 在被选元素之后插入内容

    - 4、before() - 在被选元素之前插入内容
            function afterText(){
               var txt1="<b>I </b>";             // 以 HTML 创建新元素
               var txt2=$("<i></i>").text("love ");     // 通过 jQuery 创建新元素
               var txt3=document.createElement("big");  // 通过 DOM 创建新元素
               txt3.innerHTML="jQuery!";
               $("img").after(txt1,txt2,txt3);          // 在 img 之后插入新元素
            }

- #### 4、删除
     若需删除元素和内容，一般可以使用以下两个jQuery方法
     - 1、remove() - 删除被选元素(及其子元素)
     - 2、empty() - 从被选元素中删除子元素
     - 3、过滤被删除的元素，remove()方法可接受一个参数，允许对被删元素进行过滤，例如：
            $("p").remove(".italic");
            参数可以是任何jquery选择器的语法；这个例子就是删除class=“italic”的p元素

- #### 5、CSS类
     - 实例样式表
             .important{
                 font-weight:bold;
                 font-size:xx-large;
             }
            .blue{color:blue;}

     - 1、addClass() —— 向被选元素添加一个或多个类
             下面这个例子是向不同元素添加class属性；当然在添加类时，可以选取多个元素
              $("button").click(function(){
                 $("h1,h2,p").addClass("blue");
               $("div").addClass("important");
             });
             也可以在addClass()方法中规定多个类
             $("button").click(function(){
               $("#div1").addClass("important blue");
             });
     - 2、removeClass() —— 从被选元素中移除一个或多个类
            $("button").click(function(){
               $("h1,h2,p").removeClass("blue");
            });

     - 3、toggleClass() —— 对被选元素进行添加/删除类的操作
            $("button").click(function(){
               $("h1,h2,p").toggleClass("blue");
            });

     - 4、css() —— 设置或返回样式属性

        - 返回css属性
                $("p").css("background-color");
                将返回首个匹配元素的background-color值

        - 设置css属性
                $("p").css("background-color","yellow");
                将为所有匹配元素设置bakground-color值
        - 设置多个css属性
                $("p").css({"background-color":"yellow","font-size":"200%"});

- #### 6、尺寸
    jQuery提供多个处理尺寸的重要方法
    - 1、width()
    - 2、height()
            width()和height()方法设置或返回元素的宽、高(不包括内边距、外边距、边框)
            $("button").click(function(){
               var txt="";
               txt+="Width: " + $("#div1").width() + "</br>";
               txt+="Height: " + $("#div1").height();
               $("#div1").html(txt);
            });
    - 3、innerWidth()
    - 4、innerHeight()
            innerWidth()和innerHeight()方法返回元素的宽、高(包括内边距)
            $("button").click(function(){
               var txt="";
               txt+="Inner width: " + $("#div1").innerWidth() + "</br>";
               txt+="Inner height: " + $("#div1").innerHeight();
               $("#div1").html(txt);
            });
    - 5、outerWidth()
    - 6、outerHeight()
            无参数
            outerWidth()和outerHeight()方法返回元素的宽高(包括内边距和边框)
            $("button").click(function(){
               var txt="";
               txt+="Outer width: " + $("#div1").outerWidth() + "</br>";
               txt+="Outer height: " + $("#div1").outerHeight();
               $("#div1").html(txt);
            });
            有参数
            outerWidth(true)和outerHeight(true)方法返回元素的宽高（包括内边距、边框和外边距）。
            $("button").click(function(){
               var txt="";
               txt+="Outer width (+margin): " +      $("#div1").outerWidth(true) + "</br>";
               txt+="Outer height (+margin): " + $("#div1").outerHeight(true);
              $("#div1").html(txt);
            });
    - 7、返回文档(HTML文档)和窗口(浏览器窗口)的宽高
            $("button").click(function(){
               var txt="";
               txt+="Document width/height: " + $(document).width();
               txt+="x" + $(document).height() + "\n";
               txt+="Window width/height: " + $(window).width();
               txt+="x" + $(window).height();
               alert(txt);
            });

- ### 3、jQuery遍历
    - #### 1、遍历

      - 遍历，意为"移动"，用于根据其相对于其他元素的关系来查找(或获取)HTML元素
      - 遍历方法中最大的种类是树遍历(tree-traversal)

    - #### 2、遍历-祖先
      - 通过jQuery能够向上遍历DOM树，以查找元素的祖先，
      - 以下这些方法用于向上遍历DOM树
        - 1、parent()方法返回被选元素的直接父元素；该方法只会向上一级对DOM树进行遍历
                $(document).ready(function(){
                     $("span").parent();
                });
                这个例子是直接返回span的直接父元素

        - 2、parents()方法返回被选元素的所有根元素，它一路向上直到文档的根元素(<html>)
                $(document).ready(function(){
                  $("span").parents();
                 });
                 这个例子返回的是span元素的所有祖先
        - 3、parentsUntil()方法
                $(document).ready(function(){
                  $("span").parentsUntil("div");
                });
                返回的是介于span和div之间的所有span祖先元素

    - ####3、遍历-后代
        -  通过jQuery向下遍历DOM树，以查找元素的后代

        -  一下这些方法是向下遍历DOM树的jQuery方法:

          - 1、children()方法返回被选元素的所有直接子元素;该方法只会向下一级对DOM树进行遍历
                $(document).ready(function(){
                   $("div").children();
                });
                这个例子会返回每个div的所有直接子元素
                $(document).ready(function(){
                   $("div").children("p.1");
                 });
                 这个例子会返回类名为1的所有p元素，且都是div的的直接子元素
          - 2、find()方法返回被选元素的后代元素,一路向下直到最后一个后代。
                $(document).ready(function(){
                  $("div").find("span");
                });
                这个例子会返回div后代的所有span元素
                $(document).ready(function(){
                  $("div").find("*");
                });
                这个例子返回div的所有后代

    - #### 4、遍历-同胞
       - 在DOM树中水平遍历
       - 一下方法是在DOM树进行水平遍历
         - 1、siblings()方法返回被选元素的所有同胞元素
                $(document).ready(function(){
                   $("h2").siblings();
                });
                返回h2的所有同胞元素
                $(document).ready(function(){
                   $("h2").siblings(p);
                });
                返回属于h2的同胞元素的所有p元素

         - 2、next()方法返回被选元素的下一个同胞元素

         - 3、nextAll()方法返回被选元素的所有后面的同胞元素

         - 4、nextUntil()方法返回介于两个给定参数之间的所有跟随的所有同胞元素
                $(document).ready(function(){
                  $("h2").nextUntil("h6")
                });
                返回介于h2和h6元素之间的所有同胞元素

         - 5、prev()方法返回被选元素的上一个同胞元素

         - 6、prevAll()方法返回被选元素的所有前面的同胞元素

         - 7、prevUntil()方法返回介于两个给定参数之间的所有跟随的所有同胞元素与nextUntil方法相同，只是方向相反

    - #### 5、遍历-过滤

       - 三个最基本的过滤方法是：first(), last(), eq(),它们允许基于其在一组元素中的位置来选择一个特定的元素。比如filter()和not()允许选取匹配或不匹配某项指定标准的元素。
         - 1、first()方法返回被选元素的首个元素
                $(document).ready(function(){
                   $("div p").first();
                });
                这个例子选取首个div元素内部的第一个p元素 

         - 2、last()方法返回被选元素的最后一个元素

         - 3、eq()方法返回被选元素中带有执行索引号的元素;索引号从0开始，因此首个元素的索引是0
                $(document).ready(function(){
                   $("p").eq(1);
                });
                这个例子是选取第二个p元素
         - 4、filter()方法允许自定义一个标准，不匹配这个标准的元素会从集合中删除，匹配这个标准的会返回
                $(document).ready(function(){
                  $("p").filter(".intro");
                });
                这个例子返回带有类名"intro"的所有p元素
         - 5、not方法()返回不匹配标准的所有元素;与filter()方法相反
                $(document).ready(function(){
                  $("p").filter(".intro");
                });
                这个例子返回不带有类名"intro"的所有p元素

- ### 4、jQuery Ajax

    - #### 1、jquery ajax简介

      - ajax使用服务器交换数据的技术，它在不重载全部页面的情况下，实现页面的刷新。
      - ajax = 异步 JavaScipt和XML(Asynchronos JavaScript and XML);j简单地说，在不重载整个网页的情况下，ajax通过后台加载数据，并在网页上进行显示

    - #### 2、jquery加载

      -  load()方法从服务器加载数据，并把返回的数据放入被选元素中。
      - 语法:
             $(selector).load(URL,data,callback);
         - 1、必需的URL参数规定希望加载的URL;

             $("#div1").load("demo_test.txt");
             把文件"demo_test.txt"的内容加到指定的div元素中
         - 2、可选的data参数规定与请求一同发送的查询字符串键值对集合

             $("#div1").load("demo_test.txt #p1");
             把“demo_test.txt”文件中id=“p1”的元素内容,加载到指定的div中
         - 3、可选的callback参数是load()方法完成后所要允许的回调函数。回调函数可以设置不同的参数
           - responseTxt - 包含调用成功时的结果内容
           - statusTxt - 包含调用的状态
           - xhr - 包含XMLHttpRequest对象
                 $("button").click(function(){          $("#div1").load("demo_test.txt",function(responseTxt,statusTxt,xhr){
                    if(statusTxt=="success")
                        alert("外部内容加载成功！");
                     if(statusTxt=="error")
                         alert("Error: "+xhr.status+": "+xhr.statusText);
                     });
                  });
                  load()方法成功，则显示"外部内容加载成功"；失败则显示错误信息

    - #### 3、jQuery—Ajax get() 和post()方法

      - jquery get()和post()方法用于通过http get或post请求从服务器请求数据

      - HTTP请求：GET && POST
        - 两种在客户端和服务器端进行请求-响应的常用方法是：GET和POST。
          - GET - 从指定的资源请求资源
          - POST - 向指定的资源提交要处理的数据
        - GET基本上用于从服务器获得数据。GET方法可能返回缓存数据。
        - POST也可用于从服务器获取数据,不过POST不会缓存数据，并且常用于连同请求一起发送数据。

      - jQuery $.get()方法
         - $.get()方法通过HTTP GET请求从服务器上请求数据。
         - 语法:
                $.get(URL,callback);
         - 必需的URL参数规定希望请求的URL
         - 可选的callback参数是请求成功后执行的函数名
         - 实例
                $("button").click(function(){
                  $.get("demo_test.asp",function(data,status){
                  alert("Data: " + data + "\nStatus: " + status);
                  });
               });
               $.get()的第一个参数与是要请求的URL("demo_test.asp")
               第二个参数是回调函数。第一个参数存有被请求页面的内容,第二个参数存有请求的状态。

      - jQuery $.post()方法

         - $.postt()方法通过HTTP POST请求从服务器上请求数据。

         - 语法:

           ```
           $.post(URL, data,callback);
           ```

         - 必需的URL参数规定希望请求的URL

         - 可选的data参数规定连同请求发送的数据

         - 可选的callback参数是请求成功后执行的函数名

         - 实例

           ```
           $("button").click(function(){
             $.post("demo_test_post.asp",
             {
               name:"Donald Duck",
               city:"Duckburg"
             },
             function(data,status){
               alert("Data: " + data + "\nStatus: " + status);
             });
           });
           ```

              });
              $.post()的第一个参数与是要请求的URL("demo_test.asp");然后连同请求(name和city)一起发送数据。

              第三个参数是回调函数。第一个参数存有被请求页面的内容,第二个参数存有请求的状态。
- ### 5、jQuery — noConflict()
   - #### noConflict() 方法会释放对$标识符的控制，这样其他脚本就可以使用了

   - #### 也可以通过全名代替简写的方式来使用jQuery
         $.noConflict();
         jQuery(document).ready(function(){
           jQuery("button").click(function(){
             jQuery("p").text("jQuery 仍在运行！");
           });
         });

   - #### 也可以创建自己的简写
         var jq = $.noConflict();
         jq(document).ready(function(){
           jq("button").click(function(){
             jq("p").text("jQuery 仍在运行！");
           });
         });

   - #### 当然可以把$符号作为变量传递给ready方法。这样就可以在函数内使用\$符号了，而在函数外，还是得使用“jQuery”：
          $.noConflict();
          jQuery(document).ready(function($){
            $("button").click(function(){
               $("p").text("jQuery 仍在运行！");
            });
          });