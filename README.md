# 峻爸 AI Transcriber v3.2（Adaptive Hardware Edition）


## v3.2 重要修正

- 工作區改為可捲動版面，避免「工作流程」資訊被壓縮或重疊。
- Gemini 503 / UNAVAILABLE / 429 / 5xx 會顯示倒數並自動重試。
- 文字整理 `gemini-3.8-flash` 持續高負載時會自動改用 `gemini-3.7-flash` / `gemini-3.6-flash`。
- 混合模式若雲端文字整理最後仍失敗，不再讓整個工作失敗：保留本機 Whisper 結果並正常輸出檔案。
- 執行監看會在雲端重試等待期間持續心跳，避免誤判當機。

Windows 10/11 離線 Whisper × Google Gemini 語音轉文字工具。介面顯示作者為「峻爸」；技術性檔名、EXE、快取與 GitHub Artifact 仍保留 `Junba` 英文名稱，避免舊版設定失效。

## v3.2 核心升級

- 跨電腦自適應：NVIDIA CUDA、Intel GPU/NPU、Intel/AMD CPU。
- 自動自適應 / 效能優先 / 省電優先。
- 本機成功/失敗學習紀錄，下一次自動調整路徑。
- 加速器失敗時盡量在同一音訊區段降級繼續。
- Whisper 模型可選自動，依硬體與記憶體保守選型。
- Intel/AMD CPU 永遠保底。
- AMD GPU 尚未整合專用 GPU 後端時不強行啟動，安全改走 CPU。
- 完成視窗顯示總耗時與最終裝置。
- 保留切割、Gemini、混合模式、繁體中文、Word/TXT/SRT/VTT、立即停止輸出目前結果。

## GitHub Actions

Workflow 必須位於 Repository 根目錄：

`.github/workflows/build-windows-v3.2.yml`

Actions → **Build Windows EXE v3.2** → Run workflow。

優先下載 Portable Artifact：

`Junba-AI-Transcriber-v3.2-Portable-Windows-x64`

Single EXE：

`Junba-AI-Transcriber-v3.2-Single-EXE-Windows-x64`

OpenVINO / Intel NPU/GPU 建議優先使用 Portable 版。

## 建議預設

硬體加速：`自動自適應（建議）`

Whisper 模型：`自動（依硬體／記憶體）`
