ssff
====

![Software Version](http://img.shields.io/badge/Version-v0.2.0-green.svg?style=flat)
![Python Version](http://img.shields.io/badge/Python-3.10-blue.svg?style=flat)
[![MIT License](http://img.shields.io/badge/license-MIT-blue.svg?style=flat)](LICENSE)

[English page](./README.md)  

## 概要
スクリーンショットとページ送りを行う Windows 専用のツール。Windows 専用。  
例 ) PDF, EPUB などのファイルを画像ファイルに変換する。  

## 要件
- Python3.10
    - PyAutoGui
    - PIL
    - pywin32

## 使用方法
1. `setting.json` を用意する。
2. `ssff.exe` または `python3 ssff.py` を実行する。
3. コンソール上で不足しているパラメータを入力する。
4. 終了するまで PC を触らずに待つ。

# オプション
オプションの値は設定ファイルで事前に準備することができる。 (`setting.json`).  
設定ファイルで与えられなかった値はコンソールで入力する。  

## setting.json
`setting.json` というファイル名でカレントディレクトリに用意する。    
UTF-8 エンコードの JSON 形式のファイルとする。  

サンプル :  

```json
{
    "wait_before_start_ms": 5000,
    "interval_ms": 750,
    "output_dir_prefix": "output_",
    "fname_prefix": "page_",
    "trim": "fit-onetime"
}
```


## `page_num`
ページ数または "auto"。（整数または文字列）  

この値はプログラムの終了条件となる。  
"auto" にすると、連続した同じページを見つけたときに自動的に終了する。  

## `page_direction`
ページ方向。（文字列）  

"right" ("r") または "left" ("l") 。  

## `wait_before_start_ms`
実行開始する前の待機時間 (ms) 。（整数）

## `interval_ms`
実行間隔 (ms) 。（整数）  

## `output_dir_prefix`
出力ディレクトリの接頭辞。（文字列）   

ディレクトリはカレントディレクトリに作られる。  

## `fname_prefix`
画像ファイル名の接頭辞。（文字列）  

画像ファイル名は接頭辞 + 連番となる。  

## `ss_left`, `ss_right`, `ss_top`, `ss_bottom`
スクリーンショット範囲の座標値、または "max" 。（整数または文字列）  

"max" にすると、ディスプレイサイズが使用される。  

![](./README/ss_left.png)
![](./README/ss_right.png)
![](./README/ss_top.png)
![](./README/ss_bottom.png)
![](./README/ss_area.png)

## `trim`
トリミング位置。（文字列）  

### "none" または "n".
トリミングを行わない。  

### "fit" or "f".
全てのページにスクリーンショットから、自動的に余白部分（同じ色が連続した部分）を除去する。  

![](./README/fit.png)

### "fit-onetime" or "o".
全てのページにスクリーンショットから、自動的に余白部分（同じ色が連続した部分）を除去する。先頭のページ（表紙）で算出されたトリミングサイズが全てのページに使用される。  

## `vsplit`
画像が横長の場合に垂直分割する。（文字列）  

"yes" または "no" 。    

## `target_window`
対象とするウィンドウのタイトル。（文字列）  

この値を設定すると、指定された文字列をタイトルに持つウィンドウを自動的に最前面化する。  
部分文字列でも可。  

## TODO
- [x] トリミングサイズの自動化。
- [x] 終了条件の自動化。
- [x] ページの垂直分割。
- [x] exe ファイル化。(PyInstaller を使用)