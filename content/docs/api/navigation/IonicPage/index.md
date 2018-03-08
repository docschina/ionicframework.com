---
layout: "fluid/docs_base"
version: "3.9.2"
versionHref: "/docs"
path: ""
category: api
id: "ionicpage"
title: "IonicPage"
header_sub_title: "Ionic API Documentation"
doc: "IonicPage"
docType: "function"

---









<h1 class="api-title">
<a class="anchor" name="ionic-page" href="#ionic-page"></a>

IonicPage





</h1>

<a class="improve-v2-docs" href="http://github.com/ionic-team/ionic/edit/master/src/navigation/ionic-page.ts#L9">
改进这篇文档
</a>






<p>Ionic 页面处理基于 URL 的注册和显示特定页面。它在 <code>NavController</code> 下面使用，所以它不会直接与之交互。当使用 <code>NavController</code> 推入新页面时，URL 会更新以匹配此页面的路径。</p>
<p>与传统的网络应用程序不同，URL 不指定 Ionic 应用程序中的导航。相反，URL 可以帮助我们链接到特定的内容作为面包屑（breadcrumb）。当前的 URL 在我们导航时更新，但我们使用 <code>NavController</code> 推入和弹出页面，或者用 <code>NavPush</code> 和 <code>NavPop</code> 来移动页面。这使得处理复杂的嵌套导航变得更容易。</p>
<p>我们将我们的 URL 系统称为深层链接（deep link ）系统，而不是路由，以鼓励 Ionic 开发人员将 URL 视为面包屑而不是导航的真实来源。这鼓励设计灵活的导航和全球各地的巧妙应用。</p>













<!-- @usage tag -->

<h2><a class="anchor" name="usage" href="#usage">用法</a></h2>

<p>设置 deep links 的第一步是添加页面，该页面应该是页面模块的 <code>IonicPageModule.forChild</code> 导入中的 deep link 。举个例子，这将会是 <code>MyPage</code>：</p>


<pre><code class="lang-ts">@NgModule({
  declarations: [
    MyPage
  ],
  imports: [
    IonicPageModule.forChild(MyPage)
  ],
  entryComponents: [
    MyPage
  ]
})
export class MyPageModule {}
</code></pre>
<p>然后，将 <code>@IonicPage</code> 装饰器添加到组件。最简单的用法是添加一个空的装饰器：</p>

<pre><code class="lang-ts">@IonicPage()
@Component({
  templateUrl: &#39;main.html&#39;
})
export class MyPage {}
</code></pre>
<p>这将自动创建一个到 <code>MyPage</code> 组件的链接，使用与该类相同的名称，<code>name</code>： <code>&#39;MyPage&#39;</code>。现在可以使用该名称导航页面。例如：</p>

<pre><code class="lang-ts">@Component({
  templateUrl: &#39;another-page.html&#39;
})
export class AnotherPage {
  constructor(public navCtrl: NavController) {}

