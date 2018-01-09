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

* Proxy

[PROXY](https://curl.haxx.se/libcurl/c/CURLOPT_PROXY.html)  string  
[NOPROXY](https://curl.haxx.se/libcurl/c/CURLOPT_NOPROXY.html)  string  
[PROXYPORT](https://curl.haxx.se/libcurl/c/CURLOPT_PROXYPORT.html)  number  
[PROXYTYPE](https://curl.haxx.se/libcurl/c/CURLOPT_PROXYTYPE.html)  string  
[PROXYUSERPWD](https://curl.haxx.se/libcurl/c/CURLOPT_PROXYUSERPWD.html)  string  
[PROXY_SERVICE_NAME](https://curl.haxx.se/libcurl/c/CURLOPT_PROXY_SERVICE_NAME.html)  string  

**About proxies**  

``libcurl`` respects proxy environment variables named ``http_proxy``, ``all_proxy``, ``no_proxy`` etc. options take precedence over environment variables. 

a special option named ``AUTOPROXY`` can be used to let ``libproxy`` find the proxy via WPAD and PAC.
