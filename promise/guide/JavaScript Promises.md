问题
-
	var img1 = document.querySelector('.img-1');
	  
	img1.addEventListener('load', function() {
	  // 啊哈图片加载完成
	});
	
	img1.addEventListener('error', function() {
	  // 哎哟出问题了
	});
	
在绑定load事件的时候，有可能img1已经加载完了，无法触发load事件。这时候我们需要先检查检查图片的“complete”属性：

	var img1 = document.querySelector('.img-1');
	
	function loaded() {
	  // 啊哈图片加载完成
	}
	
	if (img1.complete) {
	  loaded();
	}
	else {
	  img1.addEventListener('load', loaded);
	}
	
	img1.addEventListener('error', function() {
	  // 哎哟出问题了
	});
	
	
这样还不够，如果在添加监听函数之前图片加载发生错误，我们的监听函数还是白费，不幸的是 DOM 也没有为这个需求提供解决办法。而且，这还只是处理一张图片的情况，如果有一堆图片要处理那就更麻烦了

事件不是万金油
-
事件机制最适合处理同一个对象上反复发生的事情—— keyup、touchstart 等等。你不需要考虑当绑定监听器之前所发生的事情，当碰到异步请求成功/失败的时候，你想要的通常是这样：

	img1.callThisIfLoadedOrWhenLoaded(function() {
	  // 加载完成
	}).orIfFailedCallThis(function() {
	  // 加载失败
	});
	
	// 以及……
	whenAllTheseHaveLoaded([img1, img2]).callThis(function() {
	  // 全部加载完成
	}).orIfSomeFailedCallThis(function() {
	  // 一个或多个加载失败
	});

这就是 Promise。如果 HTML 图片元素有一个“ready()”方法的话，我们就可以这样：

	img1.ready().then(function() {
	  // 加载完成
	}, function() {
	  // 加载失败
	});
	
	// 以及……
	Promise.all([img1.ready(), img2.ready()]).then(function() {
	  // 全部加载完成
	}, function() {
	  // 一个或多个加载失败
	});
	
基本上 Promise 还是有点像事件回调的，除了：

- 一个 Promise 只能成功或失败一次，并且状态无法改变（不能从成功变为失败，反之亦然）
- 如果一个 Promise 成功或者失败之后，你为其添加针对成功/失败的回调，则相应的回调函数会立即执行

这些特性非常适合处理异步操作的成功/失败情景，你无需再担心事件发生的时间点，而只需对其做出响应。

JavaScript 的 Promise实现
-

- [Q](https://github.com/kriskowal/q)
- [when](https://github.com/cujojs/when)
- [WinJs](http://msdn.microsoft.com/en-us/library/windows/apps/br211867.aspx)
- [RSVP.js](https://github.com/tildeio/rsvp.js)