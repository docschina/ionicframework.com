---
layout: "fluid/docs_base"
version: "3.9.2"
versionHref: "/docs"
path: ""
category: api
id: "config"
title: "Config"
header_sub_title: "Ionic API Documentation"
doc: "Config"
docType: "class"
show_preview_device: true
preview_device_url: "/docs/demos/src/config/www/"
angular_controller: APIDemoCtrl
---









<h1 class="api-title">
<a class="anchor" name="config" href="#config"></a>

Config





</h1>

<a class="improve-v2-docs" href="http://github.com/ionic-team/ionic/edit/master/src/config/config.ts#L10">
改进这篇文档
</a>






<p>Config 允许你配置整个应用程序或特定平台。你可以在此处设置 tab 位置，icon 模式，动画等。</p>

<pre><code class="lang-ts">import { IonicApp, IonicModule } from &#39;ionic-angular&#39;;

@NgModule({
  declarations: [ MyApp ],
  imports: [
    BrowserModule,
    IonicModule.forRoot(MyApp, {
      backButtonText: &#39;Go Back&#39;,
      iconMode: &#39;ios&#39;,
      modalEnter: &#39;modal-slide-in&#39;,
      modalLeave: &#39;modal-slide-out&#39;,
      tabsPlacement: &#39;bottom&#39;,
      pageTransition: &#39;ios-transition&#39;
    }, {}
  )],
  bootstrap: [IonicApp],
  entryComponents: [ MyApp ],
  providers: []
})
</code></pre>
<p>Config 可以在多个层次上被覆盖，从而实现更细化的配置。下面是一个例子，其中一个应用可以覆盖任何我们想要的基于平台的设置。</p>

<pre><code class="lang-ts">import { IonicModule } from &#39;ionic-angular&#39;;

@NgModule({
  ...
  imports: [
    BrowserModule,
    IonicModule.forRoot(MyApp, {
      tabsPlacement: &#39;bottom&#39;,
      platforms: {
        ios: {
          tabsPlacement: &#39;top&#39;,
        }
      }
    }, {}
  )],
  ...
})
</code></pre>
<p>我们也可以在组件级别配置这些值。采用 <code>tabsPlacement</code>，我们可以将其配置为 <code>ion-tabs</code> 上的属性。</p>

<pre><code class="lang-html">&lt;ion-tabs tabsPlacement=&quot;top&quot;&gt;
  &lt;ion-tab tabTitle=&quot;Dash&quot; tabIcon=&quot;pulse&quot; [root]=&quot;tabRoot&quot;&gt;&lt;/ion-tab&gt;
&lt;/ion-tabs&gt;
</code></pre>
<p>我们可以配置的最后一种方式是通过 URL 查询字符串。这对在浏览器中进行测试是很有用的。只需将 <code>?ionic&lt;PROPERTYNAME&gt;=&lt;value&gt;</code> 添加到 url 即可。</p>

