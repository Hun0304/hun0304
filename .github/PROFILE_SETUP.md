# GitHub 個人頁面設定

## 啟用貪食蛇與 Stats 卡片

1. 將 `README.md`、`assets/spotify-wave.svg` 和 `.github/workflows/snake.yml` 一起提交並推送到 `main`。
2. 到儲存庫的 **Actions → Update Cyberpunk Profile**，確認首次執行成功。也可以按 **Run workflow** 手動更新。
3. 成功後，workflow 會將兩種主題的貪食蛇、GitHub Stats 與常用語言卡片寫入 `output` 分支，README 會讀取這些 SVG。

排程每天在台灣時間 **08:17** 觸發，實際執行時間可能因 GitHub 排隊而延後。首次 workflow 完成前，README 的貪食蛇與 Stats 圖片尚未產生。

已在 workflow 設定 `contents: write`，使用 GitHub 自動提供的 `GITHUB_TOKEN`，不需要新增 Secret。這份設定顯示公開資料；常用語言依公開儲存庫的程式碼統計，不代表熟練程度。若 Actions 執行失敗，可先查看該次執行的錯誤紀錄。

## Spotify 音波動畫

目前使用儲存庫內的 `assets/spotify-wave.svg`，提供純裝飾音波，並支援使用者的減少動態效果偏好。點擊圖片會開啟 Spotify。

要連到自己的個人頁或播放清單，將 README 中 `https://open.spotify.com/` 換成該頁面的分享網址即可。

### 改用即時歌曲與音波

如果要顯示自己的播放狀態，可使用 [spotify-github-profile](https://github.com/kittinan/spotify-github-profile)：

1. 開啟專案提供的 [Connect with Spotify](https://spotify-github-profile.kittinanx.com/api/login)，自行完成 Spotify 授權。
2. 複製服務產生的卡片網址中的 `uid`。
3. 將 README 的 Spotify `<img>` 改成以下設定，並把 `YOUR_UID` 換成自己的值：

```html
<img src="https://spotify-github-profile.kittinanx.com/api/view?uid=YOUR_UID&amp;cover_image=true&amp;theme=novatorem&amp;show_offline=true&amp;background_color=0d0221&amp;bar_color=00f0ff&amp;bar_color_cover=false" alt="Lucien 的 Spotify 播放狀態" width="480" />
```

這個選項會透過第三方服務讀取你授權的 Spotify 播放狀態；不需要將 Spotify 密碼或 Token 放進儲存庫。

## 使用的工具

- [Platane/snk](https://github.com/Platane/snk)：生成貢獻動畫，支援明暗主題與自訂顏色。
- [GitHub Readme Stats Action](https://github.com/stats-organization/github-readme-stats-action)：在 GitHub Actions 內生成 Stats 與語言 SVG。
- [peaceiris/actions-gh-pages](https://github.com/peaceiris/actions-gh-pages)：將產生的圖片發布到 `output` 分支，供 README 讀取；不需要啟用 GitHub Pages 網站。
