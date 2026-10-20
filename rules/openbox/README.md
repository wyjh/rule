# Open-Box 规则集

给 [Open-Box](https://github.com/liandu2024/Open-Box) 面板用的分流名单，格式为 Clash / mihomo 的 `.list`（`DOMAIN`、`DOMAIN-SUFFIX` 等），Open-Box 可直接解析并编译成内核用的 `.srs`。

## 文件

| 文件 | 内容 |
| --- | --- |
| `tmdb.list` | TMDB（The Movie Database）全部域名：主站、API、图片、文件、CDN |

## 在 Open-Box 里的用法

1. 面板 → 代理 · 策略 → 站点集 → 编辑（或新建）→ 添加规则；
2. 类型选「规则集链接」，粘贴 raw 地址：

   ```
   https://raw.githubusercontent.com/wyjh/rule/main/rules/openbox/tmdb.list
   ```

   国内拉 raw 不稳时可以换成镜像：

   ```
   https://cdn.jsdelivr.net/gh/wyjh/rule@main/rules/openbox/tmdb.list
   https://ghfast.top/https://raw.githubusercontent.com/wyjh/rule/main/rules/openbox/tmdb.list
   ```

3. 保存后点行尾的「立即更新」让内核立刻重拉，或等下次启动内核时自动更新（每 24 小时一次）。

只想一次性落地、之后不依赖外链，可以用「导入规则」把明细导进站点集（≤200 条），两种方式二选一，也可以同时用。

> 注意：填 GitHub 的 `/blob/` 网页地址会拉下一整页 HTML，解析结果必然是 0 条；必须是 raw（或镜像）地址。

## 收录范围

- `themoviedb.org`：apex、`www`、`api`、`auth`、`developer`、`files`、`media`
- `tmdb.org`：apex、`api`、`image`、`images`、`files`
- Bunny CDN：`tmdb-image-prod.b-cdn.net`、`tmdb-web-image-prod.b-cdn.net`、`tmdb-web-files-prod.b-cdn.net`
- 末尾两条 `DOMAIN-SUFFIX` 兜底，覆盖两个主域今后新增的子域

图标不在 Open-Box 内置图标库里（没有 TMDB 品牌图标），站点集里选「电影」（`misc:film`）即可。
