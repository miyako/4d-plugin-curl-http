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

* Proxy

[PROXY](https://curl.haxx.se/libcurl/c/CURLOPT_PROXY.html)  string  
[NOPROXY](https://curl.haxx.se/libcurl/c/CURLOPT_NOPROXY.html)  string  
[PROXYPORT](https://curl.haxx.se/libcurl/c/CURLOPT_PROXYPORT.html)  number  
[PROXYTYPE](https://curl.haxx.se/libcurl/c/CURLOPT_PROXYTYPE.html)  string  
[PROXYUSERNAME](https://curl.haxx.se/libcurl/c/CURLOPT_PROXYUSERNAME.html)  string  
[PROXYPASSWORD](https://curl.haxx.se/libcurl/c/CURLOPT_PROXYPASSWORD.html)  string  
[PROXYAUTH](https://curl.haxx.se/libcurl/c/CURLOPT_PROXYAUTH.html)  values: ``CURLAUTH_ANY``, ``CURLAUTH_ANYSAFE``  
[PROXY_SERVICE_NAME](https://curl.haxx.se/libcurl/c/CURLOPT_PROXY_SERVICE_NAME.html)  string  
[PROXY_SSLCERT](https://curl.haxx.se/libcurl/c/CURLOPT_PROXY_SSLCERT.html)  path  
[PROXY_SSLKEY](https://curl.haxx.se/libcurl/c/CURLOPT_PROXY_SSLKEY.html)  path  
[PROXY_SSLCERTTYPE](https://curl.haxx.se/libcurl/c/CURLOPT_PROXY_SSLCERTTYPE.html)  string  
[PROXY_SSLKEYTYPE](https://curl.haxx.se/libcurl/c/CURLOPT_PROXY_SSLKEYTYPE.html)  string  
[PROXY_TLSAUTH_USERNAME](https://curl.haxx.se/libcurl/c/CURLOPT_PROXY_TLSAUTH_USERNAME.html)  string  
[PROXY_TLSAUTH_PASSWORD](https://curl.haxx.se/libcurl/c/CURLOPT_PROXY_TLSAUTH_PASSWORD.html)  string  
[PROXY_TLSAUTH_TYPE](https://curl.haxx.se/libcurl/c/CURLOPT_PROXY_TLSAUTH_TYPE.html)  string  

**About proxies**  

``libcurl`` respects proxy environment variables named ``http_proxy``, ``all_proxy``, ``no_proxy`` etc. options take precedence over environment variables. 

a special option named ``AUTOPROXY`` can be used to let ``libproxy`` find the proxy via WPAD and PAC.

* TLS

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

