
## 基于 [openscopeproject/TrguiNG](https://github.com/openscopeproject/TrguiNG) 汉化并增加部分功能

### 更新 (260716a)
1. add: 种子列表增加下载限速和上传限速列，未启用限速时显示为空。
2. impr: 种子列表使用其他列排序时，以名称升序作为第二排序条件，使结果顺序保持稳定。
3. build: 修复 fork 的 GitHub Actions WebUI 构建产物上传，并自动下载当月或上月的 DB-IP 数据库。

### 更新 (260705a)
1. add: 种子列表右键菜单增加“导出种子文件...”，支持批量导出选中任务的 `.torrent` 文件，导出文件名使用种子列表中的名称。
2. note: WebUI 版需要能通过 `torrents/<hash>.torrent` 只读访问 Transmission 的 `/config/torrents` 目录。

### 更新 (240607a)
1. merge: openscopeproject/TrguiNG
2. add: 暂停增加子状态（已完成/未完成）
3. add: 支持tr3批量修改tracker
4. add: 列表不显示子目录种子（可配置，默认显示）
5. add: web增加字体大小调整
6. impr: 拖拽时批量处理
7. impr: 分享率固定2位小数
8. impr: web增加一些字体
9. fix: 取消当前状态显示时异常

### 更新 (240422a)
1. add: 目录分组增加复制路径功能
2. Issue #3 | fix: 一键URL访问跨域问题（简单转跳处理）
3. Issue #4 #10 | 合并 openscopeproject/TrguiNG:1.3.0
4. Issue #9 | impr: 隐藏/展示运行状态（右上角）
5. Issue #6 #7 #12 | 翻译调整
6. windows应用程序部分页面汉化补充

### 更新 (240417a)
1. fix: 体积支持 PB EB 展示
2. fix: 工具栏的一些同步问题
3. impr: version 页汉化

## 新增功能 (240416a)
1. 分组体积展示（可在分组区右键关闭该功能）
2. 双击全选分组，方便快捷操作（可在分组区右键关闭该功能）
3. 增加错误分布分组（可在分组区右键关闭该功能）
4. 增加分组后的Tracker二级过滤（位于顶部搜索框右侧）
5. 多链接下载，可设置下载间隔
6. 调整布局，左下角增加状态指示（主要用于多链接下载展示进度，平常展示列表选中项）
7. 种子列表右键菜单增加复制名称和路径（去重）

## PS. 主要是自用，有想加功能的可以提 issues，不保证实现

## 安装介绍（docker 环境）
1. 从本 fork 的 [Releases](https://github.com/silverfoxonline/TrguiNG/releases) 下载 `trguing-web-*.zip`。开发版也可在 GitHub Actions 的 `build` 工作流产物中下载。
2. 解压到 transmission 设置的 webui 目录即可
3. transmission 需要正确映射并设置环境变量(确保 index.html 位于 TRANSMISSION_WEB_HOME 所在的目录第一层):
   ```
   TRANSMISSION_WEB_HOME=/config/webui/trguing-zh
   ```

### 导出种子文件配置（WebUI）
右键导出 `.torrent` 文件时，WebUI 会按种子的 `hashString` 读取：
```
torrents/<hash>.torrent
```
如果使用 Docker，可以把 Transmission 的种子目录只读挂载到 WebUI 目录下：
```
/docker/transmission/config/torrents:/config/webui/trguing-zh/torrents:ro
```
也可以在宿主机创建软链接，确保 `/config/webui/trguing-zh/torrents` 能访问到真实的 `/config/torrents` 内容。
