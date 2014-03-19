EventHandle
===========

#事件管理器

##主要API介绍

* on  绑定事件，可以多次调用
* remove  移除事件
* fire    触发事件
* once    帮点事件，触发后自动销毁


### demo实例

  
      var obj = {};
    	var instance = new EventHandle();
    	instance.on('click',function(){
    		//alert('sss');
    	});
    	instance.once('click',function(){
    		//alert('sss');
    	});
    	instance.fire('click');
    	setTimeout(function(){
    		instance.fire('click');
    	},1000);
 
   
### 作为类的基类使用：
   

        //类式继承
      	var inherit = (function (){
      		var F = function(){};
      		return function(sub,parent){
      			F.prototype = parent.prototype;
      			sub.prototype = new F();
      			sub.prototype.constructor = sub;
      			sub.prototype.__super__ = parent.prototype;
      		};
      	})();
      	function Animate(){
      		//EventHandle.apply(this,arguments);
      		this.__super__.constructor.apply(this,arguments);
      	};
      	inherit(Animate,EventHandle);
      	//Animate.prototype = new EventHandle();
      	Animate.prototype.show = function(){};
      	var cat = new Animate();
      	cat.on('say',function(){
      		alert('I am cat');
      	});
      	cat.fire('say');
      	
      	

