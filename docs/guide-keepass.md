# KeePassでパスワードを管理する

パスワードを管理するアプリは多々あるが、オープンソースでマルチデバイス対応、作成したファイルの移動や管理が簡単という点では KeePass がおすすめだ。 KeePass 自体は Windows 用アプリだが、 Linux や Macにも移植されているし、 Android や iOS さらには Chrome 拡張機能などでも KeePass のパスワードファイルを開いたり編集したりできるアプリがある。詳しくは[公式サイト][1]の案内を見てもらうといい。

KeePass ではパスワードを保管したファイルを暗号化した単独ファイルとして保存するので、 USB メモリやクラウドストレージに保存して持ち歩くことができる。さらにパスワードの他にキーファイルがないとファイルを開けないように設定することもできるので、本体ファイルとキーファイルを別の媒体で管理すればデータを持ち歩く際の安全性が向上する。

# Classic Edition と Professional Editon

Keepass は Version 1.x から Version 2.x になった時に保存ファイルフォーマットが変わって、それぞれのバージョンに互換性がない。もちろん Version 2.x は上位互換なので古いバージョンのファイルを読み込むことができるが、新しいフォーマットに変換してしまうので変更したデータを保存してももう古いバージョで開くことはできなくなる。

通常ならアプリをバージョンアップして、データもバージョンアップしておしまいだが、マルチプラットフォームで互換アプリも多数あるので、 Version 2.x に対応していないものもまだ残っている。このため、 KeePass では Version1.x を Classic Edition として残し、 Version2.x を Professional Edition として公開している。どちらを使ってもいいが、自分が使う環境すべてに対応した方を選ばなければいけない。

# KeePassX

本家 KeePass も Linux や Macに移植されているが、マルチプラットフォーム対応で KeePass 互換アプリとしては KeePassX もある。 Mac や Windows のアプリは[公式サイト][2]からダウンロードするのだが、 Linux の場合は多くのディストリビューションで公式リポジトリに登録されているのでコマンドや GUI のアプリ管理ツールから簡単にインストールできる。

# KeePassX 0.4 と KeePassX 2.0

KeePassX も本家 KeePass の Classic Edition と Professional Edition に対応するバージョンがある。 KeePassX では Classic Edition 相当の KeePassX 0.4.x も基本的には新しい KeePassX 2.0.x にアップデートすることになるが、以前の Version 0.4.x も残っている。 Linuxで KeePassX をインストールした場合、 KeePassX 0.4 は KeePassX 2.0 で上書きされるので KeePassX 0.4 を使い続けるには注意が必要だ。

# Debian 8 で KeePassX 2.0 を利用する

Debian 8 では安定版の公式リポジトリは KeePassX 0.4 のままだ。他のプラットフォームが KeePassX 2.0 にアプデートされた場合、 sid (unstable) のファイルをインストールして KeePassX をアップデートすることができる。 [Debianのパッケージサイト][3] から対応する .deb ファイルをダウンロードして

    $ sudo gdebi ダウンロードしたファイル.deb

でインストールできる。 gdebi を使ってインストールしておけば、次からは apt で KeePassX 2.0 がアップデートの対象となる。

# Ubuntu 16.04 で KeePassX 0.4 を利用する

Ubuntu 16.04 では KeePassX 2.0 が公式リポジトリに登録されていて、 通常 KeePassX 0.4 はインストールできない。他の環境の兼ね合いで KeePassX 0.4 を使いたい場合には [Ubuntu 14.04 用パッケージ][4]をダウンロードしてインストールする。

このままでは次回アップデートの際に KeePassX 2.0 に上書きされてしまうので、これを避けるために

    $ echo "keepassx hold" | sudo dpkg --set-selections

とコマンドを実行して KeePassX のアップデートを保留するようにしておく。他のプラットフォームが KeePassX 2.0に統一されたら、

    $ echo "keepassx install" | sudo dpkg --set-selections

とコマンドを実行して KeePassX をアップデートできるようにする。

[1]: http://keepass.info/
[2]: https://www.keepassx.org/
[3]: https://packages.debian.org/sid/keepassx
[4]: http://security.ubuntu.com/ubuntu/pool/universe/k/keepassx/keepassx_0.4.3+dfsg-0.1ubuntu1.14.04.1_amd64.deb
