# API Document Viewer

API 文件檢視器，使用 [Swagger UI](https://github.com/swagger-api/swagger-ui) ，讀取 doc 目錄下的 api.yml 檔。

## Apache 密碼驗證

如果要限制特定人才可檢視 API 文件，可使用 Apache 密碼驗證機制。

首先需要產生帳密資料，步驟如下

```shell script
$ touch .htpasswd
$ htpasswd .htpasswd user1
# 輸入密碼兩次
```

然後將 public/.htaccess 內的註解移除即可。

### 啟動 .htaccess

如果上述設定未生效，請確認 Apache 有啟動 .htaccess（預設是未啟動）。

請以編輯器開啟 /etc/apache2/apache2.conf 或 /etc/httpd/conf/httpd.conf 或此虛擬網站設定檔，找到以下設定：

```text
Options Indexes FollowSymLinks
AllowOverride None
Require all granted
```

然後將 `AllowOverride None` 改成 `AllowOverride All`，再重啟 Apache 即可。
