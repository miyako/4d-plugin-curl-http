# 4d-plugin-curl-http
HTTP client based on libcurl-7.57.0

### Platform

| carbon | cocoa | win32 | win64 |
|:------:|:-----:|:---------:|:---------:|
|<img src="https://cloud.githubusercontent.com/assets/1725068/22371562/1b091f0a-e4db-11e6-8458-8653954a7cce.png" width="24" height="24" />|<img src="https://cloud.githubusercontent.com/assets/1725068/22371562/1b091f0a-e4db-11e6-8458-8653954a7cce.png" width="24" height="24" />|<img src="https://cloud.githubusercontent.com/assets/1725068/22371562/1b091f0a-e4db-11e6-8458-8653954a7cce.png" width="24" height="24" />|<img src="https://cloud.githubusercontent.com/assets/1725068/22371562/1b091f0a-e4db-11e6-8458-8653954a7cce.png" width="24" height="24" />|

### Version

<img src="https://cloud.githubusercontent.com/assets/1725068/18940649/21945000-8645-11e6-86ed-4a0f800e5a73.png" width="32" height="32" /> <img src="https://cloud.githubusercontent.com/assets/1725068/18940648/2192ddba-8645-11e6-864d-6d5692d55717.png" width="32" height="32" />

This is an HTTP specific ``libcurl`` implementation 

