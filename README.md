# dsh-mimo-studio-link

在 DeepSeek Harness 左侧栏增加一个「MiMo Studio」入口，点击后在主内容区直接内嵌原生 Xiaomi MiMo Studio 网页版 `aistudio.xiaomimimo.com`——不跳出界面、不消耗 Harness 会话 token。

## 功能

- 侧栏一键打开原生 MiMo Studio 网页版（UltraSpeed / MiMo Claw / MiMo Chat 等模式），主区内嵌显示。
- 通过 DSH 桌面壳的 `window.dshDesktop.browser` 桥创建 Electron `<webview>` 独立渲染进程，绕开站点 CSP 内嵌限制。
- 加载失败或页面退出时，面板内显示错误与「重试」按钮，不影响整个应用。
- 使用固定隔离分区，切换面板或重载后通常保持登录，且不影响 DSH 本身与其它站点的会话。
- 只提供入口与内嵌容器，不处理对话数据，也不参与模型计费；MiMo Studio 的功能与额度由其官网账号体系决定。

## 安装

在 DSH 插件页通过插件市场索引安装本包，或在 profile 目录执行：

```sh
dsh plugin --profile desktop add github:jyz48prsbr-netizen/dsh-mimo-studio-link
```

> **仅桌面版可用**：`dsh web` 浏览器形态没有 guest 租约桥，入口会提示「当前环境不支持内嵌浏览器」。
> 登录态保存在进程临时分区中，DSH 重启后可能需要重新登录。

详细配置与注意事项见 [docs/DETAIL.md](docs/DETAIL.md)。

## 许可

MIT
