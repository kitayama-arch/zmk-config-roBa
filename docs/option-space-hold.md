# Option+Spaceの長押しをホストへ届ける

2026-11-25。Speakのモード切り替え向け。

通常のSpaceは短押しで空白、長押しで既存ARROWレイヤー（2）を維持する。
左右いずれかのOptionを先に押してからSpaceを押すと、通常のSpaceキーの押下・解放をそのまま送信する。Optionはkeep-modsで保持する。
Spaceを先に押した場合は従来のレイヤー操作を選ぶため、Optionを先に押す。

Speakの実キー診断では、roBaの保持操作が約0.0004秒の押下・解放として届いた。既存の&lt 2 SPACEが長押しをレイヤー操作へ使うため、Mac側ではその保持を復元できない。KarabinerのMac本体向け例外だけでは、Karabinerの対象外になっているroBaには効かない。

修正は既存作業ブランチのコミット6504563を基点に、Spaceのbehaviorだけをラップしたもの。既存作業ツリーの未コミットroBa_R.confは含めない。DYA Studioの設定は基点から引き継ぐ。

## 実機確認項目

1. 単独Spaceの短押しで空白、長押しで矢印レイヤーが動く。
2. Optionを先に押し、Spaceを短押しするとSpeakの録音開始・停止。
3. 同じ順序でSpaceを0.55秒以上保持するとモードが一度切り替わる。解放しても録音を止めない。
4. Option/Spaceの解放後に修飾キーが残らない。

ビルド成功と書き込み・動作確認は区別する。既存のsplit/Bluetoothペアリングはリセットせず、実機書き込みの別途明示許可を受けて左右の対応UF2を更新する。

参照: https://zmk.dev/docs/keymaps/behaviors/mod-morph
