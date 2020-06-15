# atmaCup05 solution(Public: 3rd, Private: 3rd)

* [atmaCup #5](https://atma.connpass.com/event/175139/)に参加した際のソースコードです．

## 解法の概略
* モデルはWaveNetのみ．
* SWAで学習の安定化．
* pseudo-labelingでスコアの底上げ．
* rank averagingでアンサンブル．

## ディレクトリ構成
```
atmaCup05
├── input
│    └── 配布されているデータセット
├── notebook
│    ├── ensemble.ipynb
│    ├── preprocessing.ipynb
│    ├── wavenet_psedo_labeling_fix.ipynb
│    ├── wavenet_psedo_labeling.ipynb
│    └── wavenet.ipynb
├── output
└── README.md
```

## notebook 
それぞれのnotebookの内容は以下の通りです．  
上から順番に実行していただければ問題ないと思います．  
出力ファイルを利用するのでパスを適宜変更する必要があります．  
kerasでモデルを構築しているので実行毎にスコアが変化します．  

### preprocessing.ipynb
* 内容 : スペクトルデータの前処理
* 作業環境 : local (CPU)  
* 注意事項 : なし

### wavenet.ipynb
* 内容 : 5fold WaveNet
* 作業環境 : Google Colaboratory (GPU)  
* 注意事項 : なし

### wavenet_psedo_labeling.ipynb
* 内容 : `wavenet.ipynb`の出力を基にしたpseudo-labeling
* 作業環境 : Google Colaboratory (GPU)  
* 注意事項 : wavenet.ipynbの出力を用いるのでファイル名を適宜変更してください．

### ensemble.ipynb
* 内容 : `wavenet.ipynb`と`wavenet_psedo_labeling.ipynb`の出力を同じ重みでrank averaging
* 作業環境 : local(CPU)  
* 注意事項 : `wavenet.ipynb`と`wavenet_psedo_labeling.ipynb`の出力を用いるのでファイル名を適宜変更してください．

### wavenet_psedo_labeling_fix.ipynb (コンペ終了後に追加)
* 内容 : `wavenet_psedo_labeling.ipynb`のpsedo-labelingに誤りがあったので修正しました．
* 作業環境 : Google Colaboratory (GPU)  
* 注意事項 : `wavenet.ipynb`の出力を用いるのでファイル名を適宜変更してください．