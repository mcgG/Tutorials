# JWT

# ![](/assets/jwt1.png)



JSON Web Token

* Self-contained: carries all the information necessary within itself
* JSON object on its own
* Can be used/passed as part of URL\(Query String\), form body parameter, cookie or HTTP Header \(x-access-token\)
* Great for single sign-on context

#### Three sections separated with dots

* **header, payload and signature**
* All are base64 encode

#### Header

* typ - should be JWT
* alg - hasing alogrithm\(HS256, RS512, ESE384, etc.\)

#### Payload

**Contains**

* The information which we need to transmit
* The information related to token itself
* Information is JSON representation of claims\(Key: Value\)

#### Signature

A hash of header and payload using a secret

JWT = header + payload + signature

![](/assets/signature.png)

![](/assets/jwt.png)

![](/assets/jwtinreaslworld.png)



**Session + Cookie**

Cookie+Session的存在主要是为了解决HTTP这一无状态协议下服务器如何识别用户的问题，其原理就是在用户登录通过验证后，服务端将数据加密后保存到客户端浏览器的Cookie中，同时服务器保留相对应的Session（文件或DB）。用户之后发起的请求都会携带Cookie信息，服务端需要根据Cookie寻回对应的Session，从而完成验证，确认这是之前登陆过的用户。











