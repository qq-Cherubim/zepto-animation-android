# zepto-animation-android
手机端的一个动画（zepto）


主页面
<!DOCTYPE html>
<html>
	<head>
		<meta charset="UTF-8">
		<meta name="viewport" content="width=device-width,initial-scale=1,minimum-scale=1,maximum-scale=1,user-scalable=no" />
		<title>尚硅谷_zepto实战_练习</title>
		<link rel="stylesheet" href="css/reset.css">
		<link rel="stylesheet" href="css/index.css">
		<link rel="stylesheet" href="css/animation.css">
	</head>
	<body>
		<div id="container">

			<!--页面page-2-1-->
			<div class="page page-1-1 page-current">
				<img class="img1 pt-page-moveFromTop" src="img/cover.png" alt="">
				<img class="img2 pt-page-moveFromLeft" src="img/wording_cover.png" alt="">
				<img class="common_img pt-page-iconUp" src="img/icon_up.png" alt="">
			</div>

			<!--页面page-2-1-->
			<div class="page page-2-1 hide">
				<img class="img1 hide pt-page-moveFromBottom" src="img/wording.png" alt="">
				<img class="img2 hide pt-page-circle" src="img/circle.png" alt="">
				<img class="img3 hide pt-page-moveFromLeft" src="img/people.png" alt="">
				<img class="img4 hide" src="img/dot1.png" alt="">
				<img class="img5 hide pt-page-scale" src="img/check_develop.png" alt="">
				<img class="common_img pt-page-iconUp hide" src="img/icon_up.png" alt="">
				<img class="img7 pt-page-scale hide" src="img/floating_develop.png" alt="">

			</div>

			<!--页面page-2-2-->
			<div class="page page-2-2 hide">
				<img class="img1 hide pt-page-rotate" src="img/introduction.png" alt="">
				<img class="img2 hide pt-page-rotate" src="img/btn_develop.png" alt="">
				<img class="img3 hide" src="img/dot2.png" alt="">
				<img class="common_img pt-page-iconUp hide" src="img/icon_up.png" alt="">
			</div>

			<!--页面page-3-1-->
			<div class="page page-3-1 hide">
				<img class="img1 pt-page-moveFromBottom hide" src="img/wording_design.png" alt="">
				<img class="img2 pt-page-circle hide" src="img/circle-design.png" alt="">
				<img class="img3 pt-page-moveFromBottom hide" src="img/people_design.png" alt="">
				<img class="img4 pt-page-scale hide" src="img/dot1.png" alt="">
				<img class="img5 pt-page-scale hide" src="img/check_design.png" alt="">
				<img class="img6 common_img pt-page-iconUp hide" src="img/icon_up.png" alt="">
				<img class="img7 pt-page-scale hide" src="img/floating_design.png" alt="">
			</div>


			<!--页面page-3-2-->
			<div class="page page-3-2 hide">
				<img class="img1 pt-page-rotate hide" src="img/introduction_design.png" alt="">
				<img class="img2 pt-page-rotate hide" src="img/btn_design.png" alt="">
				<img class="img3 pt-page-rotate hide" src="img/dot2.png" alt="">
				<img class="common_img pt-page-iconUp hide" src="img/icon_up.png" alt="">


			</div>
			<!--页面page-4-1-->
			<div class="page page-4-1 hide">
				<img class="img1 hide pt-page-moveFromBottom" src="img/wording_production.png" alt="">
				<img class="img2 hide pt-page-circle" src="img/circle-production.png" alt="">
				<img class="img3 hide pt-page-moveFromRight" src="img/people_production.png" alt="">
				<img class="img4 hide pt-page-scale" src="img/dot1.png" alt="">
				<img class="img5 hide pt-page-scale" src="img/check_production.png" alt="">
				<img class="common_img hide pt-page-iconUp" src="img/icon_up.png" alt="">
				<img class="img7 hide pt-page-scale" src="img/floating_production.png" alt="">
				<img class="img8 hide pt-page-scale" src="img/pic_shadow_production.png" alt="">
			</div>


			<!--页面page-4-2-->

			<div class="page page-4-2 hide">
				<img class="img1 pt-page-rotate hide" src="img/introduction_production.png" alt="">
				<img class="img2 pt-page-rotate hide" src="img/btn_production.png" alt="">
				<img class="img3 pt-page-rotate hide" src="img/dot2.png" alt="">
				<img class="img4 common_img pt-page-iconUp hide" src="img/icon_up.png" alt="">

			</div>
			<!--页面page-5-1 hide-->
			<div class="page page-5-1 hide">
				<img class="img1 hide pt-page-rotateCubeBottomIn" src="img/pic_back.png" alt="">
				<img class="img2 hide pt-page-rotateCubeTopIn" src="img/btn_join.png" alt="">

			</div>
		</div>

	<script src="js/zepto.js"></script>
	<script src="js/touch.js"></script>
	<script src="js/index.js"></script>
	</body>
