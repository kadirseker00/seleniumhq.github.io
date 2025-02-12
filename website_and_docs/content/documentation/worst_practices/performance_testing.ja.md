---
title: "パフォーマンステスト"
linkTitle: "パフォーマンステスト"
weight: 6
aliases: ["/documentation/ja/worst_practices/performance_testing/"]
---


通常、SeleniumとWebDriverを使用したパフォーマンステストはお勧めしません。
それができないからではなく、ジョブに最適化されておらず、良い結果が得られないからです。

ユーザーのコンテキストでパフォーマンステストを行うのが理想的なように思えるかもしれませんが、WebDriverテストスイートは、外部および内部の脆弱性の多くのポイントにさらされます。
たとえば、ブラウザの起動速度、HTTPサーバーの速度、JavaScriptまたはCSSをホストするサードパーティサーバーの応答、およびWebDriver実装自体の計測ペナルティ。 これらのポイントが変わることで、結果が変わります。 Webサイトのパフォーマンスと外部リソースのパフォーマンスの違いを区別することは困難です。また、ブラウザでWebDriverを使用すること、特にスクリプトを挿入する場合のパフォーマンスの低下を把握することも困難です。

他の潜在的な魅力は "時間の節約" です。
機能テストとパフォーマンステストを同時に実行します。
ただし、機能テストとパフォーマンステストには反対の目的があります。
機能をテストするために、テスターは忍耐強くロードを待つ必要があるかもしれませんが、これはパフォーマンステスト結果を曖昧にし、その逆もまた同様です。

Webサイトのパフォーマンスを改善するには、改善すべき点を知るために、環境の違いに関係なく全体的なパフォーマンスを分析し、貧弱なコードプラクティス、個々のリソース（例えば、CSSまたはJavaScript）のパフォーマンスの内訳を特定できる必要があります。
このジョブを実行できるパフォーマンステストツールが既にあり、それらは改善を提案できるレポートと分析を提供します。

使用する（オープンソース）パッケージの例は次のとおりです。: [JMeter](//jmeter.apache.org/)