<pre><code class="lang-bash">http://localhost:8100/?ionicTabsPlacement=bottom
</code></pre>
<p>任何值都可以添加到 config 中，然后在任何组件中查找。</p>
<pre><code class="lang-js">config.set(&#39;ios&#39;, &#39;favoriteColor&#39;, &#39;green&#39;);

// 来自你应用中的任意页面：
config.get(&#39;favoriteColor&#39;); // &#39;green&#39; 当平台是 iOS 时
</code></pre>
<p>config 值可以来自任何地方，可以是任意东西，但每种模式都有默认值。<a href="../../../theming/platform-specific-styles/">主题</a>文档具有默认模式配置的表格。下面的表格显示了每个属性的描述以及它所控制的内容。</p>



<table>
<thead>
<tr>
<th>Config 属性</th>
<th>类型</th>
<th>详情</th>
</tr>
</thead>
<tbody>
<tr>
<td><code>activator</code></td>
<td><code>string</code></td>
<td>用于按钮，改变按下按钮的效果。可用选项：<code>&quot;ripple&quot;</code>, <code>&quot;highlight&quot;</code>。</td>
</tr>
<tr>
<td><code>actionSheetEnter</code></td>
<td><code>string</code></td>
<td>呈现 action sheet 时要使用的过渡效果（transition）的名称。</td>
</tr>
<tr>
<td><code>actionSheetLeave</code></td>
<td><code>string</code></td>
<td>关闭 action sheet 时要使用的过渡效果（transition）的名称。</td>
</tr>
<tr>
<td><code>alertEnter</code></td>
<td><code>string</code></td>
<td>呈现 alert 时要使用的过渡效果（transition）的名称。</td>
</tr>
<tr>
<td><code>alertLeave</code></td>
<td><code>string</code></td>
<td>关闭 alert 时要使用的过渡效果（transition）的名称。</td>
</tr>
<tr>
<td><code>backButtonText</code></td>
<td><code>string</code></td>
<td>navbar 中返回按钮图标显示的文本。</td>
</tr>
<tr>
<td><code>backButtonIcon</code></td>
<td><code>string</code></td>
<td>用作返回按钮图标的图标。</td>
</tr>
<tr>
<td><code>iconMode</code></td>
<td><code>string</code></td>
<td>整个应用程序中用于所有图标的模式。可用选项： <code>&quot;ios&quot;</code>, <code>&quot;md&quot;</code>。</td>
</tr>
<tr>
<td><code>locationStrategy</code></td>
<td><code>string</code></td>
<td>为了使用 Deeplinking 时移除 hashbangs，设置为 &#39;path&#39 。</td>
</tr>
<tr>
<td><code>loadingEnter</code></td>
<td><code>string</code></td>
<td>呈现 loading 时要使用的过渡效果（transition）的名称。</td>
</tr>
<tr>
<td><code>loadingLeave</code></td>
<td><code>string</code></td>
<td>关闭 loading 时要使用的过渡效果（transition）的名称。</td>
</tr>
<tr>
<td><code>menuType</code></td>
<td><code>string</code></td>
<td>要显示的菜单的类型。可用选项： <code>&quot;overlay&quot;</code>, <code>&quot;reveal&quot;</code>, <code>&quot;push&quot;</code>。</td>
</tr>
<tr>
<td><code>modalEnter</code></td>
<td><code>string</code></td>
<td>呈现 modal 时要使用的过渡效果（transition）的名称。</td>
</tr>
<tr>
<td><code>modalLeave</code></td>
<td><code>string</code></td>
<td>关闭 modal 时要使用的过渡效果（transition）的名称。</td>
</tr>
<tr>
<td><code>mode</code></td>
<td><code>string</code></td>
<td>在整个应用程序中使用的模式。</td>
</tr>
<tr>
<td><code>pageTransition</code></td>
<td><code>string</code></td>
<td>改变页面时要使用的过渡效果（transition）的名称。可选选项有：<code>&quot;ios-transition&quot;</code>, <code>&quot;md-transition&quot;</code>, <code>&quot;wp-transition&quot;</code>。</td>
</tr>
<tr>
<td><code>pickerEnter</code></td>
<td><code>string</code></td>
<td>呈现 picker 时要使用的过渡效果（transition）的名称。</td>
</tr>
<tr>
<td><code>pickerLeave</code></td>
<td><code>string</code></td>
<td>关闭 picker 时要使用的过渡效果（transition）的名称。</td>
</tr>
<tr>
<td><code>popoverEnter</code></td>
<td><code>string</code></td>
<td>呈现 popover 时要使用的过渡效果（transition）的名称。</td>
</tr>
<tr>
<td><code>popoverLeave</code></td>
<td><code>string</code></td>
<td>关闭 popover 时要使用的过渡效果（transition）的名称。</td>
</tr>
<tr>
<td><code>spinner</code></td>
<td><code>string</code></td>
<td>未定义名称时使用的默认 spinner。</td>
</tr>
<tr>
<td><code>swipeBackEnabled</code></td>
<td><code>boolean</code></td>
<td>是否启用原生 iOS 刷回后退功能。</td>
</tr>
<tr>
<td><code>tabsHighlight</code></td>
<td><code>boolean</code></td>
<td>选择时是否在 tab 下显示高亮线。</td>
</tr>
<tr>
<td><code>tabsLayout</code></td>
<td><code>string</code></td>
<td>用于所有 tabs 的布局。可用选项：<code>&quot;icon-top&quot;</code>, <code>&quot;icon-start&quot;</code>, <code>&quot;icon-end&quot;</code>, <code>&quot;icon-bottom&quot;</code>, <code>&quot;icon-hide&quot;</code>, <code>&quot;title-hide&quot;</code>。</td>
</tr>
<tr>
<td><code>tabsPlacement</code></td>
<td><code>string</code></td>
<td>tab 相对于 content 的位置。可用选项：<code>&quot;top&quot;</code>, <code>&quot;bottom&quot;</code>。</td>
</tr>
<tr>
<td><code>tabsHideOnSubPages</code></td>
<td><code>boolean</code></td>
<td>是否隐藏子页面上的 tabs。如果为 <code>true</code>，则不会显示子页面上的 tabs。</td>
</tr>
<tr>
<td><code>toastEnter</code></td>
<td><code>string</code></td>
<td>呈现 toast 时要使用的过渡效果（transition）的名称。</td>
</tr>
<tr>
<td><code>toastLeave</code></td>
<td><code>string</code></td>
<td>关闭 popover 时要使用的过渡效果（transition）的名称。</td>
</tr>
</tbody>
</table>




<!-- @usage tag -->


<!-- @property tags -->



<!-- instance methods on the class -->

<h2><a class="anchor" name="instance-members" href="#instance-members">实例成员</a></h2>

<div id="get"></div>

<h3>
<a class="anchor" name="get" href="#get">
<code>get(key,&nbsp;fallbackValue)</code>


</a>
</h3>

给定一个键，返回一个配置值。


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
        key


      </td>
      <td>

  <code>string</code>
      </td>
      <td>
        <p>配置值的键 <strong class="tag">可选的</strong></p>


      </td>
    </tr>

    <tr>
      <td>
        fallbackValue


      </td>
      <td>

  <code>any</code>
      </td>
      <td>
        <p>未找到配置值或者配置值为 <code>null</code> 时使用的回退值。回退值默认为 <code>null</code>。<strong class="tag">可选的</strong></p>




      </td>
    </tr>

  </tbody>
</table>








<div id="getBoolean"></div>

<h3>
<a class="anchor" name="getBoolean" href="#getBoolean">
<code>getBoolean(key,&nbsp;fallbackValue)</code>


</a>
</h3>

与 `get()` 相同，但总是返回一个布尔值。如果 `get()` 的值为 `null`，则它将返回默认为 `false` 的 `fallbackValue`。否则 `getBoolean()` 将返回配置值是否为真值（truthy），则 。如果配置值是字符串值 `true` ，它也会返回 `true` 。






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
        key


      </td>
      <td>

  <code>string</code>
      </td>
      <td>
        <p>配置值的键 <strong class="tag">可选的</strong></p>


      </td>
    </tr>

    <tr>
      <td>
        fallbackValue


      </td>
      <td>

  <code>boolean</code>
      </td>
      <td>
        <p>未找到配置值或者配置值为 <code>null</code> 时使用的回退值。回退值默认为 <code>false</code>。<strong class="tag">可选的</strong></p>



      </td>
    </tr>

  </tbody>
</table>








<div id="getNumber"></div>

<h3>
<a class="anchor" name="getNumber" href="#getNumber">
<code>getNumber(key,&nbsp;fallbackValue)</code>


</a>
</h3>

与 `get()` 相同，但总是返回一个数字，把来自 `get()` 的值使用 `parseFloat()` 接收。如果解析后的结果为 `NaN`，说明这个结果不是合法值，它会返回默认为 `NaN` 的 `fallbackValue`。






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
        key


      </td>
      <td>

  <code>string</code>
      </td>
      <td>
        <p>配置值的键 <strong class="tag">可选的</strong></p>


      </td>
    </tr>

    <tr>
      <td>
        fallbackValue


      </td>
      <td>

  <code>number</code>
      </td>
      <td>
        <p>配置值转成 <code>NaN</code>使用的回退值。 回退值默认为 <code>NaN</code>。<strong class="tag">可选的</strong></p>



      </td>
    </tr>

  </tbody>
</table>








<div id="set"></div>

<h3>
<a class="anchor" name="set" href="#set">
<code>set(platform,&nbsp;key,&nbsp;value)</code>


</a>
</h3>

设置单个的配置值。


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
        platform


      </td>
      <td>

  <code>string</code>
      </td>
      <td>
        <p>该配置值应适配的平台（&#39;ios&#39; 或 &#39;android&#39;）。如果留空，则会将配置值应用于所有平台。<strong class="tag">可选的</strong></p>


      </td>
    </tr>

    <tr>
      <td>
        key


      </td>
      <td>

  <code>string</code>
      </td>
      <td>
        <p>用于在稍后的时间点查找该值的键。<strong class="tag">可选的</strong></p>


      </td>
    </tr>

    <tr>
      <td>
        value


      </td>
      <td>

  <code>string</code>
      </td>
      <td>
        <p>被存储的配置值。<strong class="tag">可选的</strong></p>


      </td>
    </tr>

  </tbody>
</table>











<!-- related link --><!-- end content block -->


<!-- end body block -->

