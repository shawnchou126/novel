# 番茄小说工作台信息

## 🌐 正确的访问地址

### 作者工作台入口
**URL**: `https://fanqienovel.com/main/writer/?enter_from=author_zone`

⚠️ **重要提醒**：
- ❌ **不要使用** `author.fanqienovel.com` 域名（服务器网络限制）
- ✅ **使用** `fanqienovel.com/main/writer/` 路径

---

## 📊 数据中心地址

### 小说数据页面
**URL模板**: 
```
https://fanqienovel.com/main/writer/{book_id}/data-center/novel-data?book_id={book_id}
```

**当前书籍**:
- 书名：《豪门双生契》
- Book ID: `7630718797917195288`
- 完整URL: `https://fanqienovel.com/main/writer/7630718797917195288/data-center/novel-data?book_id=7630718797917195288`

---

## 📂 相关文件位置

### 核心脚本
```
~/.openclaw/workspace/novel/
├── scripts/
│   ├── fetch-stats.js          # 数据抓取脚本 ✅
│   ├── publish-final.js         # 章节发布脚本 ✅
│   ├── auto-create-and-publish.js  # 自动创作+发布 ✅
│   ├── check-publish-status.js  # 发布状态检查 ✅
│   ├── healthcheck.js           # 健康检查 ✅
│   ├── check-cookie.js          # Cookie检查 ✅
│   └── format-report.js         # 汇报格式化 ✅
├── session/
│   └── fanqie-auth.json         # 登录Cookie
├── data/
│   └── latest-stats.json        # 最新数据
└── last-published.json          # 发布追踪
```

### Skill文档
```
~/.openclaw/workspace/skills/fanqie-publish/
└── SKILL.md                     # 发布技能文档
```

---

## 🎯 关键配置

### Cookie存储
- **位置**: `~/.openclaw/workspace/novel/session/fanqie-auth.json`
- **格式**: `{ "cookies": [...] }`
- **过期时间**: 2026-06-19（剩余57天）

### 书籍信息
- **Book ID**: `7630718797917195288`
- **笔名**: 夜班写手甲
- **书名**: 豪门双生契

---

## 🔧 维护要点

### 1. 数据抓取
- **脚本**: `scripts/fetch-stats.js`
- **频率**: 每天随晨报自动执行
- **存储**: `data/latest-stats.json`
- **截图**: `/tmp/fanqie-stats.png`（用于调试）

### 2. 章节发布
- **脚本**: `scripts/publish-final.js`
- **追踪**: `last-published.json`（记录最后发布的章节）
- **日志**: `logs/publish-YYYY-MM-DD.log`

### 3. 自动任务
- **凌晨2-4点**: 自动创作+发布
- **早上7:00**: 检查发布状态
- **早上7:30**: 生成完整汇报

---

## ⚠️ 注意事项

### URL使用规范
1. **所有Puppeteer脚本**都必须使用 `fanqienovel.com/main/writer/` 路径
2. **禁止使用** `author.fanqienovel.com`（网络不通）
3. **发布页面**: `https://fanqienovel.com/main/writer/{book_id}/publish/`
4. **数据中心**: `https://fanqienovel.com/main/writer/{book_id}/data-center/novel-data?book_id={book_id}`

### Cookie管理
- 定期检查过期时间（提前3天警告）
- Cookie失效时及时更新
- 保持在 `session/fanqie-auth.json`

### 数据真实性
- ❌ 永不制造假数据
- ✅ 抓取失败直接说明
- ✅ 所有数据标注来源和时间

---

## 📝 维护清单

### 定期检查（每天）
- [ ] Cookie是否有效
- [ ] 数据抓取是否成功
- [ ] 发布任务是否正常
- [ ] 日志文件是否有错误

### 定期更新（按需）
- [ ] Cookie更新（过期前3天）
- [ ] 脚本优化（根据问题反馈）
- [ ] 文档更新（功能变更时）

---

**最后更新**: 2026-04-23  
**维护者**: AI Assistant  
**状态**: ✅ 所有功能正常运行
