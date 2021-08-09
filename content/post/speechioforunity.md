+++
highlight = true
tags = [
]
date = "2021-01-12T19:34:11+01:00"
title = "Unityで対話型音声認識アプリを作れるフレームワークをつくった"

[header]
  image = ""
  caption = ""
math = false

+++


> macOS, Windows両方で動く、Unityで対話型の音声認識アプリがすぐに作れるフレームワークを作りました。

__Downloads__

リポジトリへのリンク：https://github.com/HassoPlattnerInstituteHCI/SpeechIOForUnity

Unity Package: https://github.com/HassoPlattnerInstituteHCI/SpeechIOForUnity/releases/tag/v1.0

## つかいかた

__`SpeechOut/SpeechIn`を宣言し、以下のように書くだけ。__
<pre>
<code class="language-cs">
SpeechOut speechOut = new SpeechOut();
SpeechIn  speechIn  = new SpeechIn(OnRecognized);

void Start(){
    Dialog();
}

async void Dialog(){
    await speechOut.Speak("Hello!");
    await speechIn.Listen(new string[] { "Hello", "Hi", "Hey" });
    await speechOut.Speak("How are you doing?");
    await speechIn.Listen(new string[] { "I'm fine", "Nah", "I'm Sick" });

}
</code>
</pre>
## なぜつくったか

macOS, Windowsを使う学生のために、Unityを扱う授業で音声認識を使った対話型アプリを作るためのフレームワークがあればいいなと思ったので作りました。
主に非同期処理の`async/await`ベースで、逐次処理をわかりやすく書けるように、また速度や”間”などのチューニングも簡単にできるようにしました。

授業ではmac, Windowsそれぞれを使う学生を同様に対応しないといけないのですが、Unityそのものは双方で動作する一方、ネイティブOSの機能を使おうとすると相互にコードを共有できない＝他のチームやグループが作ったアプリを動作させられないことになるので、このようなコードを作りました。

授業のためとはいえ、一般的に使いやすいツールだと思います。

## OSネイティブの音声認識・音声合成

### macOS側
macOSネイティブのオフライン音声認識ツールとしては、`NSSpeechRecognizer`が、音声合成ツールとしては、コマンドラインツールとして`say`があります。このうち、`say`に関してはUnity上の`System.Diagnostics.Process`から呼び出すことで実行できます（この点、Argsをいじるだけで声質とか速度を変えられるのでサイコー）

一方の`NSSpeechRecognizer`はOSネイティブAPIとして提供されている機能なので、実行するためには`Objective-C`もしくは`Swift`で記述されたコードから実行する必要があります。

今回のフレームワークでは別途[NSSpeechForUnity](https://github.com/HassoPlattnerInstituteHCI/SpeechIOForUnity/tree/master/NSSpeechForUnity)として、`NSSpeechRecognizer`を呼び出す`Objective-C`コードを書き、外部ライブラリとして`.bundle`ファイルを書き出し、それをUnityのPluginとすることで実行しています。


### Windows側

逆にWindows側では`UnityEngine.Windows.Speech`なるモジュールがあり、音声認識に関してはUnityから直接実行できる一方、音声合成に関しては別途WindowsのネイティブAPI＝[SAPI](https://ja.wikipedia.org/wiki/Speech_Application_Programming_Interface)を叩く必要がありました。コード内で別途[WindowsVoiceProject](https://github.com/HassoPlattnerInstituteHCI/SpeechIOForUnity/tree/master/WindowsVoiceProject)として、Visual Studioから.dllをビルドできるプロジェクトを作り、その.dllをUnityのPluginにします。

---

以上２つのOSに関して独自にライブラリを書き出すことによって実現しましたが、Unity上で非同期の動作を実現させるため、それぞれの処理がきちんと終わったかどうかを常に監視するためのコードを書く必要があります。たとえば[このように](https://github.com/HassoPlattnerInstituteHCI/SpeechIOForUnity/blob/0ac6cfe8b468f970524b6dc558d0656bf501322c/NSSpeechForUnity/NSSpeechForUnity/native.m#L75)、内部のStateを逐一変えて、Unity側から監視することで、UnityのAsync/Awaitが進行するように若干HardCodedな感じではありますが、リアルタイムアプリケーションのための非同期処理を実現しています。

---



## 応用
対話型アプリケーションのためとは言いましたが、VRアプリケーションなどのための目と手が離せない際のデバッグ（イベントが起こったときにどのフラグが立ったか喋って教えてくれる）や、視覚障害者向けアプリなど、様々な用途が考えられます。「デバッグのときになにか喋ってくれたら便利だな」とか、「アクセシビリティ機能の充実したアプリを作りたいな」などというときにはぜひ使ってみてください。
