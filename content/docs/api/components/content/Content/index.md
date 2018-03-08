---
layout: "fluid/docs_base"
version: "3.9.2"
versionHref: "/docs"
path: ""
category: api
id: "content"
title: "Content"
header_sub_title: "Ionic API Documentation"
doc: "Content"
docType: "class"

---









<h1 class="api-title">
<a class="anchor" name="content" href="#content"></a>

Content
<h3><code>ion-content</code></h3>






</h1>

<a class="improve-v2-docs" href="http://github.com/ionic-team/ionic/edit/master/src/components/content/content.ts#L25">
改进这篇文档
</a>






<p>Content 组件提供了一个易于使用的内容区域和一些有用的方法来控制可滚动区域。
在单个视图（view）组件中应该只有一个 Content 组件。
如果需要额外的可滚动元素，请使用 <a href="../../scroll/Scroll">ionScroll</a>。</p>
<p>内容区域也可以使用 <a href="../../refresher/Refresher">Refresher</a> 组件实现下拉刷新。</p>






<!-- @usage tag -->

<h2><a class="anchor" name="usage" href="#usage">用法</a></h2>

<pre><code class="lang-html">&lt;ion-content&gt;
  Add your content here!
&lt;/ion-content&gt;
</code></pre>
<p>要从页面逻辑中获取对 content 组件的引用，可以使用 Angular 的 <code>@ViewChild</code> 注解：  </p>

<pre><code class="lang-ts">import { Component, ViewChild } from &#39;@angular/core&#39;;
import { Content } from &#39;ionic-angular&#39;;

@Component({...})
export class MyPage{
  @ViewChild(Content) content: Content;

  scrollToTop() {
    this.content.scrollToTop();
  }
}
</code></pre>




<!-- @property tags -->



<!-- instance methods on the class -->

<h2><a class="anchor" name="instance-members" href="#instance-members">实例成员</a></h2>

<div id="addImg"></div>

<h3>
<a class="anchor" name="addImg" href="#addImg">
<code>addImg()</code>


</a>
</h3>











<div id="contentBottom"></div>

<h3>
<a class="anchor" name="contentBottom" href="#contentBottom">
<code>contentBottom</code>


</a>
</h3>

一个数字，表示 content 组件的底部已被调整了多少个像素，可能是 padding 或 margin。这一调整是为了解决页脚所需的空间。









<div class="return-value">
<i class="icon ion-arrow-return-left"></i>
<b>返回：</b>
  <code>number</code>

</div>




<div id="contentHeight"></div>

<h3>
<a class="anchor" name="contentHeight" href="#contentHeight">
<code>contentHeight</code>


</a>
</h3>

可视区域的 Content 高度。这不包括 content 位于溢出区域之外的部分，或者位于页眉和页脚下方的 content 区域
。只读。








<div class="return-value">
<i class="icon ion-arrow-return-left"></i>
<b>返回：</b>
  <code>number</code>

</div>




<div id="contentTop"></div>

<h3>
<a class="anchor" name="contentTop" href="#contentTop">
<code>contentTop</code>


</a>
</h3>

一个数字，表示内容顶部已被调整了多少个像素，可能是 padding or margin。这种调整是为了解决标题所需的空间。









<div class="return-value">
<i class="icon ion-arrow-return-left"></i>
<b>返回：</b>
  <code>number</code>

</div>




<div id="contentWidth"></div>

<h3>
<a class="anchor" name="contentWidth" href="#contentWidth">
<code>contentWidth</code>


</a>
</h3>

Content 宽度，包括因为溢出而在屏幕上不可见的内容。只读。








<div class="return-value">
<i class="icon ion-arrow-return-left"></i>
<b>返回：</b>
  <code>number</code>

</div>




<div id="directionX"></div>

<h3>
<a class="anchor" name="directionX" href="#directionX">
<code>directionX</code>


</a>
</h3>

当前或最后一次已知的水平滚动方向。可能的字符串值包括 `right` 和 `left`。








<div class="return-value">
<i class="icon ion-arrow-return-left"></i>
<b>返回：</b>
  <code>string</code>

</div>




<div id="directionY"></div>

<h3>
<a class="anchor" name="directionY" href="#directionY">
<code>directionY</code>


</a>
</h3>

当前或最后一次已知的垂直滚动方向。可能的字符串值包括 `down` 和 `up`。








<div class="return-value">
<i class="icon ion-arrow-return-left"></i>
<b>返回：</b>
  <code>string</code>

</div>




<div id="getContentDimensions"></div>

