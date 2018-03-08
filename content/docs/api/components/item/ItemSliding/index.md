---
layout: "fluid/docs_base"
version: "3.9.2"
versionHref: "/docs"
path: ""
category: api
id: "itemsliding"
title: "ItemSliding"
header_sub_title: "Ionic API Documentation"
doc: "ItemSliding"
docType: "class"
show_preview_device: true
preview_device_url: "/docs/demos/src/item-sliding/www/"
angular_controller: APIDemoCtrl
---









<h1 class="api-title">
<a class="anchor" name="item-sliding" href="#item-sliding"></a>

ItemSliding
<h3><code>ion-item-sliding</code></h3>






</h1>

<a class="improve-v2-docs" href="http://github.com/ionic-team/ionic/edit/master/src/components/item/item-sliding.ts#L38">
改进这篇文档
</a>






<p>sliding item 是可以用滑动来显示按钮的 list item。它需要将一个 <a href="../Item">Item</a> 组件作为子项，并将 <a href="../../list/List">List</a> 组件作为父项。所有要显示的按钮都可以放在 <code>&lt;ion-item-options&gt;</code> 元素中。</p>






<!-- @usage tag -->

<h2><a class="anchor" name="usage" href="#usage">用法</a></h2>

<pre><code class="lang-html">&lt;ion-list&gt;
  &lt;ion-item-sliding #item&gt;
    &lt;ion-item&gt;
      Item
    &lt;/ion-item&gt;
    &lt;ion-item-options side=&quot;left&quot;&gt;
      &lt;button ion-button (click)=&quot;favorite(item)&quot;&gt;Favorite&lt;/button&gt;
      &lt;button ion-button color=&quot;danger&quot; (click)=&quot;share(item)&quot;&gt;Share&lt;/button&gt;
    &lt;/ion-item-options&gt;

    &lt;ion-item-options side=&quot;right&quot;&gt;
      &lt;button ion-button (click)=&quot;unread(item)&quot;&gt;Unread&lt;/button&gt;
    &lt;/ion-item-options&gt;
  &lt;/ion-item-sliding&gt;
&lt;/ion-list&gt;
</code></pre>
<h3 id="swipe-direction">滑动方向</h3>
<p>默认情况下，sliding item 从右向左滑动时显示按钮，因此按钮位于右侧。但是也可以通过在 <code>ion-item-options</code> 元素上设置 <code>side</code> 属性在右侧显示它们（从左向右滑动）。根据滑动方向，最多可以同时使用2个 <code>ion-item-options</code> 选项，用来显示两组不同的按钮。</p>




<pre><code class="lang-html">&lt;ion-item-options side=&quot;right&quot;&gt;
  &lt;button ion-button (click)=&quot;archive(item)&quot;&gt;
    &lt;ion-icon name=&quot;archive&quot;&gt;&lt;/ion-icon&gt;
    Archive
  &lt;/button&gt;
&lt;/ion-item-options&gt;

&lt;ion-item-options side=&quot;left&quot;&gt;
  &lt;button ion-button (click)=&quot;archive(item)&quot;&gt;
    &lt;ion-icon name=&quot;archive&quot;&gt;&lt;/ion-icon&gt;
    Archive
  &lt;/button&gt;
&lt;/ion-item-options&gt;
</code></pre>
<h3 id="listening-for-events-iondrag-and-ionswipe-">监听事件（ionDrag）和（ionSwipe）</h3>
<p>通过订阅 <code>ionDrag</code> 事件可以知道 sliding item 当前的相对位置。</p>

<pre><code class="lang-html">&lt;ion-item-sliding (ionDrag)=&quot;logDrag($event)&quot;&gt;
  &lt;ion-item&gt;Item&lt;/ion-item&gt;
  &lt;ion-item-options&gt;
    &lt;button ion-button&gt;Favorite&lt;/button&gt;
  &lt;/ion-item-options&gt;
&lt;/ion-item-sliding&gt;
</code></pre>
<h3 id="button-layout">按钮布局</h3>
<p>如果在选项按钮中放置了带有文本的图标，默认情况下，它将在文本顶部显示图标。通过设置 <code>icon-start</code> 作为 <code>&lt;ion-item-options&gt;</code> 元素上的一个属性，可以更改此图标以显示文本左侧的图标。</p>



