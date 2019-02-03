对称加密算法aes
引用的方法类
```php
<?php
//AES加密类
class AESMcrypt {

   public $iv = null; //秘钥向量
   public $key = null; //加密key
   public $bit = 128;
   public $mode= null;//加密模式
   private $cipher;

   public function __construct($bit, $key, $iv, $mode) {

       if(empty($bit) || empty($key) || empty($iv) || empty($mode)){
           return NULL;
       }

       $this->bit = $bit;
       $this->key = $key;
       $this->iv = $iv;
       $this->mode = $mode;

       switch($this->bit) {
           case 192:$this->cipher = MCRYPT_RIJNDAEL_192; break;
           case 256:$this->cipher = MCRYPT_RIJNDAEL_256; break;
           default: $this->cipher = MCRYPT_RIJNDAEL_128;
       } 

       switch($this->mode) {
           case 'ecb':$this->mode = MCRYPT_MODE_ECB; break;
           case 'cfb':$this->mode = MCRYPT_MODE_CFB; break;
           case 'ofb':$this->mode = MCRYPT_MODE_OFB; break;
           case 'nofb':$this->mode = MCRYPT_MODE_NOFB; break;
           case 'cbc':$this->mode = MCRYPT_MODE_CBC; break;
           default: $this->mode = MCRYPT_MODE_CBC;
       }
   }

   public function encrypt($data) {
       $data = base64_encode(mcrypt_encrypt( $this->cipher, $this->key, $data, $this->mode, $this->iv));
       return $data;
   }

   public function decrypt($data) {
       $data = mcrypt_decrypt( $this->cipher, $this->key, base64_decode($data), $this->mode, $this->iv);
       $data = rtrim(rtrim($data), "\x00..\x1F");
       return $data;
   }
}

```
具体功能实现
```php
private $aes_conf=[
		'bit'=>128,
		'key'=>'M)$7gs5mYNB|3Bsh',
		'iv' =>'J)7Nfd(ehMdj#{5M',
		'mode'=>'cdc'
	];

	private function get_data_items(){
		vendor('AESMcrypt');
		$bit=$this->aes_conf['bit'];
		$key=$this->aes_conf['key'];
		$iv=$this->aes_conf['iv'];
		$mode=$this->aes_conf['mode'];
		$aes=new \AESMcrypt($bit, $key, $iv, $mode);
		$str =file_get_contents('baseConfigureItems.json');
		$str = $aes->decrypt($str);
		$arr=json_decode($str,1);
    	return $arr;
	}
	private function save_data_items($arr){
		vendor('AESMcrypt');
		$bit=$this->aes_conf['bit'];
		$key=$this->aes_conf['key'];
		$iv=$this->aes_conf['iv'];
		$mode=$this->aes_conf['mode'];
		$aes=new \AESMcrypt($bit, $key, $iv, $mode);
		$str=json_encode($arr);
		$str = $aes->encrypt($str);
		file_put_contents('baseConfigureItems.json', $str);
	}
	private function get_data(){
		vendor('AESMcrypt');
		$bit=$this->aes_conf['bit'];
		$key=$this->aes_conf['key'];
		$iv=$this->aes_conf['iv'];
		$mode=$this->aes_conf['mode'];
		$aes=new \AESMcrypt($bit, $key, $iv, $mode);
		$str =file_get_contents('baseConfigure.json');
		$str = $aes->decrypt($str);
		$arr=json_decode($str,1);
    	return $arr;
	}
	private function save_data($arr){
		vendor('AESMcrypt');
		$bit=$this->aes_conf['bit'];
		$key=$this->aes_conf['key'];
		$iv=$this->aes_conf['iv'];
		$mode=$this->aes_conf['mode'];
		$aes=new \AESMcrypt($bit, $key, $iv, $mode);
		$str=json_encode($arr);
		$str = $aes->encrypt($str);
		file_put_contents('baseConfigure.json', $str);
	}
```