<h3>
<a class="anchor" name="getContentDimensions" href="#getContentDimensions">
<code>getContentDimensions()</code>


</a>
</h3>

返回 content 和 scroll 元素的尺寸。






<div class="return-value">
<i class="icon ion-arrow-return-left"></i>
<b>返回：</b>
  <code>object</code>


<table class="table returns-object-table param-table">
      <thead>
        <tr>
          <th>属性</th>
          <th>类型</th>
          <th>详情</th>
        </tr>
      </thead>
      <tbody>

        <tr>
          <td class="fixed-width">
            dimensions.contentHeight
          </td>
          <td>
            <code>number</code>
          </td>
          <td>
            <p>content offsetHeight</p>

          </td>
        </tr>

        <tr>
          <td class="fixed-width">
            dimensions.contentTop
          </td>
          <td>
            <code>number</code>
          </td>
          <td>
            <p>content offsetTop</p>

          </td>
        </tr>

        <tr>
          <td class="fixed-width">
            dimensions.contentBottom
          </td>
          <td>
            <code>number</code>
          </td>
          <td>
            <p>content offsetTop+offsetHeight</p>

          </td>
        </tr>

        <tr>
          <td class="fixed-width">
            dimensions.contentWidth
          </td>
          <td>
            <code>number</code>
          </td>
          <td>
            <p>content offsetWidth</p>

          </td>
        </tr>

        <tr>
          <td class="fixed-width">
            dimensions.contentLeft
          </td>
          <td>
            <code>number</code>
          </td>
          <td>
            <p>content offsetLeft</p>

          </td>
        </tr>

        <tr>
          <td class="fixed-width">
            dimensions.contentRight
          </td>
          <td>
            <code>number</code>
          </td>
          <td>
            <p>content offsetLeft + offsetWidth</p>

          </td>
        </tr>

        <tr>
          <td class="fixed-width">
            dimensions.scrollHeight
          </td>
          <td>
            <code>number</code>
          </td>
          <td>
            <p>scroll scrollHeight</p>

          </td>
        </tr>

        <tr>
          <td class="fixed-width">
            dimensions.scrollTop
          </td>
          <td>
            <code>number</code>
          </td>
          <td>
            <p>scroll scrollTop</p>

          </td>
        </tr>

        <tr>
          <td class="fixed-width">
            dimensions.scrollBottom
          </td>
          <td>
            <code>number</code>
          </td>
          <td>
            <p>scroll scrollTop + scrollHeight</p>

          </td>
        </tr>

        <tr>
          <td class="fixed-width">
            dimensions.scrollWidth
          </td>
          <td>
            <code>number</code>
          </td>
          <td>
            <p>scroll scrollWidth</p>

          </td>
        </tr>

        <tr>
          <td class="fixed-width">
            dimensions.scrollLeft
          </td>
          <td>
            <code>number</code>
          </td>
          <td>
            <p>scroll scrollLeft</p>

          </td>
        </tr>

        <tr>
          <td class="fixed-width">
            dimensions.scrollRight
          </td>
          <td>
            <code>number</code>
          </td>
          <td>
            <p>scroll scrollLeft + scrollWidth</p>

          </td>
        </tr>

      </tbody>
    </table>

</div>




<div id="getFixedElement"></div>

<h3>
<a class="anchor" name="getFixedElement" href="#getFixedElement">
<code>getFixedElement()</code>


</a>
</h3>











<div id="isScrolling"></div>

<h3>
<a class="anchor" name="isScrolling" href="#isScrolling">
<code>isScrolling</code>


</a>
</h3>

content 是否正在滚动。







<div class="return-value">
<i class="icon ion-arrow-return-left"></i>
<b>返回：</b>
  <code>boolean</code>

</div>




<div id="resize"></div>

<h3>
<a class="anchor" name="resize" href="#resize">
<code>resize()</code>


</a>
</h3>

告诉 content 重新计算其尺寸。这应该在动态添加/删除 headers, footers, 或 tabs 后调用。











<div id="scrollHeight"></div>

<h3>
<a class="anchor" name="scrollHeight" href="#scrollHeight">
<code>scrollHeight</code>


</a>
</h3>

Content 高度，包括因为溢出而在屏幕上不可见的内容。只读。








<div class="return-value">
<i class="icon ion-arrow-return-left"></i>
<b>返回：</b>
  <code>number</code>

</div>




<div id="scrollLeft"></div>

<h3>
<a class="anchor" name="scrollLeft" href="#scrollLeft">
<code>scrollLeft</code>