<pre><code class="lang-html">&lt;ion-item-options icon-start&gt;
  &lt;button ion-button (click)=&quot;archive(item)&quot;&gt;
    &lt;ion-icon name=&quot;archive&quot;&gt;&lt;/ion-icon&gt;
    Archive
  &lt;/button&gt;
&lt;/ion-item-options&gt;
</code></pre>
<h3 id="expandable-options">可扩展选项</h3>
<p>如果你滑过某个点，则可以扩展选项占据该 item 的整个宽度。这可以结合 <code>ionSwipe</code> 事件来调用该类的方法。</p>


<pre><code class="lang-html">&lt;ion-item-sliding (ionSwipe)=&quot;delete(item)&quot;&gt;
  &lt;ion-item&gt;Item&lt;/ion-item&gt;
  &lt;ion-item-options&gt;
    &lt;button ion-button expandable (click)=&quot;delete(item)&quot;&gt;Delete&lt;/button&gt;
  &lt;/ion-item-options&gt;
&lt;/ion-item-sliding&gt;
</code></pre>
<p>我们可以通过点击按钮，或者在 item 上全力滑动来调用 <code>delete</code> 功能。</p>




<!-- @property tags -->



<!-- instance methods on the class -->

<h2><a class="anchor" name="instance-members" href="#instance-members">实例成员</a></h2>

<div id="close"></div>

<h3>
<a class="anchor" name="close" href="#close">
<code>close()</code>


</a>
</h3>

关闭 sliding item。Items 也可以从 [List](../../list/List) 中关闭。



sliding item 可以通过获取 `ItemSliding` 的引用来关闭它。在下面的示例中，模板引用变量 `slidingItem` 放置在元素上并传递给 `share` 方法。

```html
<ion-list>
  <ion-item-sliding #slidingItem>
    <ion-item>
      Item
    </ion-item>
    <ion-item-options>
      <button ion-button (click)="share(slidingItem)">Share</button>
    </ion-item-options>
  </ion-item-sliding>
</ion-list>
```

```ts
import { Component } from '@angular/core';
import { ItemSliding } from 'ionic-angular';

@Component({...})
export class MyClass {
  constructor() { }

  share(slidingItem: ItemSliding) {
    slidingItem.close();
  }
}
```









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
      <td>ionDrag</td>
      <td><p>当滑动位置改变时触发。它会报告相对位置。</p>

