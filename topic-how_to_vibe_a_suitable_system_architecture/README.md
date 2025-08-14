# 統整報告：怎麼 Vibe 出合適的系統架構

> 依據社群共筆與討論，整理三位分享者觀點與可落地準則，協助以 Vibe Coding 推動架構決策與演進。

---

### 🔗 共筆連結

- 7/29 | 議題共筆：怎麼 Vibe 出合適的系統架構 — `https://hackmd.io/@tPW34DWtRkuPaVD5nh-OtA/By-MjGLDel`

---

## 🗂️ 一、講者觀點整理

### 1.1 杜岳華：從設計模式走向系統架構（Pattern → Architecture）

- 「**從設計模式到系統架構**」的路徑，示範如何在 **vibe coding** 情境下，把需求→設計模式→系統架構串起來；並主張 LLM 適合**原型組件**，而**架構治理**仍需資深工程師主導。

- **vibe coding 的實作樣式**：以「原型→加功能→重構」三段式驅動模型；對應 **State/Strategy/Template** 等模式。

- **常見架構型式與取捨**：

   - **單體**：簡單、高效、易測，但擴展與維運風險高；適合小型或原型。

   - **微服務**：可獨立部署、異質技術、可擴展；代價是分散式複雜度、資料一致性與測試困難。

   - **事件驅動**：高度解耦、非同步、具韌性；但追蹤與除錯更難，需處理最終一致性。

- **從設計模式走向架構的範例（ML 系統）**：

   - 典型 ML 系統＝**離線訓練管線**＋**線上推論服務**。

   - **訓練管線問題**：需可重複、可配置、能快速替換特徵與模型。→ **Template Method** 定流程；**Strategy** 封裝可換演算法。

   - **推論服務問題**：低延遲、模型載入/版本管理與 A/B 測試。→ **Factory** 隱藏載入細節；**Singleton** 避免重複載入。

   - **對照表**：管線＝Template+Strategy；推論＝Factory+Singleton。

- **作者對 vibe coding 的邊界判斷**：LLM 視野有限，先用來做 **prototyping components**；**架構化與組織程式碼**屬資深工程師職責。

- **從需求推導架構（決策依據）**：

   - 需求分析是架構設計基礎；錯在紙上改比上線後便宜。

   - **功能性**（做什麼）vs **非功能性**（效能、擴充、可用性、安全）—後者**驅動架構**。

   - 例：**新聞推薦系統**—NFR（<200ms、5萬併發、99.9% 可用、每日重訓）直接影響技術與架構選型。

### 1.2 林沅霖：從需求出發，用 Vibe 驅動設計與拆解

- **把 AI 當「一起開會的架構師」**，用需求驅動討論，而非一句話命令生成。Vibe Coding 很適合做 MVP，但在**加功能**與**撐規模**兩條線上，仍要用可驗證的工程做法與 AI 協作。

- **兩大挑戰**

   - **挑戰一：新增功能**—牽動資料庫與整體架構調整。

   - **挑戰二：流量／規模擴大**—必須提升穩定性與擴展性。

- **與 AI 協作的方式（像開會，不是下令）**

   1. **定義問題**：症狀是什麼？哪些指標能量化？

   2. **定位/假設**：提供現況架構與可能根因。

   3. **提案**：請 AI 依約束提出可行方案與驗證步驟。

- **新增功能的做法**

   - 先寫**User Journey / Spec**，再談落地（避免「直接做留言功能」這類含糊指令）。

   - 盤點**現有架構**能否支撐；不足再討論資料庫/權限/整合（如選擇 Supabase 等）。

- **撐規模的四個槓桿（概念→對策）**

   - **快取**：用空間換時間；先存重計算或外部呼叫結果。

   - **非同步（MQ）**：用時間換空間；長任務排隊處理，避免峰值壓垮資源（如 GPU）。

   - **水平擴展**：多開工作者節點，提升吞吐。

   - **服務拆分**：把瓶頸部位拆出獨立服務，對症加資源。

