# 統整報告：Vibe Coding 與測試

---
## 🗂️ 一、講者觀點整理

### 1.1 Cablate：測試在 AI Coding 中的定位 

- **核心分享**：  
  在傳統開發中測試往往被忽略，文件也常隨時間失效，而在 AI Coding 時代，測試與文件更需要重新定位。他認為「測試＋程式」應該取代「文件」作為最終驗證依據，並成為 Context Engineer 的核心工具。  

- **觀點重點**：  
  - **傳統開發困境**：  
    - 文件與程式碼長期脫鉤，文件更新優先度總是最低。  
    - 測試維護成本高，常因時程壓力而被犧牲。  
  - **AI Coding 的挑戰**：  
    - Spec-Driven 下規格與程式仍分離，AI 可能誤解規格。  
    - Test-Driven 需要前期投入，AI 寫的測試常不穩定。  
    - 文件、測試、程式碼三套系統彼此仍未整合。  
  - **?DD 方法論的比較**：  
    - **TDD**：保障程式邏輯正確性。  
    - **DDD**：讓程式反映領域知識模型。  
    - **BDD**：讓程式行為符合使用者預期。  
    - 在 AI 時代，測試可以同時涵蓋 Domain 與 Behavior 的驗證，提供更完整的約束。  
  - **文件的角色**：  
    - 文件是需求轉化的過渡工具，不應作為長期驗證標準。  
    - 長期文件應更像「索引」，用於掌握專案全貌，而非細節驗證。  
  - **測試對 Context Engineer 的價值**：  
    - 測試 return 即反映程式最新狀態，取代反覆更新文件。  
    - 測試失敗就是明確的修正指令，避免自然語言溝通模糊。  
    - 測試提供 AI 最精確、當下所需的 Context。  

- **案例補充**：  
  - Cablate 分享了自己在 AI 協作專案中，因缺乏測試導致文件與程式落差過大，後來透過 TDD 與 SOP（需求澄清→文件→測試→AI 程式→測試驗證）改善流程。  
  - 他強調測試可取代過時文件，直接成為 AI 驗證與協作的基石。  

- **結論**：  
  在 AI Coding 時代，測試是最強力的驗證錨點，能避免模糊與過時的文件問題。文件只需作為索引與溝通介質，真正的品質約束必須交由測試與程式來承擔。  

---

### 1.2 KoKo：用 TDD 實戰 Codex CLI + GPT-5 與 Claude Code + Opus 4.1 

- **核心分享**：  
  以「測試驅動開發（TDD）」實戰比較 OpenAI 與 Anthropic 的 CLI 工具，展示如何用測試來驅動 AI 代碼的可靠性。  

- **觀點重點**：  
  - **TDD 與 AI CLI 的結合**：  
    - 使用 TDD 方法，先寫測試再生成代碼，能避免 AI 輸出「看似正確卻邏輯錯誤」的問題。  
    - Codex CLI + GPT-5 與 Claude Code + Opus 4.1 各有特點：前者速度與廣度佳，後者長上下文與規格遵循更穩定。  
  - **AI CLI 工具的比較**：  
    - **Codex CLI + GPT-5**：適合快速原型、大規模代碼生成。  
    - **Claude Code + Opus 4.1**：擅長結構化專案、遵守規格與測試。  
  - **測試文化的重要性**：  
    - TDD 不僅是技術方法，也是團隊文化。  
    - 測試能在不同 AI 工具間建立一致的品質標準，避免專案落差。  

- **案例補充**：  
  - KoKo 現場展示如何以測試為導向，對比兩組 CLI 在需求落地與測試通過率的差異。  
  - 在複雜場景下，Claude Code 更能保持邏輯完整，而 Codex CLI 偏向快速但需人工補救。  

- **結論**：  
  TDD 是讓 AI CLI 工具「走進真實專案」的關鍵。唯有透過測試驅動，AI 的產出才能真正落地並支持長期維護。  



