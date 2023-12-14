# 砸壳后

砸壳后，得到ipa文件后，还有些事情要做：

* 确认app已解密 = 确认砸壳成功
* 安装ipa

## 确认app已解密

可以用`otool`查看字段crypt的值：

* `cryptid=1`: 已加密
* `cryptid=0`: 没加密=已解密

### 举例

* 官网原始版本，安装到iPhone中后的，抖音的二进制文件`Aweme`：已加密
  ```bash
  ➜  Aweme.app otool -l Aweme | grep crypt
      cryptoff 28672
      cryptsize 4096
        cryptid 1
  ```
* 砸壳后的抖音的ipa中的二进制文件`Aweme`：已解密
```bash
➜  Aweme.app pwd
xxx/Aweme抖音/iPhone7-137black/Aweme.app
➜  Aweme.app otool -l Aweme | grep crypt
     cryptoff 28672
    cryptsize 4096
      cryptid 0
```
