---
layout: "fluid/docs_base"
version: "3.9.2"
versionHref: "/docs"
path: ""
category: api
id: "loadingcontroller"
title: "LoadingController"
header_sub_title: "Ionic API Documentation"
doc: "LoadingController"
docType: "class"
show_preview_device: true
preview_device_url: "/docs/demos/src/loading/www/"
angular_controller: APIDemoCtrl
---









<h1 class="api-title">
<a class="anchor" name="loading-controller" href="#loading-controller"></a>

LoadingController





</h1>

<a class="improve-v2-docs" href="http://github.com/ionic-team/ionic/edit/master/src/components/loading/loading-controller.ts#L5">
改进这篇文档
</a>






<p>一个覆盖层可用于在阻塞用户交互时指示行为。
loading 指示器出现在应用程序内容的顶部，
并且可以被应用程序解除来恢复用户与应用程序的交互。
它包含一个可选的背景，可以通过在创建时设置 <code>showBackdrop: false</code> 来禁用它。
</p>
<h3><a class="anchor" name="creating" href="#creating">创建</a></h3>

<p>你可以将所有 loading 选项传递给 create 方法的第一个参数：<code>create(opts)</code>。
spinner 名称应该在 <code>spinner</code> 属性中传递，
任意可选的 HTML 都可以在 <code>content</code> 属性中传递。
如果你没有将值传递给 <code>spinner</code>，loading 指示器将使用该模式指定的 spinner。
要在整个应用中设置 spinner 名称，
请在应用的配置中设置 <code>loadingSpinner</code> 的值。
要隐藏 spinner，请在加载选项中设置 <code>loadingSpinner: &#39;hide&#39;</code> 来配置应用程序或传递 <code>spinner: &#39;hide&#39;</code>。
有关所有可用选项，请参阅下面的 <a href="#create">create</a> 方法。
</p>
<h3><a class="anchor" name="dismissing" href="#dismissing">解除</a></h3>

<p>loading 指示器可以通过传递毫秒数设定指定的时间量，来在 loading 选项的 <code>持续时间</code> 之后自动解除。默认情况下，即使在页面更改期间，loading 指示器也会显示，但可以通过将 <code>dismissOnPageChange</code>设置为 <code>true</code> 来禁用此功能。要在创建后关闭 loading 指示器，请在 loading 实例上调用 <code>dismiss()</code> 方法。可以调用 <code>onDidDismiss</code> 函数在 loading 指示器解除后执行操作。</p>







<blockquote>
<p>请注意，组件被解除后，它将不可再次使用，并且必须创建另一个组件。这可以通过将组件的创建和展示包装在可重用的函数中来避免，如下面的<code>用法</code>部分所示。</p>



</blockquote>
<h3><a class="anchor" name="limitations" href="#limitations">限制</a></h3>

<p>该元素通过设置其 <code>z-index</code> 属性被设置为出现在其他内容之上。你必须确保没有元素具有比此元素具有更高 <code>z-index</code> 的层叠上下文。</p>






<!-- @usage tag -->

<h2><a class="anchor" name="usage" href="#usage">用法</a></h2>

<pre><code class="lang-ts">constructor(public loadingCtrl: LoadingController) {

}

presentLoadingDefault() {
  let loading = this.loadingCtrl.create({
    content: &#39;Please wait...&#39;
  });

  loading.present();

  setTimeout(() =&gt; {
    loading.dismiss();
  }, 5000);
}

