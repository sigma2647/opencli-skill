# opencli Command Reference

All commands support: `-f table|json|yaml|md|csv` and `-v` (verbose/debug).

---

## 核心功能命令

| Command | Args | Description |
|---------|------|-------------|
| `list` | — | 列出所有可用 CLI 命令 |
| `explore <url>` | `--goal <text>`, `--wait <s>`, `--auto`, `--click <labels>` | 探索网站：发现 API、store，推荐策略 |
| `synthesize <target>` | `--top <n>` | 从 explore 结果合成 CLI |
| `generate <url>` | `--goal <text>`, `--site <name>` | 一键：explore → synthesize → register |
| `cascade <url>` | `--site <name>` | 策略级联：找到最简单的可行策略 |
| `doctor` | `--no-live`, `--sessions` | 诊断浏览器桥接连接状态 |
| `validate <target>` | — | 验证 CLI 定义 |
| `verify <target>` | — | 验证 + 冒烟测试 |

**高级用法示例:**
```bash
# 探索网站结构
opencli explore https://example.com

# 探索并指定目标
opencli explore https://example.com --goal "find user profile data"

# 一键生成 CLI
opencli generate https://example.com

# 诊断连接问题
opencli doctor --sessions

# 级联策略测试
opencli cascade https://example.com
```

---

## Web (通用网页)

| Command | Args | Description |
|---------|------|-------------|
| `web read` | `--url <url>` (required), `-f json\|md\|table` | 抓取任意网页并导出为 Markdown |

```bash
opencli web read --url "https://example.com" -f json
opencli web read --url "https://example.com" -f md
```


需要手动读取

