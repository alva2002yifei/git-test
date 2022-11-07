<template>
       <div id="wrapper">
    <div class="face" id="blue">
        <div class="eyes">
            <div class="eye-left">
                <div class="eye-in"></div>
            </div>
            <div class="eye-right">
                <div class="eye-in"></div>
            </div>
        </div>
        <div class="nose">
            <a></a>
            <a></a>
        </div>
        <div class="mouth">
            <div class="tooth" id="tooth1"></div>
            <div class="tooth" id="tooth2"></div>
            <div class="tooth" id="tooth3"></div>
            <div class="tooth" id="tooth4"></div>
        </div>
    </div>
    <div class="dialogue">
				<div class="dialogueContent">
					......
				</div>
				<div class="icon"></div>
			</div>
</div>

</template>

<script>
window.onload = function () {
  var eyes = [];
  eyes = document.querySelectorAll(".eye-in");
  var dialogueAtr = [
						"Don't touch me!",
						"干哈呢！摸我",
						"别碰我",
						"正经点听歌去"
					]
  document.onmousemove = function (event) {
    var mouseLeft = event.clientX,
      mouseTop = event.clientY;
      var randomNum = Math.floor(Math.random() * dialogueAtr.length)
	 var dialogueStr = dialogueAtr[randomNum]
     this.content =dialogueStr
    throttle(function () {
      $forEach(eyes, function (o, i) {
        var chaX = mouseLeft - getOffset(eyes[i]).left;
        var chaY = mouseTop - getOffset(eyes[i]).top;
        var viewportWidth = getViewportSize().width / 2;
        var viewportHeight = getViewportSize().height / 2;
        //mouseLeft 与 mouseTop的值有时候太小，导致差值太小
        eyes[i].style.left = (chaX / viewportWidth) * 50 + "%";
        eyes[i].style.top = (chaY / viewportHeight) * 50 + "%";
      });
    });
  };

  // 要用到的函数
  function throttle(method, context) {
    clearTimeout(method.tId);
    method.tId = setTimeout(function () {
      method.call(context);
    }, 70);
  }

  function $forEach(arr, callback, thisp) {
    if (arr.forEach) {
      arr.forEach(callback, thisp);
    } else {
      for (var i = 0, len = arr.length; i < len; i++) {
        callback.call(thisp, arr[i], i, arr);
      }
    }
  }

  // 单位
  function getOffset(element) {
    var actualLeft = element.offsetLeft;
    var actualTop = element.offsetTop;
    // var actualTop = element.offsetWidth / 2;
    // var actualLeft = element.offsetHeight /2;
    var current = element.offsetParent;

    while (current !== null) {
      actualTop += current.offsetTop;
      actualLeft += current.offsetLeft;
      current = current.offsetParent;
    }

    return { left: actualLeft, top: actualTop };
  }

  function getViewportSize() {
    var pageWidth = window.innerWidth,
      pageHeight = window.innerHeight;

    if (typeof pageWidth != "number") {
      pageWidth = document.documentElement.clientWidth;
      pageHeight = document.documentElement.clientHeight;
    } else {
      pageWidth = document.body.clientWidth;
      pageHeight = document.body.clientHeight;
    }
    // console.log(pageWidth);
    return { width: pageWidth, height: pageHeight };
  }
};
export default {
  data() {
    return {
      content:''
    }
  },
};
</script>


<style>
        * {
            margin: 0;
            padding: 0;
        }

        div#wrapper {
            width: 600px;
            height: 600px;
            background-color: pink;
            display: flex;
            justify-content: center;
            align-items: center;
        }

        div.face {
            position: relative;
            top: 20%;
            margin-left: 0px;
            margin-right: 0px;
            width: 200px;
            height: 250px;
            display: inline-block;
            overflow: hidden;
            background-color: #2db5ae;
            border-radius: 45% 45% 0 0;
        }


        div.eyes {
            position: relative;
            top: 70px;
            width: 100%;
            height: 80px;
            background-color: #2db5ae;
        }

        div.eye-left {
            position: absolute;
            left: 10%;
            overflow: hidden;
            width: 35%;
            height: 100%;
            background-color: white;
            border-radius: 45% 45% 55% 55%;
        }

        div.eye-right {
            position: absolute;
            right: 10%;
            overflow: hidden;
            width: 35%;
            height: 100%;
            background-color: white;
            border-radius: 45% 45% 55% 55%;
        }

        div.eye-in {
            position: relative;
            display: inline-block;
            width: 45%;
            height: 55%;
            margin-right: 0;
            margin-left: 0;
            margin-top: 20px;
            background-color: black;
            border-radius: 50% 50%;
        }

        div.nose {
            position: relative;
            top: 32%;
            text-align: center;
        }

        div.nose a {
            display: inline-block;
            background-color: white;
            height: 10px;
            width: 10px;
            border-radius: 5px;
        }

        div.mouth {
            position: relative;
            top: 90px;
            width: 100%;
            height: 25%;
            display: inline-block;
            overflow: hidden;
            text-align: center;
            background-color: #614030;
            border-radius: 81% 5% 81% 5%;
        }

        div.tooth {
            position: relative;
            height: 50px;
            width: 35px;
            display: inline-block;
            margin-left: -7px;
            background-color: white;
            border-radius: 0 0 50% 50%;
        }

        div #tooth1 {
            top: 0px;
        }

        div #tooth2 {
            top: -5px;
        }

        div #tooth3 {
            top: -10px;
        }

        div #tooth4 {
            top: -15px;
        }
        .dialogue{
				 position: absolute; 
				top: 0;
				left: auto;
				/* transform: translateY(-140%);  */
				width: 100%;
		 /* display: none;  */
			}
			.dialogue .dialogueContent{
				border-radius: 50%;
				width: 100%;
				box-sizing: border-box;
				border: 1px solid #555555;
				padding: 18px;
				background: #FFFFFF;
				text-align: center;
			}
      .icon{
				border: 1px solid #555;
				width: 10px;
				/* transform: rotate(45deg) skewX(46deg) rotate(37deg); */
				height: 20px;
				border-top: none;
				border-left: none;
				position: absolute;
				bottom: -10px;
				left: 79px;
				background: #ffffff;
			}
    </style>