</html>

/*index.js部分*/

$(function(){
    //TODO 初始化坐标变量
    var last = {row:0,col:0};
    var now = {row:1,col:1};

    //TODO 初始化四个方向的变量
    var direction = {up:1,right:2,down:3,left:4};

    //TODO  初始化是否移动变量
    var isMoving = false;

    //TODO 取消浏览器默认行为
    $(document).on('touchstart',function(e){
        e.preventDefault();
    });


    //TODO 向上滑动
    $(document).swipeUp(function(){
        if(isMoving){
            return;
        }
        //TODO 将滑动前手指作用的页面的坐标给滑动之后的上一个页面
        last.row = now.row;
        last.col = now.col;
        if(last.row!==5){
            now.col = 1;
            now.row =  last.row + 1;
            pageMove(direction.up)
        }
    });

    //TODO 向右滑动
    $(document).swipeRight(function(){
        last.row = now.row;
        last.col = now.col;
        if(last.row>1&&last.row<5&&last.col==2){
            now.col = last.col - 1;
            pageMove(direction.right);
        }


    });

    //TODO 向下滑动
    $(document).swipeDown(function(){
        last.row = now.row;
        last.col = now.col;
        if(last.row!==1){
            now.row = last.row - 1;
            now.col = 1;
            pageMove(direction.down)
        }
    });

    //TODO 向左滑动
    $(document).swipeLeft(function(){
        last.row = now.row;
        last.col = now.col;
        if(last.row>1&&last.row<5&&last.col==1){
            now.col = last.col+1;
            pageMove(direction.left);
        }


    });

    //TODO 定义 move 函数
    function pageMove(dir){

        //TODO 初始化作用的两个页面
        var lastPage = '.page-' + last.row + '-' + last.col;
        var nowPage = '.page-' + now.row + '-' + now.col;

        //TODO 初始化页面类
        var outClass = '';
        var inClass = '';

        //TODO 匹配方向
        switch(dir){
            case 1:
                outClass = 'pt-page-moveToTop';
                inClass = 'pt-page-moveFromBottom';
                break;
            case 2:
                outClass = 'pt-page-moveToRight';
                inClass = 'pt-page-moveFromLeft';
                break;

            case 3:
                outClass = 'pt-page-moveToBottom';
                inClass = 'pt-page-moveFromTop';
                break;
            case 4:
                outClass = 'pt-page-moveToLeft';
                inClass = 'pt-page-moveFromRight';
                break;
        }
        //TODO 为页面添加动画开始的类
        $(nowPage).removeClass('hide');
        $(lastPage).addClass(outClass);
        $(nowPage).addClass(inClass);
        isMoving = true;




        //TODO 处理动画完成时页面的类
        setTimeout(function(){
            $(lastPage).addClass('hide');
            $(lastPage).removeClass('page-current');
            $(lastPage).removeClass(outClass);
            $(lastPage).find('img').addClass('hide');


            $(nowPage).addClass('page-current');
            $(nowPage).removeClass(inClass);
            $(nowPage).find('img').removeClass('hide');

            isMoving = false;
        },600)

    }

})



/*index.css 部分*/

body{
    width:100%;
    height:100%;
}
#container{
    height:100%;
    width:100%;
}
.page{
    height:100%;
    width:100%;
}
.hide{
    display: none;
}
.page-current{
    z-index:2;
}

.page-1-1{
    background: #083846;
    position: absolute;
}

/*公共样式*/
.common_img{
    height: auto;
    width: 25px;
    position: absolute;
    top: 92%;
    left: 50%;
    margin-left: -12px;
}
.page-1-1 .img1{
    height: auto;
    width: 248px;
    position: absolute;
    top: 1%;
    left: 50%;
    margin-left: -124px;
}
.page-1-1 .img2{
    height: auto;
    width: 185px;
    position: absolute;
    top: 62%;
    left: 50%;
    margin-left: -92px;
}

