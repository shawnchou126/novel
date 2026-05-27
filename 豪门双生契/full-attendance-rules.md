# 全勤奖发布规则

## 📊 触发条件
**总字数达到 10万字 后**，启用全勤奖发布模式

---

## 📋 全勤奖要求

### 每日更新字数
- **最低要求**：每天发布字数 **≥ 6000字**
- **判断逻辑**：
  1. 按原计划选择发布章节（2-5章，概率分布）
  2. 计算这些章节的总字数
  3. 如果 < 6000字，追加下一章
  4. 重复步骤3，直到总字数 ≥ 6000字

### 库存管理
- **最低库存**：**10章**（比普通模式的2章更高）
- **目的**：确保有足够缓冲应对全勤要求

---

## 💡 示例场景

### 场景1：原计划2章，字数不够
```
原计划：发布2章（概率30%）
第9章：2500字
第10章：2800字
总计：5300字 < 6000字 ❌

→ 追加第11章（2600字）
新总计：7900字 ≥ 6000字 ✅
→ 实际发布3章
```

### 场景2：原计划3章，字数刚好够
```
原计划：发布3章（概率55%）
第9章：2500字
第10章：2200字
第11章：2100字
总计：6800字 ≥ 6000字 ✅

→ 实际发布3章（不需要追加）
```

### 场景3：原计划5章，字数远超
```
原计划：发布5章（概率3%）
字数总计：13000字 ≥ 6000字 ✅

→ 实际发布5章
```

---

## 🔄 发布流程（10万字后）

```javascript
function getPublishCountForFullAttendance(pendingChapters) {
  // 1. 按概率分布确定初始发布数量
  let targetCount = getPublishCount(); // 2-5章
  
  // 2. 计算字数
  let totalWords = 0;
  let actualCount = 0;
  
  for (let i = 0; i < pendingChapters.length; i++) {
    totalWords += getChapterWordCount(pendingChapters[i]);
    actualCount++;
    
    // 如果字数够了，且至少达到原计划数量
    if (totalWords >= 6000 && actualCount >= targetCount) {
      break;
    }
    
    // 保护机制：不能超过 (总存量 - 10)
    if (actualCount >= pendingChapters.length - 10) {
      break;
    }
  }
  
  // 3. 如果字数还不够，继续追加
  while (totalWords < 6000 && actualCount < pendingChapters.length - 10) {
    totalWords += getChapterWordCount(pendingChapters[actualCount]);
    actualCount++;
  }
  
  return { count: actualCount, totalWords };
}
```

---

## ⚠️ 库存保护

**硬性规则**：
- 无论如何，**必须保留至少10章库存**
- 如果存量不足，优先创作，暂停发布
- 累积到15章以上再恢复发布

---

## 📅 切换时机

**当前状态**：未达到10万字
- 已发布：8章
- 估算总字数：约 2万字

**预计切换时间**：
- 按每天发布3章（平均2500字/章）计算
- 约需发布 33章才能达到10万字
- 预计在 **10-15天后** 启用全勤模式

**切换时自动检测**：
- 每次发布前，统计已发布总字数
- 如果 ≥ 100000字，自动切换到全勤模式
- 在日志中记录："✅ 已达到10万字，启用全勤奖模式"

---

**更新时间**：2026-04-22 17:50
