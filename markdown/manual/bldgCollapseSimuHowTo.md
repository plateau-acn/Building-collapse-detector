# 2. 家屋倒壊判定モジュールを用いた土石流シミュレーションの実行方法

本章では、家屋倒壊判定モジュールを用いた土石流シミュレーションの実行方法を説明します。

## 家屋倒壊判定モジュール組み込み版のソルバexeへの切り替え

最初に、iRICのGUIで呼び出されるMorpho2DHのソルバを家屋倒壊判定モジュール組み込み版に切り替える必要があります。

1. まずフォルダ`C:\Users\[ユーザ名]\iRIC_v4\private\solvers\iRICsolvers_Morpho2DH`を作成します。`[ユーザ名]`は、PCによって異なります。
2. [morpho2DH_PK12.zip](/resources/bldgCollapseSimuHowTo/morpho2DH_PK12.zip)を
解凍して得られる`definition.xml`と`morpho2d.exe`と`translation_ja_JP.ts`を1.のフォルダのコピーします。
3. 下図のように、iRICを起動して家屋倒壊判定モジュール組み込み版ソルバ`Morpho2DH PK12`を選択して新規プロジェクトを作成し、ウィンドウタイトルに`Morpho2DH PK12`と表示されていれば、正しくソルバが切り替えられたことになります。

![capture_gui_title.png](/resources/bldgCollapseSimuHowTo/capture_gui_title.png)

> [!WARNING]
> `C:\Users\[ユーザ名]\iRIC_v4\solvers\iRICsolvers_Morpho2DH`というフォルダ(`private`がフォルダパスにないもの)がありますが、
> これはオリジナルのソルバですので、間違えて上書きしないようにしてください。


## 建物耐力の設定

前述の方法で家屋倒壊判定モジュール組み込み版ソルバ`Morpho2DH PK12`を選択して新規プロジェクトを作成し、以下のように建物耐力を設定します。
建物耐力設定以外の操作は、[1. オリジナルiRIC Morpho2DHの使い方](/gh-pages/manual/originalSimuHowTo.html)をご参照ください。

![capture01.png](/resources/bldgCollapseSimuHowTo/capture01.png)

* ①メニュー「計算条件」⇒「設定」を選択肢、「計算条件」ウィンドウを開く
* ②左のリストから「建物」を選択
* ③「建物破壊」を「使用する」とし、「編集」ボタンを押して「建物倒壊応力」ウィンドウを開く。
* ④左側テーブルのコード1の行の「限界破壊応力」に、建物耐力の数値(kN/m)です。GUIの表記は誤記ですので注意してください。今回は500kN/mと入力してください。
  * このパラメータは木造建物の基本的な耐力を設定する数値ですが、500～800kN/m程度にすると、既往の実被害の再現度が高くなることが分かっています。
  この数値の妥当性・物理的意味については今後検証していく必要があります。
  * コード7の行の「限界破壊応力」の数値は4000kN/mのままで構いません。RC造建物等の倒壊する可能性が低い建物の想定ですので、大きな数値を設定しておけばよいです。

## シミュレーションの実行

建物耐力の設定以外は、
シミュレーションの実行方法・結果の確認方法含めてオリジナル版と同じですので、
[1. オリジナルiRIC Morpho2DHの使い方](/gh-pages/manual/originalSimuHowTo.html)をご参照ください。

計算が完了し、建屋の破壊状況を可視化すると以下のような結果となります。（緑色が倒壊・赤色が非倒壊）

![capture_result.png](/resources/bldgCollapseSimuHowTo/capture_result.png)