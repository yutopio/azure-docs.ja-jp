---
title: ストレージの自動拡張 - Azure CLI - Azure Database for MySQL
description: この記事では、Azure CLI を使用して Azure Database for MySQL のストレージの自動拡張を有効にする方法について説明します。
author: ambhatna
ms.author: ambhatna
ms.service: mysql
ms.topic: how-to
ms.date: 3/18/2020
ms.openlocfilehash: fd7b9a809421aa33b83902960da2f02d4deabf9a
ms.sourcegitcommit: d7008edadc9993df960817ad4c5521efa69ffa9f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/08/2020
ms.locfileid: "86113264"
---
# <a name="auto-grow-azure-database-for-mysql-storage-using-the-azure-cli"></a>Azure CLI を使用した Azure Database for MySQL ストレージの自動拡張
この記事では、Azure Database for MySQL サーバーのストレージを、ワークロードに影響を与えることなく拡張されるように構成する方法について説明します。

[ストレージの上限に到達](https://docs.microsoft.com/azure/mysql/concepts-pricing-tiers#reaching-the-storage-limit)したサーバーは、読み取り専用に設定されます。 プロビジョニングされたストレージが 100 GB 未満のサーバーに対してストレージの自動拡張が有効にされている場合、空きストレージがプロビジョニングされたストレージの 1 GB または 10% のどちらか大きい方を下回ると、プロビジョニングされたストレージ サイズが 5 GB 単位ですぐに拡張されます。 プロビジョニングされたストレージが 100 GB を超えるサーバーの場合、空きストレージ領域がプロビジョニングされたストレージ サイズの 5% を下回ると、プロビジョニングされたストレージ サイズが 5% 単位で増加します。 [こちら](https://docs.microsoft.com/azure/mysql/concepts-pricing-tiers#storage)で指定されているストレージの上限が適用されます。

## <a name="prerequisites"></a>前提条件
このハウツー ガイドを完了するには、次が必要です。
- [Azure Database for MySQL サーバー](quickstart-create-mysql-server-database-using-azure-cli.md)

[!INCLUDE [cloud-shell-try-it.md](../../includes/cloud-shell-try-it.md)]

> [!IMPORTANT]
> このガイドで説明する方法では、Azure CLI バージョン 2.0 以降を使う必要があります。 バージョンを確認するには、Azure CLI コマンド プロンプトで「`az --version`」と入力します。 インストールまたはアップグレードする必要には、「[Azure CLI のインストール]( /cli/azure/install-azure-cli)」をご覧ください。

## <a name="enable-mysql-server-storage-auto-grow"></a>MySQL サーバー ストレージの自動拡張を有効にする

次のコマンドを使用すると、既存のサーバー上でサーバーの自動拡張ストレージが有効にされます。

```azurecli-interactive
az mysql server update --name mydemoserver --resource-group myresourcegroup --auto-grow Enabled
```

次のコマンドを使用して、新しいサーバーの作成時にサーバーの自動拡張ストレージを有効にします。

```azurecli-interactive
az mysql server create --resource-group myresourcegroup --name mydemoserver  --auto-grow Enabled --location westus --admin-user myadmin --admin-password <server_admin_password> --sku-name GP_Gen5_2 --version 5.7
```

## <a name="next-steps"></a>次のステップ

[メトリックに関するアラートを作成する方法](howto-alert-on-metric.md)について学習します。