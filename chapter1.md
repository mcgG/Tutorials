# JWT

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





