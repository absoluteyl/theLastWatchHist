# the Last Watch Hist

## Overview

the Last Watch History (以下簡稱 tLWH) 的靈感來自最近熱門的 Social-Fi 類型應用、作者本身在 OTT 產業的相關經驗以及平時在觀影時的痛點。
tLWH 主要利用區塊鏈來紀錄使用者所有的觀影紀錄，並將這些觀影紀錄再提供給各大 OTT 平台，讓使用者在平台間切換時都可以獲得精準且高度個人化且的推薦內容。
未來 tLWH 也希望能提供使用者一個可以分享自己追劇心得、尋找同好的介面及管道。

## Framework

整個專案主要分為兩部份：

1. tLWH contract: 智能合約，使用 solidity 撰寫。負責依照不同的使用者身份 (User Identity) 產生 NFT Token 並對其 metadata 進行管理。
2. tLWH service: Web3 用戶端，使用 Ruby on Rails 撰寫。負責做為智能合約與使用者、IPFS、以及 OTT 平台之間的溝通橋樑。

### 專案進度

[Github Project](https://github.com/users/absoluteyl/projects/1)

### 流程圖

```mermaid
---
title: Minting tLWH NFT
---

sequenceDiagram
  participant U as User
  participant S as tLWH Server
  participant C as tLWH Contract
  participant I as IPFS

  U->>S: Requests to mint NFT
  S->>I: Upload User Meta to IPFS
  I->>S: Return file hash
  S->>C: Calls mint function with IPFS hash
  C->>C: mint
  C->>C: setTokenURI
  C->>S: Emits mint event
  C->>S: Emits MetadataUpdated event
```

```mermaid
---
title: Sync Watch History
---

sequenceDiagram
  participant U as User
  participant O as OTT Platform
  participant S as tLWH Server

  U->>O: Watch Movie/TV Series
  S->>O: Retrieves Watch History
  O->>S: Response
  S->>U: Display Watch History

```

## Development

See Readme in each components.

## Testing

See Readme in each components.

## Usage

See Readme in each components.
