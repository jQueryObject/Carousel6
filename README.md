# jQuery手机图片触屏滑动轮播效果代码Carousel6
效果如下：
![](images/img.gif)

html code:
```
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <title>jQuery手机图片触屏滑动轮播效果代码</title>
    <link rel="stylesheet" href="css/style.css" />
</head>
<body>
<div class="main_visual">
	<div class="flicking_con">
		<a href="#">1</a>
		<a href="#">2</a>
		<a href="#">3</a>
		<a href="#">4</a>
		<a href="#">5</a>
	</div>
	<div class="main_image">
		<ul>
			<li><span class="img_3"></span></li>
			<li><span class="img_4"></span></li>
			<li><span class="img_1"></span></li>
			<li><span class="img_2"></span></li>
			<li><span class="img_5"></span></li>
		</ul>
		<a href="javascript:void(0);" id="btn_prev"></a>
		<a href="javascript:void(0);" id="btn_next"></a>
	</div>
</div>
</body>
</html>
<script src="js/jquery-1.7.1.min.js"></script>
<script src="js/jquery.event.drag-1.5.min.js"></script>
<script src="js/jquery.touchSlider.js"></script>
<script>
	$(document).ready(function(){
		$(".main_visual").hover(function(){
			$("#btn_prev,#btn_next").fadeIn()
		},function(){
			$("#btn_prev,#btn_next").fadeOut()
		});
		$dragBln = false;
		$(".main_image").touchSlider({
			flexible : true,
			speed : 200,
			btn_prev : $("#btn_prev"),
			btn_next : $("#btn_next"),
			paging : $(".flicking_con a"),
			counter : function (e){
				$(".flicking_con a").removeClass("on").eq(e.current-1).addClass("on");
			}
		});
		$(".main_image").bind("mousedown", function() {
			$dragBln = false;
		});
		$(".main_image").bind("dragstart", function() {
			$dragBln = true;
		});
		$(".main_image a").click(function(){
			if($dragBln) {
				return false;
			}
		});
		timer = setInterval(function(){
			$("#btn_next").click();
		}, 5000);
		$(".main_visual").hover(function(){
			clearInterval(timer);
		},function(){
			timer = setInterval(function(){
				$("#btn_next").click();
			},5000);
		});
		$(".main_image").bind("touchstart",function(){
			clearInterval(timer);
		}).bind("touchend", function(){
			timer = setInterval(function(){
				$("#btn_next").click();
			}, 5000);
		});
	});
</script>
```

