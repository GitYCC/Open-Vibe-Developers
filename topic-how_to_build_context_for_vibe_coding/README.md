# 統整報告：如何建立脈絡給 Vibe Coding

## 👥 貢獻者 Contributors

| 貢獻者 |   | 貢獻者 |   | 貢獻者 |   |
|--------|------|--------|------|--------|------|
| <a href="https://github.com/xxx"><img src="https://github.com/xxx.png" width="80" alt="@xxx"/></a> | 晉安 - 講者 | <a href="https://github.com/xxx"><img src="https://github.com/xxx.png" width="80" alt="@xxx"/></a> | Kled - 講者 | <a href="https://github.com/GitYCC"><img src="https://github.com/GitYCC.png" width="80" alt="@GitYCC"/></a> | YC - 講者 |
| <a href="https://github.com/rd8312"><img src="https://github.com/rd8312.png" width="80" alt="@rd8312"/></a> | Sam | <a href="https://github.com/52nlp"><img src="https://github.com/52nlp.png" width="80" alt="@52nlp"/></a> | Albert | <a href="https://github.com/smiletoeveryone"><img src="https://github.com/smiletoeveryone.png" width="80" alt="@smiletoeveryone"/></a> | Scott |
| <a href="https://www.linkedin.com/in/netghost1010"><img src="https://media.licdn.com/dms/image/v2/D5603AQGvQbEhm5YdIg/profile-displayphoto-shrink_800_800/B56ZbCoHDPGoAc-/0/1747022017493?e=1756339200&v=beta&t=39ys6-QKlvlJRcYnghs-69mBnilleiPVtaKfjYZT4uY" width="80"/></a> | SSR |



## 🗂️ 一、講者觀點整理

#### 影片連結：https://www.youtube.com/watch?v=nnNAmlDlP24&t=1109s

### 1.1 晉安：**以文件驅動 AI 協作，結構化拆解流程**

* 主張透過 **需求 → 序列圖 → 類別圖 → 測試案例** 四步驟細化任務。
* 文件類型與對應重點：

  * PRD（需求文件）：對齊產品與技術。
  * Sequence Diagram：系統行為流程。
  * Class Diagram：邏輯與結構規劃。
  * 測試案例：確保功能驗證與穩定性。
* 關鍵語句：「TDD 不是多餘的工，是讓 AI 和你都知道『何時停、何時錯、何時成功』。」

### 1.2 Kled：**無文件也能 vibe，但需靠經驗與重構**

* 若熟悉領域：用高階 spec 即可啟動專案。
* 若陌生領域：仰賴 AI draft + 多輪 prompt 調整，最後手動 refactor。
* 提出三步流程：功能定義 → 溝通調整 → 建立測試。

### 1.3 YC：**用 C4 結構化文件達成平衡**

* 三種開發模式比較：無文件對話式 / 詳細文件 / C4 分層文件。
* 推薦使用 C4 模型（Context → Container → Component → Code）配合文件撰寫，提升 AI 理解力與團隊溝通效率。
* 提出對應每層 C4 的文件撰寫指南（參見 Appendix A）。

---

## 💬 二、從 Discord 蒐集的共識與觀點

### 2.1 文件與 Vibe 的選擇是「階段性調整」，非非黑即白

* 小型專案/熟悉任務：先 vibe 再補文件
* 複雜任務/多人協作：先設計 context，導入模組化文件

### 2.2 多元實踐觀點

* **先 vibe 派**（SSR、Kuan、Edward）：快速產出、調整後補細節。
* **先寫文件派**（0xmtlNow）：降低錯誤與溝通成本。
* **平衡派**（ThinkingMelody、豆沙包）：視專案需求與人力素質彈性選擇。

### 2.3 文件是給 AI 看的

* 文件撰寫要考慮「給 AI 消化」：語意結構、索引模組化、metadata 標註等。

---

## 🎨 三、從 Figma 蒐集的建議與實驗

* **心智圖式輸入**作為非對話式 vibe coding 模式。
* 使用 **UML 圖自動轉程式**：

  * 由 Class Diagram → Sequence Diagram → PRD → DTDD。
  * 使用 Use Case 圖產出驗收案例。
