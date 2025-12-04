# Windows Subsystem for Linux を試してみた

Windows 10 Anniversary Update の目玉機能の一つである Windows 上で Linux が動く Windows Subsystem for Linux を試してみた。このところ Windows が動く機器が手元になかったのだが、ふと思い立って死蔵しているネットブックに Windows10 をインストールしてみたら遅いなりになんとか動いたのでちょっと遊んでみたというのが実情。全然実用にするつもりはないので実用的なレポートではない。あしからず。

# Windows で Linux が稼働するまでの長い流れ

さて、 Anniversary Update のベータ版の頃から次のアップデートで Windows 上で Linux が動くようになると話題になっていたが、 Anniversary Update になったからといってすぐに使えるわけではない。

まずは設定アプリを起動して “更新とセキュリティ > 開発者向け” と進んでいって、 Windows を開発者モードに変更しなければいけない。次にコントロールパネルを起動して “プログラム > プログラムと機能 > Windowsの機能の有効化または無効化” とたどっていって “Windows Subsystem for Linux” のチェックボックスを ON にしなければいけない。なかなか一筋縄では行かない。

これで bash.exe というコマンドがインストールされるのでコマンドプロンプトから bash.exe と入力して実行すると Windows Subsystem for Linux のインストールが始まる。もう使えるのかと思ったらこれからインストールだ。ここで Linux のユーザー名とパスワードを決める。

そして長い道のりを経てやっと使えるようになる。一度使えるようになるとスタートメニューに “Bash on Ubuntu on Windows” というアイコンが現れる。まさに Ubuntu のアイコンだ。

# Ubuntu の Terminal と同じ

Ubuntu のアイコンを実行すると、 Terminal 画面が出てくる。 Ubuntu の Terminal と同じ感覚で使える。最初から使えるコマンドは少ないが、エディタは nano と vim が使える。 Emacs は標準ではインストールされていないのも Ubuntu と同じだ。

# Aptが使える

最初から apt コマンドがインストールされていて、 Ubuntu のリポジトリを参照して好きなコマンドをインストールできるところまで Ubuntu そのままだ。もちろん GUI 環境はないので CLI で使えるコマンドだけだが、 Ubuntu の Terminal でできることは大抵のことができると考えていいだろう。

試しに GUI 環境が必要なアプリをインストールしてみると、エラーもなくインストールできたが、実行しようとするとエラーで実行できなかった。

# Linux から見た Windows ファイルシステムと Windows から見た Linux ファイルシステム

Linux のホームディレクトリは Windows から見ると

    C:\Users\Windowsのユーザー名\AppData\Local\lxss\home\Linuxのユーザー名

になるようだ。逆に Windows の ````C:\```` は Linux からは

    /mnt/c/

として認識される。

Linux から再帰的に ````/mnt/c/Users/Windowsのユーザー名/AppData/Local/lxss/home/```` にアクセスしようとするとアクセスを拒否された。実際には ````AppData/lxss/```` と Linux のルートは完全に一致しないので下手にアクセスできないほうがいいだろう。

# 日本語対応は完全でない

基本的に日本語環境だと Linux のメッセージも日本語対応になるが、一部文字がかけてしまう。 Excel で画面では表示されているのに印刷してみると一部が欠けるアレだ。要はマイクロソフトは今も昔も日本語はちゃんと表示できないということだ。

# 思わぬ効用

あまり使い途はないかなと思っていたのだが、思わぬ効用があった。コマンドプロンプトから

    bash

と入力すると、コマンドプロンプトから powershell が実行できるのと同じように bash が実行できる。 Windows で使うためにインストールしていた git, gpg, vi などの Windows 版がなくてもそのまま使えることに気がついた。 Git などは最初からインストールされているわけではないが apt で簡単にインストールできてバージョンアップも楽だ。

どうしても Windows を使わなければいけない理由がないなら最初から Linux を使えばいいのだが、業務用 PC が Windows 10 なら、 Windows 環境はそのままで bash が使える。
