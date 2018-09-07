linux插件phantomjs截屏 php触发

phantomjs安装


```php
public function screenshot($url){
        exec('/opt/phantomjs-2.1.1-linux-x86_64/bin/phantomjs --output-encoding=utf8 --ignore-ssl-errors=true /opt/lampstack-7.0.31-0/apache2/htdocs/app/polyscreen/controller/c.js '.$url,$output_main);
        foreach ($output_main as $key => $value) {
            if( true == preg_match("/.png/", $value)){
                return $value;
            }
        }
    }
```
```javascript
var page = require('webpage').create(),
    system = require('system'),
    t, address;
    page.zoomFactor=0.1;
if (system.args.length === 1) {
    console.log('Usage: loadspeed.js <some URL>');
    phantom.exit();
}

t = Date.now();
address = system.args[1];
page.open(address, function (status) {
    if (status !== 'success') {
        console.log('FAIL to load the address');
    } else {

    	var text = "";
    	var possible = "abcdefghijklmnopqrstuvwxyz";
    	for( var i=0; i < 5; i++ ){
    		text += possible.charAt(Math.floor(Math.random() * possible.length));
    	}

		page.render('tt233/'+text+'_'+t+'.png');
		console.log(text+'_'+t+'.png');
    }
    phantom.exit();
});
```