* 結構化文檔管理建議：以 MDC（模組文件）為中心，採索引式設計。

---

## 🌐 四、外部資源與業界趨勢

### 4.1 Context Engineering 模式圖（見原文流程圖）

* 由 UML → prompt 設計 → LLM → 產出模組
* 關鍵技術能力：

  * Prompt 分段結構化
  * 模板化輸出
  * 控制語意邊界與關聯
  * 多輪問答引導

### 4.2 實作工具建議

| 類別        | 工具推薦                        |
| --------- | --------------------------- |
| UML       | PlantUML, StarUML           |
| AI 編碼 IDE | Cursor, Claude Code, Kiro   |
| 文件向量化     | LangChain, LlamaIndex       |
| 本地 LLM    | Ollama, LLaMA3 Code         |
| 專案腳手架     | FastAPI CLI 工具              |
| 模組記憶系統    | context7, Claude MCP Plugin |

---

# ✅ 有效建議摘要

1. **小專案/熟悉任務可先 vibe、後對齊**
2. **多人協作或 AI 自動化需結構化文件先行**
3. 文件不再只是「人用說明書」，而是「AI 執行指南」
4. 推薦使用 **C4、UML、MDC 模組化文件結構**
5. 引導 AI 建議時應明確指定語意邊界與輸出格式
6. 「Context Engineering」成為下一代 AI 編碼關鍵技術

---

# 📚 值得參考的資源