web-articles
web-articles/title/*.md

---

## arxiv (学术论文)

| Command | Args | Description |
|---------|------|-------------|
| `arxiv search` | `<query>` (required), `--limit N` | 搜索 arXiv 论文 |
| `arxiv paper` | `<id>` (required) | 获取论文详情 |

```bash
opencli arxiv search "machine learning" --limit 10
opencli arxiv paper 2301.00001
```

---

## Discord

| Command | Args | Description |
|---------|------|-------------|
| (待探索) | — | Discord 相关功能 |

---

## Notion

| Command | Args | Description |
|---------|------|-------------|
| `notion search` | `<query>` | 在 Notion 中搜索页面/数据库 (Cmd+P) |
| `notion sidebar` | — | 列出侧边栏页面和数据库 |
| `notion favorites` | — | 列出收藏页面 |
| `notion read` | — | 读取当前打开的 Notion 页面内容 |
| `notion write` | `<text>` | 向当前页面追加内容 |
| `notion new` | `[title]` | 创建新页面 |
| `notion export` | — | 导出当前 Notion 页面为 Markdown |
| `notion status` | — | 检查 CDP 连接状态 |

---

## 即刻 (Jike)

| Command | Args | Description |
|---------|------|-------------|
| `jike feed` | `--limit N` | 即刻首页动态流 |
| `jike search` | `<query>` | 搜索即刻帖子 |
| `jike user` | `<username>` | 用户动态 |
| `jike topic` | `<id>` | 话题/圈子帖子 |
| `jike post` | `<id>` | 帖子详情及评论 |
| `jike notifications` | — | 通知 |
| `jike create` | `<text>` | 发布动态 |
| `jike like` | `<id>` | 点赞 |
| `jike comment` | `<id> <text>` | 评论 |
| `jike repost` | `<id>` `[text]` | 转发 |

---

## 豆瓣 (Douban)

| Command | Args | Description |
|---------|------|-------------|
| (待探索) | — | 豆瓣相关功能 |

---

## 少数派 (Steam 相关)

| Command | Args | Description |
|---------|------|-------------|
| (待探索) | — | Steam 相关功能 |

---

## 知乎 (Zhihu)

| Command | Args | Description |
|---------|------|-------------|
| `zhihu hot` | `--limit N` (default 20) | 知乎热榜 |
| `zhihu search` | `--keyword <str>` (required), `--limit N` | 搜索内容 |
| `zhihu question` | `--id <question_id>` (required), `--limit N` | 问题详情和回答 |

---

## Bilibili (B站)

| Command | Args | Description |
|---------|------|-------------|
| `bilibili hot` | `--limit N` (default 20) | B站热门视频 |
| `bilibili ranking` | `--limit N` (default 20) | 视频排行榜 |
| `bilibili search` | `--keyword <str>` (required), `--type video\|user`, `--page N`, `--limit N` | 搜索视频或用户 |
| `bilibili feed` | `--limit N`, `--type all\|video\|article` | 关注的人的动态时间线 |
| `bilibili dynamic` | `--limit N` (default 15) | 用户动态 feed |
| `bilibili history` | `--limit N` (default 20) | 我的观看历史 |
| `bilibili favorite` | `--limit N`, `--page N` | 我的默认收藏夹 |
| `bilibili following` | `--uid <id>`, `--page N`, `--limit N` | 关注列表 |
| `bilibili me` | — | 当前用户个人资料 |
| `bilibili user-videos` | `--uid <id>` (required), `--limit N`, `--order pubdate\|click\|stow`, `--page N` | 指定用户的投稿视频 |
| `bilibili subtitle` | `--bvid <bvid>` (required), `--lang <code>` | 获取视频字幕 |

---

## Twitter / X

| Command | Args | Description |
|---------|------|-------------|
| `twitter timeline` | `--limit N` (default 20) | 首页时间线 |
| `twitter trending` | `--limit N` (default 20) | 热门话题 |
| `twitter search` | `--query <str>` (required), `--limit N` | 搜索推文 |
| `twitter bookmarks` | `--limit N` (default 20) | 书签列表 |
| `twitter notifications` | `--limit N` (default 20) | 通知 |
| `twitter profile` | `--username <handle>` (required), `--limit N` | 指定用户的推文 |
| `twitter followers` | `--user <handle>`, `--limit N` | 粉丝列表 |
| `twitter following` | `--user <handle>`, `--limit N` | 关注列表 |
| `twitter post` | `--text <str>` (required) | 发推 |
| `twitter reply` | `--url <tweet_url>` (required), `--text <str>` (required) | 回复推文 |
| `twitter like` | `--url <tweet_url>` (required) | 点赞推文 |
| `twitter delete` | `--url <tweet_url>` (required) | 删除推文 |

---

## 微博 (Weibo)

| Command | Args | Description |
|---------|------|-------------|
| `weibo hot` | `--limit N` (default 30, max 50) | 微博热搜 |

---

## 小红书 (Xiaohongshu)

| Command | Args | Description |
|---------|------|-------------|
| `xiaohongshu feed` | `--limit N` (default 20) | 首页推荐 Feed |
| `xiaohongshu search` | `--keyword <str>` (required), `--limit N` | 搜索笔记 |
| `xiaohongshu notifications` | `--type mentions\|likes\|connections`, `--limit N` | 通知 |
| `xiaohongshu user` | `--id <user_id>` (required), `--limit N` | 指定用户的笔记 |

---

## Google

| Command | Args | Description |
|---------|------|-------------|
| `google news` | `[keyword]`, `--limit N` | Google 新闻 |
| `google search` | `<keyword>` (required), `--limit N` | Google 搜索 |
| `google suggest` | `<keyword>` (required) | Google 搜索建议/补全 |
| `google trends` | `--limit N` (default 20) | Google Trends 每日热门搜索 |

---

## HackerNews

| Command | Args | Description |
|---------|------|-------------|
| `hackernews top` | `--limit N` (default 20) | 热门故事 (无需登录) |

---

## V2EX

| Command | Args | Description |
|---------|------|-------------|
| `v2ex hot` | `--limit N` (default 20) | 热门话题 (无需登录) |
| `v2ex latest` | `--limit N` (default 20) | 最新话题 (无需登录) |
| `v2ex topic` | `--id <topic_id>` (required) | 主题详情和回复 |
| `v2ex me` | — | 个人资料（余额/未读提醒）|
| `v2ex daily` | — | 每日签到并领取铜币 |
| `v2ex notifications` | `--limit N` (default 20) | 提醒（回复等）|

---

## 雪球 (Xueqiu)

| Command | Args | Description |
|---------|------|-------------|
| `xueqiu hot` | `--limit N` (default 20) | 热门动态 |
| `xueqiu hot-stock` | `--limit N`, `--type 10\|12` | 热门股票榜 (10=人气榜, 12=关注榜) |
| `xueqiu feed` | `--page N`, `--limit N` | 关注用户的动态时间线 |
| `xueqiu search` | `--query <str>` (required), `--limit N` | 搜索股票 |
| `xueqiu stock` | `--symbol <code>` (required) | 股票实时行情 |
| `xueqiu watchlist` | `--category 1\|2\|3`, `--limit N` | 自选股列表 (1=自选, 2=持仓, 3=关注) |

---

## YouTube

| Command | Args | Description |
|---------|------|-------------|
| `youtube search` | `--query <str>` (required), `--limit N` | 搜索视频 |

---

## BOSS直聘

| Command | Args | Description |
|---------|------|-------------|
| `boss search` | `--query <str>` (required), `--city`, `--experience`, `--degree`, `--salary`, `--industry`, `--page N`, `--limit N` | 搜索职位 |

---

## 携程 (Ctrip)

| Command | Args | Description |
|---------|------|-------------|
| `ctrip search` | `--query <str>` (required), `--limit N` | 搜索城市或景点 |

---

## 什么值得买 (smzdm)

| Command | Args | Description |
|---------|------|-------------|
| `smzdm search` | `--keyword <str>` (required), `--limit N` | 搜索好价商品 |

---

## 路透社 (Reuters)

| Command | Args | Description |
|---------|------|-------------|
| `reuters search` | `--query <str>` (required), `--limit N` | 搜索新闻 |

---

## BBC

| Command | Args | Description |
|---------|------|-------------|
| `bbc news` | `--limit N` (default 20, max 50) | BBC新闻头条 (RSS, 无需登录) |

---

## Reddit

| Command | Args | Description |
|---------|------|-------------|
| `reddit frontpage` | `--limit N` (default 15) | Reddit首页 / r/all |
| `reddit hot` | `--subreddit <name>`, `--limit N` | 热门帖子 |
| `reddit search` | `--query <str>` (required), `--limit N` | 搜索帖子 |
| `reddit subreddit` | `--name <subreddit>` (required), `--sort hot\|new\|top\|rising`, `--limit N` | 指定 subreddit |

---

## Yahoo Finance

| Command | Args | Description |
|---------|------|-------------|
| `yahoo-finance quote` | `--symbol <ticker>` (required) | 股票行情 |

---

## 外部 CLI (已集成)

| Command | Description |
|---------|-------------|
| `opencli docker [args]` | Docker 命令行 |
| `opencli gh [args]` | GitHub CLI — repos, PRs, issues, releases, gists |
| `opencli obsidian [args]` | Obsidian vault 管理 — notes, search, tags, tasks, sync |

---

## 插件管理

| Command | Args | Description |
|---------|------|-------------|
| `plugin list` | — | 列出已安装插件 |
| `plugin install <source>` | — | 从 GitHub 安装插件 |
| `plugin uninstall <name>` | — | 卸载插件 |
| `plugin update` | `[name]` | 更新插件 |

---

## 其他已安装 CLI

以下 CLI 已安装但功能待探索：

`apple-podcasts`, `barchart`, `bloomberg`, `chaoxing`, `chatgpt`, `chatwise`, `codex`, `coupang`, `cursor`, `devto`, `dictionary`, `doubao`, `douyin`, `facebook`, `grok`, `hf`, `instagram`, `jd`, `jimeng`, `linkedin`, `linux-do`, `lobsters`, `medium`, `pixiv`, `sinablog`, `sinafinance`, `stackoverflow`, `substack`, `tiktok`, `weixin`, `weread`, `wikipedia`, `xiaoyuzhou`, `yollomi`

---

## 自定义 CLI 扩展

当 opencli 不支持某个网站时，可以使用以下方法创建新的 CLI：

```bash
# 1. 尝试自动生成
opencli generate <url>

# 2. 探索网站结构
opencli explore <url> --goal "<目标>"

# 3. 合成 CLI
opencli synthesize <target>

# 4. 验证
opencli verify <site>
```
