---
title: B2B 外部コラボレーションの設定を有効にする - Azure AD
description: Active Directory の B2B 外部コラボレーションを有効にして、ゲスト ユーザーを招待できるユーザーを管理する方法について説明します。 ゲスト招待元ロールを使用して、招待を委任します。
services: active-directory
ms.service: active-directory
ms.subservice: B2B
ms.topic: how-to
ms.date: 05/11/2020
ms.author: mimart
author: msmimart
manager: celestedg
ms.reviewer: mal
ms.collection: M365-identity-device-management
ms.openlocfilehash: c6a2c1a9b908503ee5afc2687ebef473ffed626a
ms.sourcegitcommit: 877491bd46921c11dd478bd25fc718ceee2dcc08
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2020
ms.locfileid: "85387183"
---
# <a name="enable-b2b-external-collaboration-and-manage-who-can-invite-guests"></a>B2B 外部コラボレーションを有効にしてゲストを招待できるユーザーを管理する

この記事では、Azure Active Directory (Azure AD) の B2B コラボレーションを有効にして、ゲストを招待できるユーザーを決定する方法について説明します。 既定では、管理者ロールに割り当てられていなくても、ディレクトリ内のすべてのユーザーとゲストがゲストを招待できます。 外部コラボレーションの設定を使用することで、組織内のユーザーの種類ごとに、ゲストの招待を有効にしたり無効にしたりすることができます。 また、ゲストの招待を許可するロールを割り当てることによって、個々のユーザーに招待を委任することもできます。

## <a name="configure-b2b-external-collaboration-settings"></a>B2B 外部コラボレーションの設定を構成する

Azure AD B2B コラボレーションでは、テナント管理者が次の招待ポリシーを設定できます。

- 招待を無効にする
- 管理者と、ゲストの招待元ロールのユーザーのみが招待できる
- 管理者、ゲストの招待元ロール、およびメンバーが招待できる
- ゲストを含むすべてのユーザーが招待できる

既定では、ゲストを含むすべてのユーザーが、ゲスト ユーザーを招待できます。

### <a name="to-configure-external-collaboration-settings"></a>外部コラボレーションの設定を構成するには、次のようにします。

1. テナント管理者として [Azure portal](https://portal.azure.com) にサインインします。
2. **[Azure Active Directory]** を選択します。
3. **[外部 ID]**  >  **[外部コラボレーションの設定]** を選択します。
6. **[外部コラボレーションの設定]** ページで、有効にするポリシーを選択します。

   ![外部コラボレーションの設定](./media/delegate-invitations/control-who-to-invite.png)

  - **[ゲストのアクセス許可を制限する]** : このポリシーによって、ディレクトリ内のゲストのアクセス許可を決定します。 **[はい]** を選択すると、ゲストは、特定のディレクトリ タスク (ユーザー、グループ、またはその他のディレクトリ リソースを列挙するなど) を実行できなくなります。 **[いいえ]** を選択すると、ゲストには、ディレクトリ データに対して、ディレクトリ内の通常のユーザーと同じアクセス権が付与されます。
   - **[管理者とゲスト招待元ロールのユーザーは招待ができる]** : 管理者と "ゲスト招待元" ロールのユーザーがゲストを招待できるようにするには、このポリシーを **[はい]** に設定します。
   - **[メンバーは招待ができる]** : ディレクトリ内の管理者以外のメンバーがゲストを招待できるようにするには、このポリシーを **[はい]** に設定します。
   - **[ゲストは招待ができる]** : ゲストが他のゲストを招待できるようにするには、このポリシーを **[はい]** に設定します。
   - **[ゲストの電子メール ワンタイム パスコードを有効にする (プレビュー)]** : ワンタイム パスコード機能の詳細については、「[電子メール ワンタイム パスコード認証 (プレビュー)](one-time-passcode.md)」を参照してください。
   - **[コラボレーションの制限]** : 特定ドメインへの招待の許可またはブロックの詳細については、「[B2B ユーザーに対する特定組織からの招待を許可またはブロックする](allow-deny-list.md)」を参照してください。
   
   > [!NOTE]
   > **[メンバーは招待ができる]** が **[いいえ]** に設定され、 **[管理者とゲスト招待元ロールのユーザーは招待ができる]** が **[はい]** に設定されている場合、**ゲスト招待元**ロールのユーザーは引き続きゲストを招待できます。

## <a name="assign-the-guest-inviter-role-to-a-user"></a>ゲスト招待元ロールをユーザーに割り当てる

ゲスト招待元ロールを使用すると、個々のユーザーにグローバル管理者ロールなどの管理者ロールを割り当てなくても、ゲストを招待する機能を付与できます。 ゲスト招待元ロールを個々のユーザーに割り当てます。 次に、 **[管理者とゲスト招待元ロールのユーザーは招待ができる]** が **[はい]** に設定されていることを確認します。

次の例は、PowerShell を使って、ゲストの招待元ロールにユーザーを追加する方法を示しています。

```
Add-MsolRoleMember -RoleObjectId 95e79109-95c0-4d8e-aee3-d01accf2d47b -RoleMemberEmailAddress <RoleMemberEmailAddress>
```

## <a name="next-steps"></a>次のステップ

Azure AD B2B コラボレーションに関する以下の記事を参照してください。

- [Azure AD B2B コラボレーションとは](what-is-b2b.md)
- [招待を使用せずに B2B コラボレーション ゲスト ユーザーを追加する](add-user-without-invite.md)
- [B2B コラボレーション ユーザーのロールへの追加](add-guest-to-role.md)

