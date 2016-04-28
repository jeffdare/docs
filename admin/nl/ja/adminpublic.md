---

 

copyright:

  years: 2015, 2016

 

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}

# 管理: 
{: #administer}
*最終更新日: 2016 年 2 月 29 日*

**「アカウントとサポート」**アイコン ![アカウントとサポート](../support/images/account_support.svg) をクリックし、次に**「組織の管理」**を選択して、組織、スペース、割り当てられたユーザーを管理します。 {{site.data.keyword.Bluemix_notm}} Local または {{site.data.keyword.Bluemix_notm}} Dedicated のユーザーの場合、[「{{site.data.keyword.Bluemix_notm}} Local および {{site.data.keyword.Bluemix_notm}} Dedicated の管理」](../admin/index.html#mng) を参照して、ローカルや専用インスタンスの管理情報を入手してください。
{:shortdesc}

## {{site.data.keyword.Bluemix_notm}} Public の管理 
{: #mngacct}

{{site.data.keyword.Bluemix}} Public では、ユーザーのアクセス権限を含め、組織およびスペースを、すべてユーザー・インターフェースのダッシュボードから管理できます。また、使用量と請求をモニターすることもできます。
{:shortdesc}

### 組織およびスペース
{: #orgsandspaces}

組織管理者またはアカウント所有者は、「組織の管理」ページを使用して、ユーザーのアクセス権限など、組織またはスペースの設定を表示および管理することができます。「組織の管理」ページを開くには、**「アカウントとサポート」** アイコン ![アカウントとサポート](../support/images/account_support.svg) をクリックし、次に**「組織の管理」**を選択します。

#### 組織

組織は以下の項目によって定義されます。


<dl>
<dt>users</dt>
<dd>組織とスペースの基本的なアクセス権限を付与された役割です。
組織内のスペースに対するその他のアクセス権を付与されるためには、
ユーザーは組織に割り当てられる必要があります。詳しくは、『[ユーザーと役割 (Users
and roles)](adminpublic.html#userroles)』を参照してください。</dd>
<dt>ドメイン</dt>
<dd>組織に割り振られるインターネットへの経路を提供します。
経路にはサブドメインとドメインがあります。サブドメインは通常アプリケーション名です。
ドメインは、システム・ドメインであるか、または、アプリケーション用に登録したカスタム・ドメインである場合があります。<br/>
<p>**注**: カスタム・ドメインを追加する場合、そのカスタム・ドメインが {{site.data.keyword.Bluemix_notm}} システム・ドメインを指すように解決されるよう、DNS サーバーを構成する必要があります。この方法では、{{site.data.keyword.Bluemix_notm}}
はカスタム・ドメインの要求を受け取ると、ご使用のアプリケーションに適切に経路指定することができます。
</p></dd>
<dt>割り当て量</dt>
<dd>組織による使用に割り振ることが可能なサービス数およびメモリー容量を含む、組織のリソース限度を示します。割り当て量は、組織の作成時に割り当てられます。組織のスペースにおけるアプリケーションまたはサービスはすべて、
割り当て量の使用に寄与します。従量課金 (PAYG) プランまたはサブスクリプション・プランの場合、組織変更による必要に応じて、Cloud Foundry のアプリケーションおよびコンテナーの割り当て量を調整できます。</dd>
</dl>

{{site.data.keyword.Bluemix_notm}} では、
組織を使用してユーザー間のコラボレーションを可能にし、以下の方法で
プロジェクト・リソースの論理的なグループ化を容易にすることができます。

<ul>
<li>スペース、アプリケーション、サービス、ドメイン、経路、およびユーザーのセットを一緒にして
組織内でグループ化できます。</li>
<li>スペースおよび組織へのアクセス権限を、ユーザー・ベースで管理することができます。</li>
</ul>

組織を作成する際は、
組織名は {{site.data.keyword.Bluemix_notm}} で固有にする必要があります。
組織を作成したユーザーには、自動的に*組織管理者*権限が割り当てられ、組織名の編集、組織の削除、組織内のスペースの作成が可能になります。

組織を削除すると、組織内のすべてのスペース、アプリケーション、およびサービスが削除されます。


{{site.data.keyword.Bluemix_notm}}
は、組織内および組織のスペース内にユーザーを割り当てることで、プロジェクト間のコラボレーションを
可能にします。**「ユーザー」**タブを使用して、組織のユーザーを表示および管理できます。
**「ユーザー」**タブの**「新規ユーザーの招待」**リンクをクリックすることによって、組織にユーザーを招待することもできます。以下の権限を組織内のユーザーに割り当てることができます。


<ul>
<li>組織ユーザー</li>
<li>組織管理者</li>
<li>組織請求管理者</li>
<li>組織監査員</li>
</ul>

#### スペース

組織内でスペースを使用して、
アプリケーション、サービス、およびユーザーのセットをグループ化することができます。


ユーザーを組織に追加した後、そのユーザーに組織内のスペースへのアクセス権を付与することができます。
組織と同様に、スペースにもユーザーに割り当てることができるアクセス権のセットがあります。


<ul>
<li>スペース管理者</li>
<li>スペース開発者</li>
<li>スペース監査員</li>
</ul>

**注**: ユーザーには、スペース内で少なくとも 1 つのアクセス権が割り当てられていなければなりません。

スペースの**「ドメイン」**タブは、
スペースに割り当てられたドメインの読み取り専用リストです。
システム・ドメインはスペースで常に使用可能で、カスタム・ドメインもまたスペースに割り振ることができます。
スペースで作成されたアプリケーションは、
リストされたスペース用のドメインのいずれかを使用することができます。

### ユーザーと役割
{: #userroles}

アカウント所有者は、組織およびスペースですべての操作を実行します。


####ユーザーのタイプ

ユーザーはアカウントのメンバーまたはコラボレーターになることができます。

<dl>
<dt>メンバー</dt>
<dd>ユーザーが自分で {{site.data.keyword.Bluemix_notm}} アカウントを作成した場合、またはアカウントへの招待を受けて、{{site.data.keyword.Bluemix_notm}} での最初の体験としてその招待から登録した場合、そのユーザーはそのアカウントのメンバーです。</dd>
<dt>コラボレーター</dt>
<dd>ユーザーが以前に別のアカウントで {{site.data.keyword.Bluemix_notm}} を使用したことがあり、その後このアカウントに招待されてそれを受け入れた場合、そのユーザーは {{site.data.keyword.Bluemix_notm}} アカウントのコラボレーターです。</dd>
</dl>

#### ユーザー役割

ユーザーは、以下のアクセス権を割り当てられ、組織またはスペースにおいてさまざまなユーザー役割を担うことができます。

<dl>
<dt>組織管理者</dt>
<dd>組織管理者は以下のアクセス権限を所有します。<ul>
<li>組織内のスペースの作成、削除。</li>
<li>そのユーザーが組織のメンバーまたはアカウント所有者でもある場合、組織にユーザーを招待します。</li>
<li>既に組織内に存在する既存ユーザーを管理します。</li>
<li>組織のドメインの管理。</li>
</ul>
<p>**注**: ユーザー・タイプがコラボレーターであり、以前に別のアカウントで {{site.data.keyword.Bluemix_notm}} を使用したことがあるユーザーは、組織管理者役割が割り当てられていても、組織にユーザーを招待することはできません。ユーザーを招待するには、ユーザー・タイプがメンバーでなければなりません。この問題に対処する方法については、『<a href="../troubleshoot/index.html#ts_adduser">ユーザーを組織に追加できない</a>』を参照してください。</p>
</dd>
<dt>請求管理者</dt>
<dd>請求管理者は、組織のランタイム情報およびサービス使用量情報を表示するアクセス権限を所有します。</dd>
<dt>組織監査員</dt>
<dd>組織監査員は、スペースのアプリケーションおよびサービス・コンテンツを表示するアクセス権限を所有します。</dd>
<dt>スペース管理者</dt>
<dd>スペース管理者は以下のアクセス権限を所有します。<ul>
<li>ユーザーをスペースに追加して、ユーザーを管理します。</li>
<li>スペースに対してフィーチャーを使用可能にします。</li>
</ul>
</dd>
<dt>スペース開発者</dt>
<dd>スペース開発者は以下のアクセス権限を所有します。<ul>
<li>スペース内でアプリケーションおよびサービスを作成、削除、および管理します。
</li>
<li>スペース内でログへのアクセス権限を所有します。</li>
</ul>
</dd>
<dt>スペース監査員</dt>
<dd>スペース監査員は、アプリケーションおよびサービス、設定、レポート、ログの各情報など、
スペースに関するすべての情報に対して読み取り専用アクセス権限を所有します。</dd>
</dl>

**注**: 管理者または開発者の役割を割り当てられたユーザーは、VCAP_SERVICES 環境変数にアクセスできます。しかし、監査員の役割を割り当てられたユーザーは、VCAP_SERVICES にアクセスできません。 

### 組織の管理
{: #orgmng}

組織管理者またはアカウント所有者は、自身の組織を管理することができます。管理タスクには、組織の作成、組織の名前変更、スペースの作成、スペースへのユーザーの招待、ユーザーの役割の変更、および既存の組織の削除が含まれます。

#### 組織の作成

支払アカウントを保有するユーザーのみが組織を作成することができます。支払アカウントを保有している場合は、以下の手順を実行して組織を作成できます。

<ol>
<li>{{site.data.keyword.Bluemix_notm}} ダッシュボードに移動し、**「アカウントとサポート」** アイコン ![アカウントとサポート](../support/images/account_support.svg) をクリックし、次に**「組織の管理」**を選択します。</li>
<li>**「組織の作成」**をクリックし、プロンプトに従って組織を作成します。</li>
</ol>

#### 組織の名前変更

組織を名前変更するには、以下の手順を実行します。

<ol>
<li>{{site.data.keyword.Bluemix_notm}} ダッシュボードに移動し、**「アカウントとサポート」**アイコン ![アカウントとサポート](images/account_support.svg) をクリックし、**「組織の管理」**を選択します。</li>
<li>名前変更する組織を選択します。</li>
<li>**「組織」**フィールドに新しい名前を入力し、**「保存」**をクリックします。</li>
</ol>

#### メンバーのリスト 

組織またはスペースのメンバーをリストするには、以下の手順を実行します。


<ol>
<li>{{site.data.keyword.Bluemix_notm}} ダッシュボードに移動し、**「アカウントとサポート」** アイコン ![アカウントとサポート](../support/images/account_support.svg) をクリックし、次に**「組織の管理」**を選択します。**「ユーザー」**タブで組織のメンバーとメンバーの役割を確認できます。
</li>
<li>組織内のスペース名をクリックして、このスペースのメンバーとメンバーの役割を確認します。
</li>
</ol>

#### スペースの作成

組織内にスペースを作成できます。例えば、開発環境として *dev* スペース、テスト環境として *test* スペース、実稼働環境として *production* スペースを作成できます。その後、アプリをスペースに関連付けることができます。スペースを作成するには、以下の手順を実行します。

<ol>
<li>{{site.data.keyword.Bluemix_notm}} ダッシュボードに移動し、**「アカウントとサポート」** アイコン ![アカウントとサポート](images/account_support.svg) をクリックし、次に**「組織の管理」**を選択します。</li>
<li>ユーザーの組織名の後の**「スペースの作成」**をクリックし、プロンプトに従ってスペースを作成します。</li>
</ol>

#### スペースへのユーザーの招待

E メール・アドレスによってユーザーを組織およびスペースに招待できます。ユーザーは、自身が追加されたスペースにのみアクセスできます。 

招待されたユーザーが IBM ID を持っているかどうかに応じて、そのユーザーには、アカウントの `member` の役割または `collaborator` の役割が割り当てられます。次の表に、招待のタイプによるアカウントの役割の割り当て方法の詳細を示します。

*表 1. アカウントの役割の割り当て*

| **招待された E メールのタイプ** | **割り当てられるアカウントの役割** | 
|----------------|------------------|
|ユーザーは招待された E メール・アドレスにリンクされた IBM ID アカウントを持っている  | メンバー  | 
|ユーザーは IBM ID を持っていない | 送信された E メール・アドレスに一致する IBM ID が作成され、ユーザーはメンバーとして追加される | 
|現在の {{site.data.keyword.Bluemix_notm}} ユーザーの E メール・アドレス | コラボレーター | 

割り当てられた役割を持つユーザーを、選択した組織の特定のスペースに追加するには、以下の手順を実行します。

<ol>
<li>**「アカウントとサポート」** &gt; **「アカウント」** &gt; **「組織の管理」**に移動します。</li>
<li>**「ユーザーの招待」**を選択します。</li>
<li>招待するユーザーの E メール・アドレスを入力します。</li>
<li>新規ユーザーを招待する予定の組織の役割を選択します。</li>
<li>新規ユーザーを招待する予定のスペースの役割を選択します。</li>
<li>**「招待」**を選択します。</li>
<li>招待が**「保留中」**セクションに送信されたことの確認が表示されます。保留中の招待に対してアクションを実行するには、**「E メールの再送」**または**「招待のキャンセル」**を選択します。</li>
</ol>

#### ユーザーの役割の変更


ユーザーの役割を変更するには、以下の手順を実行します。

<ol>
<li>{{site.data.keyword.Bluemix_notm}} ユーザー・インターフェースから**「アカウントとサポート」** アイコン ![アカウントとサポート](images/account_support.svg) をクリックし、次に**「組織の管理」**を選択します。</li>
<li>**「ユーザー」**タブで**「管理者」**、**「請求管理者」**、または**「監査員」**のチェック・ボックスを選択して、組織内のユーザーの役割を変更します。あるいは、ナビゲーション・ペインからスペースを選択し、次に**「ユーザー」**タブで**「管理者」**、**「開発者」**、または**「監査員」**のチェック・ボックスを選択して、スペース内のユーザーの役割を変更します。</li>
<li>**「保存」**をクリックします。</li>
</ol>

#### 既存の組織の削除

組織を削除するには、{{site.data.keyword.Bluemix_notm}} の登録および ID サポートに連絡します。

**注**: 削除操作は元に戻せません。組織を削除すると、その組織に関連付けられたすべてのアプリケーションとサービスが失われます。