| 類別      | 資源                                                                                                                 | 備註            |
| ------- | ------------------------------------------------------------------------------------------------------------------ | ------------- |
| 實務文     | [Cursor + Vibe](https://words.bobchao.net/cursor-ai-programming-a98a583ff96b)                                      | 中文整理          |
| 教程      | [Context Engineering Guide](https://analyticsindiamag.com/ai-features/context-engineering-is-the-new-vibe-coding/) | 教學文章          |
| 工具      | [Kiro IDE](https://kiro.dev/blog/introducing-kiro/)                                                                | AWS 推出 AI IDE |
| YouTube | [Claude Code 用了 30 天](https://youtu.be/sOvi9Iu1Dq8)                                                                | 中文心得          |
| GitHub  | [Context Engineering Intro](https://github.com/coleam00/context-engineering-intro)                                 | 技術實作          |
| 社群經驗    | [Serena MDC 設計分享](https://www.facebook.com/share/p/19RZVFpDzN/)                                                    | 模組化實務         |

---

# ❓ 待解決的疑問

1. **PRD 文件如何與 AI 共創？**：要怎麼共同編輯並避免偏離原意？
2. **文件與 code 的同步機制？**：AI 怎麼知道哪裡變了？
3. **對沒有文件的既有 code，如何補上文件？**
4. **不同 VC 階段（Prototype vs Production），要用哪種 LLM 工具最合適？Claude Code、Cursor 還是 Kiro？**
5. **Non-dev 可以完成大型 vibe 專案嗎？還是需要一定技術基礎？**

---

# 📎 Appendix 附錄

## A. 🔷 C4 模型與對應文件撰寫建議

| 圖層        | 對象/目的                    | 文件內容建議                                                                                                                  |
| --------- | ------------------------ | ----------------------------------------------------------------------------------------------------------------------- |
| Context   | 商業決策者、PM、整體理解需求者         | - 系統簡介（這是什麼系統、解決什麼問題）<br>- 使用者清單（有哪些角色互動）<br>- 外部整合系統（OAuth, Line API, etc.）<br>- 系統邊界（哪些功能不屬於此系統）                      |
| Container | 架構師、DevOps、後端開發者         | - 容器清單（Web, API, DB...）<br>- 各容器責任<br>- 技術選型（Python, Node, Postgres）<br>- 容器間通訊協議（REST/gRPC/MQ）<br>- 容器部署建議（Docker/K8s） |
| Component | 模組開發者、維護者、Code Review 用者 | - 容器內模組職責與界線（Service / Handler / Middleware）<br>- 相依性說明（Lib / DB）<br>- 使用 Library 或框架說明<br>- 每個模組對應的測試點                 |
| Code      | 撰寫實作者、重構者、AI 編碼助理        | - 關鍵類別職責與方法<br>- 函式與資料結構說明（input/output）<br>- 資料流程圖、邏輯判斷樹<br>- 關鍵函數的測試覆蓋建議                                              |

---

## B. 🧩 UML 圖與 Vibe Coding 結合範例

### UML → Prompt → AI 編碼的步驟範本

```plaintext
UML 類別圖：
Class: User
 - id: int
 - name: str
 - email: str

Class: Order
 - id: int
 - amount: float
 - user: User (Many-to-One)
```

### Prompt：

```markdown
請使用 FastAPI 與 SQLAlchemy 根據下列 UML 建立資料模型與 CRUD API：

- models.py: 定義 User 與 Order ORM 類別（含 ForeignKey）
- schemas.py: 對應 Pydantic 模型
- routers/order.py: 包含 create/read/update/delete 路由
- main.py: 為應用程式入口點
```

### 額外提示技巧（Context Engineering）：

| 技巧        | 說明                                        |
| --------- | ----------------------------------------- |
| 🧱 分段結構   | 需求說明 → 類別說明 → 架構設計 → 輸出規則，模組化清晰           |
| 🎯 控制語意邊界 | 明定框架、語言、資料庫技術（ex: FastAPI + SQLAlchemy）   |
| 📐 模板輸出格式 | 指定哪些檔案要產出、要放什麼內容，強化一致性                    |
| 🔁 多輪引導   | 一開始只產生 models.py，下一輪請 AI 寫 router.py，可控性高 |

---

## C. 🗃️ 文件模組化建議（MDC 結構）

推薦使用 `.mdc` 格式模擬大型知識系統，方便 AI 使用檔案檢索。

```plaintext
📂 knowledge-base/
├── index.mdc                # 整體結構與分類入口
├── core-standards.mdc       # 開發規範（命名、結構、test 準則）
├── team-protocol.mdc        # 團隊協作流程與 prompt 寫法建議
├── auth-module.mdc          # 模組功能邏輯與測試情境
├── project-a.mdc            # 專案 A 的使用案例與技術選型
```

### 推薦檔案段落格式：

```md
## 模組名稱：Auth Handler

### 功能描述
處理使用者登入、JWT 產生與驗證。

### 使用技術
- FastAPI
- pyjwt
- bcrypt

### API 介面
- POST /login
- GET /me

### 邏輯流程圖
（可插入 PlantUML）

### 測試情境
- 登入失敗（錯誤密碼）
- 登入成功 + JWT 正確解析
```

---

## D. ⚙️ 工具推薦對照表

| 目的       | 工具                        | 特點                        |
| -------- | ------------------------- | ------------------------- |
| UML 繪製   | PlantUML, StarUML         | 可輸出文字 + API 整合            |
| AI IDE   | Cursor, Claude Code, Kiro | 自動補全 + prompt 設計能力        |
| 向量化文件    | LlamaIndex, LangChain     | 提供 retrieval 能力，配合 RAG 使用 |
| AI 引擎    | GPT-4, Claude 3, LLaMA3   | 程式碼理解力強，適用多語言生成           |
| 本地推論工具   | Ollama + LLaMA3           | 可離線運行、低成本                 |
| 文件記憶與支援  | context7, Claude MCP      | 建構 context-aware 的 AI 工作流 |
| API 快速啟動 | FastAPI CLI               | 提供 scaffold 結構，適合生成整合碼    |

---

## E. 🧪 DTDD / CoVe / 自動化測試策略範例

| 文件 → 測試連動             | 說明與用途                                              |
| --------------------- | -------------------------------------------------- |
| 用例圖（Use Case）         | 描述使用者旅程，對應驗收測試場景（UAT）                              |
| 類別圖（Class Diagram）    | 對應單元測試：類別方法邊界與異常處理                                 |
| 序列圖（Sequence Diagram） | 對應整合測試（API 順序、非同步任務、timeout 檢查等）                   |
| PRD 文件                | 轉換為 Gherkin 格式（Given/When/Then），用於 BDD 測試自動化       |
| CoVe 框架實踐             | 可設計一條鏈條：PRD → 測試條件 → 執行測試 → 回報不一致情況，並標註來源文件與參照上下文。 |

---

## F. 🧠 概念總表

| 概念/術語                       | 定義                                                   |
| --------------------------- | ---------------------------------------------------- |
| Vibe Coding                 | 與 AI 即興對話式開發，意圖驅動、實作由 AI 產出                          |
| Context Engineering         | 設計「語意上下文結構」以引導 AI 精準運作，強調 Prompt + 文件 + 結構並行         |
| C4 Model                    | 四層架構圖：Context, Container, Component, Code，從高到低描繪系統架構 |
| MDC 文件                      | 模組化文檔格式（index.mdc 等）讓 AI 可用文件為知識節點進行 query 與記憶       |
| DTDD（Design→Test→Dev）       | 以設計文件為基礎推導出測試，再推導程式碼，提升一致性                           |
| CoVe（Chain of Verification） | 透過鏈式驗證機制自動檢查 LLM 輸出是否符合規格，可結合 BDD 驗收、靜態分析等機制         |
| RAG                         | Retrieval-Augmented Generation，結合語意檢索與 LLM 強化精準性     |

當然可以，以下是補充於 Appendix 的一節，針對 **TDD、BDD、ATDD** 三種方法論進行系統性說明，並強調它們與文件撰寫與 AI 導入的關聯：

---

## G. 🧪 TDD / BDD / ATDD 三大開發方法論

在結構化系統開發中，**測試先行**是實現可預測與高品質輸出的核心原則。以下是三種常見的測試驅動開發方法論，以及其適用場景與特色：

| 方法論      | 中文名稱     | 核心觀點                                       | 產出物                    | 適用角色       |
| -------- | -------- | ------------------------------------------ | ---------------------- | ---------- |
| **TDD**  | 測試驅動開發   | 「先寫單元測試，再寫實作」<br>確保每個函式、模組在微觀層級可驗證         | 測試代碼（單元測試）<br>程式碼      | 工程師、AI 生成者 |
| **BDD**  | 行為驅動開發   | 「先寫使用行為，再推導邏輯」<br>以自然語言撰寫驗收條件，與使用者共識一致     | `Given-When-Then` 測試腳本 | QA、PM、工程師  |
| **ATDD** | 驗收測試驅動開發 | 「先寫業務驗收條件，再開發程式」<br>業務與開發共同定義測試場景，確保業務目標對齊 | 驗收測試案例（多與 CI 整合）       | 業主、PM、開發團隊 |

---

### 🔁 三者差異圖解（流程對比）

```plaintext
TDD 流程：
[寫測試（單元）] → [寫程式碼] → [重構] → ✅

BDD 流程：
[定義使用情境] → [撰寫 Gherkin 測試] → [開發邏輯] → ✅

ATDD 流程：
[討論業務驗收條件] → [自動化測試腳本] → [開發功能] → ✅
```

### 🧠 與文件化 / AI 開發的關聯

| 方法論  | 對應文件類型               | 可結合 AI 的方式                       |
| ---- | -------------------- | -------------------------------- |
| TDD  | `component.mdc`, 類別圖 | 可提示 AI 根據函式簽名產生 pytest 測試        |
| BDD  | PRD 文件、UML + 行為流程圖   | 可用自然語言轉換成 Gherkin，並由 AI 生成對應測試邏輯 |
| ATDD | PRD、驗收條件、用例流程表       | 可轉換為自動驗收腳本（CI/CD 整合）並驗證是否達成業務需求  |


### 📌 結合 AI 工具的實作建議

| AI 工具                                  | 功能                               |
| -------------------------------------- | -------------------------------- |
| **OpenAI GPT + Prompt Template**       | 可將 BDD/ATDD 用例轉成測試框架，協助生成自動化測試代碼 |
| **TestPilot（Cursor/JetBrains Plugin）** | 自動產生單元測試、mock 情境、異常處理情境          |
| **CoVe (Chain of Verification)**       | 檢查 TDD 或 ATDD 案例是否符合預定行為，並標示違規處  |


### ✅ 小提醒：選用建議

| 開發階段           | 建議搭配的方法論 |
| -------------- | -------- |
| 初期模組設計、邏輯推導    | TDD      |
| 使用者故事驗證、PRD 對齊 | BDD      |
| 業務需求落實、CI 驗收   | ATDD     |
