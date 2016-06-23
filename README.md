# mordiford/platform_manifest

どうせ需要ないから日本語で書くぞ

## これなん

- Snapdragon 800/801/805/808/810/820 搭載端末向けに諸々~~削られ~~最適化された `platform_manifest` です
    - 他のSoC向けの `hardware/` 以下のリポジトリやLinux-x86以外のホスト向けのToolchain群は無慈悲にコメントアウトされました
    - `oneplus2` で動作確認済です
- Toolchainを[UBERTC](https://bitbucket.org/DespairFactor/)に変更しています
    - `arm64`の場合は `BoardConfig.mk` で `KERNEL_TOOLCHAIN` を[適切に指定](https://github.com/mordiford/android_device_oneplus_oneplus2/commit/a65779f962056c02be4b8cd397ffd3c4458f12a1)しないと確実にビルドがコケるので注意してください
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
- `packages_apps_ResurrectionStats` がprebuiltsのを使ってて翻訳反映させてくれないので[ソースからビルドさせる](https://github.com/mordiford/packages_apps_ResurrectionStats)ようにしてます
    - その関係で `android_vendor_resurrection` も[手を入れたもの](https://github.com/mordiford/android_vendor_resurrection)に変更しています

## 使い方

[Resurrection Remix のビルド方法 - dev:mordiford](http://dev.maud.io/entry/2016/03/18/how-to-build-rr) で `2-b-3` を適当に `mordiford` に読み替えてください。

```
repo init -u https://github.com/mordiford/platform_manifest.git -b marshmallow
```

```
repo sync -j8 -c -f --force-sync --no-clone-bundle
```
