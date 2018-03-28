---
layout: "fluid/docs_base"
version: "3.9.2"
versionHref: "/docs"
path: ""
category: api
id: "item"
title: "Item"
header_sub_title: "Ionic API Documentation"
doc: "Item"
docType: "class"
show_preview_device: true
preview_device_url: "/docs/demos/src/item/www/"
angular_controller: APIDemoCtrl
---









<h1 class="api-title">
<a class="anchor" name="item" href="#item"></a>

Item
<h3><code>ion-list-header,ion-item,[ion-item],ion-item-divider</code></h3>






</h1>

<a class="improve-v2-docs" href="http://github.com/ionic-team/ionic/edit/v3/src/components/item/item.ts#L8">
改进这篇文档
</a>






<p>一个 item 可以包含文本，图像和其他任意东西。通常它被放在有其他 items 的列表里。它可以被轻松地刷动（swiped），删除，重新排列，编辑等等。如果需要通过手势操作该项目，则只需要一个项目在<a href="../../list/List">列表</a>中。它需要一个 <a href="../ItemSliding">ItemSliding</a> 包装元素才能被刷过。</p>
<h2 id="common-usage">普通用法</h2>
<p>有少量元素可以被视为 item，
但并非所有元素都被设计为相同的样式。
基本的 item 可以写成 <code>&lt;ion-item&gt;</code> 元素，或者可以通过添加 <code>ion-item</code> 作为属性添加到任何元素。列表头和 item 分隔符虽然样式不同，但也是 item，可以分别编写为 <code>&lt;ion-list-header&gt;</code> 和 <code>&lt;ion-item-divider&gt;</code>。</p>




<h3><a class="anchor" name="as-an-element" href="#as-an-element">作为一个元素</a></h3>

<p>当基本 item 不可点击时，应将其写为 <code>&lt;ion-item&gt;</code> 元素。</p>
<pre><code class="lang-html">&lt;ion-item&gt;
  Item
&lt;/ion-item&gt;
</code></pre>
<p>列表头应该写为 <code>&lt;ion-list-header&gt;</code>。</p>
<pre><code class="lang-html">&lt;ion-list-header&gt;
  List Header
&lt;/ion-list-header&gt;
</code></pre>
<p>项目分隔线应该写成 <code>&lt;ion-item-divider&gt;</code>。</p>
<pre><code class="lang-html">&lt;ion-item-divider&gt;
  Item Divider
&lt;/ion-item-divider&gt;
</code></pre>
<h3><a class="anchor" name="as-an-attribute" href="#as-an-attribute">作为属性</a></h3>

<p>当 item 可以被点击或触击(tapped)时，属性 <code>ion-item</code> 应该被添加到一个 <code>&lt;button&gt;</code>。当项目需要包含 <code>href</code> 时，它应该被添加到 <code>&lt;a&gt;</code> 元素。它可以作为一个属性添加到任意元素上应用 item 的样式。</p>


<pre><code class="lang-html">&lt;button ion-item (click)=&quot;buttonClick()&quot;&gt;
  Button Item
&lt;/button&gt;

&lt;a ion-item href=&quot;https://www.ionicframework.com&quot;&gt;
  Anchor Item
&lt;/a&gt;
</code></pre>
<p>注意：不要将 <code>ion-item</code> 作为属性添加到 <code>&lt;ion-list-header&gt;</code> 或 <code>&lt;ion-item-divider&gt;</code> 元素，因为它们已经是 item，它们的样式将会更改为基本的 item 样子。</p>
<h2 id="detail-arrows">详情箭头</h2>
<p>默认情况下，具有 <code>ion-item</code> 属性的 <code>&lt;button&gt;</code> 和 <code>&lt;a&gt;</code> 元素将在 <code>ios</code> 模式下显示右箭头图标。要隐藏这些元素中任意一个右箭头图标，请将 <code>detail-none</code> 属性添加到该 item。要在非原生显示的元素上显示右箭头图标，请将 <code>detail-push</code> 属性添加到该 item。</p>




<pre><code class="lang-html">&lt;ion-item detail-push&gt;
  Item with Detail Arrow
&lt;/ion-item&gt;

&lt;button ion-item (click)=&quot;buttonClick()&quot;&gt;
  Button Item with Detail Arrow
&lt;/button&gt;

&lt;a ion-item detail-none href=&quot;https://www.ionicframework.com&quot;&gt;
  Anchor Item with no Detail Arrow