## 💬 二、Discord 精華與觀點

### 2.1 影片與資源

- [Augmented Coding: Beyond the Vibes](https://tidyfirst.substack.com/p/augmented-coding-beyond-the-vibes)  
  - **主題**：作者以 AI（稱為 genie）協作開發 B+ Tree 函式庫的經驗，對比 Vibe Coding 與 Augmented Coding。  
  - **重點整理**：  
    1. **背景**：挑戰高難度專案，利用 AI 完成 Rust 與 Python 版本的 B+ Tree，效能可與內建結構競爭。  
    2. **方法論差異**：  
       - Vibe Coding：快速迭代、遇錯就修。  
       - Augmented Coding：重視結構、測試與整潔性，避免複雜化。  
    3. **實作策略**：採 TDD 與 Tidy First 原則；人類負責架構與決策，AI 處理細節。  
    4. **跨語言挑戰**：Rust 易卡死，先以 Python 開發再翻譯；甚至 AI 主動建議用 C 擴充模組以提升效能。  
    5. **成果反思**：效能佳但仍有偶然複雜度；AI 減少雜務，人類專注設計與決策。  
    6. **啟示**：未來程式設計將被改造，工程師聚焦架構決策、測試設計與複雜度控制。  

- [Elite Context Engineering with Claude Code](https://www.youtube.com/watch?v=Kf5-HWJPTIE)  
  - **主題**：探討 Claude Code 的 Context Engineering（情境工程）手法，強調「減少（Reduce）」與「委派（Delegate）」。  
  - **重點整理**：  
    - **入門**：上下文預載（context priming），避免浪費 token。  
    - **進階**：子代理（sub-agents），將任務委派，保持主代理乾淨。  
    - **高階**：上下文捆綁包（context bundles）、背景代理任務（background agent tasks），實現自動化與狀態重現。  
    - **核心觀點**：專注、單一目的代理是效能與擴展的關鍵。  

- **spec-kit / Specification-Driven Development (SDD)**, [github](https://github.com/github/spec-kit), [github 中文](https://github.com/GitYCC/spec-kit?fbclid=IwY2xjawNDgztleHRuA2FlbQIxMABicmlkETFHN0xKRkhFZklKaE1Zek5CAR5vEZWeGp0efhavNmwKzfvX4otNFKYFgLuYsbn4u78EuYwrRLicZFjyIyTvKQ_aem_yhDa9fZgiDnldKfzl3nx2A)
  - **主題**：以規格文件為唯一可信來源，程式碼成為規格的表達。  
  - **重點整理**：  
    - **傳統問題**：規格與程式碼脫節，文件快速過時。  
    - **SDD 顛覆**：規格文件驅動開發，AI 生成並維護程式碼。  
    - **流程**：`specify`（產生規格） → `plan`（實作計畫） → `tasks`（任務清單）。  
    - **效率**：傳統 12 小時 → SDD 僅需 15 分鐘完成規格與測試。  
    - **核心原則**：規格 = 主要產物；模組化；測試優先；避免過度工程。  
    - **意義**：軟體工程從「程式碼驅動」轉為「意圖驅動」，開發者專注於設計與批判思維。  

- [awesome-claude-code-subagents](https://github.com/VoltAgent/awesome-claude-code-subagents)  
  - **主題**：社群維護的 Claude Code 子代理大全。  
  - **特色**：收錄超過 100 個子代理，涵蓋全端開發、DevOps、資料科學與營運，並附角色、權限與工作流程，可直接應用於實務。  




## 📌 三、實作準則與架構決策對照

### 3.1 Cablate：AI Coding 中測試與文件的實作準則

- **實作準則**  
  1. 把「測試＋程式」視為最終驗證依據，而不是長期依賴文件。  
  2. 將文件定位為「需求轉化工具」與「索引」，而非持續維護的驗證標準。  
  3. 在 AI 協作流程中，建立 SOP：需求澄清 → 文件 → 測試撰寫 → AI 生成程式 → 測試驗證 → 修正。  
  4. 使用測試 return 作為 Context Engineer 的錨點，避免 AI 理解偏移。  
  5. 以測試失敗訊號作為明確的修正指令，取代反覆人工解釋與確認。  
  6. 結合 TDD/DDD/BDD 的優點，讓測試同時承載需求、領域、行為三層約束。  


### 3.2 KoKo：TDD 驅動的 AI CLI 工具實作準則

- **實作準則**  
  1. 採用 TDD 方法，先寫測試再生成程式碼，確保 AI 輸出可驗證。  
  2. 針對不同工具（Codex CLI vs Claude Code），選擇最適合的應用場景：  
     - Codex CLI + GPT-5：快速原型、廣度探索。  
     - Claude Code + Opus 4.1：長上下文、嚴謹規格專案。  
  3. 將測試納入團隊協作文化，讓不同工具生成的程式都能在統一的驗證標準下被比較。  
  4. 在專案流程中，利用測試提升 AI 輸出的可維護性，避免短期 demo 無法延續。  
  5. 把「測試即契約」的思維內化為團隊默契，讓測試通過成為交付的唯一標準。  

## ✅ 有效建議摘要

1. **以測試為核心驗證標準**  
   將「測試＋程式」視為最終依據，文件僅作為需求轉化與索引。透過 TDD 讓 AI 輸出能被即時驗證，避免文件與程式脫節。  

2. **依場景選擇合適的 AI 工具**  
   Codex CLI + GPT-5 適合快速原型與廣度探索；Claude Code + Opus 4.1 更適合長上下文與嚴謹規格專案。根據專案需求做取捨。  

3. **建立 SOP 與團隊共識**  
   在協作流程中引入 SOP（需求澄清 → 測試撰寫 → AI 生成程式 → 測試驗證），並將「測試即契約」內化為團隊默契。  

4. **結合多種方法論的優勢**  
   TDD 確保邏輯正確，DDD 反映領域知識，BDD 驗證行為需求。三者結合，讓測試同時承載需求、領域與使用者意圖。  

5. **將測試文化化**  
   測試不只是技術手段，而是一種團隊文化。透過跨工具一致的測試契約，確保 AI 協作成果具備可維護性與長期價值。  


## ❓ 待解決的疑問

1. **測試與文件的角色定位**  
   測試能否真正取代文件？如何在「文件作為索引」與「測試作為驗證錨點」之間取得平衡？  

2. **AI 生成測試的穩定性**  
   當前 AI 產生的測試常不可靠，如何確保其覆蓋度與可維護性，避免成為另一種技術債？

3. **跨工具一致性**  
   不同 AI 工具生成程式碼的品質差異大，如何建立統一的測試契約來確保跨工具結果一致？  

4. **團隊文化轉變**  
   測試不只是技術方法，更是一種文化。如何讓團隊從「測試是負擔」轉變為「測試即契約」的共識？  




## 🌐 四、外部資源（精選）

- [Augmented Coding: Beyond the Vibes](https://tidyfirst.substack.com/p/augmented-coding-beyond-the-vibes) — 展示 Augmented Coding 結合 AI 與 TDD 的應用實例。  
- [Elite Context Engineering with Claude Code](https://www.youtube.com/watch?v=Kf5-HWJPTIE) — 說明 Context Engineering 的多層次手法與最佳實踐。  
- [spec-kit (Specification-Driven Development)](https://www.facebook.com/share/p/15Wakn8w9a/) — SDD 工作流程與核心指令的完整介紹。  
- [awesome-claude-code-subagents](https://github.com/VoltAgent/awesome-claude-code-subagents) — 超過百個可投入實務的 Claude Code 子代理集合。  
- [Agentic AI Developer Day Taipei 2025 ADK Workshop](https://github.com/LiuYuWei/agentic-ai-developer-day-2025-adk-workshop)