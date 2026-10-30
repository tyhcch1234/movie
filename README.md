# 影片庫 / Video Library

AI 重構畫面短片作品集。線上瀏覽：**https://tyhcch1234.github.io/movie/**

## 目前內容

| 影片 | 長度 | 比例 | 主題 |
|---|---|---|---|
| 嘉利大廈大火（1996） | 60s | 9:16 | 香港史／火警／粵語旁白 |

## 目錄結構

```
movie/
├─ index.html          # 片庫首頁（讀 videos.json 自動列出）
├─ videos.json         # 片庫清單（加片只需改呢個檔）
└─ videos/
   └─ <id>/            # 每段片一個資料夾
      ├─ <id>.mp4      # 主檔（H.264 + AAC，建議 < 100 MB）
      └─ poster.jpg    # 封面圖（9:16，720×1280）
```

## 新增一段影片

1. 建立資料夾 `videos/<id>/`，放入 `<id>.mp4` 與 `poster.jpg`
2. 在 `videos.json` 的 `videos` 陣列加一筆：

```json
{
  "id": "my-video",
  "title": "影片標題",
  "subtitle": "一句說明",
  "date": "2026-11-01",
  "duration": 58,
  "ratio": "9:16",
  "tags": ["標籤一", "標籤二"],
  "description": "詳細描述，會在播放器下方顯示。",
  "src": "videos/my-video/my-video.mp4",
  "poster": "videos/my-video/poster.jpg",
  "note": "畫面為 AI 重構，非真實影像。",
  "size": "38 MB"
}
```

3. `git add -A && git commit -m "add: <id>" && git push`

首頁會自動按 `date` 由新到舊排列，統計段數同總時長。

## 規格建議

- 視訊：H.264 / yuv420p / 1080×1920（9:16）/ 30fps，`-movflags +faststart`
- 音訊：AAC 48kHz 立體聲
- 單檔上限：GitHub 單檔硬限 100 MB，超過請改用 Releases 或 Git LFS
- 檔案愈多，clone 會愈慢；如片量過大，可考慮把 mp4 移到 Releases，repo 只留 poster 同清單

## 授權與聲明

各影片畫面為 AI 生成重構，非真實影像。歷史資料來源見個別影片的 `description` / `note` 欄位。
