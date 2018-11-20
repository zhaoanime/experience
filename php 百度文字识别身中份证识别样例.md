```php
public function addPost(){
		// header( "Content-type: image/jpeg");
		$data=$this->request->param();
		//图片完整地址
		$img=$data['post']['thumbpic'];
		$img=cmf_get_image_url($img);

		$picturedata=file_get_contents($img);
		$picturedata=base64_encode($picturedata);
		// echo $picturedata;die;
		$token=session("idcard_token");
		if(empty($token)){
			$ak="XuSGz3Utxf3IttosVbbGOFmu";
			$sk="rj5uKv5PtGlFefBXAXhIWOoU9ypL9uuW";
			$url="https://aip.baidubce.com/oauth/2.0/token?grant_type=client_credentials&client_id=$ak&client_secret=$sk";
			$string=cmf_curl_get($url);
			$codedata=json_decode($string,1);
			$token=$codedata['access_token'];
			sesssion('idcard_token',$token);
		}
		$url="https://aip.baidubce.com/rest/2.0/ocr/v1/idcard?access_token=$token";
		// $url="https://aip.baidubce.com/rest/2.0/ocr/v1/idcard?access_token=24.056112c95eb63066d1dfd4b265b02852.2592000.1542260166.282335-14410595";
		// $post_data['detect_direction']=false;
		$post_data['id_card_side']="front";
		$post_data['image']=$picturedata;
		/*
		iVBORw0KGgoAAAANSUhEUgAAAigAAAEwCAYAAACdYIruAAAgAElEQVR42uy9S48k2Xmm+di52TEzv0XktU....SR7qlOd6lSnOtWpfuDq1KCc6lSnOtWpTnWqH7g6NSinOtWpTnWqU53qB67+XwfzkwFFGmWVAAAAAElFTkSuQmCC
		 */
		$result=$this->curl_post_urlencoded($post_data,$url);
		P($result);
	}

	private function curl_post_urlencoded($post_data,$url){
	    $ch = curl_init();
	    curl_setopt($ch, CURLOPT_URL, $url);
        curl_setopt($ch, CURLOPT_POST, 1);
        curl_setopt($ch, CURLOPT_HEADER, false);
        curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
	    curl_setopt($ch, CURLOPT_SSL_VERIFYPEER, false);
        curl_setopt($ch, CURLOPT_HTTPHEADER,['Content-Type:application/x-www-form-urlencoded']);
        curl_setopt($ch, CURLOPT_POSTFIELDS, is_array($post_data) ? http_build_query($post_data) : $post_data);
	    curl_setopt($ch, CURLOPT_TIMEOUT_MS, 60000);
	    curl_setopt($ch, CURLOPT_CONNECTTIMEOUT_MS, 60000);
	    $content = curl_exec($ch);
	    $code = curl_getinfo($ch, CURLINFO_HTTP_CODE);

        if($code === 0){
            throw new Exception(curl_error($ch));
        }
	    curl_close($ch);
	    return $content;
	}

```