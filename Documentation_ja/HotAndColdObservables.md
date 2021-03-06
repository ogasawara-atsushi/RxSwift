Hot と Cold Observables
========================

私見ですが、シーケンスのプロパティのように種類を分けないでもっと考えることを提案します。  
なぜなら`Observable`シーケンスはそれらに完全に適合する同じ抽象概念によって表現されるからです。

これはReactiveX.ioからの定義です。

> いつobservableはそのアイテムのシーケンスを放出し始めるのでしょうか？ それはObservableによります。  
  "hot" Observableは作られてすぐにアイテムを放出し始めるでしょう、  
  なので全てのobserverが後からsubscribeして、どこかのシーケンスの監視を途中で開始してもよいのです。  
  "cold" Observableは、observerがsubscribeされるまで待ってからアイテムを放出し始めます。  
  そのように、このようなobserverは最初から全てのシーケンスを見届けることが保証されています。

| Hot Observables                                                                                         | Cold observables                                                              |
|---------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------|
| シーケンスである                                                                                           | シーケンスである                                                                 |
| 任意のsubscribeしているobserverがいるかに関わらず、リソースを使用する                                            | observerがsubscribeするまで、リソースを使用しない           |
| 変数 / プロパティ / 定数, タップ座標, マウス座標, UIコントロール値, 現在時間 | 非同期操作, HTTPコネクション, TCPコネクション, ストリーム                  |
| 通常、N個の要素を含む                                                                           | 通常、1個の要素を含む                                                  |
| 任意のsubscribeしているobserverがいるかに関わらず、シーケンス要素は生産される                                     | observerがsubscribeされた場合のみ、シーケンス要素は生産される        |
| 通常、シーケンスの計算リソースはsubscribeしているobserverの間で共有される              | 通常、シーケンスの計算リソースはsubscribeしているobserver毎に確保される |
| 通常、ステートフル                                                                                       | 通常、ステートレス                                                             |
