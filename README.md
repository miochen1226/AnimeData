---
AIGC:
    Label: "1"
    ContentProducer: 001191440300708461136T1XGW3
    ProduceID: 5390991e442c1cc0a64dcd85c8a2ecc3_b0ed2b09af3e11f18f50525400aeaaa3
    ReservedCode1: /ZuW3Yd1kiYZr2LOZoCouhcOB2YL6tZF+CQM9f2y/dMdNkJ6CqXp57BZ7xXOCjznHBWo6YPq/xlzn/GN7qKvJPjiQuoBXXv24IzQ5CkTfdQRwgKRJJLz4Pdhf6ZY0jmYJatUIqyzm8F6AQ2pmUDj2Kj51gGuJfb26JGIqB6qUkBz8dQzIFf1pUTX1Dg=
    ContentPropagator: 001191440300708461136T1XGW3
    PropagateID: 5390991e442c1cc0a64dcd85c8a2ecc3_b0ed2b09af3e11f18f50525400aeaaa3
    ReservedCode2: /ZuW3Yd1kiYZr2LOZoCouhcOB2YL6tZF+CQM9f2y/dMdNkJ6CqXp57BZ7xXOCjznHBWo6YPq/xlzn/GN7qKvJPjiQuoBXXv24IzQ5CkTfdQRwgKRJJLz4Pdhf6ZY0jmYJatUIqyzm8F6AQ2pmUDj2Kj51gGuJfb26JGIqB6qUkBz8dQzIFf1pUTX1Dg=
---

# AnimeData

Android TV 動畫櫃 App 的片單資料源。App 只讀這裡的 JSON 與縮圖，**要加片、改片單，只改這個倉庫，不用重新編譯 APK**。

## 目錄結構

```
catalog.json              # 首頁索引：有哪些動畫
shows/<id>.json           # 單部動畫：集數、標題、縮圖、m3u8 直鏈
thumbs/<id>/cover.jpg     # 封面（首頁卡片用）
thumbs/<id>/ep_001.jpg    # 各集縮圖
```

## 新增一部動畫

1. 在 `thumbs/<新id>/` 放封面 `cover.jpg` 與各集縮圖 `ep_001.jpg`、`ep_002.jpg`…（建議 480x270，每張 < 30KB）
2. 建 `shows/<新id>.json`
3. 在 `catalog.json` 的 `shows` 陣列加一筆

## 格式

`catalog.json`

```json
{
  "version": 1,
  "updated": "2026-09-13",
  "shows": [
    {
      "id": "steins_gate",
      "title": "命運石之門",
      "titleEn": "Steins;Gate",
      "cover": "thumbs/steins_gate/cover.jpg",
      "source": "shows/steins_gate.json",
      "episodeCount": 50
    }
  ]
}
```

`shows/<id>.json`

```json
{
  "id": "steins_gate",
  "title": "命運石之門",
  "titleEn": "Steins;Gate",
  "cover": "thumbs/steins_gate/cover.jpg",
  "episodes": [
    {
      "ep": 1,
      "title": "開始與終結的序章",
      "thumb": "thumbs/steins_gate/ep_001.jpg",
      "url": "https://example.com/path/playlist.m3u8"
    }
  ]
}
```

- `url` 支援 HLS（`m3u8`）與一般影片直鏈
- 圖片路徑一律用**相對路徑**，App 會自動接上 GitHub 網址
- App 依序嘗試 `raw.githubusercontent.com` → `cdn.jsdelivr.net`，兩邊都通即可

## 目前片單

| id | 作品 | 集數 |
|----|------|------|
| steins_gate | 命運石之門 | 50 |
| nigumiaomiao_riyu | 尼古喵喵【日語】 | 10 |
*（内容由AI生成，仅供参考）*