&lt;/a&gt;
</code></pre>
<p> <code>md</code> 和 <code>wp</code> 模式默认不启用此功能，但可以通过将 Sass 变量 <code>$item-md-detail-push-show</code> 和 <code>$item-wp-detail-push-show</code> 分别设置为 true 来启用此功能。通过将 <code>$item-ios-detail-push-show</code> 设置为 <code>false</code> 来禁用 ios。有关覆盖 Sass 变量的更多信息，请参阅 <a href="https://ionicframework.com/docs/theming/overriding-ionic-variables/">主题文档</a>。</p>
<h2 id="item-placement">Item 布置</h2>
<p>Items 严重依赖内容投影来定位内容。 item 根据元素或属性抓取内容并将其定位。这种逻辑使得使用简单易懂的标记编写复杂的项目成为可能，而不必担心元素的样式和定位。</p>
<p>下面的图表详细说明了 item 要查找的属性以及将该元素放置在 item 内的位置：</p>








<table>
<thead>
<tr>
<th>属性</th>
<th>描述</th>
</tr>
</thead>
<tbody>
<tr>
<td><code>item-start</code></td>
<td>放置在所有 inner item 之外的其他元素的左侧。</td>
</tr>
<tr>
<td><code>item-end</code></td>
<td>放置在所有 inner item 之内，input 包装之外的其他元素的右侧。</td>
</tr>
<tr>
<td><code>item-content</code></td>
<td>放置在所有 input 包装之内的<code>ion-label</code>的右侧。</td>
</tr>
</tbody>
</table>
<h3><a class="anchor" name="checkboxes-radios-and-toggles" href="#checkboxes-radios-and-toggles">Checkboxes, Radios 和 Toggles</a></h3>

<p><a href="../../checkbox/Checkbox">Checkboxes</a> 与 <code>item-start</code> 属性位于同一位置。
<a href="../../radio/RadioButton">Radios</a> 和 <a href="../../toggle/Toggle">Toggles</a> 与 <code>item-end</code> 属性位于同一位置。
通过添加 <code>item-start</code> 或 <code>item-end</code> 属性，
所有的这些组件都可以有不同的定位。</p>
<h3><a class="anchor" name="content-and-inputs" href="#content-and-inputs">Content 和 Inputs</a></h3>

<p>A <a href="../../label/Label">Label</a> 放置在所有 content 和 input 左侧的 item 里。
以下组件都放置在与 <code>item-content</code> 属性相同的位置：
<a href="../../select/Select">Select</a>,<a href="../../input/Input">Input</a>, <a href="../../input/TextArea">TextArea</a>, <a href="../../datetime/DateTime">DateTime</a>,和 <a href="../../range/Range">Range</a>。</p>
<p>任何直接放置在 <code>&lt;ion-item&gt;</code> 中的元素都没有前面提到的属性，
并且不是以上元素，
它们将放置在 <a href="../../label/Label">Label</a> 内。</p>
<h3><a class="anchor" name="text-alignment" href="#text-alignment">文本对齐</a></h3>

<p>默认情况下，Items 会将文本向左对齐，并在文本宽于 item 时添加省略号。查看<a href="../../../../theming/css-utilities/">实用属性文档</a> 以获取可添加到 <code>ion-item</code> 以转换文本的属性。</p>






<!-- @usage tag -->

<h2><a class="anchor" name="usage" href="#usage">用法</a></h2>

<pre><code class="lang-html">&lt;ion-list&gt;

  &lt;ion-list-header&gt;
    Header
  &lt;/ion-list-header&gt;

  &lt;ion-item&gt;
    Item
  &lt;/ion-item&gt;

  &lt;ion-item detail-push&gt;
    Item with Detail Arrow
  &lt;/ion-item&gt;

  &lt;button ion-item (click)=&quot;buttonClick()&quot;&gt;
    Button Item
  &lt;/button&gt;

  &lt;ion-item-divider&gt;
    Item Divider
  &lt;/ion-item-divider&gt;

  &lt;button ion-item detail-none (click)=&quot;buttonClick()&quot;&gt;
    Button Item with no Detail Arrow
  &lt;/button&gt;

  &lt;a ion-item href=&quot;https://www.ionicframework.com&quot;&gt;
    Anchor Item
  &lt;/a&gt;

  &lt;ion-item no-lines&gt;
    Item with no border
  &lt;/ion-item&gt;

  &lt;ion-item text-wrap&gt;
    Multiline text that should wrap when it is too long
    to fit on one line in the item.
  &lt;/ion-item&gt;

