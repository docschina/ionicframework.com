---
layout: "fluid/docs_base"
version: "3.9.2"
versionHref: "/docs"
path: ""
category: api
id: "infinitescroll"
title: "InfiniteScroll"
header_sub_title: "Ionic API Documentation"
doc: "InfiniteScroll"
docType: "class"
show_preview_device: true
preview_device_url: "/docs/demos/src/infinite-scroll/www/"
angular_controller: APIDemoCtrl
---









<h1 class="api-title">
<a class="anchor" name="infinite-scroll" href="#infinite-scroll"></a>

InfiniteScroll
<h3><code>ion-infinite-scroll</code></h3>






</h1>

<a class="improve-v2-docs" href="http://github.com/ionic-team/ionic/edit/v3/src/components/infinite-scroll/infinite-scroll.ts#L4">
改进这篇文档
</a>






<p>Infinite Scroll 允许你在用户从页面底部或顶部滚动指定的距离时执行操作。</p>
<p>当用户滚动到指定距离时， <code>infinite</code> 事件的表达式就会被调用。当这个表达式完成它的任务时，它就会在 infinite scroll 实例上调用 <code>complete()</code> 方法。</p>








<!-- @usage tag -->

<h2><a class="anchor" name="usage" href="#usage">用法</a></h2>

<pre><code class="lang-html">&lt;ion-content&gt;

 &lt;ion-list&gt;
   &lt;ion-item *ngFor=&quot;let i of items&quot;&gt;{% raw %}{{i}}{% endraw %}&lt;/ion-item&gt;
 &lt;/ion-list&gt;

 &lt;ion-infinite-scroll (ionInfinite)=&quot;doInfinite($event)&quot;&gt;
   &lt;ion-infinite-scroll-content&gt;&lt;/ion-infinite-scroll-content&gt;
 &lt;/ion-infinite-scroll&gt;

&lt;/ion-content&gt;
</code></pre>
<pre><code class="lang-ts">@Component({...})
export class NewsFeedPage {
  items = [];

  constructor() {
    for (let i = 0; i &lt; 30; i++) {
      this.items.push( this.items.length );
    }
  }

