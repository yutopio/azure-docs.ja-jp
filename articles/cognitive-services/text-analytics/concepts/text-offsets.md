---
title: Text Analytics API のテキスト オフセット
titleSuffix: Azure Cognitive Services
description: 多言語および絵文字エンコードに起因するオフセットについて説明します。
services: cognitive-services
author: aahill
manager: nitinme
ms.service: cognitive-services
ms.subservice: text-analytics
ms.topic: article
ms.date: 03/09/2020
ms.author: aahi
ms.reviewer: jdesousa
ms.openlocfilehash: 6e404c710a244f06676edf50c3f5c95a7d681e35
ms.sourcegitcommit: 2ec4b3d0bad7dc0071400c2a2264399e4fe34897
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/28/2020
ms.locfileid: "79218529"
---
# <a name="text-offsets-in-the-text-analytics-api-output"></a>Text Analytics API の出力でのテキスト オフセット

多言語および絵文字のサポートにより、複数の[コード ポイント](https://wikipedia.org/wiki/Code_point)を使用して書記素と呼ばれる単一の表示文字を表す Unicode エンコードに至りました。 たとえば、🌷 や 👍 のような絵文字では、複数の文字を使用して形を構成し、スキン トーンなどの視覚属性用の追加文字を使用できます。 同様に、ヒンディー語の `अनुच्छेद` は、5 つの文字と 3 つの結合記号としてエンコードされます。

多言語と絵文字のエンコードで可能な長さは異なるため、Text Analytics API の応答でオフセットが返される場合があります。

## <a name="offsets-in-the-api-response"></a>API 応答のオフセット 

[名前付きエンティティの認識](../how-tos/text-analytics-how-to-entity-linking.md)や[感情分析](../how-tos/text-analytics-how-to-sentiment-analysis.md)などの API 応答でオフセットが返されるときは、次の点に注意してください。

* 応答内の要素は、呼び出されたエンドポイントに固有のものである可能性があります。 
* HTTP POST/GET ペイロードは [UTF-8](https://www.w3schools.com/charsets/ref_html_utf8.asp) でエンコードされます。これは、クライアント側コンパイラまたはオペレーティング システムの既定の文字エンコードである場合もそうでない場合もあります。
* オフセットでは、文字の数ではなく [Unicode 8.0.0](https://unicode.org/versions/Unicode8.0.0) 標準に基づく書記素の数が参照されます。

## <a name="extracting-substrings-from-text-with-offsets"></a>オフセットを使用したテキストからの部分文字列の抽出

文字ベースの部分文字列メソッドを .NET [substring ()](https://docs.microsoft.com/dotnet/api/system.string.substring?view=netframework-4.8) メソッドなどで使用すると、オフセットによる問題が発生する可能性があります。 問題の 1 つとして、オフセットが原因で、部分文字列メソッドが複数文字の書記素エンコードの末尾ではなく途中で終了することがあります。

.NET では、[StringInfo](https://docs.microsoft.com/dotnet/api/system.globalization.stringinfo?view=netframework-4.8) クラスを使用することを検討してください。これにより、個々の文字オブジェクトではなく、一連のテキスト要素として文字列を操作できます。 任意のソフトウェア環境で、書記素スプリッター ライブラリを検索することもできます。 

Text Analytics API では、便宜上、これらのテキスト要素も返されます。

## <a name="see-also"></a>関連項目

* [Text Analytics の概要](../overview.md)
* [感情分析](../how-tos/text-analytics-how-to-sentiment-analysis.md)
* [エンティティの認識](../how-tos/text-analytics-how-to-entity-linking.md)
* [言語を検出する](../how-tos/text-analytics-how-to-keyword-extraction.md)
* [言語の認識](../how-tos/text-analytics-how-to-language-detection.md)
