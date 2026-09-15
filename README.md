---
AIGC:
    Label: "1"
    ContentProducer: 001191440300708461136T1XGW3
    ProduceID: 5390991e442c1cc0a64dcd85c8a2ecc3_b533a0e8b0e411f18874525400287e28
    ReservedCode1: 18YuPmR0P1vFtoZ6SliJclHIMd5wNQgQVOBRPkt72QNm/vk2qMekz7xuHh69xOe/OqnBnnwVIXX6G+yRV19oG+yvEu5xKTLqd6DG10oOhVY7K4ptvkcE1Vie+s9QBon8yjHB/4GSKqilJdOg9x4KU6uP4AByJirPevle4ZFc0ZcYYHHFo3uzYKM3a4E=
    ContentPropagator: 001191440300708461136T1XGW3
    PropagateID: 5390991e442c1cc0a64dcd85c8a2ecc3_b533a0e8b0e411f18874525400287e28
    ReservedCode2: 18YuPmR0P1vFtoZ6SliJclHIMd5wNQgQVOBRPkt72QNm/vk2qMekz7xuHh69xOe/OqnBnnwVIXX6G+yRV19oG+yvEu5xKTLqd6DG10oOhVY7K4ptvkcE1Vie+s9QBon8yjHB/4GSKqilJdOg9x4KU6uP4AByJirPevle4ZFc0ZcYYHHFo3uzYKM3a4E=
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
| zuoheouxiangshichuanqi_riyu | 佐賀偶像是傳奇 第1-2季【日語】 | 24 |
| qihun_guoyu | 棋魂（棋靈王、光之棋）【國語】 | 76 |
| lycoris_recoil_riyu | 彼岸花的后坐力（莉可丽丝、Lycoris Recoil）【日語】 | 13 |
| gundam_hathaway_kirke_riyu | 機動戰士高達：閃光的哈薩維 喀耳刻的魔女【日語】 | 1 |
| jojo_golden_wind_riyu | JOJO的奇妙冒險 黃金之風（JOJO's Bizarre Adventure Golden Wind）（4K）【日語】 | 39 |
*（内容由AI生成，仅供参考）*
*（内容由AI生成，仅供参考）*
*（内容由AI生成，仅供参考）*
