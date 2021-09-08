---
title: "ConnectInterceptor"
subtitle: ""
date: 2021-09-07T17:45:01+08:00
lastmod: 2021-09-07T17:45:01+08:00
draft: false
authors: []
description: ""

tags: []
categories: []
series: [第三方框架]

hiddenFromHomePage: false
hiddenFromSearch: false

featuredImage: ""
featuredImagePreview: ""

toc:
  enable: true
math:
  enable: false
lightgallery: false
license: ""
---

```java
public final class ConnectInterceptor implements Interceptor {

  public final OkHttpClient client;

  public ConnectInterceptor(OkHttpClient client) {
    this.client = client;
  }

  @Override public Response intercept(Chain chain) throws IOException {

    RealInterceptorChain realChain = (RealInterceptorChain) chain;

    Request request = realChain.request();

    StreamAllocation streamAllocation = realChain.streamAllocation();

    boolean doExtensiveHealthChecks = !request.method().equals("GET");

    HttpCodec httpCodec = streamAllocation.newStream(client, chain, doExtensiveHealthChecks);
    
    RealConnection connection = streamAllocation.connection();

    return realChain.proceed(request, streamAllocation, httpCodec, connection);
  }
}
```