![logo](./logo.svg)<br>

## ！！！声明！！！

**本程序仅供于学习交流，请使用者遵守《中华人民共和国网络安全法》，勿将此工具用于非授权的测试，开发者不负任何连带法律责任。**


### ✨新版本特性

- 🔥支持自动解密(`windows`从路径上提取`wxAppId`)
- 🔥自动合并子包
- 🔥支持解析最新版`wxapkg` (`APP_V3`/`APP_V4`/`APP_SUBPACKAGE_V2`)
- 🔥支持解析最新版小程序插件 (`APP_PLUGIN_V1`)
- 🔥采用`@babel/core`直接解析语法树，精准提取源码(`1.x`是正则提取)
- 🔥使用`Threadjs`做的线程池，`cpu`直接干到顶(🤡解析语法树特别吃`cpu`)



- 子命令是为了后续集成别的平台小程序解包功能 
- 子命令默认为 `wx`

| 子命令   | 参数                      | 解释                                                         |
| -------- | ------------------------- | ------------------------------------------------------------ |
| `global` | `-l, --log-level <level>` | 设置日志等级 `debug`，`info`，`warn`，`error` 默认 `info`    |
| `wx`     | `<packages...>`           | `wxapkg`的路径，可以是多个，也可以是一个目录                 |
| `wx`     | `-i, --appid <appid>`     | 解密`windows`上的 `wxapkg`时需要提供**🔥已经支持自动从路径中提取** |
| `wx`     | `-f, --format`            | 是否需要格式化解析出来的代码                                 |
| `wx`     | `--no-clear-decompile`    | 不清除反编译时的残留文件                                     |
| `wx`     | `--no-clear-save`         | 不清除之前的编译结果                                         |
| `wx`     | `--no-parse`              | 只提取`wxapkg`中的文件，不进行反编译                         |
| `wx`     | `-d, --depth <depth>`     | 设置从目录中查找`wxapkg`的深度默认: `1` 设置为`0`时不限制深度 |
| `wx`     | ` -o, --output <path>`    | 设置反编译输出路径                                           |

### 💡使用示例

```bash
# 直接解包整个目录
$ unveilr /path/to/wxapkg/dir/
# 解包多个包
$ unveilr /path/to/1.wxapkg /path/to/2.wxapkg ...
# 指定子命令并指定微信AppId
$ unveilr wx /path/to/wxapkg/dir/ -i wx11aa22bb33cc44dd
# 格式化解析出来的代码
$ unveilr wx /path/to/wxapkg/dir/ -f
# 只提取源文件不解析进行反编译
$ unveilr wx /path/to/wxapkg/dir/ --no-parse
```
