# Actions-OpenWrt

[![LICENSE](https://img.shields.io/github/license/mashape/apistatus.svg?style=flat-square&label=LICENSE)](https://github.com/P3TERX/Actions-OpenWrt/blob/master/LICENSE)
![GitHub Stars](https://img.shields.io/github/stars/P3TERX/Actions-OpenWrt.svg?style=flat-square&label=Stars&logo=github)
![GitHub Forks](https://img.shields.io/github/forks/P3TERX/Actions-OpenWrt.svg?style=flat-square&label=Forks&logo=github)

Build OpenWrt using GitHub Actions

[Read the details in my blog (in Chinese) | 中文教程](https://p3terx.com/archives/build-openwrt-with-github-actions.html)

## Usage

- Click the [Use this template](https://github.com/P3TERX/Actions-OpenWrt/generate) button to create a new repository.
- Generate `.config` files using [Lean's OpenWrt](https://github.com/coolsnowwolf/lede) source code. ( You can change it through environment variables in the workflow file. )
- Push `.config` file to the GitHub repository, and the build starts automatically.Progress can be viewed on the Actions page.
- When the build is complete, click the `Artifacts` button in the upper right corner of the Actions page to download the binaries.
- 通过修改`diypart1.sh`文件修改`feeds.conf.default`配置。
- 通过修改`diypart2.sh`文件可以自定义默认IP，登陆密码等。按我的需要现在的默认IP为`192.168.2.1`,不需要更改的加`#`注释就可以。
- 自定义编译的方法可以搭配使用，自己需要的服务一般不会随意变化，就可以在 `make menuconfig` 选好（新手参考[OpenWrt MenuConfig设置和LuCI插件选项说明](https://mtom.ml/827.html)）后执行 `./scripts/diffconfig.sh > seed.config` 复制一下这个`seed.config`的文本内容到项目根目录的`.config`文件中（建议自命名），这样就不用每次都SSH连接到 Actions生成编译配置，真正一键编译。

## SSH 连接到 Actions.
- 通过 tmate 连接到 GitHub Ac­tions 虚拟服务器环境，可直接进行 make menuconfig 操作生成编译配置，或者任意的客制化操作。也就是说，你不需要再自己搭建编译环境了。这可能改变之前所有使用 GitHub Ac­tions 的编译 Open­Wrt 方式
- 在Run Workflow时把SSH connection to Actions的值改为true（或者也可以不修改，而是通过 webhook 方式发送带有ssh触发关键词的请求。）
- 在触发工作流程后，在 Actions 日志页面等待执行到SSH connection to Actions步骤，会出现类似下面的信息：

 To connect to this session copy-n-paste the following into a terminal or browser:
 
 ssh Y26QeagDtsPXp2mT6me5cnMRd@nyc1.tmate.io
 
 https://tmate.io/t/Y26QeagDtsPXp2mT6me5cnMRd
 
- 复制 SSH 连接命令粘贴到终端内执行，或者复制链接在浏览器中打开使用网页终端。（网页终端可能会遇到黑屏的情况，按 Ctrl+C 即可）
cd openwrt && make menuconfig
- 完成后按Ctrl+D组合键或执行exit命令退出，后续编译工作将自动进行。
- TIPS: 固件目录下有个config.seed文件，如果你需要再次编译可以使用它。

### Tips

It may take a long time to create a `.config` file and build the OpenWrt firmware. Thus, before create repository to build your own firmware, you may check out if others have already built it which meet your needs by simply [search `Actions-Openwrt` in GitHub](https://github.com/search?q=Actions-openwrt).

Add some meta info of your built firmware (such as firmware architecture and installed packages) to your repository introduction, this will save others' time.

## Acknowledgments

- [Microsoft](https://www.microsoft.com)
- [Microsoft Azure](https://azure.microsoft.com)
- [GitHub](https://github.com)
- [GitHub Actions](https://github.com/features/actions)
- [tmate](https://github.com/tmate-io/tmate)
- [mxschmitt/action-tmate](https://github.com/mxschmitt/action-tmate)
- [csexton/debugger-action](https://github.com/csexton/debugger-action)
- [Cisco](https://www.cisco.com/)
- [OpenWrt](https://github.com/openwrt/openwrt)
- [Lean's OpenWrt](https://github.com/coolsnowwolf/lede)
- [Cowtransfer](https://cowtransfer.com)
- [WeTransfer](https://wetransfer.com/)
- [Mikubill/transfer](https://github.com/Mikubill/transfer)

## License

[MIT](https://github.com/P3TERX/Actions-OpenWrt/blob/main/LICENSE) © P3TERX
