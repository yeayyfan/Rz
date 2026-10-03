# 染舟科技 RANZHOU 官网 · 静态网站

这是已经生成好的网站文件，**不需要安装、不需要编译**。把本文件夹里的全部内容放到任意静态托管上就能访问。

- 中文首页：`index.html`，英文首页：`en/index.html`
- 产品页：RZ Titan、RZ Spider、RZ Radar（`products/` 下）
- 所有链接都是相对路径：放在网站根目录、子目录（如 `/ranzhou-web/`）或自定义域名下都能直接使用

## 发布到 GitHub Pages

1. 在 GitHub 新建一个仓库，例如 `ranzhou-web`。
2. 把本文件夹的**全部内容**上传到仓库根目录（`index.html` 要在最外层，不要多套一层文件夹）。
   - 推荐用 GitHub Desktop 或命令行 `git` 上传。
   - 用网页上传时，单次能拖入的文件数量有限，可以分几次拖入；单个文件都小于 25 MB。
   - `.nojekyll` 是隐藏文件（macOS 访达默认看不到），用 `git` 上传会自动带上；就算漏传，网站也能正常显示。
3. 打开仓库 **Settings → Pages**：Source 选 **Deploy from a branch**，Branch 选 `main`，目录选 `/ (root)`，点 Save。
4. 等一两分钟，访问 `https://<用户名>.github.io/<仓库名>/`。

绑定自己的域名：在同一页面的 Custom domain 填写域名，并按 GitHub 提示配置 DNS。网站放在子目录时，404 页面会自动识别所在目录。

## 本地查看

- 直接双击 `index.html` 即可浏览（Chrome 以本地文件方式打开时不加载网页字体，会显示系统字体，属正常现象）。
- 更接近线上效果：在本文件夹打开终端运行 `python3 -m http.server 8000`，然后访问 http://localhost:8000/ 。

## 更新网站

网站由 `ranzhou-web` 源码项目生成：文字在 `src/content/*.json`，图片视频在 `public/`。改完后在源码目录运行

```
node build.mjs --zip ranzhou-web-site.zip
```

会得到新的压缩包，解压后覆盖仓库里的文件再提交即可。
