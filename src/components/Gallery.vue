<script setup>
  import $ from 'jquery';
</script>

<template>
  <link rel="stylesheet" type="text/css" href="src/css/font.css">
  <h1 class="gallery_open"><br><br>Gallery</h1>
  <div class="container">
	
  <div class="gallery">
    <div class="main">
      <div class="main-img">
        <div class="item-img active" data-slide="1"><img src="../assets/images/10.jpg" style="width: 75vh; height: auto;"></div>
        <div class="item-img" data-slide="2"><img src="../assets/images/11.jpg" style="width: 75vh; height: auto;"></div>
        <div class="item-img" data-slide="3"><img src="../assets/images/13.jpg" style="width: 75vh; height: auto;"></div>
        <div class="item-img" data-slide="4"><img src="../assets/images/14.jpg" style="width: 75vh; height: auto;"></div>
        <div class="item-img" data-slide="5"><img src="../assets/images/10.jpg" style="width: 75vh; height: auto;"></div>
        <div class="item-img" data-slide="6"><img src="../assets/images/11.jpg" style="width: 75vh; height: auto;"></div>
        <div class="item-img" data-slide="7"><img src="../assets/images/13.jpg" style="width: 75vh; height: auto;"></div>
        <div class="item-img" data-slide="8"><img src="../assets/images/14.jpg" style="width: 75vh; height: auto;"></div>
      </div>
      <div class="nutslide">
        <span class="prev"><img src="../assets/images/left.png" style="width: 30px; height: auto;"></span>
        <span class="next"><img src="../assets/images/right.png" style="width: 30px; height: auto;"></span>
      </div>
    </div><!--cot-1-->
    <div class="list-img">
      <div class="img-thumbnail">
        <img src="../assets/images/10.jpg" class="item-list active" style="height: 12vh; width: auto;">
        <img src="../assets/images/11.jpg" class="item-list" style="height: 12vh; width: auto;">
        <img src="../assets/images/13.jpg" class="item-list" style="height: 12vh; width: auto;">
        <img src="../assets/images/14.jpg" class="item-list" style="height: 12vh; width: auto;">
        <img src="../assets/images/10.jpg" class="item-list" style="height: 12vh; width: auto;">
        <img src="../assets/images/11.jpg" class="item-list" style="height: 12vh; width: auto;">
        <img src="../assets/images/13.jpg" class="item-list" style="height: 12vh; width: auto;">
        <img src="../assets/images/14.jpg" class="item-list" style="height: 12vh; width: auto;">
      </div><!--img-thumbnail-->
    </div><!--list-img-->
  </div><!--gallery-->
</div>
</template>
<style>
  *{
    box-sizing: border-box;
  }
  .gallery_open {
    text-align:center;
    font-size: 200%;
    font-family: 'EngWedding';
    color: black;
  }
 .container{
     width: 80%;
     margin:0 auto;
}
 .gallery{
     width: 100%;
     overflow: hidden;
}
 .list-img{
     display: flex;
     overflow: hidden;
     width: 100%;
     padding-top: 20px;
}
 .list-img img{
     width: 15%;
     height: 20%;
     padding-right: 20px;
     cursor: pointer;
}
 .main-img{
     display: flex;
     position: relative;
     height: 75%;
     width: auto;
}
 .main-img img{
     width: 75%;
     height: 75%;
}
 .col-main{
     position: relative;
     width: 100%;
}
 .main-img .item-img{
     height: 75%;
     min-width: 100%;
}
 img.item-list{
     opacity: 0.3;
}
 .item-list.active{
     opacity: 1;
}
 .nutslide{
     position: absolute;
     top: 50%;
     transform: translateY(-50%);
     width: 100%;
}
 span.next{
     right: 14px;
     position: absolute;
     font-size: 14;
     color: #000;
     width: 35px;
     height: 36px;
     padding-left: 8px;
     padding-right: 10px;
     border-radius: 4px;
     padding-top: 1px;
     cursor: pointer;
}
 span.prev {
     left: 14px;
     position: absolute;
     font-size: 14;
     color: #000;
     width: 35px;
     height: 36px;
     padding-left: 8px;
     padding-right: 10px;
     border-radius: 4px;
     padding-top: 1px;
     cursor: pointer;
}
 .main{
     position: relative;
     width: 100%;
}
 .img-thumbnail{
     display: flex;
     position: relative;
     width: 100%;
}

</style>
<script>
  var angle = 0;
  export default {
    data: () => ({
    }),
    created() {
      $(function() {
        $('.item-list').click(function() {
            $('.item-img').removeClass('active');
            $('.item-list').removeClass('active');
            $(this).addClass('active');
            var index = $(this).index() + 1;
            var index2 = $('.item-img:nth-child(' + index + ')').addClass('active');
            $('.main-img').animate({
                left: 0 - index2.position().left
            }, 500);
            var test = $('.item-img.active').index() + 1;
            var a = $('.item-list:nth-child(' + test + ')');
            $('.img-thumbnail').animate({
                left: 0 - (a.position().left / 2)
            }, 300);
        });
        function next() {
            var sau = $('.active').next();
            $('.item-img').removeClass('active');
            $('.item-list').removeClass('active');
            sau.addClass('active');
            if (sau.length == 0) {
                $('.main-img').animate({
                    left: 0 - $('.item-img:first-child').position().left
                }, 500);
                $('.item-img:first-child').addClass('active');
                $('.item-list:first-child').addClass('active');
            } else {
                var hay = $('.item-img.active').attr('data-slide');
                var index5 = $('.item-img:nth-child(' + hay + ')').addClass('active');
                $('.main-img').animate({
                    left: 0 - index5.position().left
                }, 500);
            }
        }
        function prev() {
            var sau = $('.active').prev();
            $('.item-img').removeClass('active');
            $('.item-list').removeClass('active');
            sau.addClass('active');
            if (sau.length == 0) {
                $('.main-img').animate({
                    left: 0 - $('.item-img:last-child').position().left
                }, 500);
                $('.item-img:last-child').addClass('active');
                $('.item-list:last-child').addClass('active');
            }
            var hay = $('.item-img.active').attr('data-slide');
            var index5 = $('.item-img:nth-child(' + hay + ')').addClass('active');
            $('.main-img').animate({
                left: 0 - index5.position().left
            }, 500);
        }
        
        $('.gallery').mouseover(function() {
            clearTimeout(2000);
        });
        $('.gallery').mouseout(function() {
        });
        //click next
        $('.next').click(function() {
            next();
            var test = $('.item-img.active').index() + 1;
            var a = $('.item-list:nth-child(' + test + ')');
            $('.img-thumbnail').animate({
                left: 0 - (a.position().left / 2)
            }, 500);
        });
        //click prev
        $('.prev').click(function() {
            prev();
            var test = $('.item-img.active').index() + 1;
            var a = $('.item-list:nth-child(' + test + ')');
            $('.img-thumbnail').animate({
                left: 0 - (a.position().left / 2)
            }, 500);
        });
    });
    },
    methods: {
    }
  }

</script>