</a>
</h3>

左侧到最左侧可见内容的距离。







<div class="return-value">
<i class="icon ion-arrow-return-left"></i>
<b>返回：</b>
  <code>number</code>

</div>




<div id="scrollTo"></div>

<h3>
<a class="anchor" name="scrollTo" href="#scrollTo">
<code>scrollTo(x,&nbsp;y,&nbsp;duration)</code>


</a>
</h3>

滚动到指定的位置。



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
        x


      </td>
      <td>

  <code>number</code>
      </td>
      <td>
        <p>需要滚动的 x 值。</p>


      </td>
    </tr>

    <tr>
      <td>
        y


      </td>
      <td>

  <code>number</code>
      </td>
      <td>
        <p>需要滚动的 y 值。</p>


      </td>
    </tr>

    <tr>
      <td>
        duration


      </td>
      <td>

  <code>number</code>
      </td>
      <td>
        <p>滚动动画的持续时间（以毫秒为单位）。默认为<code>300</code>。<strong class="tag">可选的</strong></p>


      </td>
    </tr>

  </tbody>
</table>





<div class="return-value">
<i class="icon ion-arrow-return-left"></i>
<b>返回：</b>
  <code>Promise</code> <p>返回滚动完成后的一个确定的（resolved） promise。</p>


</div>




<div id="scrollToBottom"></div>

<h3>
<a class="anchor" name="scrollToBottom" href="#scrollToBottom">
<code>scrollToBottom(duration)</code>


</a>
</h3>

滚动到 content 组件的底部。



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
        duration


      </td>
      <td>

  <code>number</code>
      </td>
      <td>
        <p>滚动动画的持续时间（以毫秒为单位）。默认为<code>300</code>。<strong class="tag">可选的</strong></p>


      </td>
    </tr>

  </tbody>
</table>





<div class="return-value">
<i class="icon ion-arrow-return-left"></i>
<b>返回：</b>
  <code>Promise</code> <p>返回滚动完成后的一个确定的（resolved） promise。</p>


</div>




<div id="scrollToTop"></div>

<h3>
<a class="anchor" name="scrollToTop" href="#scrollToTop">
<code>scrollToTop(duration)</code>


</a>
</h3>

滚动到 content 组件的顶部。



<table class="table param-table" style="margin:0;">
  <thead>
    <tr>
      <th>Param</th>
      <th>Type</th>
      <th>Details</th>
    </tr>
  </thead>
  <tbody>

    <tr>
      <td>
        duration


      </td>
      <td>

  <code>number</code>
      </td>
      <td>
        <p>滚动动画的持续时间（以毫秒为单位）。默认为<code>300</code>。<strong class="tag">可选的</strong></p>


      </td>
    </tr>

  </tbody>
</table>





<div class="return-value">
<i class="icon ion-arrow-return-left"></i>
<b>返回：</b>
  <code>Promise</code> <p>返回滚动完成后的一个确定的（resolved） promise。</p>


</div>




<div id="scrollTop"></div>

<h3>
<a class="anchor" name="scrollTop" href="#scrollTop">
<code>scrollTop</code>


</a>
</h3>

content 的顶部到最顶部的可见内容距离。







<div class="return-value">
<i class="icon ion-arrow-return-left"></i>
<b>返回：</b>
  <code>number</code>

</div>




<div id="scrollWidth"></div>

<h3>
<a class="anchor" name="scrollWidth" href="#scrollWidth">
<code>scrollWidth</code>


</a>
</h3>

Content 宽度，包括因为溢出而不可见的内容。只读。








<div class="return-value">
<i class="icon ion-arrow-return-left"></i>
<b>返回：</b>
  <code>number</code>

</div>



<!-- input methods on the class -->
<h2><a class="anchor" name="input-properties" href="#input-properties">Input Properties</a></h2>
<table class="table param-table" style="margin:0;">
  <thead>
    <tr>
      <th>Attr</th>
      <th>Type</th>
      <th>Details</th>
    </tr>
  </thead>
  <tbody>

    <tr>
      <td>fullscreen</td>
      <td><code>boolean</code></td>
      <td><p> If true, the content will scroll behind the headers
and footers. This effect can easily be seen by setting the toolbar
to transparent.</p>
</td>
    </tr>

    <tr>
      <td>scrollDownOnLoad</td>
      <td><code>boolean</code></td>
      <td><p> If true, the content will scroll down on load.</p>
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
      <td>ionScroll</td>
      <td><p>在每个滚动事件中都会触发。</p>
