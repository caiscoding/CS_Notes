# IP地址表示

### IPv4 地址

我们常见的 IP 地址类型都是 IPv4 地址。例如常见的 `192.168.0.1` 就是 IPv4 地址，像上面这种 IPv4 地址表示法我们称之为 **点分四组表示法** （又称为 **点分十进制表示法** ）。实际上真正的 IPv4 地址是由二进制组成的，上面这种表示法只是为了方便我们的记忆。IPv4 地址长度为 **32位** ，即 32 位由 `0` 和 `1` 组成的二进制数字。因此，IPv4 地址空间支持

&#x20;$$2^{32}(4 \; 294 \; 967 \; 296)$$

个地址。 **点分四组表示法** 就是把这 32 位地址分为四组，每组都把二进制转换为十进制表示，并使用点把每组分隔开，所以上面例子中真正的 IPv4 地址为 `11000000 10101000 00000000 00000001` 。下图演示了如何将 IPv4 真正的地址转换为点分四组表示法表示。

![图解 IPv4 地址表示](<../../.gitbook/assets/ipv4 (1).png>)

下表是 IPv4 地址表示的几个例子。

|                二进制表示                |      点分四组表示     |
| :---------------------------------: | :-------------: |
| 00000000 00000000 00000000 00000000 |     0.0.0.0     |
| 11000000 10101000 00000001 01100100 |  192.168.1.100  |
| 11111111 11111111 11111111 11111111 | 255.255.255.255 |

### IPv6 地址

相对于 IPv4 ，IPv6 是互联网工程任务组（IETF）设计的用于替代 IPv4 的下一代 IP 协议。 IPv6 地址长度为 **128位** ，因此 IPv6 地址空间支持

$$2^{128}(340 \; 282 \; 366 \; 920 \; 938 \; 463 \; 463 \; 374 \; 607 \; 431 \; 768 \; 211 \; 456)$$

个地址。 IPv6 地址表示方法为 **字段（块）的四个十六进制数** 。字段（块）由冒号 `:` 分隔。例如：IPv6地址 `2001:0db8:86a3:08d3:1319:8a2e:0370:7344` 。下图演示了如何将 IPv6 真正的地址转换为字段（块）的四个十六进制数表示。

![图解 IPv6 地址表示](<../../.gitbook/assets/ipv6 (1).png>)

当然，因为 IPv6 地址实在是太长了，所以有以下的简化表示法：

（根据[RFC4291](https://tools.ietf.org/html/rfc4291)，RFC4291用于IPv4和IPv6的过渡阶段）

1. 一个字段中，前导的 `0` 不需要写。例如： IPv6 地址 `2000:07a8:01aa:0000:0000:0000:0000:0c21` ，可以简化为 `2000:7a8:1aa:0:0:0:0:c21` 。
2. 全为 `0` 的字段可以直接省略，并使用符号 `::` 代替全为 `0` 的字段。特别注意，一个 IPv6 地址中符号 `::` 只能出现一次。例如： IPv6 地址 `2000:7a8:1aa:0:0:0:0:c21` ，可以简化为 `2000:7a8:1aa::c21` 。
3. IPv4 映射的 IPv6 地址。例如： IPv4 地址 `10.0.0.1` 可以表示 IPv6 地址 `::ffff:10.0.0.1` 。这种类型的地址允许 IPv6 应用程序直接与 IPv4 应用程序通信。

根据[RFC5952](https://tools.ietf.org/html/rfc5952)，有以下规定：

1. 一个字段中，前导的 `0` 必须省略压缩。
2. 符号::只能用于影响最大的地方（即压缩最多的 `0` ）。在多个字段包含相同长度0的情况下，靠前的字段被替换。
3. 十六进制字母要用小写表示。

&#x20;IP 地址在线转换计算器，其网址为： [**http://www.subnetmask.info/**](http://www.subnetmask.info)