/*page-2-1*/
.page-2-1{
    background: #9261BF;
    position: absolute;
}
.page-2-1 .img1{
    height: auto;
    width: 158px;
    position: absolute;
    top: 2%;
    left: 50%;
    margin-left: -79px;
    z-index: 2;
}
.page-2-1 .img2{
    height: auto;
    width: 240px;
    position: absolute;
    top: 28%;
    left: 50%;
    margin-left: -120px;
}
.page-2-1 .img3{
    height: auto;
    width: 241px;
    position: absolute;
    top: 36%;
    left: 50%;
    margin-left: -120px;
}
.page-2-1 .img4{
    height: auto;
    width: 20px;
    position: absolute;
    top: 87%;
    left: 50%;
    margin-left: -10px;
}
.page-2-1 .img5{
    height: auto;
    width: 142px;
    position: absolute;
    top: 82%;
    left: 50%;
    margin-left: -71px;
}


.page-2-1 .img7{
    height: auto;
    width: 248px;
    position: absolute;
    top: 8%;
    left: 50%;
    margin-left: -124px;
}

.page-2-2{
    background: #9261BF;
    position: absolute;
}
.page-2-2 .img1{
    height: auto;
    width: 293px;
    position: absolute;
    left: 50%;
    top: 5%;
    margin-left: -146px;
}
.page-2-2 .img2{
    height: auto;
    width: 260px;
    position: absolute;
    left: 50%;
    top: 75%;
    margin-left: -130px;
}
.page-2-2 .img3{
    height: auto;
    width: 20px;
    position: absolute;
    left: 50%;
    top: 87%;
    margin-left: -10px;
}
.page-2-2 .img6{
    height: auto;
    width: 25px;
    position: absolute;
    left: 50%;
    top: 92%;
    margin-left: -12px;
}

.page-3-1{
    background-color: #F3533C;
    position:absolute;
}
.page-3-1 .img1{
    height: auto;
    width: 166px;
    position: absolute;
    left: 50%;
    top: 2%;
    margin-left: -86px;
    z-index: 2;
}
.page-3-1 .img2{
    height: auto;
    width: 250px;
    position: absolute;
    left: 50%;
    top: 30%;
    margin-left: -125px;
}
.page-3-1 .img3{
    height: auto;
    width: 172px;
    position: absolute;
    left: 50%;
    top: 28%;
    margin-left: -55px;
}
.page-3-1 .img4{
    height: auto;
    width: 20px;
    position: absolute;
    left: 50%;
    top: 87%;
    margin-left: -10px;
}

.page-3-1 .img5{
    height: auto;
    width: 142px;
    position: absolute;
    left: 50%;
    top: 82%;
    margin-left: -71px;
}
.page-3-1 .img6{
    height: auto;
    width: 25px;
    position: absolute;
    left: 50%;
    top: 92%;
    margin-left: -12px;
}
.page-3-1 .img7{
     height: auto;
     width: 248px;
     position: absolute;
     left: 50%;
     top: 43%;
     margin-left: -124px;
}
.page-3-2{
    background-color: #F3533C;
    position:absolute;
}
.page-3-2 .img1{
    height: auto;
    width: 296px;
    position: absolute;
    left: 50%;
    top: 5%;
    margin-left: -148px;
}
.page-3-2 .img2{
    height: auto;
    width: 260px;
    position: absolute;
    left: 50%;
    top: 75%;
    margin-left: -130px;
}
.page-3-2 .img3{
    height: auto;
    width: 20px;
    position: absolute;
    left: 50%;
    top: 87%;
    margin-left: -10px;
}
.page-4-1{
    background-color: #FFBF50;
    position:absolute;
}
.page-4-1 .img1{
    height: auto;
    width: 162px;
    position: absolute;
    left: 50%;
    top: 2%;
    margin-left: -84px;
    z-index: 2;
}
.page-4-1 .img2{
    height: auto;
    width: 230px;
    position: absolute;
    left: 50%;
    top: 28%;
    margin-left: -115px;
}
.page-4-1 .img3{
    height: auto;
    width: 161px;
    position: absolute;
    left: 50%;
    top: 28%;
    margin-left: -80px;
}
.page-4-1 .img4{
    height: auto;
    width: 20px;
    position: absolute;
    left: 50%;
    top: 87%;
    margin-left: -10px;
}

