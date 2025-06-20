# 第N回

1. [ ] 説明する内容
2. [ ] ...

---

## コンパイル周りの補足

To start the slide show:

- `pnpm install`
- `pnpm dev`
- visit <http://localhost:3030>

## Github Pagesにビルド

[N]のところを回数に置き換えてください．

- `pnpm build --base /Foundations-of-RL-[N] --out docs`

---

## その他注意

これ参考にしよう：
* スライド: https://sli.dev/demo/starter/1
* コード: https://github.com/slidevjs/slidev/blob/main/demo/starter/slides.md

* PDF吐き出すときは
```
pnpm export --per-slide
```
じゃないとページ番号がバグる．
（ここにもっと情報あるかも：https://sli.dev/features/global-layers ）

* 同じLANからアクセスするとき：
* `pnpm dev --remote`　して，[IP]:3030/entryにアクセスする

## 動画

* 画面全体を録画しよう．タブだけだとバグる
* 出力はWEBM (Vp9) & HD 720p 24fpsでいいかも．Qualityはlowで．

```bash
# 音声分離 
ffmpeg -i [title].webm -vn -acodec copy [title].oga

# 音声の入れ替え
ffmpeg -i [title].webm -i [title].mp3 -c:v libvpx-vp9 -c:a libopus -map 0:v:0 -map 1:a:0 [title].webm
```