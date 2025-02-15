# Spoiler Detector (Chrome Extension)

用于检测搜索/输入文本中是否包含剧透，结合**关键词过滤**与 **OpenAI GPT-3.5-turbo**进行判断。

## 功能

1. **关键词过滤**：匹配用户自定义关键词。  
2. **短路逻辑**：若文本内含“spoiler”且不含“not spoiler”等否定短语，直接视为剧透。  
3. **多档灵敏度**：`low / medium / high`，通过不同 Prompt 让模型只回答“YES/NO”。  
4. **OpenAI 判断**：若关键词匹配则调用 API，否则跳过。

## 使用

1. **加载扩展**  
   - 打开 `chrome://extensions/` → 开发者模式 → “加载已解压”。  
2. **在弹窗 (Popup) 设置**  
   - 启用检测（Enable Search Detection）  
   - 选择剧透等级 (Low/Medium/High)  
   - 输入关键词列表（逗号分隔）  
3. **搜索/输入**  
   - 若检测到剧透，显示红色警告或对文本模糊。  

## 主要文件

- **manifest.json**：声明扩展信息，注入 content scripts  
- **background.js**：接收“CHECK_SPOILER”请求，判断关键词/OpenAI结果  
- **content.js**：侦听网页输入或评论文本，发送检测请求并显示结果

## 注意事项

- **OpenAI Key**：在 `background.js` 内硬编码，请勿公开。建议后端代理或私密配置。  
- **性能/费用**：可加截断、缓存、更多过滤减少 API 调用。  
- **准确率**：仅供演示，模型判定有误差，难以覆盖所有剧透场景。

---
