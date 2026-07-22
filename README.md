# T. Johnny T. — Illustration

イラストレーションのギャラリー。GitHub Pages で公開している。
将来的に `illust.rollplayingcomics.com` に載せ替える予定（DNS 切替後）。

## 構成

```
index.html      1ページのみ。ギャラリー本体
assets/img/     画像（すべて WebP）
```

ビルド不要の静的サイト。CSS と JS は index.html に直接書いている。

## レイアウト

`grid-auto-rows: 1px` の上で、各作品の縦横比から必要な行数を JS が計算して敷き詰める。
画像の読み込みを待たずに寸法が決まるよう、`width` / `height` 属性を必ず入れること。

調整用の値は `.gallery` の CSS 変数にまとまっている。JS も同じ値を読むので、
ここだけ変えれば見た目と行数計算の両方に反映される。

| 変数 | 意味 |
|---|---|
| `--col-gap` | 列と列の間隔 |
| `--row-gap` | 行と行の間隔 |
| `--wide-w`  | 横長作品の幅（ギャラリー幅に対する割合） |

横長の作品には `class="art wide"` を付ける。全幅を占有し、途中に置くと行が分断されて
上に隙間が空くため、末尾にまとめている。

## 画像の追加手順

1. 元画像を `assets/img/` に `art_NN_名前.png` の形で置く
2. `python ../tools/to_webp.py --src assets/img` で WebP 化する（元ファイルは変更されない）
3. `index.html` に `<figure class="art">` を足す。`width` / `height` は変換後の実寸を書く
4. 元の PNG / JPG は `assets/img/` から削除する（gitignore 済みなので公開はされない）

## 注意

掲載しているクライアントワークは不採用案のみ。採用作は権利がクライアントにあるため載せない。
ファイル名を `art_NN_*` に統一しているのは、案件名・クライアント名を公開 URL に出さないため。
