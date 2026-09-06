# William's Correction Notes

William 的互動式訂正筆記，發佈在 GitHub Pages 供他隨時複習。

## 網址

<https://cecilia224422.github.io/wnotes/>

## 結構

| 檔案 | 內容 |
|---|---|
| `index.html` | 總目錄。首頁預設顯示固定的能力主題；`TOPICS` 管主題與週末下一階，`LESSONS` 保留每次作業／訂正來源，`TODAY_MISSIONS` 管目前複習入口 |
| `factors-multiples.html` | 2026-08-15 因數與倍數（Math in Focus 4A Ch.2） |
| `fractions.html` | 2026-08-18 分數比較與加減（Math in Focus 4A Ch.3, p.251–258） |
| `rounding.html` | 2026-08-19 四捨五入與估算（K5 Learning） |
| `img/skzoo-*.png` | 8 隻 SKZOO 學習夥伴，頁尾隨機輪替 |
| `robots.txt` | 擋搜尋引擎收錄 |
| `.nojekyll` | 讓 GitHub Pages 直接吐靜態檔，不跑 Jekyll |

每一課都是**單一自足的 HTML**：CSS、JS 都寫在檔案裡，沒有外部相依（Google Fonts 除外）。作業剪貼一律用 CSS 重畫，不放作業照片；唯一的圖片是 `img/` 裡的 8 隻 SKZOO 學習夥伴。

## 能力主題架構

首頁採「**一個能力主題＝一張長期主卡**」，不再採「一份功課＝一張首頁卡」。舊課程頁不刪，作為主題卡內可追溯的 Lesson grid；主題收起時以最新一課的原 SVG 作封面，展開後用兩欄圖卡保留每一課的 SVG、標題、來源與日期。首頁另有折疊的 Homework History 可看完整原卡片。

- 每筆 `LESSONS` 必須有穩定的 `topic` ID，歸入既有 `TOPICS`。
- 同章節或同一解題機制的新作業，只新增 lesson history，不新增主題卡。
- 只有需要另一套完整 Notice → Do → Why → Prove 推理鏈的新能力，才新增 `TOPICS`。
- 新 lesson 的 `thumb` 不得因歸入 topic 而消失：主題封面取最新一課，展開 grid 顯示全部課程縮圖。
- `TOPICS.next` 只接受 `foundation`、`checkpoint`、`advanced`：分別代表週末下一題要補基礎、先快問驗收、或可給進階題。
- William 在 Today’s Mission 的勾選不改變 `TOPICS.next`；只有新題、不看筆記的獨立證據才能升降階。

## 今日任務傳送門

首頁的 `TODAY_MISSIONS` 是 William 的目前複習入口。收到 worksheet 完成卷或作業掃描截圖並完成批改後，同一回合更新：

- 同一能力主題的回饋合併成一張任務卡，不因不同作業或題目變多就重複堆卡。
- 每張卡保留來源類型、需要補強的短句，以及直接進入該課（可含 anchor）的 `href`。
- 圈題或尚未獨立通過的能力持續留在佇列；只有後續不看筆記的換題驗收通過，才可移除。
- William 的勾選只表示「今天已回去複習」，不是熟練證據；完成狀態只存在目前瀏覽器的 `localStorage`，不跨裝置同步，也不回寫 vault。
- 換一批任務時更新 `date` 與每張卡的唯一 `id`，讓新一輪從未勾選開始。

## 新增一課的流程

1. 在 claude.ai 的「互動式教學」Project 產出 `William訂正筆記-<主題>.html`，下載
2. 檔案改成 ASCII 檔名（例：`area-perimeter.html`）放進這個資料夾
3. 在檔案的 `<body ...>` 後面貼上回目錄按鈕（`.wn-back`），頁尾貼上學習夥伴區塊（`.wn-buddy` + 隨機挑角色的小 script）——兩段都直接從任一現有課程頁複製，只改 `.line` 那句話（英文、≤15 字、每頁不同、不可跟頁尾標語重複）
4. 先找 `TOPICS` 中既有的能力主題，再在 `index.html` 的 `LESSONS` 陣列最前面加一筆；`topic` 不可省略：

```js
{
  subject:"math", topic:"math-geometry", date:"2026-09-01",
  title:"Area & Perimeter", zh:"面積與周長",
  desc:"One-line English summary of what this lesson fixes.",
  zhDesc:"一句中文說明。",
  source:"Math in Focus 4A · Chapter 5 · pages 12–20",
  fixes:3, thumb:"grid",
  href:"area-perimeter.html"
}
```

5. 只有找不到可承接的既有能力主題時，才在 `TOPICS` 新增主卡，並設定 `next` 與週末基礎／進階路線。
6. `git add . && git commit -m "add: area & perimeter" && git push`

`thumb` 可用的值：`sieve`（篩法格子）、`fraction`（分數長條）、`numberline`（數線四捨五入）、`grid`（空白橫線頁，預設備用）。要新主題的縮圖就在 `index.html` 的 `THUMBS` 物件裡加一個新函式。

## 製作規範

課程頁的設計規範（語言、版面、視覺、互動元件）真相源在 vault：
`04 個人/孩子/William/互動式教學-專案說明.md`

## 隱私

站台是公開的，但：

- `robots.txt` 與每頁的 `<meta name="robots" content="noindex, nofollow">` 擋搜尋引擎
- 頁面上只有 William 一個名字，沒有姓氏、學號、校名、老師名、作業照片
- repo 名字不帶可辨識資訊

這是「搜尋不到」等級的保護，不是「有密碼」等級。不要把含個資的東西放進這個 repo。
