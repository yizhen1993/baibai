# 🏮 雲端天后宮 (Cloud Mazu Temple) — `baibai`

[![Site Live](https://img.shields.io/badge/Live-https%3A%2F%2Fbaibai.kopipeng.online-success?style=for-the-badge&logo=cloudflare)](https://baibai.kopipeng.online/)

> **雲端天后宮**：多人同殿參拜、擲筊求籤、點光明燈、夜市小遊戲、布袋戲酬神、煙火祈福。  
> 100% 完整複製自 [https://mazu-temple.harper88888.workers.dev/](https://mazu-temple.harper88888.workers.dev/)，具備完整靜態 3D 資產、全套 REST API 以及十殿即時多人同步 WebSocket 伺服器。

---

## 🌐 線上訪問

- **正式網址**：[https://baibai.kopipeng.online/](https://baibai.kopipeng.online/)
- **代碼庫**：[https://github.com/yizhen1993/baibai](https://github.com/yizhen1993/baibai)

---

## 🏛️ 功能特色 (100% 模組完整對齊)

### 1. 三維全景神殿 (Three.js 3D Engine)
- **大殿與神龕**：完整載入 35+ 款高精度/輕量化 GLB 3D 模型（天上聖母媽祖、千里眼、順風耳、觀音菩薩、玄天上帝、關聖帝君、財神爺、月老星君、虎爺、天公爐、金爐、註生娘娘、九天玄女、地藏王、斗姆元君、文昌帝君、土地公、石獅等）。
- **神殿殿宇建築**：重簷歇山頂、立體花窗、藻井斗栱、正殿/偏殿/迴廊。
- **動態環境與日夜天氣**：晝夜光照系統、神殿燈火通明、雨雪天氣即時模擬。

### 2. 十殿即時多人連線 (Real-Time Multi-User Hall)
- **十殿分流系統**：正殿、二殿、三殿、四殿、五殿、六殿、七殿、八殿、九殿、十殿，各殿容納 100 位香客。
- **即時走動與動作廣播**：透過高效能 WebSocket `/ws` 即時同步香客位置、外觀裝扮、走動朝拜、頭飾、持香、手勢動作。
- **全服即時事件廣播**：跑馬燈宣傳、紅包雨、全殿放天燈、全服贈禮、神壇放煙火。

### 3. 傳統參拜禮儀與信仰系統
- **上香敬神**：請清香、供奉鮮花、素果、素糕、茶水與金紙。
- **擲筊求籤**：六十甲子籤、觀音靈籤、月老姻緣籤，擲出聖筊求得籤詩並附完整詩意解說。
- **光明燈祈福**：大殿 140 盞光明燈，香客可點燈祈願、常年護佑。
- **許願池與祈願牆**：寫下心願與祝福，留存於廟宇祈願簿。

### 4. 廟埕夜市與民俗娛樂 (Night Market & Minigames)
- **彈珠台 (Pachinko)**：復古彈珠台小遊戲，挑戰累積最多鋼珠。
- **撈金魚 (Goldfish Scooping)**：紙網撈魚技巧比拼。
- **射氣球 (Balloon Pop)**：飛鏢射氣球闖關。
- **烤魷魚串烤 (Night Market BBQ)**：夜市炭烤翻面烤熟比速度。
- **地瓜球 (QQ Sweet Potato Balls)**：壓油鍋翻炸累積滿滿讚數。
- **珍珠奶茶 (Boba Tea)**：搖泡沫珍奶調飲比手速。
- **香腸擲骰 (Sausage Dice)**：烤香腸攤擲十八啦。
- **野台戲曲與掌中布袋戲**：戲台定時演出北管曲牌與布袋戲酬神。
- **招財貓與愛心浪貓互動**：撫摸、餵罐頭、清貓砂與領養廟貓。
- **周邊商街店鋪**：便利商店、抓娃娃機店、文創服飾店。

---

## 🛠️ 技術架構

```
baibai/
├── public/                 # 254+ 完整 3D 模型、貼圖、音效與前端檔案
│   ├── index.html          # 主頁面與 3D 渲染主體 (1.8MB)
│   ├── sw.js               # Service Worker 離線快取
│   ├── lunar.js            # 農民曆與干支天干演算法
│   ├── manifest.webmanifest# PWA 應用清單
│   ├── *.glb               # 所有神尊與殿閣 3D 模型 (70 款)
│   ├── *.webp / *.jpg      # 介面、貼圖、背景與畫卷
│   ├── *.mp3               # 國樂、梵唄、夜市背景音樂與音效
│   ├── *.json              # 神明數據與香客姓名庫
│   ├── nm/                 # 夜市遊戲精靈圖資
│   ├── shop/               # 商店玻璃與櫥窗貼圖
│   └── ads/                # 廟報宣傳海報
├── server/
│   ├── server.js           # Express + WebSocket 十殿同步伺服器
│   └── state.json          # 廟宇即時狀態持久化儲存
├── Dockerfile              # 輕量 Alpine Node.js 映像
├── docker-compose.yml      # Docker 部署設定 (Port 3011, kopipeng-net)
└── package.json            # 依賴套件 (express, ws, cors)
```

---

## 🚀 部署與啟動指令

### 本地開發啟動
```bash
npm install
npm start
```

### Docker 容器部署
```bash
docker compose up -d --build
```
容器內部監聽連接埠 `3000`，外部映射至主機 `3011`，透過 `kopipeng-net` 由 Nginx Gateway 統一負責 SSL 終結與 HTTP/2 代理轉發。
