---
title: サーバーレス Python 関数アプリを作成する - Azure CLI
description: Azure CLI を使用してサーバーレス Python 関数アプリを作成する
ms.assetid: 0e221db6-ee2d-4e16-9bf6-a456cd05b6e7
ms.topic: sample
ms.date: 11/23/2019
ms.custom: tracking-python, devx-track-azurecli
ms.openlocfilehash: c0c94c8682cdd3c5509bca1e223e28b3bef94a28
ms.sourcegitcommit: 11e2521679415f05d3d2c4c49858940677c57900
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/31/2020
ms.locfileid: "87498261"
---
# <a name="create-a-serverless-python-function-app-using-azure-cli"></a>Azure CLI を使用してサーバーレス Python 関数アプリを作成する

この Azure Functions サンプル スクリプトでは、関数のコンテナーである関数アプリを作成します。 

>[!NOTE]
>作成された関数アプリは、Python バージョン 3.6 上で実行されます。 Python バージョン 3.7 も、Azure Functions でサポートされています。

[!INCLUDE [quickstarts-free-trial-note](../../../includes/quickstarts-free-trial-note.md)]

[!INCLUDE [cloud-shell-try-it.md](../../../includes/cloud-shell-try-it.md)]

CLI をローカルにインストールして使用する場合、この記事では、Azure CLI バージョン 2.0 以降を実行していることが要件です。 バージョンを確認するには、`az --version` を実行します。 インストールまたはアップグレードが必要な場合は、[Azure CLI のインストール]( /cli/azure/install-azure-cli)に関するページを参照してください。 

## <a name="sample-script"></a>サンプル スクリプト

このスクリプトでは、[従量課金プラン](../functions-scale.md#consumption-plan)を使用して Azure Function App が作成されます。

[!code-azurecli-interactive[main](../../../cli_scripts/azure-functions/create-function-app-consumption-python/create-function-app-consumption-python.sh "Create an Azure Function on a Consumption plan")]

[!INCLUDE [cli-script-clean-up](../../../includes/cli-script-clean-up.md)]

## <a name="script-explanation"></a>スクリプトの説明

表内の各コマンドは、それぞれのドキュメントにリンクされています。 このスクリプトでは以下のコマンドを使用します。

| command | メモ |
|---|---|
| [az group create](/cli/azure/group#az-group-create) | すべてのリソースを格納するリソース グループを作成します。 |
| [az storage account create](/cli/azure/storage/account#az-storage-account-create) | Azure Storage アカウントを作成します。 |
| [az functionapp create](/cli/azure/functionapp#az-functionapp-create) | Function App を作成します。 |

## <a name="next-steps"></a>次のステップ

Azure CLI の詳細については、[Azure CLI のドキュメント](/cli/azure)のページをご覧ください。

その他の Azure Functions CLI のサンプル スクリプトは、[Azure Functions のドキュメント](../functions-cli-samples.md)で確認できます。