  goToMyPage() {
    // 前往 MyPage 组件
    this.navCtrl.push(&#39;MyPage&#39;);
  }
}
</code></pre>
<p> <code>@IonicPage</code> 装饰器接受 <code>DeepLinkMetadataType</code> 对象。该对象接受以下属性：<code>name</code>, <code>segment</code>, <code>defaultHistory</code>, 和 <code>priority</code>。它们都是可选的，但可用于创建复杂的导航链接。</p>
<h3 id="changing-name">更改名称</h3>
<p>如前所述，如果没有提供 <code>name</code> 属性，它将被设置为类名称。更改链接的名称非常简单。要更改用于链接到组件的名称，只需在装饰器中传递它即可：</p>




<pre><code class="lang-ts">@IonicPage({
  name: &#39;my-page&#39;
})
</code></pre>
<p>这将使用名称 <code>&#39;my-page&#39;</code> 创建一个到 <code>MyPage</code> 组件的链接。与前面的示例类似，可以使用以下名称导航页面：</p>

<pre><code class="lang-ts">goToMyPage() {
  // 前往 MyPage 组件
  this.navCtrl.push(&#39;my-page&#39;);
}
</code></pre>
<h3 id="setting-url-path">设置 URL 路径</h3>
<p><code>segment</code> 属性用于设置页面的 URL。如果未提供此属性，那么 <code>segment</code> 将使用 <code>name</code> 的值。由于组件可以在应用程序的任意位置加载，因此该 <code>segment</code> 不需要完整的 URL 路径。当页面成为激活页面时，该 <code>segment</code> 将附加到 URL。</p>
<p>该 <code>segment</code> 可以更改为任意内容并且不必与 <code>name</code> 匹配。例如，传递 <code>name</code> 和 <code>segment</code>的值：</p>




<pre><code class="lang-ts">@IonicPage({
  name: &#39;my-page&#39;,
  segment: &#39;some-path&#39;
})
</code></pre>
<p>当导航到此页面作为应用程序的第一页时，该 URL 将如下所示：</p>
<pre><code>http://localhost:8101/#/some-path
</code></pre>
<p>但是，导航到页面仍然会像前面的示例那样使用 <code>name</code>。</p>
<h3 id="dynamic-links">动态链接</h3>
<p><code>segment</code> 属性对于创建动态链接很有用。有时 URL 并未提早被了解，所以它可以作为变量传递。</p>
<p>由于传递数据是应用程序中的常见做法，因此可以使用 <code>:param</code> 语法将其映射到应用程序的 URL 中。例如，在 <code>@IonicPage</code> 装饰器中设置 <code>segment</code>：</p>


<pre><code class="lang-ts">@IonicPage({
  name: &#39;detail-page&#39;,
  segment: &#39;detail/:id&#39;
})
</code></pre>
<p>在这种情况下，当我们 <code>push</code> 到 <code>&#39;detail-page&#39;</code> 的新实例时，传递给 <code>push</code> 的 <code>detailInfo</code> 数据中的 <code>id</code> 值将替换 URL 中的 <code>:id</code>。</p>
<p>重要提示：属性需要是可以转换为字符串的东西，不支持对象。</p>
<p>例如，要推入 <code>ListPage</code> 组件中的 <code>&#39;detail-page&#39;</code>，可以使用以下代码：</p>



<pre><code class="lang-ts">@IonicPage({
  name: &#39;list&#39;
})
export class ListPage {
  constructor(public navCtrl: NavController) {}

  pushPage(detailInfo) {
    // 将一个 `id` 推到 `&#39;detail-page&#39;`
    this.navCtrl.push(&#39;detail-page&#39;, {
      &#39;id&#39;: detailInfo.id
    })
  }
}
</code></pre>
<p>例如，如果 <code>detailInfo.id</code> 的值是 <code>12</code>，则 URL 最终会看起来像这样：</p>
<pre><code>http://localhost:8101/#/list/detail/12
</code></pre>
<p>由于此 <code>id</code> 将用于提取特定详细信息页面的数据，因此重要的是该 <code>id</code> 是唯一的。</p>
<p>注意：即使 <code>name</code> 是 <code>detail-page</code>， <code>segment</code> 使用 <code>detail/:id</code>，URL 也将使用该 <code>segment</code>。</p>
<h3 id="default-history">默认历史</h3>
<p>可以将页面导航到应用程序中任意位置的深度链接，但有时应用程序是从 URL 启动的，并且该页面需要具有相同的历史记录，就像从应用程序内部导航一样。</p>
<p>默认情况下，页面将被导航到堆栈中的第一页，并且没有以前的历史记录。一个很好的例子就是 iOS 上的 App Store。点击 App Store 中应用程序的 URL 将会加载应用程序的详细信息，而不需要后退按钮，就好像它是有史以来的第一页。</p>
<p>任何页面的默认历史记录都可以在 <code>defaultHistory</code> 属性中设置。只有当历史记录不存在时才会使用此历史记录，这意味着如果你导航到页面，历史记录里的页面将是从中导航的页面。</p>
<p><code>defaultHistory</code> 属性需要一个字符串数组。例如，将详情页面的历史记录设置为 <code>name</code> 列表所在的 <code>list</code> 页面：</p>









<pre><code class="lang-ts">@IonicPage({
  name: &#39;detail-page&#39;,
  segment: &#39;detail/:id&#39;,
  defaultHistory: [&#39;list&#39;]
})
</code></pre>
<p>在本例中，如果应用程序在 <code>http://localhost:8101/#/detail/my-detail</code> 中启动，那么显示的页面将成为具有 <code>my-detail</code> 标识的 <code>&#39;detail-page&#39;</code>，并显示一个可以返回到 <code>&#39;list&#39;</code> 页面的返回按钮。</p>
<p>一个设置历史堆栈的应用程序的示例是 Instagram 应用程序。在 Instagram 上打开指向图片的链接，会在用户的个人资料页面上显示返回按钮，以显示该图片的详细信息。没有“正确”的方式来设置页面的历史记录，这取决于应用程序。</p>
<h3 id="priority">优先级</h3>
<p><code>priority</code> 属性仅用于预加载。默认情况下，预加载是关闭的，因此设置此属性将不会执行任何操作。
预加载在应用程序引导后迅速地加载所有 deep links，而不是根据需要按需加载。要启用预加载，请将主应用程序模块配置中的 <code>preloadModules</code> 设置为 <code>true</code>：</p>






<pre><code class="lang-ts">@NgModule({
  declarations: [
    MyApp
  ],
  imports: [
    BrowserModule,
    IonicModule.forRoot(MyApp, {
      preloadModules: true
    })
  ],
  bootstrap: [IonicApp],
  entryComponents: [
    MyApp
  ]
})
export class AppModule { }
</code></pre>
<p>如果打开预加载，它将根据 <code>priority</code> 值加载模块。以下值可用于 <code>priority</code>： <code>&quot;high&quot;</code>, <code>&quot;low&quot;</code>, 和 <code>&quot;off&quot;</code>。当没有 <code>priority</code>时，它将被设置为 <code>&quot;low&quot;</code>。</p>
<p>所有优先级设置为 <code>&quot;high&quot;</code> 的 deep links 将首先加载。在加载 <code>&quot;high&quot;</code> 优先级模块完成后，将加载所有具有 <code>&quot;low&quot;</code> （或无优先级）的 deep links。如果优先级设置为 <code>&quot;off&quot;</code>，则 link 不会被预加载。设置 <code>priority</code> 与将它传递给 <code>@IonicPage</code> 装饰器一样简单：</p>





<pre><code class="lang-ts">@IonicPage({
  name: &#39;my-page&#39;,
  priority: &#39;high&#39;
})
</code></pre>
<p>我们建议在启动应用程序时首先将页面上的 <code>priority</code> 设置为 <code>&quot;high&quot;</code>。</p>





<!-- @property tags -->



<!-- instance methods on the class -->




<!-- related link --><!-- end content block -->


<!-- end body block -->