For generic ``libcurl`` implementation, see [4d-plugin-curl](https://github.com/miyako/4d-plugin-curl)

This is an FTP specific ``libcurl`` implementation see [4d-plugin-curl-ftp](https://github.com/miyako/4d-plugin-curl-ftp)

## Syntax

```
error:=cURL_HTTP_Request(options;request;response{;callbackMethod})
```

Parameter|Type|Description
------------|------------|----
options|TEXT|``JSON``
request|BLOB|
response|BLOB|
callbackMethod|TEXT|optional
error|LONGINT|[Error code](https://curl.haxx.se/libcurl/c/libcurl-errors.html)

---

Signature of ``callbackMethod``

```
abort:=method(curlInfo;userInfo)
```

Parameter|Type|Description
------------|------------|----
curlInfo|TEXT|``JSON`` (``curl_easy_getinfo``)
userInfo|TEXT|the text passed as the ``PRIVATE`` property of ``option``
abort|BOOLEAN|

[``CURLcode``](https://curl.haxx.se/libcurl/c/libcurl-errors.html) is returned in ``error``. when ``True`` is returned from the callback method, ``CURLE_ABORTED_BY_CALLBACK (42)`` is returned. same if the process has been aborted via the runtime explorer. aborting the debugger will not kill the process immediately.

---

Properties of ``options``

* General

[URL](https://curl.haxx.se/libcurl/c/CURLOPT_URL.html)  string  
[USERNAME](https://curl.haxx.se/libcurl/c/CURLOPT_USERNAME.html)  string  
[PASSWORD](https://curl.haxx.se/libcurl/c/CURLOPT_PASSWORD.html)  string  
[PRIVATE](https://curl.haxx.se/libcurl/c/CURLOPT_PRIVATE.html)  string  

* HTTP

[UPLOAD](https://curl.haxx.se/libcurl/c/CURLOPT_UPLOAD.html)  number  
[NOBODY](https://curl.haxx.se/libcurl/c/CURLOPT_NOBODY.html)  number  
[HTTP_VERSION](https://curl.haxx.se/libcurl/c/CURLOPT_HTTP_VERSION.html)  value: ``1.0`` ``1.1`` ``2`` ``2_TLS`` ``2_PRIOR_KNOWLEDGE``  
[PROXYHEADER](https://curl.haxx.se/libcurl/c/CURLOPT_PROXYHEADER.html)  value: ``["Shoesize: 10", "Accept:"...]``  
[HTTPHEADER](https://curl.haxx.se/libcurl/c/CURLOPT_HTTPHEADER.html)  value: ``["Shoesize: 10", "Accept:"...]``  
[HEADEROPT](https://curl.haxx.se/libcurl/c/CURLOPT_HEADEROPT.html)  value: ``UNIFIED``, ``SEPARATE``  
[AUTOREFERER](https://curl.haxx.se/libcurl/c/CURLOPT_AUTOREFERER.html)  number  
[ACCEPT_ENCODING](https://curl.haxx.se/libcurl/c/CURLOPT_ACCEPT_ENCODING.html)  string  
[FOLLOWLOCATION](https://curl.haxx.se/libcurl/c/CURLOPT_FOLLOWLOCATION.html)  number  
[UNRESTRICTED_AUTH](https://curl.haxx.se/libcurl/c/CURLOPT_UNRESTRICTED_AUTH.html)  number  
[REFERER](https://curl.haxx.se/libcurl/c/CURLOPT_REFERER.html)  string  
[USERAGENT](https://curl.haxx.se/libcurl/c/CURLOPT_USERAGENT.html)  string  
[HTTP200ALIASES](https://curl.haxx.se/libcurl/c/CURLOPT_HTTP200ALIASES.html)  value] ``["ICY 200 OK", "WEIRDO 99 FINE"...]``  
[COOKIE](https://curl.haxx.se/libcurl/c/CURLOPT_COOKIE.html)  string  
[COOKIEFILE](https://curl.haxx.se/libcurl/c/CURLOPT_COOKIEFILE.html)  path  
[COOKIEJAR](https://curl.haxx.se/libcurl/c/CURLOPT_COOKIEJAR.html)  path  
[COOKIESESSION](https://curl.haxx.se/libcurl/c/CURLOPT_COOKIESESSION.html)  number  
[COOKIELIST](https://curl.haxx.se/libcurl/c/CURLOPT_COOKIELIST.html)  string  
[REQUEST_TARGET](https://curl.haxx.se/libcurl/c/CURLOPT_REQUEST_TARGET.html)  string  
[IGNORE_CONTENT_LENGTH](https://curl.haxx.se/libcurl/c/CURLOPT_IGNORE_CONTENT_LENGTH.html)  number  
[CONTENT_DECODING](https://curl.haxx.se/libcurl/c/CURLOPT_HTTP_CONTENT_DECODING.html)  number  
[TRANSFER_ENCODING](https://curl.haxx.se/libcurl/c/CURLOPT_TRANSFER_ENCODING.html)  number  
[TRANSFER_DECODING](https://curl.haxx.se/libcurl/c/CURLOPT_HTTP_TRANSFER_DECODING.html)  number  
[RANGE](https://curl.haxx.se/libcurl/c/CURLOPT_RANGE.html)  string  
[RESUME_FROM](https://curl.haxx.se/libcurl/c/CURLOPT_RESUME_FROM.html)  number
[RESUME_FROM_LARGE](https://curl.haxx.se/libcurl/c/CURLOPT_RESUME_FROM_LARGE.html)  string  
[CUSTOMREQUEST](https://curl.haxx.se/libcurl/c/CURLOPT_CUSTOMREQUEST.html)  string  
[HTTPAUTH](https://curl.haxx.se/libcurl/c/CURLOPT_HTTPAUTH.html)  values: ``ANY`` ``ANYSAFE`` ``BASIC`` ``DIGEST`` ``NEGOTIATE`` ``NTLM``  

**About HTTP**

a special option named ``REQUEST`` and ``RESPONSE`` can be used to specify a file as input an output.

* Limits

[CONNECTTIMEOUT](https://curl.haxx.se/libcurl/c/CURLOPT_CONNECTTIMEOUT.html)  number  
[TIMEOUT](https://curl.haxx.se/libcurl/c/CURLOPT_TIMEOUT.html)  number  
[LOW_SPEED_TIME](https://curl.haxx.se/libcurl/c/CURLOPT_LOW_SPEED_TIME.html)  number  
[LOW_SPEED_LIMIT](https://curl.haxx.se/libcurl/c/CURLOPT_LOW_SPEED_LIMIT.html)  number  
[MAXREDIRS](https://curl.haxx.se/libcurl/c/CURLOPT_MAXREDIRS.html)  number  
[MAXFILESIZE](https://curl.haxx.se/libcurl/c/CURLOPT_MAXFILESIZE.html)  number  
[TCP_KEEPIDLE](https://curl.haxx.se/libcurl/c/CURLOPT_TCP_KEEPIDLE.html)  number  
[TCP_KEEPALIVE](https://curl.haxx.se/libcurl/c/CURLOPT_TCP_KEEPALIVE.html)  number  
[TCP_KEEPINTVL](https://curl.haxx.se/libcurl/c/CURLOPT_TCP_KEEPINTVL.html)  number  
[DNS_CACHE_TIMEOUT](https://curl.haxx.se/libcurl/c/CURLOPT_DNS_CACHE_TIMEOUT.html)  number  
[EXPECT_100_TIMEOUT_MS](https://curl.haxx.se/libcurl/c/CURLOPT_EXPECT_100_TIMEOUT_MS.html)  number  

* Proxy

[PROXY](https://curl.haxx.se/libcurl/c/CURLOPT_PROXY.html)  string  
[NOPROXY](https://curl.haxx.se/libcurl/c/CURLOPT_NOPROXY.html)  string  
[PROXYPORT](https://curl.haxx.se/libcurl/c/CURLOPT_PROXYPORT.html)  number  
[PROXYTYPE](https://curl.haxx.se/libcurl/c/CURLOPT_PROXYTYPE.html)  string  
[PROXYUSERNAME](https://curl.haxx.se/libcurl/c/CURLOPT_PROXYUSERNAME.html)  string  
[PROXYPASSWORD](https://curl.haxx.se/libcurl/c/CURLOPT_PROXYPASSWORD.html)  string  
[PROXYAUTH](https://curl.haxx.se/libcurl/c/CURLOPT_PROXYAUTH.html)  values: ``ANY`` ``ANYSAFE`` ``BASIC`` ``DIGEST`` ``NEGOTIATE`` ``NTLM``  
[PROXY_SERVICE_NAME](https://curl.haxx.se/libcurl/c/CURLOPT_PROXY_SERVICE_NAME.html)  string  
[PROXY_SSLCERT](https://curl.haxx.se/libcurl/c/CURLOPT_PROXY_SSLCERT.html)  path  
[PROXY_SSLKEY](https://curl.haxx.se/libcurl/c/CURLOPT_PROXY_SSLKEY.html)  path  
[PROXY_SSLCERTTYPE](https://curl.haxx.se/libcurl/c/CURLOPT_PROXY_SSLCERTTYPE.html)  string  
[PROXY_SSLKEYTYPE](https://curl.haxx.se/libcurl/c/CURLOPT_PROXY_SSLKEYTYPE.html)  string  
[PROXY_TLSAUTH_USERNAME](https://curl.haxx.se/libcurl/c/CURLOPT_PROXY_TLSAUTH_USERNAME.html)  string  
[PROXY_TLSAUTH_PASSWORD](https://curl.haxx.se/libcurl/c/CURLOPT_PROXY_TLSAUTH_PASSWORD.html)  string  
[PROXY_TLSAUTH_TYPE](https://curl.haxx.se/libcurl/c/CURLOPT_PROXY_TLSAUTH_TYPE.html)  string  
[PROXY_SSL_CIPHER_LIST](https://curl.haxx.se/libcurl/c/CURLOPT_PROXY_SSL_CIPHER_LIST.html)  string  
[PROXY_PINNEDPUBLICKEY](https://curl.haxx.se/libcurl/c/CURLOPT_PROXY_PINNEDPUBLICKEY.html)  path  
[PROXY_CAINFO](https://curl.haxx.se/libcurl/c/CURLOPT_PROXY_CAINFO.html)  path  
[PROXY_CRLFILE](https://curl.haxx.se/libcurl/c/CURLOPT_PROXY_CRLFILE.html)  path  
[PROXY_SSL_VERIFYHOST](https://curl.haxx.se/libcurl/c/CURLOPT_PROXY_SSL_VERIFYHOST.html)  number  
[PROXY_SSL_VERIFYPEER](https://curl.haxx.se/libcurl/c/CURLOPT_PROXY_SSL_VERIFYPEER.html)  number  
[PROXY_KEYPASSWD](https://curl.haxx.se/libcurl/c/CURLOPT_PROXY_KEYPASSWD.html)  string  
[PROXY_SSLVERSION](https://curl.haxx.se/libcurl/c/CURLOPT_PROXY_SSLVERSION.html)  value: ``SSLv2`` ``SSLv3`` ``TLSv1.0`` ``TLSv1.1`` ``TLSv1.2`` ``TLSv1.3``  

**About proxies**  

``libcurl`` respects proxy environment variables named ``http_proxy`` ``all_proxy`` ``no_proxy`` etc. options take precedence over environment variables. 

a special option named ``AUTOPROXY`` can be used to let ``libproxy`` find the proxy via WPAD and PAC.

* SSL/TLS

[USE_SSL](https://curl.haxx.se/libcurl/c/CURLOPT_USE_SSL.html)  values: ``USESSL_NONE`` ``USESSL_TRY`` ``USESSL_CONTROL`` ``USESSL_ALL``  
[SSL_VERIFYHOST](https://curl.haxx.se/libcurl/c/CURLOPT_SSL_VERIFYHOST.html)  number    
[SSL_VERIFYPEER](https://curl.haxx.se/libcurl/c/CURLOPT_SSL_VERIFYPEER.html)  number  
[CAINFO](https://curl.haxx.se/libcurl/c/CURLOPT_CAINFO.html)  path  
[SSLCERT](https://curl.haxx.se/libcurl/c/CURLOPT_SSLCERT.html)  path  
[SSLKEY](https://curl.haxx.se/libcurl/c/CURLOPT_SSLKEY.html)  path  
[SSLCERTTYPE](https://curl.haxx.se/libcurl/c/CURLOPT_SSLCERTTYPE.html)  string  
[SSLKEYTYPE](https://curl.haxx.se/libcurl/c/CURLOPT_SSLKEYTYPE.html)  string  
[TLSAUTH_TYPE](https://curl.haxx.se/libcurl/c/CURLOPT_TLSAUTH_TYPE.html)  string  
[TLSAUTH_USERNAME](https://curl.haxx.se/libcurl/c/CURLOPT_TLSAUTH_USERNAME.html)  string  
[TLSAUTH_PASSWORD](https://curl.haxx.se/libcurl/c/CURLOPT_TLSAUTH_PASSWORD.html)  string  
[SSL_CIPHER_LIST](https://curl.haxx.se/libcurl/c/CURLOPT_SSL_CIPHER_LIST.html)  string  
[SSL_SESSIONID_CACHE](https://curl.haxx.se/libcurl/c/CURLOPT_SSL_SESSIONID_CACHE.html)  number  
[PINNEDPUBLICKEY](https://curl.haxx.se/libcurl/c/CURLOPT_PINNEDPUBLICKEY.html)  path  
[ISSUERCERT](https://curl.haxx.se/libcurl/c/CURLOPT_ISSUERCERT.html)  path  
[CRLFILE](https://curl.haxx.se/libcurl/c/CURLOPT_CRLFILE.html)  path  
[SSL_ENABLE_ALPN](https://curl.haxx.se/libcurl/c/CURLOPT_SSL_ENABLE_ALPN.html)  number  
[SSL_ENABLE_NPN](https://curl.haxx.se/libcurl/c/CURLOPT_SSL_ENABLE_NPN.html)  number  
[SSL_FALSESTART](https://curl.haxx.se/libcurl/c/CURLOPT_SSL_FALSESTART.html)  number  
[SSLVERSION](https://curl.haxx.se/libcurl/c/CURLOPT_SSLVERSION.html)  value: ``SSLv2`` ``SSLv3`` ``TLSv1.0`` ``TLSv1.1`` ``TLSv1.2`` ``TLSv1.3``  
[VERIFYSTATUS](https://curl.haxx.se/libcurl/c/CURLOPT_SSL_VERIFYSTATUS.html)  number  
[KEYPASSWD](https://curl.haxx.se/libcurl/c/CURLOPT_KEYPASSWD.html)  string  
