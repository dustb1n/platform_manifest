# mordiford/platform_manifest 

- README for `marshmallow-msm8974`
    - どうせ需要ないから日本語で書くぞ

## これなん

- `msm8974` こと Snapdragon 800/801 搭載端末向けに諸々~~削られ~~最適化された `platform_manifest` です
    - `hammerhead` で検証済です
    - `apq8084` も一応残してるんで Snapdragon 805 もいける？(未確認)
    - 他のSoC向けの `hardware/` 以下のリポジトリやLinux-x86以外のホスト向けのToolchain群は無慈悲にコメントアウトされました
        - 軽量化のため仕方がなかった
- Toolchainを[UBERTC](https://bitbucket.org/DespairFactor/)に変更しています
- 独断で必要無さそうな以下のパッケージを削りました
    - packages/
        - apps/
            - AudioFX
            - Browser
            - Eleven
            - FMRadio
        - screensavers/
            - Basic
            - PhotoTables
            - WebView
        - wallpapers/
            - Basic
            - Galaxy4
            - HoloSpiral
            - NoiseField
            - PhaseBeam
            - PhotoPhase
    - 手元でhammerhead向けにビルドしようとしたらライブ壁紙周りでコケるので[適当に削ってください](https://github.com/obsidians/proprietary_vendor_lge_hammerhead/commit/212c2b91f4964570f77add2737f5a4a5ba21a8cb)
    - ブラウザ排除してますがCyanogen Browserこと `gello` は残してるので良さげなブラウザが最初から欲しい人はデバイスツリー側で `device.mk` にいい感じに以下追加してください

```
# Gello
PRODUCT_PACKAGES += \
   Gello
```


## 使い方

[Resurrection Remix のビルド方法 - dev:mordiford](http://dev.maud.io/entry/2016/03/18/how-to-build-rr) で `2-b-3` を適当に `mordiford` に読み替えてください。

```
repo init -u https://github.com/mordiford/platform_manifest.git -b marshmallow-msm8974
```

```
repo sync -j8 -c -f --force-sync --no-clone-bundle
```