&lt;/ion-list&gt;
</code></pre>




<!-- @property tags -->



<!-- instance methods on the class --><h2><a class="anchor" name="advanced" href="#advanced">进阶</a></h2>
<pre><code class="lang-html">&lt;ion-list&gt;

  &lt;!-- List header with buttons on each side --&gt;
  &lt;ion-list-header&gt;
    &lt;button ion-button item-start (click)=&quot;buttonClick()&quot;&gt;Button&lt;/button&gt;
    List Header
    &lt;button ion-button outline item-end (click)=&quot;buttonClick()&quot;&gt;Outline&lt;/button&gt;
  &lt;/ion-list-header&gt;

  &lt;!-- Loops through and creates multiple items --&gt;
  &lt;ion-item *ngFor=&quot;let item of items&quot;&gt;
    Item {% raw %}{{item}}{% endraw %}
  &lt;/ion-item&gt;

  &lt;!-- Button item with an icon on the left --&gt;
  &lt;button ion-item&gt;
    &lt;ion-icon name=&quot;star&quot; item-start&gt;&lt;/ion-icon&gt;
    Button Item
  &lt;/button&gt;

  &lt;!-- Item with a label and content --&gt;
  &lt;ion-item&gt;
    &lt;ion-label&gt;
      Item Label
    &lt;/ion-label&gt;
    &lt;div item-content&gt;
      Item Content next to the label
    &lt;/div&gt;
  &lt;/ion-item&gt;

  &lt;!-- Item with left and right buttons --&gt;
  &lt;ion-item&gt;
    &lt;button ion-button item-start (click)=&quot;buttonClick()&quot;&gt;Button&lt;/button&gt;
    Item
    &lt;button ion-button outline item-end (click)=&quot;buttonClick()&quot;&gt;Outline&lt;/button&gt;
  &lt;/ion-item&gt;

  &lt;!-- Item divider with a right button --&gt;
  &lt;ion-item-divider&gt;
    Item Divider
    &lt;button ion-button item-end&gt;Button&lt;/button&gt;
  &lt;/ion-item-divider&gt;

  &lt;!-- Disabled button item with left and right buttons --&gt;
  &lt;button ion-item disabled&gt;
    &lt;button ion-button item-start (click)=&quot;buttonClick()&quot;&gt;
      &lt;ion-icon name=&quot;home&quot;&gt;&lt;/ion-icon&gt;
      Left Icon
    &lt;/button&gt;
    Disabled Button Item
    &lt;button ion-button outline item-end (click)=&quot;buttonClick()&quot;&gt;
      &lt;ion-icon name=&quot;star&quot;&gt;&lt;/ion-icon&gt;
      Left Icon
    &lt;/button&gt;
  &lt;/button&gt;

  &lt;!-- Item with an avatar on the left and button on the right --&gt;
  &lt;ion-item&gt;
    &lt;ion-avatar item-start&gt;
      &lt;img src=&quot;img/my-avatar.png&quot;&gt;
    &lt;/ion-avatar&gt;
    Avatar Item
    &lt;button ion-button outline item-end&gt;View&lt;/button&gt;
  &lt;/ion-item&gt;

  &lt;!-- Item with a thumbnail on the right --&gt;
  &lt;ion-item&gt;
    &lt;h2&gt;Item&lt;/h2&gt;
    &lt;p&gt;Item Paragraph&lt;/p&gt;
    &lt;ion-thumbnail item-end&gt;
      &lt;img src=&quot;img/my-thumbnail.png&quot;&gt;
    &lt;/ion-thumbnail&gt;
  &lt;/ion-item&gt;

  &lt;!-- Sliding item --&gt;
  &lt;ion-item-sliding&gt;
    &lt;ion-item&gt;
      Item
    &lt;/ion-item&gt;
    &lt;ion-item-options&gt;
      &lt;button ion-button color=&quot;primary&quot; (click)=&quot;archive()&quot;&gt;Archive&lt;/button&gt;
    &lt;/ion-item-options&gt;
  &lt;/ion-item-sliding&gt;

&lt;/ion-list&gt;
</code></pre>



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
<a href="../../list/List">List API Docs</a>,
<a href="../ItemSliding">ItemSliding API Docs</a><!-- end content block -->


<!-- end body block -->

