# 前端优化

优化方向 | 优化手段
--- | --- | ----
请求数量 | 合并脚本和样式表，CSS Sprites，拆分初始化负载，划分主域
请求带宽 | 开启GZip，精简JavaScript，移除重复脚本，图像优化
缓存利用 | 使用CDN，使用外部JavaScript和CSS，添加Expires头，减少DNS查找，配置ETag，使AjaX可缓存
页面结构 | 将样式表放在顶部，将脚本放在底部，尽早刷新文档的输出
代码校验 | 避免CSS表达式，避免重定向

[前端工程与性能优化](https://github.com/fouber/blog/issues/3)