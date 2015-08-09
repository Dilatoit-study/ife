  在前端开发中使用css来居中html元素是一个常见的开发场景。比如，水平或者是垂直居中一个元素以及水平垂直居中一个元素。方法也非常多，前两天正好看到一篇全面总结css居中技术的文章，原文地址：[https://css-tricks.com/centering-css-complete-guide/]

水平居中

 行内元素居中
  对于像普通文本或者是链接元素，要使它居中非常容易：

     .center-children {
    	text-align: center;
     }
块状元素居中

对于已知宽度的块状元素，可以使用margin:0 auto这个属性来使它居中：

    .center-me {
    	margin: 0 auto;
    }

多个块状元素居中

如果你有两个以上的元素需要水平居中。可以使用display属性来声明元素表现为行内块状元素即display:inline-block；

垂直居中

行内元素垂直居中

使用padding来使它垂直居中：

	.link {
	    padding-top: 30px;
	    padding-bottom: 30px;
	}
如果有时候使用padding不合适的话，可以使用行高line-height来使元素垂直居中。

	.center-text-trick {
	    height: 100px;
	    line-height: 100px;
	    white-space: nowrap;
	}
多行文字元素居中

使用padding能使多行的文字元素居中，不过也并不是随时都可以用。这时候可以使用display来使元素具有表格元素的属性即table-cell，然后使用vertical－align为middle来使元素居中，vertical-align：

使用css3中的flex属性也很容易使元素居中。

	.flex-center-vertically {
	    display: flex;
	    justify-content: center;
	    flex-direction: column;
	    height: 400px;      
	}

要注意的是这里是相对与父元素的高度来居中的，所以这里设置来父元素的高度。

如果上面的技术都不使用，还有一种称只为ghost element的技术来居中，主要是使用伪元素设置元素的高度配合vertical－middle属性来使元素居中：

	.ghost-center {
	    position: relative;
	}
	.ghost-center::before {
	    content: " ";
	    display: inline-block;
	    height: 100%;
	    width: 1%;
	    vertical-align: middle;
	}
	.ghost-center p {
	    display: inline-block;
	    vertical-align: middle;
	}
块状元素居中

如果知道一个元素的高度，那可以这样来做：

	.parent {
	    position: relative;
	}
	.child {
	    position: absolute;
	    top: 50%;
	    height: 100px;
	    margin-top: -50px; /* account for padding and border if not using box-sizing: border-box; */
	}

如果不知道元素的高度呢？

可以配合使用transform的属性来使它垂直居中：

	.parent {
	    position: relative;
	}
	.child {
	    position: absolute;
	    top: 50%;
	    transform: translateY(-50%);
	}

使用flexbox

使用flexbox就更容易来使元素垂直居中了。

	.parent {
	    display: flex;
	    flex-direction: column;
	    justify-content: center;
	}

知道元素的宽高

使用绝对定位就可以使元素水平垂直居中：

	.parent {
	    position: relative;
	}
	
	.child {
	    width: 300px;
	    height: 100px;
	    padding: 20px;
	
	    position: absolute;
	    top: 50%;
	    left: 50%;
	
	    margin: -70px 0 0 -170px;
	}

不知道元素的宽高

如果不知道元素的宽高，可以使用transform中的translate属性来使之居中：

	.parent {
	    position: relative;
	}
	.child {
	    position: absolute;
	    top: 50%;
	    left: 50%;
	    transform: translate(-50%, -50%);
	}

还可以使用flexbox来使元素居中：

	.parent {
	    display: flex;
	    justify-content: center;
	    align-items: center;
	}