presentLoadingCustom() {
  let loading = this.loadingCtrl.create({
    spinner: &#39;hide&#39;,
    content: `
      &lt;div class=&quot;custom-spinner-container&quot;&gt;
        &lt;div class=&quot;custom-spinner-box&quot;&gt;&lt;/div&gt;
      &lt;/div&gt;`,
    duration: 5000
  });

  loading.onDidDismiss(() =&gt; {
    console.log(&#39;Dismissed loading&#39;);
  });

  loading.present();
}

presentLoadingText() {
  let loading = this.loadingCtrl.create({
    spinner: &#39;hide&#39;,
    content: &#39;Loading Please Wait...&#39;
  });

  loading.present();

  setTimeout(() =&gt; {
    this.nav.push(Page2);
  }, 1000);

  setTimeout(() =&gt; {
    loading.dismiss();
  }, 5000);
}
</code></pre>




<!-- @property tags -->



<!-- instance methods on the class -->

<h2><a class="anchor" name="instance-members" href="#instance-members">实例成员</a></h2>

<div id="config"></div>

<h3>
<a class="anchor" name="config" href="#config">
<code>config</code>


</a>
</h3>











<div id="create"></div>

<h3>
<a class="anchor" name="create" href="#create">
<code>create(opts)</code>


</a>
</h3>

创建一个 loading 指示器。请参阅下面的选项。


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
        opts


      </td>
      <td>

  <code>LoadingOptions</code>
      </td>
      <td>
        <p>Loading 选项<strong class="tag">可选的</strong></p>


      </td>
    </tr>

  </tbody>
</table>





<div class="return-value">
<i class="icon ion-arrow-return-left"></i>
<b>返回：</b>
  <code>Loading</code> <p>返回一个 Loading 实例</p>


</div>


<h2><a class="anchor" name="advanced" href="#advanced">进阶</a></h2>
<p>Loading 选项</p>
<table>
<thead>
<tr>
<th>选项</th>
<th>类型</th>
<th>描述</th>
</tr>
</thead>
<tbody>
<tr>
<td>spinner</td>
<td><code>string</code></td>
<td>加载指示器的 SVG spinner 的名称。</td>
</tr>
<tr>
<td>content</td>
<td><code>string</code></td>
<td>loading 指示器的 html 内容。</td>
</tr>
<tr>
<td>cssClass</td>
<td><code>string</code></td>
<td>自定义样式的其他类，以空格分隔。</td>
</tr>
<tr>
<td>showBackdrop</td>
<td><code>boolean</code></td>
<td>是否显示背景。默认为 true。</td>
</tr>
<tr>
<td>enableBackdropDismiss</td>
<td><code>boolean</code></td>
<td>是否应通过点击背景来解除 loading 指示符。默认为 false。</td>
</tr>
<tr>
<td>dismissOnPageChange</td>
<td><code>boolean</code></td>
<td>是否在导航到新页面时关闭指示器。默认为 false。</td>
</tr>
<tr>
<td>duration</td>
<td><code>number</code></td>
<td>隐藏指示器之前要等待多少毫秒。默认情况下，它会显示，直到 <code>dismiss()</code> 被调用。</td>
</tr>
</tbody>
</table>



  <h2 id="sass-variable-header"><a class="anchor" name="sass-variables" href="#sass-variables">Sass Variables</a></h2>
  <div id="sass-variables" ng-controller="SassToggleCtrl">
  <div class="sass-platform-toggle">



      <a ng-init="setSassPlatform('ios')" ng-class="{ active: active === 'ios' }" ng-click="setSassPlatform('ios')" >iOS</a>



      <a ng-class="{ active: active === 'md' }" ng-click="setSassPlatform('md')">Material Design</a>



      <a ng-class="{ active: active === 'wp' }" ng-click="setSassPlatform('wp')">Windows Platform</a>



  </div>



  <table ng-show="active === 'ios'" id="sass-ios" class="table param-table" style="margin:0;">
    <thead>
      <tr>
        <th>Property</th>
        <th>Default</th>
        <th>Description</th>
      </tr>
    </thead>
    <tbody>

      <tr>
        <td><code>$loading-ios-padding-top</code></td>

          <td><code>24px</code></td>

        <td><p>Padding top of the loading wrapper</p>
</td>
      </tr>

      <tr>
        <td><code>$loading-ios-padding-end</code></td>

          <td><code>34px</code></td>

        <td><p>Padding end of the loading wrapper</p>
</td>
      </tr>

      <tr>
        <td><code>$loading-ios-padding-bottom</code></td>

          <td><code>$loading-ios-padding-top</code></td>

        <td><p>Padding bottom of the loading wrapper</p>
</td>
      </tr>

      <tr>
        <td><code>$loading-ios-padding-start</code></td>

          <td><code>$loading-ios-padding-end</code></td>

        <td><p>Padding start of the loading wrapper</p>
</td>
      </tr>

      <tr>
        <td><code>$loading-ios-max-width</code></td>

          <td><code>270px</code></td>

        <td><p>Max width of the loading wrapper</p>
</td>
      </tr>

      <tr>
        <td><code>$loading-ios-max-height</code></td>

          <td><code>90%</code></td>

        <td><p>Maximum height of the loading wrapper</p>
</td>
      </tr>

      <tr>
        <td><code>$loading-ios-border-radius</code></td>

          <td><code>8px</code></td>

        <td><p>Border radius of the loading wrapper</p>
</td>
      </tr>

      <tr>
        <td><code>$loading-ios-text-color</code></td>

          <td><code>#000</code></td>

        <td><p>Text color of the loading wrapper</p>
</td>
      </tr>

      <tr>
        <td><code>$loading-ios-background</code></td>

          <td><code>#f8f8f8</code></td>

        <td><p>Background of the loading wrapper</p>
</td>
      </tr>

      <tr>
        <td><code>$loading-ios-content-font-weight</code></td>

          <td><code>bold</code></td>

        <td><p>Font weight of the loading content</p>
</td>
      </tr>

      <tr>
        <td><code>$loading-ios-content-margin-start</code></td>

          <td><code>$content-ios-margin</code></td>

        <td><p>Margin start of the loading content next to a spinner</p>
</td>
      </tr>

      <tr>
        <td><code>$loading-ios-spinner-color</code></td>

          <td><code>#69717d</code></td>

        <td><p>Color of the loading spinner</p>
</td>
      </tr>

      <tr>
        <td><code>$loading-ios-spinner-ios-color</code></td>

          <td><code>$loading-ios-spinner-color</code></td>

        <td><p>Color of the ios loading spinner</p>
</td>
      </tr>

      <tr>
        <td><code>$loading-ios-spinner-bubbles-color</code></td>

          <td><code>$loading-ios-spinner-color</code></td>

        <td><p>Color of the bubbles loading spinner</p>
</td>
      </tr>

      <tr>
        <td><code>$loading-ios-spinner-circles-color</code></td>

          <td><code>$loading-ios-spinner-color</code></td>

        <td><p>Color of the circles loading spinner</p>
</td>
      </tr>

      <tr>
        <td><code>$loading-ios-spinner-crescent-color</code></td>

          <td><code>$loading-ios-spinner-color</code></td>

        <td><p>Color of the crescent loading spinner</p>
</td>
      </tr>

      <tr>
        <td><code>$loading-ios-spinner-dots-color</code></td>

          <td><code>$loading-ios-spinner-color</code></td>

        <td><p>Color of the dots loading spinner</p>
</td>
      </tr>

    </tbody>
  </table>

  <table ng-show="active === 'md'" id="sass-md" class="table param-table" style="margin:0;">
    <thead>
      <tr>
        <th>Property</th>
        <th>Default</th>
        <th>Description</th>
      </tr>
    </thead>
    <tbody>

      <tr>
        <td><code>$loading-md-padding-top</code></td>

          <td><code>24px</code></td>

        <td><p>Padding top of the loading wrapper</p>
</td>
      </tr>

      <tr>
        <td><code>$loading-md-padding-end</code></td>

          <td><code>$loading-md-padding-top</code></td>

        <td><p>Padding end of the loading wrapper</p>
</td>
      </tr>

      <tr>
        <td><code>$loading-md-padding-bottom</code></td>

          <td><code>$loading-md-padding-top</code></td>

        <td><p>Padding bottom of the loading wrapper</p>
</td>
      </tr>

      <tr>
        <td><code>$loading-md-padding-start</code></td>

          <td><code>$loading-md-padding-end</code></td>

        <td><p>Padding start of the loading wrapper</p>
</td>
      </tr>

      <tr>
        <td><code>$loading-md-max-width</code></td>

          <td><code>280px</code></td>

        <td><p>Max width of the loading wrapper</p>
</td>
      </tr>

      <tr>
        <td><code>$loading-md-max-height</code></td>

          <td><code>90%</code></td>

        <td><p>Maximum height of the loading wrapper</p>
</td>
      </tr>

      <tr>
        <td><code>$loading-md-border-radius</code></td>

          <td><code>2px</code></td>

        <td><p>Border radius of the loading wrapper</p>
</td>
      </tr>

      <tr>
        <td><code>$loading-md-text-color</code></td>

          <td><code>rgba(0, 0, 0, .5)</code></td>

        <td><p>Text color of the loading wrapper</p>
</td>
      </tr>

      <tr>
        <td><code>$loading-md-background</code></td>

          <td><code>#fafafa</code></td>

        <td><p>Background of the loading wrapper</p>
</td>
      </tr>

      <tr>
        <td><code>$loading-md-box-shadow-color</code></td>

          <td><code>rgba(0, 0, 0, .4)</code></td>

        <td><p>Box shadow color of the loading wrapper</p>
</td>
      </tr>

      <tr>
        <td><code>$loading-md-box-shadow</code></td>

          <td><code>0 16px 20px $loading-md-box-shadow-color</code></td>

        <td><p>Box shadow of the loading wrapper</p>
</td>
      </tr>

      <tr>
        <td><code>$loading-md-content-margin-start</code></td>

          <td><code>$content-md-margin</code></td>

        <td><p>Margin start of the loading content next to a spinner</p>
</td>
      </tr>

      <tr>
        <td><code>$loading-md-spinner-color</code></td>

          <td><code>color($colors-md, primary)</code></td>

        <td><p>Color of the loading spinner</p>
</td>
      </tr>

      <tr>
        <td><code>$loading-md-spinner-ios-color</code></td>

          <td><code>$loading-md-spinner-color</code></td>

        <td><p>Color of the ios loading spinner</p>
</td>
      </tr>

      <tr>
        <td><code>$loading-md-spinner-bubbles-color</code></td>

          <td><code>$loading-md-spinner-color</code></td>

        <td><p>Color of the bubbles loading spinner</p>
</td>
      </tr>

      <tr>
        <td><code>$loading-md-spinner-circles-color</code></td>

          <td><code>$loading-md-spinner-color</code></td>

        <td><p>Color of the circles loading spinner</p>
</td>
      </tr>

      <tr>
        <td><code>$loading-md-spinner-crescent-color</code></td>

          <td><code>$loading-md-spinner-color</code></td>

        <td><p>Color of the crescent loading spinner</p>
</td>
      </tr>

      <tr>
        <td><code>$loading-md-spinner-dots-color</code></td>

          <td><code>$loading-md-spinner-color</code></td>

        <td><p>Color of the dots loading spinner</p>
</td>
      </tr>

    </tbody>
  </table>

  <table ng-show="active === 'wp'" id="sass-wp" class="table param-table" style="margin:0;">
    <thead>
      <tr>
        <th>Property</th>
        <th>Default</th>
        <th>Description</th>
      </tr>
    </thead>
    <tbody>

      <tr>
        <td><code>$loading-wp-padding-top</code></td>

          <td><code>20px</code></td>

        <td><p>Padding top of the loading wrapper</p>
</td>
      </tr>

      <tr>
        <td><code>$loading-wp-padding-end</code></td>

          <td><code>$loading-wp-padding-top</code></td>

        <td><p>Padding end of the loading wrapper</p>
</td>
      </tr>

      <tr>
        <td><code>$loading-wp-padding-bottom</code></td>

          <td><code>$loading-wp-padding-top</code></td>

        <td><p>Padding bottom of the loading wrapper</p>
</td>
      </tr>

      <tr>
        <td><code>$loading-wp-padding-start</code></td>

          <td><code>$loading-wp-padding-end</code></td>

        <td><p>Padding start of the loading wrapper</p>
</td>
      </tr>

      <tr>
        <td><code>$loading-wp-max-width</code></td>

          <td><code>280px</code></td>

        <td><p>Max width of the loading wrapper</p>
</td>
      </tr>

      <tr>
        <td><code>$loading-wp-max-height</code></td>

          <td><code>90%</code></td>

        <td><p>Maximum height of the loading wrapper</p>
</td>
      </tr>

      <tr>
        <td><code>$loading-wp-border-radius</code></td>

          <td><code>2px</code></td>

        <td><p>Border radius of the loading wrapper</p>
</td>
      </tr>

      <tr>
        <td><code>$loading-wp-text-color</code></td>

          <td><code>#fff</code></td>

        <td><p>Text color of the loading wrapper</p>
</td>
      </tr>

      <tr>
        <td><code>$loading-wp-background</code></td>

          <td><code>#000</code></td>

        <td><p>Background of the loading wrapper</p>
</td>
      </tr>

      <tr>
        <td><code>$loading-wp-content-margin-start</code></td>

          <td><code>$content-wp-margin</code></td>

        <td><p>Margin start of the loading content next to a spinner</p>
</td>
      </tr>

      <tr>
        <td><code>$loading-wp-spinner-color</code></td>

          <td><code>$loading-wp-text-color</code></td>

        <td><p>Color of the loading spinner</p>
</td>
      </tr>

      <tr>
        <td><code>$loading-wp-spinner-ios-color</code></td>

          <td><code>$loading-wp-spinner-color</code></td>

        <td><p>Color of the ios loading spinner</p>
</td>
      </tr>

      <tr>
        <td><code>$loading-wp-spinner-bubbles-color</code></td>

          <td><code>$loading-wp-spinner-color</code></td>

        <td><p>Color of the bubbles loading spinner</p>
</td>
      </tr>

      <tr>
        <td><code>$loading-wp-spinner-circles-color</code></td>

          <td><code>$loading-wp-spinner-color</code></td>

        <td><p>Color of the circles loading spinner</p>
</td>
      </tr>

      <tr>
        <td><code>$loading-wp-spinner-crescent-color</code></td>

          <td><code>$loading-wp-spinner-color</code></td>

        <td><p>Color of the crescent loading spinner</p>
</td>
      </tr>

      <tr>
        <td><code>$loading-wp-spinner-dots-color</code></td>

          <td><code>$loading-wp-spinner-color</code></td>

        <td><p>Color of the dots loading spinner</p>
</td>
      </tr>

    </tbody>
  </table>

</div>



<!-- related link -->

<h2><a class="anchor" name="related" href="#related">Related</a></h2>

<a href="/docs/api/components/spinner/Spinner">Spinner API Docs</a><!-- end content block -->


<!-- end body block -->

