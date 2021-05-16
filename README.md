# shinra display ner

tokenのリストとIOB2タグのリストを引数に取ると、 IOB2タグの対応関係を可視化したHtmlファイルを出力します。  

spacyを利用しています。  
https://explosion.ai/demos/displacy-ent  

## 使い方
以下のようにtokenリストとIOB2タグのリストを渡すことでHtmlファイルを出力することができます。  
**※token.txtとlabel.txtはpickleで保存されていることを想定しています。**

```txt:tokens.txt
[['シャネル','は','フランス','の','企業','で','ある'], ['1909','年','パリ','17','区','マルゼルブ','大通り','（fr）','160','番地','に','女性','用','の','帽子','店','を','開業','する']]
```
```txt:labels.txt
[['B-正式名称','O','B-本拠地国','O','O','O','O'], ['B-設立年','I-設立年','B-創業地','I-創業地','I-創業地','I-創業地','I-創業地','I-創業地','I-創業地','I-創業地','O','B-創業時の事業','I-創業時の事業','I-創業時の事業','I-創業時の事業','I-創業時の事業','O','O','O']]
```
  
```
python3 shinra_display_ner [ tokensのリスト.txt のパス] \
                           [ labelsのリスト.txt のパス]
```
  

## 出力結果
![image](https://user-images.githubusercontent.com/68231213/118390720-91df0480-b66b-11eb-820e-2ba57f4e0fef.png)

## Pythonモジュールとして呼び出す
以下のようにコードをshinra_display_nerと同じ階層においてください。  
```
・shinra_display_ner/
・test.py
```

以下のようにimportすることでモジュールとして使用できます。
```
from shinra_display_ner import display_ner
```

### 使用例
以下のように使います。
```python:test.py
from shinra_display_ner import display_ner

tokens = [['シャネル','は','フランス','の','企業','で','ある'], ['1909','年','パリ','17','区','マルゼルブ','大通り','（fr）','160','番地','に','女性','用','の','帽子','店','を','開業','する']]
labels = [['B-正式名称','O','B-本拠地国','O','O','O','O'], ['B-設立年','I-設立年','B-創業地','I-創業地','I-創業地','I-創業地','I-創業地','I-創業地','I-創業地','I-創業地','O','B-創業時の事業','I-創業時の事業','I-創業時の事業','I-創業時の事業','I-創業時の事業','O','O','O']]

if __name__ == "__main__":
    display_ner(tokens, labels)

```