- **案例：AI 文生圖服務**

   - 以 **MQ** 處理生成任務（回傳「排隊／進度」）；

   - 以**水平擴展**增加生成工作者，確保在高並發下維持吞吐。

- **總結**

   - 從 **Vibe Coding → 系統設計**：用需求與指標驅動架構演進。

   - **先釐清需求與現況架構，再請 AI 提案**；擁抱快取／非同步／水平擴展／拆分等可擴展性原則。

   - 與 AI **協作討論**（可驗證假設與計畫），而不是單向命令。

### 1.3 Yu Hao：Vibe Coding 架構參考與 DX 觀點

- **命題**：架構決策不只技術，亦是**情緒體驗**；錯一個 config 能炸掉系統，團隊壓力隨之上升。

- **研究指引**：正向情緒 ↗︎ → **生產力、品質**↗︎；反之會拖慢 debug 時間（投射 30% 等級）。

- **DX 三支柱**：理解度 × 工具鏈順暢 × 協作心流 → 交集處才是**卓越架構**。

- **單體（Monolith）**：初期舒適、掌控強；後期焦慮增、維護吃力。**轉折訊號**：單次部署/建置 > 1 小時，該考慮拆分。

- **微服務（Microservices）**：初期自由感強；後期易迷航、維護負擔大。**轉折訊號**：服務數量 > 團隊人數 × 2，需重新評估邊界。

- **情感驅動決策流程**：情感掃描 → 根因探勘 → 技術對照 → **小步驗證** → 迭代回掃描。示例：微服務初期焦慮 → 發現**可觀測性不足** → 導入分散式追蹤 → 焦慮指數↓約 60%。

- **行動矩陣**：以「問題複雜度 × 情緒正負」決定行動：

   - 負向×簡單：立即修正/止血；

   - 正向×簡單：持續優化、沉澱 SOP；

   - 負向×複雜：重設計/深度分析/考慮重構；

   - 正向×複雜：漸進演進、預留緩衝。

- **結語**：優秀架構 = **技術傑作 × 情感平衡**（工程與人因同等重要）。

**網站簡述（[claudecraft.ai](claudecraft.ai)）**

- **定位**：主打「**Vibe Coding 的視覺風格解決方案**」，販售/提供「**設計風格包**」＝海報**提示詞**＋**React 組件庫**＋**氛圍編碼指南**，宣稱可在 AI 生成與代碼間維持**風格一致**。有「風格模板、價格、組件庫、教學、FAQ」等欄位。

- **賣點**：標稱「**風格基因**」確保輸出一致、跨平台應用（Claude、Midjourney、GPT-4o Image…），並提供**7 天 100% 退款**；方案起價 **$9.99**。＊頁面未揭露技術細節，較偏體驗/產物導向。

- **導流與承諾**：提供**風格範例/組件體驗**、方案比較、會員權益與法務（條款/隱私/退款）；由 **Welfree Studio Ltd.** 製作。

---

## 💬 二、Discord 精華與觀點

### 2.1 影片與資源

