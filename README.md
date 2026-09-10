# 政府网站公开内容爬取存档 (GitHub mirror)

多站点存档仓库。当前站点:

- **putian_gov/** : 莆田市人民政府门户网站 —— 政务公开 /zwgk/、政府信息公开 /zfxxgk/、解读回应 /jdhy/ 及直接链接的 *.putian.gov.cn 子站文章(一跳)

## putian_gov 存档状态

| 指标 | 数量 |
| --- | --- |
| 栏目(channel)数 | 327 |
| 文章页 总数 | 58,952 |
| 文章页 已抓取(page.txt 落盘) | 58,316 |
| 文章页 待抓取 | 0 |
| 抓取失败(含死链 404) | 50 |
| 附件/图片 总数 | 10,128 |
| 附件/图片 已下载 | 9,422 |
| 附件 下载失败(几乎全为子站 404 死链) | 706 |
| 站外/越界链接记录 | 321 |
| 本仓库跟踪文件数 | 173,309 |

- 每篇文档一个目录:`page.txt`(标题/发布时间/文号/发布机构/栏目/原始链接/附件与图片链接/正文)、`page.html`(原始网页存档)、`links.tsv`(attachment/image/link 三类链接记录)、`attachments/`(同域附件与图片)
- 全局索引:putian_gov/`_index.tsv`(全部文章)、`_attachments.tsv`(附件与图片)、`_outbound_links.tsv`(站外链接)、`_failed_pages.tsv`(失败清单,404 死链属正常)、`_filtered_over_25mb.txt`(超过 25MB 未推送清单,本次为空)、`_directory_tree.txt`(完整目录与文件大小清单)、`README.md`(各栏目进度表)
- **二进制文件(附件/图片/文档原件)不进本仓库**:仓库只保存文本类档案(page.txt / page.html / links.tsv)与索引;附件二进制保存在本地完整副本,其 URL 与元数据记录在 `_attachments.tsv`,目录结构与大小见 `_directory_tree.txt`
- 抓取方式:单线程低速礼貌抓取(文章页随机延时 2.0-4.5s、列表/接口 1.5-3.0s、附件 1.2-2.2s;失败退避重试 5/15/45/120s,4xx 不重试);robots.txt 返回 404(无限制),全程未触发反爬
- 状态库:putian_crawler/state.db(SQLite,支持断点续爬)
