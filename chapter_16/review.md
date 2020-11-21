# 第十六章复习题

## 1. 以下哪种攻击对机密性有威胁？

嗅探

## 2. 以下哪种攻击对完整性有威胁？

篡改，重复

## 3. 以下哪种攻击对可用性有威胁？

拒绝服务

## 4. 以下哪个词汇意思是“秘密书写”，哪个是“掩饰书写”？

密码术：秘密书写

隐写术：掩饰书写

## 5. 当密封的信件从Alice发给Bob时，这是一个使用密码术或隐写术来保障机密性的例子吗？

否。

## 6. 从Alice发给Bob的信件使用只有这两人理解的语言写成，这是一个使用密码术或隐写术的例子吗？

是，这是一个使用密码术的例子。

## 7. Alice找到一个秘密写给Bob的方法，每次她都用一个新的文本，比如报纸上的一篇文章，但会在单词之间插入1或2个空格，单空格表示二进制的0，双空格表示二进制的1。Bob抽取这些二进制数码，并用ASCII码译解。这是一个使用密码术或隐写术的例子吗？请说明。

是。这是一个使用隐写术的例子。

## 8. Alice和Bob互相交换机密信息。他们共享一个非常大的数字作为双向的加密和解密密钥。这是一个使用对称密钥或非对称密钥密码术的例子吗？请说明。

是。这是一个使用对称密钥密码术的例子。

## 9. Alice加密信息发送给Bob以及解密收到Bob的信息都使用了同样的密钥。这是一个使用对称密钥或非对称密钥密码术的例子吗？请说明。

是。这是一个使用对称密钥密码术的例子。

## 10. 区分替换密码和置换密码

替换密码：将字符或位按规则进行替换的密码

置换密码：将字符或位按规则重新排序的密码

## 11. 在密码中，所有明文中的A变化成密文中的D并且所有明文中的D变化成密文中的H。这是一个单字母或多字母的替换密码吗？请说明。

不是。这种加密方式无法解密字符H。

## 12. 单字母或多字母密码，哪个更容易破解？

单字母。该加密方法可以通过统计字符出现频率推测消息。

## 13. 假设Alice和Bob使用模26的加法密码算法。入侵者Eve要通过尝试所有可能的密钥来破解（蛮力攻击），她要平均尝试多少个密钥？

13.5个。

## 14. 假设我们有一个1000字符的纯文本。按照下列密码，各需要多少密钥来加密或解密这些信息？

* 加法密码：1个
* 单字母密码：1个
* 自动密钥密码：1个

## 15. 根据流和密码块的定义，找出下列密码哪个是流密码？

加法密码，单字母密码，自动密钥密码均为流密码。

## 16. 如果一次一密乱码是最简单和最安全的密码，为什么不一直使用？

因为每次加密都需要让双方知道密钥是什么。这个成本是巨大的。

## 17. 为什么你认为非对称密钥密码术只用于少量信息？

非对称密钥密码术加密涉及到大数取模运算，这会使其运算速度比对称密钥密码术慢很多。故不适合用于大量信息加密。

## 18. 在一个非对称密钥密码中，哪个密钥用于加密，哪个密钥用于解密？

公钥用于加密，私钥用于解密。

## 19. 在RSA密码中，为什么Bob不能选择1作为公钥e？

因为当加密的数字P比n小的时候，加密前后的内容并没有区别。

## 20. 加入散列函数中的密钥（MAC）扮演了什么角色？请说明。

MAC扮演的是用于验证完整性的摘要的角色。MAC会跟消息M本身一起发送给接收者，接收者将消息M用同样的散列方式生成摘要与MAC对比以确认消息完整性。

## 21. 区别信息验证和实体验证

信息验证为验证信息本身的安全

实体验证为验证信息发送方/接收方是否为本人行为

## 22. Alice为她发送给Bob的信息签名以证明她是该信息的发送者。Alice需要使用以下哪个密钥？

Alice的私钥

## 23. Alice需要给50人的组群发信息。如果Alice需要使用信息验证，你推荐以下哪种方式？

MAC

## 24. 数字签名不支持以下哪种服务？

机密性
