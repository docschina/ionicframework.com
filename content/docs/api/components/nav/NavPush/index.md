---
layout: "fluid/docs_base"
version: "3.9.2"
versionHref: "/docs"
path: ""
category: api
id: "navpush"
title: "NavPush"
header_sub_title: "Ionic API Documentation"
doc: "NavPush"
docType: "class"
show_preview_device: true
preview_device_url: "/docs/demos/src/navigation/www/"
angular_controller: APIDemoCtrl
---









<h1 class="api-title">
<a class="anchor" name="nav-push" href="#nav-push"></a>

NavPush
<h3><code>[navPush]</code></h3>






</h1>

<a class="improve-v2-docs" href="http://github.com/ionic-team/ionic/edit/master/src/components/nav/nav-push.ts#L3">
改进这篇文档
</a>






<p>声明性地将新页面推入到当前导航堆栈的指令。</p>





<!-- @usage tag -->

<h2><a class="anchor" name="usage" href="#usage">用法</a></h2>

<pre><code class="lang-html">&lt;button ion-button [navPush]=&quot;pushPage&quot;&gt;&lt;/button&gt;
</code></pre>
<p>要指定参数，你可以使用数组语法或 <code>navParams</code> 属性：</p>

<pre><code class="lang-html">&lt;button ion-button [navPush]=&quot;pushPage&quot; [navParams]=&quot;params&quot;&gt;Go&lt;/button&gt;
</code></pre>
<p>在你的组件中指定了 <code>pushPage</code> 和 <code>params</code>，并且 <code>pushPage</code> 包含你想要推入的组件的引用：</p>


<pre><code class="lang-ts">import { LoginPage } from &#39;./login&#39;;

@Component({
  template: `&lt;button ion-button [navPush]=&quot;pushPage&quot; [navParams]=&quot;params&quot;&gt;Go&lt;/button&gt;`
})
class MyPage {
  params: Object;
  pushPage: any;
  constructor(){
    this.pushPage = LoginPage;
    this.params = { id: 42 };
  }
}
</code></pre>




<!-- @property tags -->



<!-- instance methods on the class -->
<!-- input methods on the class -->
<h2><a class="anchor" name="input-properties" href="#input-properties">输入属性</a></h2>
<table class="table param-table" style="margin:0;">
  <thead>
    <tr>
      <th>属性</th>
      <th>类型</th>
      <th>详情</th>
    </tr>
  </thead>
  <tbody>

    <tr>
      <td>navParams</td>
      <td><code>any</code></td>
      <td><p>你想要传递给下一个视图的任何 NavParams。</p>
</td>
    </tr>

    <tr>
      <td>navPush</td>
      <td><code>Page | string</code></td>
      <td><p>要推入导航堆栈的组件类或深层链接（deeplink）名称。</p>
</td>
    </tr>

  </tbody>
</table>




<!-- related link -->

<h2><a class="anchor" name="related" href="#related">Related</a></h2>

<a href="/docs/components#navigation">Navigation Component Docs</a>,
<a href="../NavPop">NavPop API Docs</a><!-- end content block -->


<!-- end body block -->