  doInfinite(infiniteScroll) {
    console.log(&#39;Begin async operation&#39;);

    setTimeout(() =&gt; {
      for (let i = 0; i &lt; 30; i++) {
        this.items.push( this.items.length );
      }

      console.log(&#39;Async operation has ended&#39;);
      infiniteScroll.complete();
    }, 500);
  }

}
</code></pre>
<h2 id="-waitfor-method-of-infinitescroll"><code>waitFor</code> 方法的 InfiniteScroll</h2>
<p>如果你的异步操作返回 promise，你可以在你的模板中使用 <code>waitFor</code> 方法。</p>

<pre><code class="lang-html">&lt;ion-content&gt;

 &lt;ion-list&gt;
   &lt;ion-item *ngFor=&quot;let item of items&quot;&gt;{{item}}&lt;/ion-item&gt;
 &lt;/ion-list&gt;

 &lt;ion-infinite-scroll (ionInfinite)=&quot;$event.waitFor(doInfinite())&quot;&gt;
   &lt;ion-infinite-scroll-content&gt;&lt;/ion-infinite-scroll-content&gt;
 &lt;/ion-infinite-scroll&gt;

&lt;/ion-content&gt;
</code></pre>
<pre><code class="lang-ts">@Component({...})
export class NewsFeedPage {
  items = [];

  constructor() {
    for (var i = 0; i &lt; 30; i++) {
      this.items.push( this.items.length );
    }
  }

  doInfinite(): Promise&lt;any&gt; {
    console.log(&#39;Begin async operation&#39;);

    return new Promise((resolve) =&gt; {
      setTimeout(() =&gt; {
        for (var i = 0; i &lt; 30; i++) {
          this.items.push( this.items.length );
        }

        console.log(&#39;Async operation has ended&#39;);
        resolve();
      }, 500);
    })
  }
}
</code></pre>
<h2 id="infinite-scroll-content">Infinite Scroll 内容</h2>
<p>默认情况下，Ionic 使用最适合用户所在平台的 infinite scroll spinner。但是，你可以通过向 <code>ion-infinite-scroll-content</code> 组件添加属性来更改默认 spinner 或添加文本。</p>



<pre><code class="lang-html">&lt;ion-content&gt;

  &lt;ion-infinite-scroll (ionInfinite)=&quot;doInfinite($event)&quot;&gt;
    &lt;ion-infinite-scroll-content
      loadingSpinner=&quot;bubbles&quot;
      loadingText=&quot;Loading more data...&quot;&gt;
    &lt;/ion-infinite-scroll-content&gt;
  &lt;/ion-infinite-scroll&gt;

&lt;/ion-content&gt;
</code></pre>
<h2 id="further-customizing-infinite-scroll-content">进一步定制 Infinite Scroll Content</h2>
<p><code>ion-infinite-scroll</code> 组件保存无限滚动逻辑，需要一个子组件才能显示内容。 Ionic 默认使用 <code>ion-infinite-scroll-content</code>。此组件会显示 infinite scroll 并根据无限滚动的状态更改外观。分离这些组件允许开发人员创建他们自己的 infinite scroll content 组件。你也可以使用自定义 SVG 或 CSS 动画替换我们的默认内容。</p>










<!-- @property tags -->



<!-- instance methods on the class -->

<h2><a class="anchor" name="instance-members" href="#instance-members">实例成员</a></h2>

<div id="complete"></div>

<h3>
<a class="anchor" name="complete" href="#complete">
<code>complete()</code>


</a>
</h3>

当异步操作完成时，在 `infinite` 事件处理函数中调用 `complete()`。
例如， `loading` 状态是应用程序执行异步操作时，比如从 AJAX 请求接收更多数据，将更多项添加到数据列表。
一旦接收到这些数据并更新 UI，就调用此方法来表示加载已完成。
这种方法会将 infinite scroll 状态从 `loading` 更改为 `enabled`。














<div id="enable"></div>

<h3>
<a class="anchor" name="enable" href="#enable">
<code>enable(shouldEnable)</code>


</a>
</h3>

调用 `enable(false)` 可禁用无限滚动，以便在滚动时主动尝试接收新数据。当已知不再有可以添加的数据，并且不再需要无限滚动时，此方法非常有用。





<table class="table param-table" style="margin:0;">
  <thead>
    <tr>
      <th>参数</th>
      <th>类型</th>
      <th>详情</th>
    </tr>
  </thead>
  <tbody>

    <tr>
      <td>
        shouldEnable


      </td>
      <td>

  <code>boolean</code>
      </td>
      <td>
        <p> infinite scroll 是否启用。设置为 <code>false</code> 将删除滚动事件侦听器并隐藏显示。</p>




      </td>
    </tr>

  </tbody>
</table>








<div id="waitFor"></div>

<h3>
<a class="anchor" name="waitFor" href="#waitFor">
<code>waitFor()</code>


</a>
</h3>

Pass a promise inside `waitFor()` within the `infinite` output event handler in order to
change state of infiniteScroll to "complete"









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
      <td>enabled</td>
      <td><code>boolean</code></td>
      <td><p>如果为true，就启用无限滚动。设置为 <code>false</code> 将删除滚动事件侦听器并隐藏显示。</p>


</td>
    </tr>

    <tr>
      <td>position</td>
      <td><code>string</code></td>
      <td><p>无限滚动元素的位置。该值可以是<code>top</code> 或 <code>bottom</code>。默认是 <code>bottom</code>。</p>


</td>
    </tr>

    <tr>
      <td>threshold</td>
      <td><code>string</code></td>
      <td><p>滚动时，从 content 底部开始调用 <code>infinite</code> 输出事件的阈值距离。阈值可以是百分比，也可以是像素。例如，当用户从页面底部滚动 <code>10%</code> 时，就会将 <code>infinite</code> 输出事件的值设为10％。当滚动距离页面底部100像素以内时，请使用值 <code>100px</code> 。默认值是 <code>15%</code>。</p>







</td>
    </tr>

  </tbody>
</table>
<!-- output events on the class -->
<h2><a class="anchor" name="output-events" href="#output-events">输出事件</a></h2>
<table class="table param-table" style="margin:0;">
  <thead>
    <tr>
      <th>属性</th>
      <th>详情</th>
    </tr>
  </thead>
  <tbody>

    <tr>
      <td>ionInfinite</td>
      <td><p>当滚动达到阈值距离时触发。在你的 infinite 处理函数中，当异步操作完成时，你必须调用无限滚动的 <code>complete()</code> 方法。</p>



</td>
    </tr>

  </tbody>
</table>


  <h2 id="sass-variable-header"><a class="anchor" name="sass-variables" href="#sass-variables">Sass Variables</a></h2>
  <div id="sass-variables" ng-controller="SassToggleCtrl">
  <div class="sass-platform-toggle">

    <h3 ng-init="setSassPlatform('base')">All</h3>

  </div>



  <table ng-show="active === 'base'" id="sass-base" class="table param-table" style="margin:0;">
    <thead>
      <tr>
        <th>Property</th>
        <th>Default</th>
        <th>Description</th>
      </tr>
    </thead>
    <tbody>

      <tr>
        <td><code>$infinite-scroll-loading-margin-top</code></td>

          <td><code>0</code></td>

        <td><p>Margin top of the infinite scroll loading icon</p>
</td>
      </tr>

      <tr>
        <td><code>$infinite-scroll-loading-margin-end</code></td>

          <td><code>0</code></td>

        <td><p>Margin end of the infinite scroll loading icon</p>
</td>
      </tr>

      <tr>
        <td><code>$infinite-scroll-loading-margin-bottom</code></td>

          <td><code>32px</code></td>

        <td><p>Margin bottom of the infinite scroll loading icon</p>
</td>
      </tr>

      <tr>
        <td><code>$infinite-scroll-loading-margin-start</code></td>

          <td><code>0</code></td>

        <td><p>Margin start of the infinite scroll loading icon</p>
</td>
      </tr>

      <tr>
        <td><code>$infinite-scroll-loading-color</code></td>

          <td><code>#666</code></td>

        <td><p>Color of the infinite scroll loading indicator</p>
</td>
      </tr>

      <tr>
        <td><code>$infinite-scroll-loading-text-color</code></td>

          <td><code>$infinite-scroll-loading-color</code></td>

        <td><p>Text color of the infinite scroll loading indicator</p>
</td>
      </tr>

      <tr>
        <td><code>$infinite-scroll-loading-text-margin-top</code></td>

          <td><code>4px</code></td>

        <td><p>Margin top of the infinite scroll loading text</p>
</td>
      </tr>

      <tr>
        <td><code>$infinite-scroll-loading-text-margin-end</code></td>

          <td><code>32px</code></td>

        <td><p>Margin end of the infinite scroll loading text</p>
</td>
      </tr>

      <tr>
        <td><code>$infinite-scroll-loading-text-margin-bottom</code></td>

          <td><code>0</code></td>

        <td><p>Margin bottom of the infinite scroll loading text</p>
</td>
      </tr>

      <tr>
        <td><code>$infinite-scroll-loading-text-margin-start</code></td>

          <td><code>32px</code></td>

        <td><p>Margin start of the infinite scroll loading text</p>
</td>
      </tr>

    </tbody>
  </table>

</div>



<!-- related link --><!-- end content block -->


<!-- end body block -->