</td>
    </tr>

    <tr>
      <td>ionScrollEnd</td>
      <td><p>当滚动完成后触发。</p>
</td>
    </tr>

    <tr>
      <td>ionScrollStart</td>
      <td><p>当滚动首次开始时触发。</p>
</td>
    </tr>

  </tbody>
</table><h2><a class="anchor" name="advanced" href="#advanced">进阶</a></h2>
<h3 id="scroll-events">Scroll 事件</h3>
<p>滚动事件发生在 Angular 的 Zones 之外。出于性能原因。所以如果你试图将一个值绑定到任何滚动事件上，它需要包装在一个 <code>zone.run()</code> 里。</p>


<pre><code class="lang-ts">import { Component, NgZone } from &#39;@angular/core&#39;;
@Component({
  template: `
    &lt;ion-header&gt;
      &lt;ion-navbar&gt;
        &lt;ion-title&gt;{{scrollAmount}}&lt;/ion-title&gt;
      &lt;/ion-navbar&gt;
    &lt;/ion-header&gt;
    &lt;ion-content (ionScroll)=&quot;scrollHandler($event)&quot;&gt;
       &lt;p&gt; Some realllllllly long content &lt;/p&gt;
    &lt;/ion-content&gt;
`})
class E2EPage {
 public scrollAmount = 0;
 constructor( public zone: NgZone){}
 scrollHandler(event) {
   console.log(`ScrollEvent: ${event}`)
   this.zone.run(()=&gt;{
     // 因为 scrollAmount 是数据绑定的，
     // 更新需要在 zone 中发生
     this.scrollAmount++
   })
 }
}
</code></pre>
<p>这适用于任何滚动事件，而不仅仅是 <code>ionScroll</code>。</p>
<h3 id="resizing-the-content">调整 content 的尺寸</h3>
<p>如果 <code>ion-header</code>, <code>ion-footer</code> 或 <code>ion-tabbar</code>的高度是动态变化的，则必须调用 <code>content.resize()</code> 来更新 Content 的布局。</p>


<pre><code class="lang-ts">@Component({
  template: `
    &lt;ion-header&gt;
      &lt;ion-navbar&gt;
        &lt;ion-title&gt;Main Navbar&lt;/ion-title&gt;
      &lt;/ion-navbar&gt;
      &lt;ion-toolbar *ngIf=&quot;showToolbar&quot;&gt;
        &lt;ion-title&gt;Dynamic Toolbar&lt;/ion-title&gt;
      &lt;/ion-toolbar&gt;
    &lt;/ion-header&gt;
    &lt;ion-content&gt;
      &lt;button ion-button (click)=&quot;toggleToolbar()&quot;&gt;Toggle Toolbar&lt;/button&gt;
    &lt;/ion-content&gt;
`})

class E2EPage {
  @ViewChild(Content) content: Content;
  showToolbar: boolean = false;

  toggleToolbar() {
    this.showToolbar = !this.showToolbar;
    this.content.resize();
  }
}
</code></pre>
<p>滚动到特定的位置</p>
<pre><code class="lang-ts">import { Component, ViewChild } from &#39;@angular/core&#39;;
import { Content } from &#39;ionic-angular&#39;;

@Component({
  template: `&lt;ion-content&gt;
               &lt;button ion-button (click)=&quot;scrollTo()&quot;&gt;Down 500px&lt;/button&gt;
             &lt;/ion-content&gt;`
)}
export class MyPage{
  @ViewChild(Content) content: Content;

  scrollTo() {
    // 将 scrollLeft 设置为0px，将 scrollTop 设置为500px
    // 滚动时间持续200ms
    this.content.scrollTo(0, 500, 200);
  }
}
</code></pre>



  <h2 id="sass-variable-header"><a class="anchor" name="sass-variables" href="#sass-variables">Sass Variables</a></h2>
  <div id="sass-variables" ng-controller="SassToggleCtrl">
  <div class="sass-platform-toggle">

    <h3 ng-init="setSassPlatform('ios')">iOS</h3>

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
        <td><code>$content-ios-outer-background</code></td>

          <td><code>#efeff4</code></td>

        <td><p>Background color of the outer content</p>
</td>
      </tr>

      <tr>
        <td><code>$content-ios-transition-background</code></td>

          <td><code>#000</code></td>

        <td><p>Background color of the content when making transition</p>
</td>
      </tr>

    </tbody>
  </table>

</div>



<!-- related link --><!-- end content block -->


<!-- end body block -->

