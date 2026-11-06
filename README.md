# 蓝莓视频 API 协议 Demo（安卓原生）

> 逆向学习用途。协议细节见 `../蓝莓视频_API文档_开发用.md`。

## GitHub Actions 云端编译（推荐，无需本地环境）

1. 把本目录内容推到 GitHub 仓库（**本目录作为仓库根**）：

```bash
cd android_demo
git init
git add .
git commit -m "init demo"
git remote add origin https://github.com/<你的用户名>/<仓库名>.git
git push -u origin main
```

2. 仓库页 → **Actions** 标签 → 选 `Android CI` → 等待绿灯
3. 构建完成 → 页面底部 **Artifacts** → 下载 `app-debug` → 解压得到 `app-debug.apk`
4. 传到手机安装（未知来源应用放行）

> workflow 用 `gradle/actions/setup-gradle@v4` 安装 Gradle 8.9（项目不带 wrapper），AGP 8.5.2 + JDK 17。

## 本地编译

- Android Studio 打开本目录，直接 Run
- 或命令行：装 Gradle 8.9 后 `gradle assembleDebug`

## 功能

- 域名引导（init → 动态域名 → 缓存）
- 搜索（/api/v2/vod/clever，参数 wd）
- 详情（/api/v2/vod/info）→ 播放地址（/api/v2/vod/playurl）
- ExoPlayer（media3）播放，线路自动容错
- 签名 + 响应 AES 解密全自动