- Our designer built an OS with Cursor（ryOS）：[YouTube](https://www.youtube.com/watch?v=TQhv6Wol6Ns) · [FB 介紹](https://www.facebook.com/share/p/1Etk4BTwNr/)
  - 要點：Vibe 不是讀心術；需以結構化對話將想法轉為可驗證步驟與產出。
- The New Code — Sean Grove（OpenAI）：[演講](https://www.youtube.com/watch?v=8rABwKRsec4) · [逐字稿/整理](https://my.infocaptor.com/hub/summaries/ai-engineer/the-new-code-sean-grove-openai-8rABwKRsec4)
  - 要點：規格（spec）是新的程式碼；結構化溝通作為人與模型的共同信任錨。

### 2.2 討論摘錄

- YC：toward to vibe architect（以架構視角協作 AI）
- 杜岳華：開發者需站在高點規劃產品並指揮 AI 完成實作
- Edward：複雜系統的 UI 與效能仍需更多實踐經驗以降低試錯

### 2.3 社群觀察

- Vibe Coding 能降低啟動成本，但要交付可維護、可擴展、可觀測且安全的系統，仍需工程紀律與明確的人機邊界。

---

## 📌 三、實作準則與架構決策對照

### 3.1 需求與 NFR 駕馭架構

- 延遲、併發量、可用性、重訓頻率、安全等直接影響技術選型與切分策略。

### 3.2 擴展四槓桿

- 快取：空間換時間，封存重計算或外呼結果。
- 非同步（MQ）：時間換空間，削峰填谷、隔離長任務（如 GPU 工作）。
- 水平擴展：增加 worker 與節點以提升吞吐。
- 服務拆分：以瓶頸為中心拆分，聚焦資源投放與責任邊界。

### 3.3 模式映射小抄（ML/推論服務）

- Template + Strategy（管線）；Factory + Singleton（推論載入）。

### 3.4 轉折訊號（何時調整架構邊界）

- 部署/建置時間過長、服務數爆量、可觀測性不足、回歸成本升高等。

---

## ✅ 有效建議摘要

1. 以「原型 → 加功能 → 重構」迭代，並用設計模式穩定變化點。
2. 先釐清需求與 NFR，再請 AI 依約束給方案與驗證步驟。
3. 擴展優先套用：快取、MQ、水平擴展、針對瓶頸拆分。
4. 把 AI 當會議夥伴：提供現況、假設、數據指標，請其提出可驗證計畫。
5. 留意 DX 與組織負擔的轉折訊號，採小步驗證、可觀測性先行。

---

## ❓ 待解決的疑問

- 單體 → 微服務的明確切分準則與最小拆分單位？
- 事件驅動導入的最小可行觀測性（Tracing/Log/Metric）基線？
- AI 參與架構決策的邊界如何界定與驗證？
- 在多模型/多版本推論下的流量導流（A/B、金絲雀）與回滾機制？

---

## 🌐 四、外部資源（精選）

### 4.1 Agent / 工具與指南

- Agent Infrastructure：LangChain Blog — [Why agent infrastructure matters](https://blog.langchain.com/why-agent-infrastructure/)
- Context Engineering：Repomix — [網站](https://repomix.com/) · [GitHub](https://github.com/yamadashy/repomix)
- 程式開發代理工具組：Serena — [GitHub](https://github.com/oraios/serena)
- Claude Code 課程：DeepLearning.AI — [課程連結](https://www.deeplearning.ai/short-courses/claude-code-a-highly-agentic-coding-assistant/)
- Claude Sub-Agents：
  - Docs — [Anthropic Subagents](https://docs.anthropic.com/en/docs/claude-code/sub-agents)
  - 範本 — [Contains Studio Agents](https://github.com/contains-studio/agents) · [中文版整理](https://github.com/tboydar/Contains-studio-agents) · [awesome-claude-agents](https://github.com/vijaythecoder/awesome-claude-agents)
- AI 協作完整指南（Claude × Cursor）：[HackMD](https://hackmd.io/@65T13wwWTxOnIR8p3_yIPw/Bkv8vyTDle)
- Claude Code 用量監測： [ccusage](https://github.com/ryoppippi/ccusage) · [claude-monitor](https://github.com/Maciek-roboblog/Claude-Code-Usage-Monitor)
- MCP Server：n8n-mcp — [GitHub](https://github.com/czlonkowski/n8n-mcp)

### 4.2 Blog 與 YouTube

- Blog：
  - Python Vibe Coding Tools — [The New Stack](https://thenewstack.io/python-vibe-coding-tools/)
  - Demystify Temperature / Max Tokens / Top P — [Medium](https://medium.com/@ai-miner/demystify-temperature-max-tokens-and-top-p-in-prompt-engineering-b6a338e588a6)
- YouTube：
  - AI 编程：Vibe Coding 的原理是什麼？— [影片](https://www.youtube.com/watch?v=ZXzYZ2fk-vk)
  - Open Vibe Developers：Vibe Coding 的最佳實踐（COSCUP）— [影片](https://www.youtube.com/watch?v=uPy_82FQZjY)

---


