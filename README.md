概述
=

椭圆曲线数字签名算法（ECDSA）是使用椭圆曲线密码（ECC）对数字签名算法（DSA）的模拟。ECDSA于1999年成为ANSI标准，并于2000年成为IEEE和NIST标准。

与普通的离散对数问题（discrete logarithm problem DLP）和大数分解问题（integer factorization problem IFP）不同，椭圆曲线离散对数问题（elliptic curve discrete logarithm problem ECDLP）没有亚指数时间的解决方法。因此椭圆曲线密码的单位比特强度要高于其他公钥体制。

椭圆曲线密码体制的安全性基于椭圆曲线离散对数问题（ECDLP）的难解性。椭圆曲线离散对数问题远难于离散对数问题，椭圆曲线密码系统的单位比特强度要远高于传统的离散对数系统。因此在使用较短的密钥的情况下，ECC可以达到于DL系统相同的安全级别。这带来的好处就是计算参数更小，密钥更短，运算速度更快，签名也更加短小。因此椭圆曲线密码尤其适用于处理能力、存储空间、带宽及功耗受限的场合。

原理
=

签名过程如下：
1、选择一条椭圆曲线Ep(a,b)，和基点G；
2、选择私有密钥k（k<n，n为G的阶），利用基点G计算公开密钥K=kG；
3、产生一个随机整数r（r<n），计算点R=rG；
4、将原数据和点R的坐标值x,y作为参数，计算SHA1做为hash，即Hash=SHA1(原数据,x,y)；
5、计算s≡r - Hash * k (mod n)
6、r和s做为签名值，如果r和s其中一个为0，重新从第3步开始执行

验证过程如下：
1、接受方在收到消息(m)和签名值(r,s)后，进行以下运算
2、计算：sG+H(m)P=(x1,y1), r1≡ x1 mod p。
3、验证等式：r1 ≡ r mod p。
4、如果等式成立，接受签名，否则签名无效。

ECDSA标准
=

1.ANSI X9.62
该项目始于1995年，并于1999年正式作为ANSI标准颁布。ANSI X9.62具有高安全性和通用性。

2.FIPS 186-2
1997年，NIST开始制定包括椭圆曲线和RSA签名算法的FIPS 186标准。

3、IEEE 1363-2000
该标准于2000年作为IEEE标准问世。IEEE 1363的覆盖面很广，包括公钥加密，密钥协商，基于IFP、DLP、ECDLP的数字签名。它与ANSI X9.62和FIPS 186完全不同，它没有最低安全性限制（比如不再对基点阶进行限制），用户可以有充分的自由。
因此IEEE 1363-2000并不是一个安全标准，也不具有良好的通用性，它的意义在于给各种应用提供参照。它的基域可以是，也可以是。 中的元素可以以多项式形式或正规基形式来表示。中元素表示形式是整数，中元素表示形式是字符串。这与ANSI X9. 62和FIPS 186是一致的。

4.ISO/IEC 14888-3
这个标准包含若干签名算法，其中ECDSA部分与ANSI X9.62一致。

ECDSA与区块链
=

1.比特币目前使用的 ECDSA 签名算法与建议的 Schnorr 签名算法，都属于椭圆曲线数字签名算法，它们使用的椭圆曲线都是 secp256k1。

2.ECDSA是基于 ECC 的数字签名算法，在比特币、以太坊等区块链网络中大量使用。每一笔区块链交易执行之前都必须进行权限校验，以确保该交易是由账户对应的私钥签发。256 位私钥的 ECDSA 签名可以达到 3072 位 RSA 签名的安全强度。




参考文献
=
[1]https://blog.csdn.net/m0_37458552/article/details/80250258
[2]https://blog.csdn.net/jingzi123456789/article/details/104805530
[3]https://zhuanlan.zhihu.com/p/421523789#:~:text=ECDSA%20%E5%85%A8%E7%A7%B0%20Elliptic%20Curve,Digital%20Signature%20Algorith%EF%BC%8C%E6%98%AF%E5%9F%BA%E4%BA%8E%20ECC%20%E7%9A%84%E6%95%B0%E5%AD%97%E7%AD%BE%E5%90%8D%E7%AE%97%E6%B3%95%EF%BC%8C%E5%9C%A8%E6%AF%94%E7%89%B9%E5%B8%81%E3%80%81%E4%BB%A5%E5%A4%AA%E5%9D%8A%E7%AD%89%E5%8C%BA%E5%9D%97%E9%93%BE%E7%BD%91%E7%BB%9C%E4%B8%AD%E5%A4%A7%E9%87%8F%E4%BD%BF%E7%94%A8%E3%80%82















