kakuyuu
=======
<?php
// twitteroauth.phpを読み込む。パスはあなたが置いた適切な場所に変更してください
require_once("twitteroauth.php");

// Consumer keyの値
$consumer_key = "X44sZ5xg27SsnrQwLHIPWO55l";
// Consumer secretの値
$consumer_secret = "v9T6O0rotp2j2GsIcIgxWKdkPjIvF3Jpi7A7utz4oupgyxp9cC";
// Access Tokenの値
$access_token = "2881882430-AlDTWW4vEHWnTXxav1LnGansQpZJ75uPmnyTJ3v";
// Access Token Secretの値
$access_token_secret = "x2GunLHFdRij5AsBR9TB2XEkqes04torl9bjnPzNAC412";

// OAuthオブジェクト生成
$to = new TwitterOAuth($consumer_key,$consumer_secret,$access_token,$access_token_secret);

// TwitterへPOSTする。パラメーターは配列に格納する
// in_reply_to_status_idを指定するのならば array("status"=>"@hogehoge reply","in_reply_to_status_id"=>"0000000000"); とする。
$req = $to->OAuthRequest("https://api.twitter.com/1.1/statuses/update.json","POST",array("status"=>"OAuth経由のツイートテスト"));
// TwitterへPOSTするときのパラメーターなど詳しい情報はTwitterのAPI仕様書を参照してください

// Twitterから返されたJSONをデコードする
$result = json_decode($req);
// JSONの配列（結果）を表示する
echo "<pre>";
var_dump($result);
?>
