# prepare

## Description

* Ansibleのcopy,file,templateモジュールではselinuxが無効であるか、libselinux-pythonがインストールされていることが前提となる。
* Selinuxが有効の場合:
  yumが利用できる環境であればlibseliux-pythonをインストールします。
  yumが利用できる環境じゃない場合、異常終了します。
* Selinuxが無効の場合:
  処理を継続します。
