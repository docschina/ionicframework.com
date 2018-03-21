---
layout: "fluid/docs_base"
version: "3.9.2"
versionHref: "/docs"
path: ""
category: api
id: "modalcontroller"
title: "ModalController"
header_sub_title: "Ionic API Documentation"
doc: "ModalController"
docType: "class"
show_preview_device: true
preview_device_url: "/docs/demos/src/modal/www/"
angular_controller: APIDemoCtrl
---









<h1 class="api-title">
<a class="anchor" name="modal-controller" href="#modal-controller"></a>

ModalController





</h1>

<a class="improve-v2-docs" href="http://github.com/ionic-team/ionic/edit/master/src/components/modal/modal-controller.ts#L6">
改进这篇文档
</a>






<p>
Modal 是覆盖用户当前页面的内容面板。
通常用于选择或编辑 item。
一个 modal 使用 <code>NavController</code> 将其自身<a href="/docs/api/components/nav/NavController/#present">呈现</a>在根导航堆栈中。它被添加到堆栈中，类似于 <a href="/docs/api/components/nav/NavController/#push">NavController.push</a> 的工作方式。</p>
<p>当一个 modal（或任意其他覆盖层，如 alert 或 actionsheet）被“呈现”到导航控制器时，覆盖层将被添加到应用程序的根导航栏中。在 modal 被呈现之后，从组件实例中通过使用 ViewController 的 <code>dismiss</code> 方法，modal 可以延迟关闭被或“解除”。此外，你可以通过在根导航控制器上使用 <code>pop</code> 来关闭任何覆盖层。Modals 不可重用。当一个 modal 被解除时，它会被销毁。</p>
<p>数据可以通过 <code>Modal.create()</code> 作为第二个参数传递给一个新的 modal。然后可以通过注入 <code>NavParams</code> 的方式从打开的页面访问数据。请注意，作为 modal 打开的页面中没有特殊的“模态框”逻辑，但使用<code>NavParams</code> 就与标准页面没有区别。</p>

















<!-- @usage tag -->

<h2><a class="anchor" name="usage" href="#usage">用法</a></h2>

<pre><code class="lang-ts">import { ModalController, NavParams } from &#39;ionic-angular&#39;;

@Component(...)
class HomePage {

 constructor(public modalCtrl: ModalController) {

 }

 presentProfileModal() {
   let profileModal = this.modalCtrl.create(Profile, { userId: 8675309 });
   profileModal.present();
 }

}

@Component(...)
class Profile {