<pre><code class="lang-ts">ondrag(item) {
  let percent = item.getSlidingPercent();
  if (percent &gt; 0) {
    // 正的
    console.log(&#39;right side&#39;);
  } else {
    // 负的
    console.log(&#39;left side&#39;);
  }
  if (Math.abs(percent) &gt; 1) {
    console.log(&#39;overscroll&#39;);
  }
}
</code></pre>
</td>
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
        <td><code>$item-ios-body-text-font-size</code></td>

          <td><code>1.7rem</code></td>

        <td><p>Font size of the item text</p>
</td>
      </tr>

      <tr>
        <td><code>$item-ios-paragraph-margin-top</code></td>

          <td><code>0</code></td>

        <td><p>Margin top of the item paragraph</p>
</td>
      </tr>

      <tr>
        <td><code>$item-ios-paragraph-margin-end</code></td>

          <td><code>0</code></td>

        <td><p>Margin end of the item paragraph</p>
</td>
      </tr>

      <tr>
        <td><code>$item-ios-paragraph-margin-bottom</code></td>

          <td><code>2px</code></td>

        <td><p>Margin bottom of the item paragraph</p>
</td>
      </tr>

      <tr>
        <td><code>$item-ios-paragraph-margin-start</code></td>

          <td><code>$item-ios-paragraph-margin-end</code></td>

        <td><p>Margin start of the item paragraph</p>
</td>
      </tr>

      <tr>
        <td><code>$item-ios-paragraph-font-size</code></td>

          <td><code>1.4rem</code></td>

        <td><p>Font size of the item paragraph</p>
</td>
      </tr>

      <tr>
        <td><code>$item-ios-paragraph-text-color</code></td>

          <td><code>#8e9093</code></td>

        <td><p>Color of the item paragraph</p>
</td>
      </tr>

      <tr>
        <td><code>$item-ios-avatar-size</code></td>

          <td><code>36px</code></td>

        <td><p>Size of the avatar in the item</p>
</td>
      </tr>

      <tr>
        <td><code>$item-ios-avatar-border-radius</code></td>

          <td><code>50%</code></td>

        <td><p>Border radius of the avatar in the item</p>
</td>
      </tr>

      <tr>
        <td><code>$item-ios-thumbnail-size</code></td>

          <td><code>56px</code></td>

        <td><p>Size of the thumbnail in the item</p>
</td>
      </tr>

      <tr>
        <td><code>$item-ios-detail-push-show</code></td>

          <td><code>true</code></td>

        <td><p>Shows the detail arrow icon on an item</p>
</td>
      </tr>

      <tr>
        <td><code>$item-ios-detail-push-color</code></td>

          <td><code>$list-ios-border-color</code></td>

        <td><p>Color of the detail arrow icon</p>
</td>
      </tr>

      <tr>
        <td><code>$item-ios-detail-push-svg</code></td>

          <td><code>&quot;&lt;svg xmlns=&#39;http://www.w3.org/2000/svg&#39; viewBox=&#39;0 0 12 20&#39;&gt;&lt;path d=&#39;M2,20l-2-2l8-8L0,2l2-2l10,10L2,20z&#39; fill=&#39;#{$item-ios-detail-push-color}&#39;/&gt;&lt;/svg&gt;&quot;</code></td>

        <td><p>Icon for the detail arrow</p>
</td>
      </tr>

      <tr>
        <td><code>$item-ios-divider-background</code></td>

          <td><code>#f7f7f7</code></td>

        <td><p>Background for the divider</p>
</td>
      </tr>

      <tr>
        <td><code>$item-ios-divider-color</code></td>

          <td><code>#222</code></td>

        <td><p>Color for the divider</p>
</td>
      </tr>

      <tr>
        <td><code>$item-ios-sliding-content-background</code></td>

          <td><code>$list-ios-background-color</code></td>

        <td><p>Background for the sliding content</p>
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
        <td><code>$item-md-body-text-font-size</code></td>

          <td><code>1.4rem</code></td>

        <td><p>Font size of the item text</p>
</td>
      </tr>

      <tr>
        <td><code>$item-md-body-text-line-height</code></td>

          <td><code>1.5</code></td>

        <td><p>line height of the item text</p>
</td>
      </tr>

      <tr>
        <td><code>$item-md-paragraph-text-color</code></td>

          <td><code>#666</code></td>

        <td><p>Color of the item paragraph</p>
</td>
      </tr>

      <tr>
        <td><code>$item-md-font-size</code></td>

          <td><code>1.6rem</code></td>

        <td><p>Font size of the item</p>
</td>
      </tr>

      <tr>
        <td><code>$item-md-avatar-size</code></td>

          <td><code>40px</code></td>

        <td><p>Size of the avatar in the item</p>
</td>
      </tr>

      <tr>
        <td><code>$item-md-avatar-border-radius</code></td>

          <td><code>50%</code></td>

        <td><p>Border radius of the avatar in the item</p>
</td>
      </tr>

      <tr>
        <td><code>$item-md-thumbnail-size</code></td>

          <td><code>80px</code></td>

        <td><p>Size of the thumbnail in the item</p>
</td>
      </tr>

      <tr>
        <td><code>$item-md-detail-push-show</code></td>

          <td><code>false</code></td>

        <td><p>Shows the detail arrow icon on an item</p>
</td>
      </tr>

      <tr>
        <td><code>$item-md-detail-push-color</code></td>

          <td><code>$list-md-border-color</code></td>

        <td><p>Color of the detail arrow icon</p>
</td>
      </tr>

      <tr>
        <td><code>$item-md-detail-push-svg</code></td>

          <td><code>&quot;&lt;svg xmlns=&#39;http://www.w3.org/2000/svg&#39; viewBox=&#39;0 0 12 20&#39;&gt;&lt;path d=&#39;M2,20l-2-2l8-8L0,2l2-2l10,10L2,20z&#39; fill=&#39;#{$item-md-detail-push-color}&#39;/&gt;&lt;/svg&gt;&quot;</code></td>

        <td><p>Icon for the detail arrow</p>
</td>
      </tr>

      <tr>
        <td><code>$item-md-divider-color</code></td>

          <td><code>#858585</code></td>

        <td><p>Color for the divider</p>
</td>
      </tr>

      <tr>
        <td><code>$item-md-divider-background</code></td>

          <td><code>#fff</code></td>

        <td><p>Background for the divider</p>
</td>
      </tr>

      <tr>
        <td><code>$item-md-divider-font-size</code></td>

          <td><code>$item-md-body-text-font-size</code></td>

        <td><p>Font size for the divider</p>
</td>
      </tr>

      <tr>
        <td><code>$item-md-divider-border-bottom</code></td>

          <td><code>1px solid $list-md-border-color</code></td>

        <td><p>Border bottom for the divider</p>
</td>
      </tr>

      <tr>
        <td><code>$item-md-sliding-content-background</code></td>

          <td><code>$list-md-background-color</code></td>

        <td><p>Background for the sliding content</p>
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
        <td><code>$item-wp-body-text-font-size</code></td>

          <td><code>1.4rem</code></td>

        <td><p>Font size of the item text</p>
</td>
      </tr>

      <tr>
        <td><code>$item-wp-body-text-line-height</code></td>

          <td><code>1.5</code></td>

        <td><p>line height of the item text</p>
</td>
      </tr>

      <tr>
        <td><code>$item-wp-body-background-color</code></td>

          <td><code>$list-wp-background-color</code></td>

        <td><p>Background color of the item</p>
</td>
      </tr>

      <tr>
        <td><code>$item-wp-body-text-color</code></td>

          <td><code>$list-wp-text-color</code></td>

        <td><p>Color of the item text</p>
</td>
      </tr>

      <tr>
        <td><code>$item-wp-paragraph-text-color</code></td>

          <td><code>#666</code></td>

        <td><p>Color of the item paragraph</p>
</td>
      </tr>

      <tr>
        <td><code>$item-wp-font-size</code></td>

          <td><code>1.6rem</code></td>

        <td><p>Font size of the item</p>
</td>
      </tr>

      <tr>
        <td><code>$item-wp-avatar-size</code></td>

          <td><code>40px</code></td>

        <td><p>Size of the avatar in the item</p>
</td>
      </tr>

      <tr>
        <td><code>$item-wp-avatar-border-radius</code></td>

          <td><code>50%</code></td>

        <td><p>Border radius of the avatar in the item</p>
</td>
      </tr>

      <tr>
        <td><code>$item-wp-thumbnail-size</code></td>

          <td><code>80px</code></td>

        <td><p>Size of the thumbnail in the item</p>
</td>
      </tr>

      <tr>
        <td><code>$item-wp-detail-push-show</code></td>

          <td><code>false</code></td>

        <td><p>Shows the detail arrow icon on an item</p>
</td>
      </tr>

      <tr>
        <td><code>$item-wp-detail-push-color</code></td>

          <td><code>$input-wp-border-color</code></td>

        <td><p>Color of the detail arrow icon</p>
</td>
      </tr>

      <tr>
        <td><code>$item-wp-detail-push-svg</code></td>

          <td><code>&quot;&lt;svg xmlns=&#39;http://www.w3.org/2000/svg&#39; viewBox=&#39;0 0 12 20&#39;&gt;&lt;path d=&#39;M2,20l-2-2l8-8L0,2l2-2l10,10L2,20z&#39; fill=&#39;#{$item-wp-detail-push-color}&#39;/&gt;&lt;/svg&gt;&quot;</code></td>

        <td><p>Icon for the detail arrow</p>
</td>
      </tr>

      <tr>
        <td><code>$item-wp-divider-color</code></td>

          <td><code>$list-wp-text-color</code></td>

        <td><p>Color for the divider</p>
</td>
      </tr>

      <tr>
        <td><code>$item-wp-divider-background</code></td>

          <td><code>#fff</code></td>

        <td><p>Background for the divider</p>
</td>
      </tr>

      <tr>
        <td><code>$item-wp-divider-border-bottom</code></td>

          <td><code>1px solid $list-wp-border-color</code></td>

        <td><p>Bodrer bottom for the divider</p>
</td>
      </tr>

      <tr>
        <td><code>$item-wp-divider-font-size</code></td>

          <td><code>2rem</code></td>

        <td><p>Font size for the divider</p>
</td>
      </tr>

      <tr>
        <td><code>$item-wp-sliding-content-background</code></td>

          <td><code>$list-wp-background-color</code></td>

        <td><p>Background for the sliding content</p>
</td>
      </tr>

    </tbody>
  </table>

</div>



<!-- related link -->

<h2><a class="anchor" name="related" href="#related">Related</a></h2>

<a href="/docs/components#lists">List Component Docs</a>,
<a href="../Item">Item API Docs</a>,
<a href="../../list/List">List API Docs</a><!-- end content block -->


<!-- end body block -->

