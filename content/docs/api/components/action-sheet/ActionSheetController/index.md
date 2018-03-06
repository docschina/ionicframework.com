---
layout: "fluid/docs_base"
version: "3.9.2"
versionHref: "/docs"
path: ""
category: api
id: "actionsheetcontroller"
title: "ActionSheetController"
header_sub_title: "Ionic API Documentation"
doc: "ActionSheetController"
docType: "class"
show_preview_device: true
preview_device_url: "/docs/demos/src/action-sheet/www/"
angular_controller: APIDemoCtrl 
---









<h1 class="api-title">
<a class="anchor" name="action-sheet-controller" href="#action-sheet-controller"></a>

ActionSheetController





</h1>

<a class="improve-v2-docs" href="http://github.com/ionic-team/ionic/edit/master/src/components/action-sheet/action-sheet-controller.ts#L5">
Improve this doc
</a>






<p>每个 Action Sheet 组件都是一个能让用户从一组选项中进行选择的对话框。它会在顶部显示应用的内容，并且在用户恢复与应用程序交互之前，必须由用户手动解除。在 <code>ios</code> 模式下，危险的（破坏性）选项是显而易见的。使用简单的方法就可以取消 action sheet，例如点击背景或在桌面上按下 Esc 键。</p>
<p>一个 action sheet 是由一组 <code>buttons</code> 创建的，每个按钮都包含其 <code>text</code> 属性，以及可选的 <code>handle</code> 和 <code>role</code>。如果处理函数返回 <code>false</code> ，则 Action Sheet 组件不会被解除。 Action Sheet 组件还可以有 <code>title</code>, <code>subTitle</code> 和一个 <code>icon</code>。</p>
<p>按钮的 <code>role</code> 属性可以是 <code>destructive</code> 或者 <code>cancel</code>。没有 role 属性的按钮将根据平台显示默认的外观。具有 <code>cancel</code> role 的按钮将始终作为底部按钮加载，无论它们位于数组中的什么位置。所有其他的按钮将按照它们添加到 <code>buttons</code> 数组的顺序显示。注意：我们建议 <code>destructive</code> 按钮始终是数组中的第一个按钮，使其成为顶部按钮。另外，如果通过点击背景解除了 Action Sheet 组件，那么它将从具有 cancel role 的按钮中触发处理函数。</p>
<p>你可以将所有 Action Sheet 组件的选项传递给 create 方法的第一个参数： <code>ActionSheet.create(opts)</code>。否则， Action Sheet 组件的实例会调用方法来添加选项，比如 <code>setTitle()</code> 或 <code>addButton()</code>。</p>





















<!-- @usage tag -->

<h2><a class="anchor" name="usage" href="#usage">用法</a></h2>

<pre><code class="lang-ts">import { ActionSheetController } from &#39;ionic-angular&#39;

export class MyClass{

 constructor(public actionSheetCtrl: ActionSheetController) {}