 constructor(params: NavParams) {
   console.log(&#39;UserId&#39;, params.get(&#39;userId&#39;));
 }

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
<code>create(component,&nbsp;data,&nbsp;opts)</code>


</a>
</h3>

创建一个 modal 来显示。请参阅下面的选项。



<table class="table param-table" style="margin:0;">
  <thead>
    <tr>
      <th>传输</th>
      <th>类型</th>
      <th>详情</th>
    </tr>
  </thead>
  <tbody>

    <tr>
      <td>
        component


      </td>
      <td>

  <code>object</code>
      </td>
      <td>
        <p>Modal 视图</p>


      </td>
    </tr>

    <tr>
      <td>
        data


      </td>
      <td>

  <code>object</code>
      </td>
      <td>
        <p>传递到 Modal 视图的任意数据</p>


      </td>
    </tr>

    <tr>
      <td>
        opts


      </td>
      <td>

  <code>object</code>
      </td>
      <td>
        <p>Modal 选项</p>


      </td>
    </tr>

  </tbody>
</table>






<h2><a class="anchor" name="advanced" href="#advanced">进阶</a></h2>
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
<td>showBackdrop</td>
<td><code>boolean</code></td>
<td>是否显示背景。默认为 true。</td>
</tr>
<tr>
<td>enableBackdropDismiss</td>
<td><code>boolean</code></td>
<td>是否应通过点击背景来解除弹出窗口。默认为 true。</td>
</tr>
<tr>
<td>cssClass</td>
<td><code>string</code></td>
<td>自定义样式的其他类，以空格分隔。</td>
</tr>
</tbody>
</table>
<p>modal 也可以发射数据，这在用于添加或编辑数据时非常有用。例如，配置文件页面可能会在 modal 中向上滑动，并且在提交时，提交按钮可能会传递更新后的配置文件数据，然后关闭 modal。</p>



<pre><code class="lang-ts">import { Component } from &#39;@angular/core&#39;;
import { ModalController, ViewController } from &#39;ionic-angular&#39;;

@Component(...)
class HomePage {

 constructor(public modalCtrl: ModalController) {

 }

 presentContactModal() {
   let contactModal = this.modalCtrl.create(ContactUs);
   contactModal.present();
 }

 presentProfileModal() {
   let profileModal = this.modalCtrl.create(Profile, { userId: 8675309 });
   profileModal.onDidDismiss(data =&gt; {
     console.log(data);
   });
   profileModal.present();
 }

}

@Component(...)
class Profile {

 constructor(public viewCtrl: ViewController) {

 }

 dismiss() {
   let data = { &#39;foo&#39;: &#39;bar&#39; };
   this.viewCtrl.dismiss(data);
 }

}
</code></pre>



  <h2 id="sass-variable-header"><a class="anchor" name="sass-variables" href="#sass-variables">Sass Variables</a></h2>
  <div id="sass-variables" ng-controller="SassToggleCtrl">
  <div class="sass-platform-toggle">



      <a ng-init="setSassPlatform('base')" ng-class="{ active: active === 'base' }" ng-click="setSassPlatform('base')" >All</a>



      <a ng-class="{ active: active === 'ios' }" ng-click="setSassPlatform('ios')">iOS</a>



      <a ng-class="{ active: active === 'md' }" ng-click="setSassPlatform('md')">Material Design</a>



      <a ng-class="{ active: active === 'wp' }" ng-click="setSassPlatform('wp')">Windows Platform</a>



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
        <td><code>$modal-inset-min-width</code></td>

          <td><code>768px</code></td>

        <td><p>Min width of the modal inset</p>
</td>
      </tr>

      <tr>
        <td><code>$modal-inset-min-height-small</code></td>

          <td><code>600px</code></td>

        <td><p>Minimum height of the small modal inset</p>
</td>
      </tr>

      <tr>
        <td><code>$modal-inset-min-height-large</code></td>

          <td><code>768px</code></td>

        <td><p>Minimum height of the large modal inset</p>
</td>
      </tr>

      <tr>
        <td><code>$modal-inset-width</code></td>

          <td><code>600px</code></td>

        <td><p>Width of the large modal inset</p>
</td>
      </tr>

      <tr>
        <td><code>$modal-inset-height-small</code></td>

          <td><code>500px</code></td>

        <td><p>Height of the small modal inset</p>
</td>
      </tr>

      <tr>
        <td><code>$modal-inset-height-large</code></td>

          <td><code>600px</code></td>

        <td><p>Height of the large modal inset</p>
</td>
      </tr>

    </tbody>
  </table>

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
        <td><code>$modal-ios-background-color</code></td>

          <td><code>$background-ios-color</code></td>

        <td><p>Background color for the modal</p>
</td>
      </tr>

      <tr>
        <td><code>$modal-ios-border-radius</code></td>

          <td><code>10px</code></td>

        <td><p>Border radius for the modal</p>
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
        <td><code>$modal-md-background-color</code></td>

          <td><code>$background-md-color</code></td>

        <td><p>Background color for the modal</p>
</td>
      </tr>

      <tr>
        <td><code>$modal-inset-box-shadow-color</code></td>

          <td><code>rgba(0, 0, 0, .4)</code></td>

        <td><p>Box shadow color of the alert</p>
</td>
      </tr>

      <tr>
        <td><code>$modal-inset-box-shadow</code></td>

          <td><code>0 28px 48px $modal-inset-box-shadow-color</code></td>

        <td><p>Box shadow of the alert</p>
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
        <td><code>$modal-wp-background-color</code></td>

          <td><code>$background-wp-color</code></td>

        <td><p>Background color for the modal</p>
</td>
      </tr>

    </tbody>
  </table>

</div>



<!-- related link -->

<h2><a class="anchor" name="related" href="#related">Related</a></h2>

<a href="/docs/components#modals">Modal Component Docs</a><!-- end content block -->


<!-- end body block -->