.page-4-1 .img5{
    height: auto;
    width: 142px;
    position: absolute;
    left: 50%;
    top: 82%;
    margin-left: -71px;
}
.page-4-1 .img7{
    height: auto;
    width: 271px;
    position: absolute;
    left: 50%;
    top: 33%;
    margin-left: -135px;
}
.page-4-1 .img8{
    height: auto;
    width: 169px;
    position: absolute;
    left: 50%;
    top: 75%;
    margin-left: -84px;
}
.page-4-2{
    background-color: #FFBF50;
    position:absolute;
}
.page-4-2 .img1{
    height: auto;
    width: 298px;
    position: absolute;
    left: 50%;
    top: 5%;
    margin-left: -149px;
}
.page-4-2 .img2{
    height: auto;
    width: 260px;
    position: absolute;
    left: 50%;
    top: 75%;
    margin-left: -130px;
}
.page-4-2 .img3{
    height: auto;
    width: 20px;
    position: absolute;
    left: 50%;
    top: 87%;
    margin-left: -10px;
}
.page-4-2 .img4{
    height: auto;
    width: 25px;
    position: absolute;
    left: 50%;
    top: 92%;
    margin-left: -12px;
}
.page-5-1{
    background-color: #083846;
    position:absolute;
}
.page-5-1 .img1{
    height: auto;
    width: 280px;
    position: absolute;
    left: 50%;
    top: 20%;
    margin-left: -140px;
}
.page-5-1 .img2{
    height: auto;
    width: 260px;
    position: absolute;
    left: 50%;
    top: 67%;
    margin-left: -130px;
}


/*animation.css    动画部分的 css*/

.pt-page-moveFromTop{
    animation: moveFromTop .6s ease both;
}
@keyframes moveFromTop {
    from{transform: translateY(-100%)}
    to{}
}
.pt-page-moveToTop{
    animation: moveToTop .6s ease both;
}
@keyframes moveToTop {
    from{}
    to{transform: translateY(-100%)}
}
.pt-page-moveFromBottom{
    animation: moveFromBottom .6s ease both;
}
@keyframes moveFromBottom {
    from{transform: translateY(100%)}
    to{}
}
.pt-page-moveToBottom{
    animation: moveToBottom .6s ease both;
}
@keyframes moveToBottom {
    from{}
    to{transform: translateY(100%)}
}

.pt-page-moveFromLeft{
    animation: moveFromLeft .6s ease both;
}
@keyframes moveFromLeft {
    from{transform: translateX(-100%)}
    to{}
}
.pt-page-moveToLeft{
    animation: moveToLeft .6s ease both;
}
@keyframes moveToLeft {
    from{}
    to{transform: translateX(-100%)}
}

.pt-page-moveFromRight{
    animation: moveFromRight .6s ease both;
}
@keyframes moveFromRight {
    from{transform: translateX(100%)}
    to{}
}
.pt-page-moveToRight{
    animation: moveToRight .6s ease both;
}
@keyframes moveToRight {
    from{}
    to{transform: translateX(100%)}
}
.pt-page-iconUp{
    animation: iconUp 1.5s ease both infinite;
}
@keyframes iconUp {
    0%{transform: translateY(80%);opacity:0}
    50%{opacity:1}
    100%{transform: translateY(-80%);opacity:0}

}
.pt-page-circle{
    animation: circle 1.5s ease both;
}
@keyframes circle {
    0%{transform: translateY(-80%);opacity: 0.4}
    5%{transform: translateY(-80%);opacity: 0.8}
    35%{transform: translateY(50%)}
    65%{transform: translateY(-30%)}
    100%{}

}
.pt-page-scale{
    animation: scale 0.6s ease both;
}
@keyframes scale {
    from{transform: scale(.4)}
    to{}

}
.pt-page-rotate{
    animation: rotate 0.6s ease both;
}
@keyframes rotate {
    from{transform: rotateY(-90deg)}
    to{}

}

/*定义page-5-1*/
.pt-page-rotateCubeBottomIn{
    animation:rotateCubeBottomIn .6s ease-in both ;
    transform-origin: 50% 100%;
}

@keyframes rotateCubeBottomIn {
    0%{transform: translateY(-100%) rotateX(90deg);opacity: 0.3}
    50%{animation-timing-function: ease-out; transform: translateY(-50%) translateZ(-200px) rotateX(45deg);}
}

.pt-page-rotateCubeTopIn{
    animation: rotateCubeTopIn 0.6s ease both;
    transform-origin: 100% 50%;
}

@keyframes rotateCubeTopIn {
    0%{translateY(100%) rotateX(-90deg);opacity: 0.3}
    50%{animation-timing-function: ease-out;transform:translateY(50%) translateZ(-200px) rotateX(-45deg) ;}

}