 presentActionSheet() {
   let actionSheet = this.actionSheetCtrl.create({
     title: &#39;Modify your album&#39;,
     buttons: [
       {
         text: &#39;Destructive&#39;,
         role: &#39;destructive&#39;,
         handler: () =&gt; {
           console.log(&#39;Destructive clicked&#39;);
         }
       },
       {
         text: &#39;Archive&#39;,
         handler: () =&gt; {
           console.log(&#39;Archive clicked&#39;);
         }
       },
       {
         text: &#39;Cancel&#39;,
         role: &#39;cancel&#39;,
         handler: () =&gt; {
           console.log(&#39;Cancel clicked&#39;);
         }
       }
     ]
   });

   actionSheet.present();
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
<code>create(opts)</code>
  

</a>
</h3>

打开一个带有标题，子标题和一组按钮的 action sheet 


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
        
  <code>ActionSheetOptions</code>
      </td>
      <td>
        <p>Action sheet 选项</p>

        
      </td>
    </tr>
    
  </tbody>
</table>






<h2><a class="anchor" name="advanced" href="#advanced">进阶</a></h2>
<p>ActionSheet 创建选项</p>
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
<td>title</td>
<td><code>string</code></td>
<td>Action Sheet 的标题</td>
</tr>
<tr>
<td>subTitle</td>
<td><code>string</code></td>
<td>Action Sheet 的子标题</td>
</tr>
<tr>
<td>cssClass</td>
<td><code>string</code></td>
<td>自定义样式的其他类，以空格分隔。</td>
</tr>
<tr>
<td>enableBackdropDismiss</td>
<td><code>boolean</code></td>
<td>是否应该通过点击背景来解除 Action Sheet 。</td>
</tr>
<tr>
<td>buttons</td>
<td><code>array&lt;any&gt;</code></td>
<td>要显示的一组按钮。</td>
</tr>
</tbody>
</table>
<p>ActionSheet 按钮选项</p>
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
<td>text</td>
<td><code>string</code></td>
<td>按钮的文本。</td>
</tr>
<tr>
<td>icon</td>
<td><code>icon</code></td>
<td>按钮的图标。</td>
</tr>
<tr>
<td>handler</td>
<td><code>any</code></td>
<td>按钮应该执行的一个表达式。</td>
</tr>
<tr>
<td>cssClass</td>
<td><code>string</code></td>
<td>自定义样式的其他类，以空格分隔。</td>
</tr>
<tr>
<td>role</td>
<td><code>string</code></td>
<td>应该如何显示按钮，<code>destructive</code> 或 <code>cancel</code>。如果没有提供角色，这个按钮将不会显示任何其他样式。</td>
</tr>
</tbody>
</table>
<h3 id="dismissing-and-async-navigation">解除 action sheets 和异步导航</h3>
<p>在 action sheet 被解除后，应用程序可能还需要根据处理函数的逻辑过渡到另一个页面。但是，由于多个转换几乎同时发生， 导航控制器难以清晰地给可能异步启动的多个转换加上动画。这在 <a href="../../nav/NavController/#nav-transition-promises"><code>Nav Transition Promises</code></a> 部分有进一步的描述。对于 action sheets 而言，这意味着最好等待 action sheets 在同一个导航控制器上开始新的转换之前就完成其转换。</p>
<p>在下面的示例中，按钮被单击后，其处理函数会等待异步操作完成，<em>然后</em>使用 <code>pop</code> 导航到同一堆栈中的页面。 潜在的问题是，异步操作可能在 action sheet 结束其转换之前就已经完成了。在这种情况下，最好确保警告先完成其转换，然后再开始下一个转换。</p>












<pre><code class="lang-ts">let actionSheet = this.actionSheetCtrl.create({
  title: &#39;Hello&#39;,
  buttons: [{
    text: &#39;Ok&#39;,
    handler: () =&gt; {
      // user has clicked the action sheet button
      // begin the action sheet&#39;s dimiss transition
      let navTransition = actionSheet.dismiss();

      // start some async method
      someAsyncOperation().then(() =&gt; {
        // once the async operation has completed
        // then run the next nav transition after the
        // first transition has finished animating out

        navTransition.then(() =&gt; {
          this.nav.pop();
        });
      });
      return false;
    }
  }]
});

actionSheet.present();
</code></pre>
<p>注意到处理函数返回 <code>false</code>是很重要的。
按钮处理函数的一个功能是：当按钮被点击时，
它们会自动关闭 action sheet 。
但是，我们需要对这个转换过程进行更多的控制。
由于处理程序返回 <code>false</code>，因此 action sheet 不会自动消除。
相反，你现在可以完全控制 action sheet 何时完成过渡，
以及能够在开始新过渡之前等待 action sheet 完成过渡。</p>



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
        <td><code>$action-sheet-width</code></td>
        
          <td><code>100%</code></td>
        
        <td><p>Width of the action sheet</p>
</td>
      </tr>
      
      <tr>
        <td><code>$action-sheet-max-width</code></td>
        
          <td><code>500px</code></td>
        
        <td><p>Maximum width of the action sheet</p>
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
        <td><code>$action-sheet-ios-text-align</code></td>
        
          <td><code>center</code></td>
        
        <td><p>Text align of the action sheet</p>
</td>
      </tr>
      
      <tr>
        <td><code>$action-sheet-ios-padding-top</code></td>
        
          <td><code>0</code></td>
        
        <td><p>Padding top of the action sheet</p>
</td>
      </tr>
      
      <tr>
        <td><code>$action-sheet-ios-padding-end</code></td>
        
          <td><code>10px</code></td>
        
        <td><p>Padding end of the action sheet</p>
</td>
      </tr>
      
      <tr>
        <td><code>$action-sheet-ios-padding-bottom</code></td>
        
          <td><code>$action-sheet-ios-padding-top</code></td>
        
        <td><p>Padding bottom of the action sheet</p>
</td>
      </tr>
      
      <tr>
        <td><code>$action-sheet-ios-padding-start</code></td>
        
          <td><code>$action-sheet-ios-padding-end</code></td>
        
        <td><p>Padding start of the action sheet</p>
</td>
      </tr>
      
      <tr>
        <td><code>$action-sheet-ios-group-margin-bottom</code></td>
        
          <td><code>10px</code></td>
        
        <td><p>Bottom margin of the action sheet button group</p>
</td>
      </tr>
      
      <tr>
        <td><code>$action-sheet-ios-background</code></td>
        
          <td><code>#f9f9f9</code></td>
        
        <td><p>Background color of the action sheet</p>
</td>
      </tr>
      
      <tr>
        <td><code>$action-sheet-ios-border-color</code></td>
        
          <td><code>#d6d6da</code></td>
        
        <td><p>Border color of the action sheet</p>
</td>
      </tr>
      
      <tr>
        <td><code>$action-sheet-ios-border-radius</code></td>
        
          <td><code>13px</code></td>
        
        <td><p>Border radius of the action sheet</p>
</td>
      </tr>
      
      <tr>
        <td><code>$action-sheet-ios-title-padding</code></td>
        
          <td><code>1.5rem</code></td>
        
        <td><p>Padding of the action sheet title</p>
</td>
      </tr>
      
      <tr>
        <td><code>$action-sheet-ios-title-color</code></td>
        
          <td><code>#8f8f8f</code></td>
        
        <td><p>Color of the action sheet title</p>
</td>
      </tr>
      
      <tr>
        <td><code>$action-sheet-ios-title-font-size</code></td>
        
          <td><code>1.3rem</code></td>
        
        <td><p>Font size of the action sheet title</p>
</td>
      </tr>
      
      <tr>
        <td><code>$action-sheet-ios-title-font-weight</code></td>
        
          <td><code>400</code></td>
        
        <td><p>Font weight of the action sheet title</p>
</td>
      </tr>
      
      <tr>
        <td><code>$action-sheet-ios-title-border-radius</code></td>
        
          <td><code>0</code></td>
        
        <td><p>Border radius of the action sheet title</p>
</td>
      </tr>
      
      <tr>
        <td><code>$action-sheet-ios-button-min-height</code></td>
        
          <td><code>5.6rem</code></td>
        
        <td><p>Minimum height of the action sheet button</p>
</td>
      </tr>
      
      <tr>
        <td><code>$action-sheet-ios-button-padding</code></td>
        
          <td><code>18px</code></td>
        
        <td><p>Padding of the action sheet button</p>
</td>
      </tr>
      
      <tr>
        <td><code>$action-sheet-ios-button-text-color</code></td>
        
          <td><code>#007aff</code></td>
        
        <td><p>Text color of the action sheet button</p>
</td>
      </tr>
      
      <tr>
        <td><code>$action-sheet-ios-button-font-size</code></td>
        
          <td><code>2rem</code></td>
        
        <td><p>Font size of the action sheet button</p>
</td>
      </tr>
      
      <tr>
        <td><code>$action-sheet-ios-button-border-width</code></td>
        
          <td><code>$hairlines-width</code></td>
        
        <td><p>Border width of the action sheet button</p>
</td>
      </tr>
      
      <tr>
        <td><code>$action-sheet-ios-button-border-style</code></td>
        
          <td><code>solid</code></td>
        
        <td><p>Border style of the action sheet button</p>
</td>
      </tr>
      
      <tr>
        <td><code>$action-sheet-ios-button-border-color</code></td>
        
          <td><code>#d1d3d6</code></td>
        
        <td><p>Border color of the action sheet button</p>
</td>
      </tr>
      
      <tr>
        <td><code>$action-sheet-ios-button-background</code></td>
        
          <td><code>transparent</code></td>
        
        <td><p>Background color of the action sheet button</p>
</td>
      </tr>
      
      <tr>
        <td><code>$action-sheet-ios-button-background-activated</code></td>
        
          <td><code>#ebebeb</code></td>
        
        <td><p>Background color of the activated action sheet button</p>
</td>
      </tr>
      
      <tr>
        <td><code>$action-sheet-ios-button-destructive-text-color</code></td>
        
          <td><code>#f53d3d</code></td>
        
        <td><p>Destructive text color of the action sheet button</p>
</td>
      </tr>
      
      <tr>
        <td><code>$action-sheet-ios-button-cancel-background</code></td>
        
          <td><code>#fff</code></td>
        
        <td><p>Background color of the action sheet cancel button</p>
</td>
      </tr>
      
      <tr>
        <td><code>$action-sheet-ios-button-cancel-font-weight</code></td>
        
          <td><code>600</code></td>
        
        <td><p>Font weight of the action sheet cancel button</p>
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
        <td><code>$action-sheet-md-text-align</code></td>
        
          <td><code>start</code></td>
        
        <td><p>Text align of the action sheet</p>
</td>
      </tr>
      
      <tr>
        <td><code>$action-sheet-md-background</code></td>
        
          <td><code>#fafafa</code></td>
        
        <td><p>Background color of the action sheet</p>
</td>
      </tr>
      
      <tr>
        <td><code>$action-sheet-md-group-margin-bottom</code></td>
        
          <td><code>8px</code></td>
        
        <td><p>Bottom margin of the action sheet button group</p>
</td>
      </tr>
      
      <tr>
        <td><code>$action-sheet-md-title-color</code></td>
        
          <td><code>#757575</code></td>
        
        <td><p>Color of the action sheet title</p>
</td>
      </tr>
      
      <tr>
        <td><code>$action-sheet-md-title-font-size</code></td>
        
          <td><code>1.6rem</code></td>
        
        <td><p>Font size of the action sheet title</p>
</td>
      </tr>
      
      <tr>
        <td><code>$action-sheet-md-title-padding-top</code></td>
        
          <td><code>11px</code></td>
        
        <td><p>Padding top of the action sheet title</p>
</td>
      </tr>
      
      <tr>
        <td><code>$action-sheet-md-title-padding-end</code></td>
        
          <td><code>16px</code></td>
        
        <td><p>Padding end of the action sheet title</p>
</td>
      </tr>
      
      <tr>
        <td><code>$action-sheet-md-title-padding-bottom</code></td>
        
          <td><code>17px</code></td>
        
        <td><p>Padding bottom of the action sheet title</p>
</td>
      </tr>
      
      <tr>
        <td><code>$action-sheet-md-title-padding-start</code></td>
        
          <td><code>$action-sheet-md-title-padding-end</code></td>
        
        <td><p>Padding start of the action sheet title</p>
</td>
      </tr>
      
      <tr>
        <td><code>$action-sheet-md-button-min-height</code></td>
        
          <td><code>4.8rem</code></td>
        
        <td><p>Minimum height of the action sheet button</p>
</td>
      </tr>
      
      <tr>
        <td><code>$action-sheet-md-button-text-color</code></td>
        
          <td><code>#222</code></td>
        
        <td><p>Text color of the action sheet button</p>
</td>
      </tr>
      
      <tr>
        <td><code>$action-sheet-md-button-font-size</code></td>
        
          <td><code>1.6rem</code></td>
        
        <td><p>Font size of the action sheet button</p>
</td>
      </tr>
      
      <tr>
        <td><code>$action-sheet-md-button-padding-top</code></td>
        
          <td><code>0</code></td>
        
        <td><p>Padding top of the action sheet button</p>
</td>
      </tr>
      
      <tr>
        <td><code>$action-sheet-md-button-padding-end</code></td>
        
          <td><code>16px</code></td>
        
        <td><p>Padding end of the action sheet button</p>
</td>
      </tr>
      
      <tr>
        <td><code>$action-sheet-md-button-padding-bottom</code></td>
        
          <td><code>$action-sheet-md-button-padding-top</code></td>
        
        <td><p>Padding bottom of the action sheet button</p>
</td>
      </tr>
      
      <tr>
        <td><code>$action-sheet-md-button-padding-start</code></td>
        
          <td><code>$action-sheet-md-button-padding-end</code></td>
        
        <td><p>Padding start of the action sheet button</p>
</td>
      </tr>
      
      <tr>
        <td><code>$action-sheet-md-button-background</code></td>
        
          <td><code>transparent</code></td>
        
        <td><p>Background color of the action sheet button</p>
</td>
      </tr>
      
      <tr>
        <td><code>$action-sheet-md-button-background-activated</code></td>
        
          <td><code>#f1f1f1</code></td>
        
        <td><p>Background color of the action sheet activated button</p>
</td>
      </tr>
      
      <tr>
        <td><code>$action-sheet-md-icon-font-size</code></td>
        
          <td><code>2.4rem</code></td>
        
        <td><p>Font size of the icon in the action sheet button</p>
</td>
      </tr>
      
      <tr>
        <td><code>$action-sheet-md-icon-width</code></td>
        
          <td><code>2.3rem</code></td>
        
        <td><p>Width of the icon in the action sheet button</p>
</td>
      </tr>
      
      <tr>
        <td><code>$action-sheet-md-icon-text-align</code></td>
        
          <td><code>center</code></td>
        
        <td><p>Text align of the icon in the action sheet button</p>
</td>
      </tr>
      
      <tr>
        <td><code>$action-sheet-md-icon-vertical-align</code></td>
        
          <td><code>middle</code></td>
        
        <td><p>Vertical align of the icon in the action sheet button</p>
</td>
      </tr>
      
      <tr>
        <td><code>$action-sheet-md-icon-margin-top</code></td>
        
          <td><code>0</code></td>
        
        <td><p>Margin top of the icon in the action sheet button</p>
</td>
      </tr>
      
      <tr>
        <td><code>$action-sheet-md-icon-margin-end</code></td>
        
          <td><code>32px</code></td>
        
        <td><p>Margin end of the icon in the action sheet button</p>
</td>
      </tr>
      
      <tr>
        <td><code>$action-sheet-md-icon-margin-bottom</code></td>
        
          <td><code>0</code></td>
        
        <td><p>Margin bottom of the icon in the action sheet button</p>
</td>
      </tr>
      
      <tr>
        <td><code>$action-sheet-md-icon-margin-start</code></td>
        
          <td><code>0</code></td>
        
        <td><p>Margin start of the icon in the action sheet button</p>
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
        <td><code>$action-sheet-wp-text-align</code></td>
        
          <td><code>start</code></td>
        
        <td><p>Text align of the action sheet</p>
</td>
      </tr>
      
      <tr>
        <td><code>$action-sheet-wp-background</code></td>
        
          <td><code>#fff</code></td>
        
        <td><p>Background color of the action sheet</p>
</td>
      </tr>
      
      <tr>
        <td><code>$action-sheet-wp-box-shadow-color</code></td>
        
          <td><code>rgba(0, 0, 0, .2)</code></td>
        
        <td><p>Box shadow color of the action sheet</p>
</td>
      </tr>
      
      <tr>
        <td><code>$action-sheet-wp-box-shadow</code></td>
        
          <td><code>0 -1px 0 $action-sheet-wp-box-shadow-color</code></td>
        
        <td><p>Box shadow of the action sheet</p>
</td>
      </tr>
      
      <tr>
        <td><code>$action-sheet-wp-title-padding-top</code></td>
        
          <td><code>11px</code></td>
        
        <td><p>Padding top of the action sheet title</p>
</td>
      </tr>
      
      <tr>
        <td><code>$action-sheet-wp-title-padding-end</code></td>
        
          <td><code>16px</code></td>
        
        <td><p>Padding end of the action sheet title</p>
</td>
      </tr>
      
      <tr>
        <td><code>$action-sheet-wp-title-padding-bottom</code></td>
        
          <td><code>17px</code></td>
        
        <td><p>Padding bottom of the action sheet title</p>
</td>
      </tr>
      
      <tr>
        <td><code>$action-sheet-wp-title-padding-start</code></td>
        
          <td><code>$action-sheet-wp-title-padding-end</code></td>
        
        <td><p>Padding start of the action sheet title</p>
</td>
      </tr>
      
      <tr>
        <td><code>$action-sheet-wp-title-font-size</code></td>
        
          <td><code>2rem</code></td>
        
        <td><p>Font size of the action sheet title</p>
</td>
      </tr>
      
      <tr>
        <td><code>$action-sheet-wp-title-color</code></td>
        
          <td><code>#4d4d4d</code></td>
        
        <td><p>Color of the action sheet title</p>
</td>
      </tr>
      
      <tr>
        <td><code>$action-sheet-wp-title-text-align</code></td>
        
          <td><code>$action-sheet-wp-text-align</code></td>
        
        <td><p>Text align of the action sheet title</p>
</td>
      </tr>
      
      <tr>
        <td><code>$action-sheet-wp-button-height</code></td>
        
          <td><code>4.8rem</code></td>
        
        <td><p>Height of the action sheet button</p>
</td>
      </tr>
      
      <tr>
        <td><code>$action-sheet-wp-button-text-color</code></td>
        
          <td><code>#4d4d4d</code></td>
        
        <td><p>Text color of the action sheet button</p>
</td>
      </tr>
      
      <tr>
        <td><code>$action-sheet-wp-button-font-size</code></td>
        
          <td><code>1.5rem</code></td>
        
        <td><p>Font size of the action sheet button</p>
</td>
      </tr>
      
      <tr>
        <td><code>$action-sheet-wp-button-padding-top</code></td>
        
          <td><code>0</code></td>
        
        <td><p>Padding top of the action sheet button</p>
</td>
      </tr>
      
      <tr>
        <td><code>$action-sheet-wp-button-padding-end</code></td>
        
          <td><code>16px</code></td>
        
        <td><p>Padding end of the action sheet button</p>
</td>
      </tr>
      
      <tr>
        <td><code>$action-sheet-wp-button-padding-bottom</code></td>
        
          <td><code>$action-sheet-wp-button-padding-top</code></td>
        
        <td><p>Padding bottom of the action sheet button</p>
</td>
      </tr>
      
      <tr>
        <td><code>$action-sheet-wp-button-padding-start</code></td>
        
          <td><code>$action-sheet-wp-button-padding-end</code></td>
        
        <td><p>Padding start of the action sheet button</p>
</td>
      </tr>
      
      <tr>
        <td><code>$action-sheet-wp-button-text-align</code></td>
        
          <td><code>$action-sheet-wp-text-align</code></td>
        
        <td><p>Text align of the action sheet button</p>
</td>
      </tr>
      
      <tr>
        <td><code>$action-sheet-wp-button-background</code></td>
        
          <td><code>transparent</code></td>
        
        <td><p>Background color of the action sheet button</p>
</td>
      </tr>
      
      <tr>
        <td><code>$action-sheet-wp-button-background-activated</code></td>
        
          <td><code>$list-wp-activated-background-color</code></td>
        
        <td><p>Background color of the action sheet activated button</p>
</td>
      </tr>
      
      <tr>
        <td><code>$action-sheet-wp-icon-font-size</code></td>
        
          <td><code>2.4rem</code></td>
        
        <td><p>Font size of the icon in the action sheet button</p>
</td>
      </tr>
      
      <tr>
        <td><code>$action-sheet-wp-icon-width</code></td>
        
          <td><code>2.3rem</code></td>
        
        <td><p>Width of the icon in the action sheet button</p>
</td>
      </tr>
      
      <tr>
        <td><code>$action-sheet-wp-icon-text-align</code></td>
        
          <td><code>center</code></td>
        
        <td><p>Text align of the icon in the action sheet button</p>
</td>
      </tr>
      
      <tr>
        <td><code>$action-sheet-wp-icon-vertical-align</code></td>
        
          <td><code>middle</code></td>
        
        <td><p>Vertical align of the icon in the action sheet button</p>
</td>
      </tr>
      
      <tr>
        <td><code>$action-sheet-wp-icon-margin-top</code></td>
        
          <td><code>0</code></td>
        
        <td><p>Margin top of the icon in the action sheet button</p>
</td>
      </tr>
      
      <tr>
        <td><code>$action-sheet-wp-icon-margin-end</code></td>
        
          <td><code>20px</code></td>
        
        <td><p>Margin end of the icon in the action sheet button</p>
</td>
      </tr>
      
      <tr>
        <td><code>$action-sheet-wp-icon-margin-bottom</code></td>
        
          <td><code>0</code></td>
        
        <td><p>Margin bottom of the icon in the action sheet button</p>
</td>
      </tr>
      
      <tr>
        <td><code>$action-sheet-wp-icon-margin-start</code></td>
        
          <td><code>0</code></td>
        
        <td><p>Margin start of the icon in the action sheet button</p>
</td>
      </tr>
      
    </tbody>
  </table>
  
</div>



<!-- related link -->

<h2><a class="anchor" name="related" href="#related">Related</a></h2>

<a href="/docs/components#action-sheets">ActionSheet Component Docs</a><!-- end content block -->


<!-- end body block -->

