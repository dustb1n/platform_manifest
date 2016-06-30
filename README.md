# mordiford/platform_manifest

どうせ需要ないから日本語で書くぞ

## これなん

- Snapdragon 800/801/808/810 こと `msm8974`/`msm8994`(`msm8992`) 搭載端末向けに諸々~~削られ~~最適化された `platform_manifest` です
    - `lindwurm` ブランチなので自分用です。自分で必要なSoCに絞りました
    - 他のSoC向けの `hardware/` 以下のリポジトリやLinux-x86以外のホスト向けのToolchain群は無慈悲にコメントアウトされました
    - `oneplus2` と `hammerhead` で動作確認済です
- Toolchainを[UBERTC](https://bitbucket.org/DespairFactor/)に変更しています
    - `arm64`の場合は `BoardConfig.mk` で `KERNEL_TOOLCHAIN` を[適切に指定](https://github.com/mordiford/android_device_oneplus_oneplus2/commit/a65779f962056c02be4b8cd397ffd3c4458f12a1)しないと確実にビルドがコケるので注意してください
- 独断で必要無さそうな以下のパッケージを削りました
    - packages/
        - apps/
            - AudioFX
            - Browser
            - Camera2
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
    - 手元で `hammerhead` 向けにビルドしようとしたらライブ壁紙周りでコケるので[適当に削ってください](https://github.com/obsidians/proprietary_vendor_lge_hammerhead/commit/212c2b91f4964570f77add2737f5a4a5ba21a8cb)
    - ブラウザ排除してますがCyanogen Browserこと `gello` は残してるので良さげなブラウザが最初から欲しい人はデバイスツリー側で `device.mk` にいい感じに以下追加してください

```
# Gello
PRODUCT_PACKAGES += \
   Gello
```

## 使い方

[Resurrection Remix のビルド方法 - dev:mordiford](http://dev.maud.io/entry/2016/03/18/how-to-build-rr) で `2-b-3` を適当に `mordiford` に読み替えてください。

```
repo init -u https://github.com/mordiford/platform_manifest.git -b lindwurm
```

```
repo sync -j8 -c -f --force-sync --no-clone-bundle
```
