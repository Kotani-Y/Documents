# Apache1台

docker-compose.ymlでphp-fpmをprivate,publicの2つを作成
httpd.confにVirtualHost追加

アクセス->ProxyError

hostsには
192.168.99.100	private.qiilo-local.jp
192.168.99.100	public.qiilo-local.jp
を記載済
