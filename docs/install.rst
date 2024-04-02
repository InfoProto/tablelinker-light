.. _install:

インストール手順
================

.. note::

    他の Python パッケージと同様に、 Tablelinker-light は
    多くの依存パッケージをインストールします。システムの
    Python 環境を汚さないように
    `pyenv <https://github.com/pyenv/pyenv>`_,
    `venv <https://docs.python.org/ja/3/library/venv.html>`_
    などで仮想環境を作成し、その中にインストールすることをお勧めします。

Tablelinker-light のインストール
--------------------------------

Tablelinker-light は pip コマンドでインストールできます。 ::

    pip3 install tablelinker-light

ただし、 Python のバージョンが 3.7 以上である必要があります。

Windows の場合
^^^^^^^^^^^^^^

Microsoft Store から Python 3.10 をインストールし、
PowerShell を開いて上記の pip コマンドを利用すれば
Tablelinker をインストールできます。

.. code-block:: powershell

    > pip install tablelinker-light

複数の Python バージョンをインストールしている場合、
Python launcher ``py.exe`` を実行して `利用するバージョンを指定する
<https://docs.python.org/ja/3/using/windows.html#from-the-command-line>`_ 
必要があります。

.. code-block:: powershell

    > py --list
    Installed Pythons found by C:\WINDOWS\py.exe Launcher for Windows
     -3.9-64 *
     -3.10-64
    > py -3.10 -m pip install tablelinker-light

インストール中に、以下のような警告が表示されます。 ::

    ...
    Installing collected packages: tablelinker
      WARNING: The script tablelinker.exe is installed in 'C:\Users\foo\AppData\Local\Packages\PythonSoftwareFoundation.Python.3.10_qbz5n2kfra8p0\LocalCache\local-packages\Python310\Scripts' which is not on PATH.
      Consider adding this directory to PATH or, if you prefer to suppress this warning, use --no-warn-script-location.
    Successfully installed tablelinker-1.0.0

``tablelinker.exe`` は :ref:`as_command` で説明するコマンドです。
このコマンドを利用したい場合は、警告の `... is installed in` の後ろに
表示されているディレクトリを環境変数 ``PATH`` に追加してください。

上の例では ``C:\Users\foo\AppData\Local\Packages\PythonSoftwareFoundation.Python.3.10_qbz5n2kfra8p0\LocalCache\local-packages\Python310\Scripts`` となっていますが、実行中の Python
環境によって異なりますので、必ず表示されているメッセージに合わせてください。

環境変数 ``PATH`` にディレクトリを追加するには、
コントロールパネルのシステム設定を利用するなどいろいろな方法があります。
ウェブ検索するなどして、やりやすい方法を利用してください。

コマンドラインでの操作に慣れている場合は、
PowerShell から以下の方法で追加できます。

.. code-block:: powershell

    > # 現在の Path の値を表示して、最後が ; で終わっているかどうか確認する
    > $Env:Path
    > # ; で終わっている場合は
    > $Env:Path += "C:\Users\foo\AppData\Local\Packages\PythonSoftwareFoundation.Python.3.10_qbz5n2kfra8p0\LocalCache\local-packages\Python310\Scripts"
    > # ; で終わっていない場合は
    > $Env:Path += ";C:\Users\foo\AppData\Local\Packages\PythonSoftwareFoundation.Python.3.10_qbz5n2kfra8p0\LocalCache\local-packages\Python310\Scripts"


Linux, MacOSX の場合
^^^^^^^^^^^^^^^^^^^^

Python3 と pip3 をインストールして、ターミナル上で上記の pip3 コマンドを
利用すれば Tablelinker-light をインストールできます。

.. code-block:: bash

    (Ubuntu の場合)
    $ sudo apt install python3 python3-pip
    $ pip3 install tablelinker-light


住所辞書データのインストール
----------------------------

住所ジオコーディング機能が必要なコンバータを利用するには、
別途住所辞書データをダウンロード・インストールする必要があります。
住所ジオコーディング機能を利用しない場合は住所辞書データは不要です。

住所辞書データは `こちらからダウンロード <https://www.info-proto.com/static/jageocoder/latest/>`_ してください。
また、ダウンロードしたファイルを次の手順でインストールしてください。 ::
    
    (jukyo_all_v21.zip をダウンロードした場合)
    $ jageocoder install-dictionary jukyo_all_v21.zip

詳細は `jageocoderのインストール手順 <https://jageocoder.readthedocs.io/ja/latest/install.html#install-dictionary>`_ を参照してください。


アンインストール手順
--------------------

住所辞書データをインストールした場合、 Tablelinker パッケージを
アンインストールする前に辞書をアンインストールしてください。 ::

    $ jageocoder uninstall-dictionary

Tablelinker パッケージは pip uninstall でアンインストールできます。 ::

    pip uninstall tablelinker-light

Windows の場合
^^^^^^^^^^^^^^

複数の Python バージョンをインストールしている場合、
Python launcher ``py.exe`` を実行して、
Tablelinker をインストールした Python バージョンを指定する
必要があります。

.. code-block:: powershell

    > py -3.10 -m pip uninstall tablelinker-light
