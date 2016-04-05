#Knwl.Js AKA Natural Language Parser#
Öncellikle ne yaptığını anlatayım başta diğer sorunları çözmüş oluruz. Nerede kullanılır ve ne için ihtiyacımız olur o kısmı açıkcası bende bilmiyorum. Lakin karşılaştım ve çok hoşuma gitti paylaşmak istedim.

Efendim öncelikle **Natural Language Parser** dediğimiz şey bir text ya da dokümandaki verilerin fizyolojik konuşma diline uygun olarak parse edilmesine yarayan bir yapı. Örnğ;

"Bazen yolda giderken 30 nisan'a nasıl yetişeceğimi düşünüyorum. Bu 2016 senesi biraz zorlu olabilir. Ayrıca 053.... numarayı aramalıydım bugun." gibi bir içeriği inceleyip size 

```
date = > 30 Nisan 2016,
phones = > 053...
```

diye ayrım yapmakta. Knwl js ise bu işi yapan bir javascript kütüphanesi.

Kullanımı hakkında ise;

#### ```npm```:

```console
	npm install knwl.js
```

	```javascript
		var Knwl = require("./knwl.js");
		
		var knwlInstance = new Knwl('english');

		knwlInstance.register('dates', require('./default_plugins/dates'));
	```
	
	*Note: The plugins in the ```./default_plugins``` directory will be loaded automatically.*

###For the Browser

**Note: A packaged version of Knwl.js for the browser with default plugins is available in the ```./dist``` directory.**

These steps require the ```npm``` package.

1. Run ```npm install``` to install dependencies.

2. ```browserify``` may be used to build a Knwl.js project from Node.js for the browser.

	Use the following syntax in the terminal:
	
	```console
		./node_modules/.bin/browserify script.js knwl.js > output.js
	```
	
	The ```script.js``` file is the Node.js file you wish to package for the browser.

## Usage Guide


	``` javascript
	knwlInstance.init("This is a string. This was written on the 2nd of June, of 2015.");
	```
	
	This line runs the initial parser functions that
	prepare the String for plugins to use. **Plugins
	will not function without this method first being called
	on the String.**
	
4. Initiate a plugin to parse the String.
	
	``` javascript
	var dates = knwlInstance.get('dates');
	```
	
	The first parameter of ```knwl.get()``` is the
	name of the parser plugin you're trying to access (make sure you've added the plugin's .js file to the header of the page).
	The names of all default parser plugins are provided
	 towards the end of this document. If you're using
	plugins other than the defaults, see their respective
	documentation.
	
	Anyways, if the parser plugin is found, ```knwl.get()``` will return
	an array of this format:
	
	```javascript
	var results = [
		{ //result
			//plugin-specific properties
			"preview": "This was written on the 2nd of June of 2015.", //the sentence of rough location of the data from the String
			"found": integer //the position (in words) of the result in the String
		}
	]
	```
	
	For example, here's what is returned from ```knwl.get('dates')``` when called on the previously mentioned String:
	
	```json
	[
		{
			"year": 2015,
			"month": 6,
			"day": 2,
			"preview": "This was written on the 2nd of June of 2015.",
			"found": 5
		}
	]
	```

## Default Plugins

These are automatically loaded by default.

###dates.js
```javascript
knwl.get('dates');
	
	//Returns any dates found in the String.
```

###times.js
```javascript
knwl.get('times');
	
	//Returns any times found in the String.
	
```

###phones.js
```javascript		
knwl.get('phones')

	//Returns any phone numbers found in the String.

```

###links.js
```javascript
knwl.get('links')

	//Returns any links found in the String.

```

###emails.js
```javascript
knwl.get('emails')
	
	//Returns any email addresses found in the String.
```

### places.js
```javascript
knwl.get('places')

	//Returns any places found in the String.
```



----------


#RadioJS#

Radiojs basit olarak **observer pattern**'i implemente etmiş pub/sub kütüphanesidir. Key özellikleri ise;

1. Dependency free olması. Tam olarak olmasada minimal seviyede olması
2. Chainable method desteği olması ki bu bence güzel bir özellik. Bknz **Fluent Api**
3. **this** sorunsalını çözebilmek için çağırdığı metodlara context alması.
4. Callback methodları olması
5. boyutunun küçük olması yaklaşık 1kb

Örnek olarak bakmamız gerekirse;

```javascript

//Event adında bir pub-sub oluşturuyoruz.
radio('event').subscribe(yourFunction);

//bu event e bağlı tüm subscriberlara datayı publish ediyoruz.
radio('event').broadcast(data);

//ve silebiliyoruz.
radio('event').unsubscribe(yourFunction);
```

Subscribe methodu callback alırken bahsettiğimiz üzere callback contexti'de verebiliyoruz. bknz **this sorunsalı** 

`radio('event').subscribe([callback,context]);`

Ayrıca subscribe'a n tane callback tanımlayabiliyoruz.
```javascript
radio('event').subscribe(callback,callback2,callback3,[callback4.init,callback4]);
//or
radio('event').subscribe(callback).subscribe(callback2)...
```

------

#OverApi#

Over api bir websitesi aslında [buradan](http://overapi.com/) ulaşabilirsiniz sitesine.

Burada herhangi bir konu hakkında içerisinde barındırdığı tüm api lara ulaşmanız mümkün. Gayet sade ve açıklayıcı olan yapısı genel bilgi verme konusunda çok başarılı.

örnğn;

[nodejs](http://overapi.com/nodejs) hakkında api isteğinden bulunduğunuz da node js ile alakalı size sunulan tüm fonksiyonları görüntüleyebiliyorsunuz. Bu fonksiyonların detaylarını merak ediyorsanız link olarak sunulan bu apiler sizi referanslara direk götürüyor.

![preview](http://snag.gy/98QWA.jpg)

ayrıca [chrome eklentisi](https://chrome.google.com/webstore/detail/all-cheat-sheets/oedodeocfdeegliepeeoieemhdgoijod) olarak ta ekleyebiliyorsunuz. 

Bence çok yararlı bir kaynak.

----

#Bootsnote#

Notlarınızı tutabilmenize olanak sağlayan NodeJS ve electron kullanılarak geliştirilmiş uygulama olan *Bootsnote* kullanım kolaylığı ve direk markdown özelliği built in gelmesi sebebi ile gayet güzel duruyor. Kullanımızı tavsiye ederim.
