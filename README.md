# William's Correction Notes

William 的互動式訂正筆記，發佈在 GitHub Pages 供他隨時複習。

## 網址

<https://cecilia224422.github.io/wnotes/>

## 結構

| 檔案 | 內容 |
|---|---|
| `index.html` | 總目錄。所有課程的清單、科目篩選、統計。**新增一課只需要改這一個檔的 `LESSONS` 陣列** |
| `factors-multiples.html` | 2026-08-15 因數與倍數（Math in Focus 4A Ch.2） |
| `fractions.html` | 2026-08-18 分數比較與加減（Math in Focus 4A Ch.3, p.251–258） |
| `rounding.html` | 2026-08-19 四捨五入與估算（K5 Learning） |
| `img/skzoo-*.png` | 8 隻 SKZOO 學習夥伴，頁尾隨機輪替 |
| `robots.txt` | 擋搜尋引擎收錄 |
| `.nojekyll` | 讓 GitHub Pages 直接吐靜態檔，不跑 Jekyll |

每一課都是**單一自足的 HTML**：CSS、JS 都寫在檔案裡，沒有外部相依（Google Fonts 除外）。作業剪貼一律用 CSS 重畫，不放作業照片；唯一的圖片是 `img/` 裡的 8 隻 SKZOO 學習夥伴。

## 新增一課的流程

1. 在 claude.ai 的「互動式教學」Project 產出 `William訂正筆記-<主題>.html`，下載
2. 檔案改成 ASCII 檔名（例：`area-perimeter.html`）放進這個資料夾
3. 在檔案的 `<body ...>` 後面貼上回目錄按鈕（`.wn-back`），頁尾貼上學習夥伴區塊（`.wn-buddy` + 隨機挑角色的小 script）——兩段都直接從任一現有課程頁複製，只改 `.line` 那句話（英文、≤15 字、每頁不同、不可跟頁尾標語重複）
4. 在 `index.html` 的 `LESSONS` 陣列最前面加一筆：

```js
{
  subject:"math", date:"2026-09-01",
  title:"Area & Perimeter", zh:"面積與周長",
  desc:"One-line English summary of what this lesson fixes.",
  zhDesc:"一句中文說明。",
  source:"Math in Focus 4A · Chapter 5 · pages 12–20",
  fixes:3, thumb:"grid",
  href:"area-perimeter.html"
}
```

5. `git add . && git commit -m "add: area & perimeter" && git push`

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
