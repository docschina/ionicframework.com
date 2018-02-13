---
layout: "fluid/docs_base"
version: "3.9.2"
versionHref: "/docs"
path: ""
category: api
id: "alertcontroller"
title: "AlertController"
header_sub_title: "Ionic API Documentation"
doc: "AlertController"
docType: "class"
show_preview_device: true
preview_device_url: "/docs/demos/src/alert/www/"
angular_controller: APIDemoCtrl 
---









<h1 class="api-title">
<a class="anchor" name="alert-controller" href="#alert-controller"></a>

AlertController





</h1>

<a class="improve-v2-docs" href="http://github.com/ionic-team/ionic/edit/master/src/components/alert/alert-controller.ts#L5">
Improve this doc
</a>






<p>Alert 组件
是一个向用户提供或收集来自用户输入的信息的对话框。
它会在顶部显示应用的内容，并且在用户恢复与应用程序交互之前，
必须由用户手动解除。
它也可以有一个<code>标题</code>，<code>副标题</code>和<code>消息</code>。</p>
<p>你可以在 create 方法的第一个参数中传递所有Alert 组件的选项：<code>create(opts)</code>。
另外，Alert 组件的实例也有方法添加选项，
像<code>setTitle()</code>或<code>addButton()</code>。</p>
<h3><a class="anchor" name="alert-buttons" href="#alert-buttons">Alert 按钮</a></h3>


<p>在<code>按钮</code>的数组中，
每个按钮都包含<code>文本</code>的属性，
和可选的<code>处理函数</code>。
如果处理函数返回<code> false </code>，则Alert 组件在按钮被点击时不会自动解除。
所有按钮将按照它们被添加到<code>buttons</code>数组的从左到右的顺序显示数组。
注意：最右边的按钮（数组的最后一个按钮）是主要按钮。</p>
<p>或者，可以将<code>role</code>属性添加到按钮，
例如<code>cancel</code>。
如果某个<code>cancel</code> role 位于其中一个按钮上，则该Alert 组件可以通过点击背景来解除，
然后它将触发那个 cancel role 按钮的处理函数。</p>
<h3><a class="anchor" name="alert-inputs" href="#alert-inputs">Alert 输入</a></h3>


<p>Alert 组件还可以包括一些能够传递数据给应用的不同输入。
可以将提示用户的信息用一个简单的方法来输入，单选按钮，复选框和文本输入都可以，
但他们不能混着用。
例如，Alert 组件可以全部是单选按钮输入，或全部是复选框输入，
但同一个Alert 组件不能混合单选按钮和复选框来输入。
注意，不同类型的“文本”输入是可以混合使用的，比如<code>url</code>，<code>email</code>，<code>text</code>等。
如果你需要复杂的表单UI，
是不符合Alert 组件的使用原则的，
我们推荐在一个 modal 组件中构建表单。</p>




<!-- @usage tag -->

<h2><a class="anchor" name="usage" href="#usage">用法</a></h2>

<pre><code class="lang-ts">import { AlertController } from &#39;ionic-angular&#39;;

constructor(private alertCtrl: AlertController) {

}

presentAlert() {
  let alert = this.alertCtrl.create({
    title: &#39;Low battery&#39;,
    subTitle: &#39;10% of battery remaining&#39;,
    buttons: [&#39;Dismiss&#39;]
  });
  alert.present();
}

presentConfirm() {
  let alert = this.alertCtrl.create({
    title: &#39;Confirm purchase&#39;,
    message: &#39;Do you want to buy this book?&#39;,
    buttons: [
      {
        text: &#39;Cancel&#39;,
        role: &#39;cancel&#39;,
        handler: () =&gt; {
          console.log(&#39;Cancel clicked&#39;);
        }
      },
      {
        text: &#39;Buy&#39;,
        handler: () =&gt; {
          console.log(&#39;Buy clicked&#39;);
        }
      }
    ]
  });
  alert.present();
}

presentPrompt() {
  let alert = this.alertCtrl.create({
    title: &#39;Login&#39;,
    inputs: [
      {
        name: &#39;username&#39;,
        placeholder: &#39;Username&#39;
      },
      {
        name: &#39;password&#39;,
        placeholder: &#39;Password&#39;,
        type: &#39;password&#39;
      }
    ],
    buttons: [
      {
        text: &#39;Cancel&#39;,
        role: &#39;cancel&#39;,
        handler: data =&gt; {
          console.log(&#39;Cancel clicked&#39;);
        }
      },
      {
        text: &#39;Login&#39;,
        handler: data =&gt; {
          if (User.isValid(data.username, data.password)) {
            // 已登录！
          } else {
            // 不合法的登录
            return false;
          }
        }
      }
    ]
  });
  alert.present();
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

 &nbsp;&nbsp;&nbsp;显示一个带有标题，输入框和按钮的 Alert 组件。


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
        
  <code>AlertOptions</code>
      </td>
      <td>
        <p>Alert 组件，请参阅下面的表</p>

        
      </td>
    </tr>
    
  </tbody>
</table>






<h2><a class="anchor" name="advanced" href="#advanced">进阶</a></h2>
<p>Alert 参数</p>
<table>
<thead>
<tr>
<th>属性</th>
<th>类型</th>
<th>描述</th>
</tr>
</thead>
<tbody>
<tr>
<td>title</td>
<td><code>string</code></td>
<td>Alert 组件的标题</td>
</tr>
<tr>
<td>subTitle</td>
<td><code>string</code></td>
<td>Alert 组件的副标题</td>
</tr>
<tr>
<td>message</td>
<td><code>string</code></td>
<td>Alert 组件的消息</td>
</tr>
<tr>
<td>cssClass</td>
<td><code>string</code></td>
<td>自定义样式的其他类，以空格分隔。</td>
</tr>
<tr>
<td>inputs</td>
<td><code>array</code></td>
<td>Alert 组件的输入数组，请参阅输入框选项。</td>
</tr>
<tr>
<td>buttons</td>
<td><code>array</code></td>
<td>Alert 组件的按钮数组。请参阅按钮选项。</td>
</tr>
<tr>
<td>enableBackdropDismiss</td>
<td><code>boolean</code></td>
<td>是否应该通过点击背景来解除 Alert 。默认为 true 。</td>
</tr>
</tbody>
</table>
<p>输入框选项</p>
<table>
<thead>
<tr>
<th>属性</th>
<th>类型</th>
<th>描述</th>
</tr>
</thead>
<tbody>
<tr>
<td>type</td>
<td><code>string</code></td>
<td>输入值的类型应该是：text ，tel ，number 等。</td>
</tr>
<tr>
<td>name</td>
<td><code>string</code></td>
<td>输入框的名称。</td>
</tr>
<tr>
<td>placeholder</td>
<td><code>string</code></td>
<td>输入框的占位符（用于文本/数字输入）。</td>
</tr>
<tr>
<td>value</td>
<td><code>string</code></td>
<td>输入框的值。</td>
</tr>
<tr>
<td>label</td>
<td><code>string</code></td>
<td>输入框的标签（仅用于单选按钮/复选框输入）</td>
</tr>
<tr>
<td>checked</td>
<td><code>boolean</code></td>
<td>输入框是否校验</td>
</tr>
<tr>
<td>id</td>
<td><code>string</code></td>
<td>输入框的 id 。</td>
</tr>
</tbody>
</table>
<p>按钮选项</p>
<table>
<thead>
<tr>
<th>属性</th>
<th>类型</th>
<th>描述</th>
</tr>
</thead>
<tbody>
<tr>
<td>text</td>
<td><code>string</code></td>
<td>按钮显示的文本值。</td>
</tr>
<tr>
<td>handler</td>
<td><code>any</code></td>
<td>当按钮被按下时触发的处理函数。</td>
</tr>
<tr>
<td>cssClass</td>
<td><code>string</code></td>
<td>按钮的附加 CSS 类。</td>
</tr>
<tr>
<td>role</td>
<td><code>string</code></td>
<td>按钮 role ，null 或 <code>cancel</code>。</td>
</tr>
</tbody>
</table>
<h3 id="dismissing-and-async-navigation">解除警告和异步导航</h3>
<p>Alert 解除后，
应用可能还需要根据处理函数的逻辑过渡到另一个页面。
但是，由于多个转换几乎同时发生，
导航控制器难以清晰地
给可能异步启动的多个转换加上动画。
这在<a href="../../nav/NavController"><code>Nav Transition Promises</code></a>部分会进一步解释。
对于警告来说，
这意味着最好等待 Alert 组件在同一个导航控制器上开始新的转换之前
就完成其转换。</p>
<p>在下面的示例中，警告按钮被单击后，
其处理函数会等待异步操作完成，
<em>然后</em>使用<code>pop</code>导航到同一堆栈中的页面。
潜在的问题是，异步操作可能在警告结束其转换之前就已经完成了。
在这种情况下，最好确保警告先完成其转换，<em>然后</em>再开始下一个转换。</p>
<pre><code class="lang-ts">let alert = this.alertCtrl.create({
  title: &#39;Hello&#39;,
  buttons: [{
    text: &#39;Ok&#39;,
    handler: () =&gt; {
      // 用户已点击警告按钮
      // 启动警告的解散过渡
      let navTransition = alert.dismiss();

      // 启动一些异步方法
      someAsyncOperation().then(() =&gt; {
        // 一旦异步方法完成
        // 就在第一次转换完成动画之后
        // 运行下一个导航过渡

        navTransition.then(() =&gt; {
          this.nav.pop();
        });
      });
      return false;
    }
  }]
});

alert.present();
</code></pre>
<p>注意到处理函数返回 <code>false</code>是很重要的。
按钮处理函数的一个功能是：当按钮被点击时，
它们会自动关闭警告。
但是，我们需要对这个转换过程进行更多的控制。
由于处理程序返回 <code>false</code>，因此警告不会自动消除。
相反，你现在可以完全控制警告何时完成过渡，
以及能够在开始新过渡之前等待警告完成过渡。</p>



  <h2 id="sass-variable-header"><a class="anchor" name="sass-variables" href="#sass-variables">Sass 变量</a></h2>
  <div id="sass-variables" ng-controller="SassToggleCtrl">
  <div class="sass-platform-toggle">
    
      
      
      <a ng-init="setSassPlatform('base')" ng-class="{ active: active === 'base' }" ng-click="setSassPlatform('base')" >全部</a>
      
      
      
      <a ng-class="{ active: active === 'ios' }" ng-click="setSassPlatform('ios')">iOS</a>
      
      
      
      <a ng-class="{ active: active === 'md' }" ng-click="setSassPlatform('md')">Material 设计</a>
      
      
      
      <a ng-class="{ active: active === 'wp' }" ng-click="setSassPlatform('wp')">Windows 平台</a>
      
      
    
  </div>


  
  <table ng-show="active === 'base'" id="sass-base" class="table param-table" style="margin:0;">
    <thead>
      <tr>
        <th>属性</th>
        <th>默认值</th>
        <th>描述</th>
      </tr>
    </thead>
    <tbody>
      
      <tr>
        <td><code>$alert-min-width</code></td>
        
          <td><code>250px</code></td>
        
        <td><p>Alert 组件的最小宽度</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-max-height</code></td>
        
          <td><code>90%</code></td>
        
        <td><p>Alert 组件的最大高度</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-button-line-height</code></td>
        
          <td><code>20px</code></td>
        
        <td><p>Alert 组件按钮的行高</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-button-font-size</code></td>
        
          <td><code>14px</code></td>
        
        <td><p>Alert 组件按钮的字体大小</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-input-placeholder-color</code></td>
        
          <td><code>#999</code></td>
        
        <td><p>Alert 组件输入框占位符的颜色</p>
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
        <td><code>$alert-ios-max-width</code></td>
        
          <td><code>270px</code></td>
        
        <td><p>Alert 组件的最大宽度</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-ios-border-radius</code></td>
        
          <td><code>13px</code></td>
        
        <td><p>Alert 组件的边框半径</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-ios-background</code></td>
        
          <td><code>#f8f8f8</code></td>
        
        <td><p>Alert 组件的背景颜色</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-ios-box-shadow</code></td>
        
          <td><code>none</code></td>
        
        <td><p>提示框的阴影</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-ios-head-padding-top</code></td>
        
          <td><code>12px</code></td>
        
        <td><p>Alert 组件头的顶部填充</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-ios-head-padding-end</code></td>
        
          <td><code>16px</code></td>
        
        <td><p>Alert 组件头的右填充</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-ios-head-padding-bottom</code></td>
        
          <td><code>7px</code></td>
        
        <td><p>Alert 组件头的底部填充</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-ios-head-padding-start</code></td>
        
          <td><code>$alert-ios-head-padding-end</code></td>
        
        <td><p>Alert 组件头的左填充</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-ios-head-text-align</code></td>
        
          <td><code>center</code></td>
        
        <td><p>Alert 组件头的文本对齐</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-ios-title-margin-top</code></td>
        
          <td><code>8px</code></td>
        
        <td><p>Alert 组件标题的页边距</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-ios-title-font-size</code></td>
        
          <td><code>17px</code></td>
        
        <td><p>Alert 组件标题的字体大小</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-ios-title-font-weight</code></td>
        
          <td><code>600</code></td>
        
        <td><p>警告标题的字体粗细</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-ios-sub-title-font-size</code></td>
        
          <td><code>14px</code></td>
        
        <td><p>Alert 组件子标题的字体大小</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-ios-sub-title-text-color</code></td>
        
          <td><code>#666</code></td>
        
        <td><p>Alert 组件子标题的文本颜色</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-ios-message-padding-top</code></td>
        
          <td><code>0</code></td>
        
        <td><p>Alert 组件消息的顶部填充</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-ios-message-padding-end</code></td>
        
          <td><code>16px</code></td>
        
        <td><p>Alert 组件消息的右填充</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-ios-message-padding-bottom</code></td>
        
          <td><code>21px</code></td>
        
        <td><p>Alert 组件消息的底部填充</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-ios-message-padding-start</code></td>
        
          <td><code>$alert-ios-message-padding-end</code></td>
        
        <td><p>Alert 组件消息的左填充</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-ios-message-font-size</code></td>
        
          <td><code>13px</code></td>
        
        <td><p>Alert 组件消息的字体大小</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-ios-message-text-align</code></td>
        
          <td><code>center</code></td>
        
        <td><p>Alert 组件消息的文本对齐</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-ios-message-text-color</code></td>
        
          <td><code>inherit</code></td>
        
        <td><p>Alert 组件消息的文本颜色</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-ios-message-empty-padding-top</code></td>
        
          <td><code>0</code></td>
        
        <td><p>Padding top of the alert empty message</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-ios-message-empty-padding-end</code></td>
        
          <td><code>0</code></td>
        
        <td><p>Padding end of the alert empty message</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-ios-message-empty-padding-bottom</code></td>
        
          <td><code>12px</code></td>
        
        <td><p>Padding bottom of the alert empty message</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-ios-message-empty-padding-start</code></td>
        
          <td><code>0</code></td>
        
        <td><p>Padding start of the alert empty message</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-ios-content-max-height</code></td>
        
          <td><code>240px</code></td>
        
        <td><p>Maximum height of the alert content</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-ios-input-margin-top</code></td>
        
          <td><code>10px</code></td>
        
        <td><p>Margin top of the alert input</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-ios-input-padding-top</code></td>
        
          <td><code>6px</code></td>
        
        <td><p>Padding top on the alert input</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-ios-input-padding-end</code></td>
        
          <td><code>$alert-ios-input-padding-top</code></td>
        
        <td><p>Padding end on the alert input</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-ios-input-padding-bottom</code></td>
        
          <td><code>$alert-ios-input-padding-top</code></td>
        
        <td><p>Padding bottom on the alert input</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-ios-input-padding-start</code></td>
        
          <td><code>$alert-ios-input-padding-end</code></td>
        
        <td><p>Padding start on the alert input</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-ios-input-border-color</code></td>
        
          <td><code>#ccc</code></td>
        
        <td><p>Border color of the alert input</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-ios-input-border</code></td>
        
          <td><code>$hairlines-width solid $alert-ios-input-border-color</code></td>
        
        <td><p>Border of the alert input</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-ios-input-border-radius</code></td>
        
          <td><code>4px</code></td>
        
        <td><p>Border radius of the alert input</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-ios-input-background-color</code></td>
        
          <td><code>#fff</code></td>
        
        <td><p>Background color of the alert input</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-ios-button-group-flex-wrap</code></td>
        
          <td><code>wrap</code></td>
        
        <td><p>Flex wrap of the alert button group</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-ios-button-flex</code></td>
        
          <td><code>1 1 auto</code></td>
        
        <td><p>Flex of the alert button</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-ios-button-margin</code></td>
        
          <td><code>0</code></td>
        
        <td><p>Margin of the alert button</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-ios-button-min-width</code></td>
        
          <td><code>50%</code></td>
        
        <td><p>Min width of the alert button</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-ios-button-min-height</code></td>
        
          <td><code>44px</code></td>
        
        <td><p>Minimum height of the alert button</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-ios-button-font-size</code></td>
        
          <td><code>17px</code></td>
        
        <td><p>Font size of the alert button</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-ios-button-text-color</code></td>
        
          <td><code>color($colors-ios, primary)</code></td>
        
        <td><p>Color of the text in the alert button</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-ios-button-background-color</code></td>
        
          <td><code>transparent</code></td>
        
        <td><p>Background color of the alert button</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-ios-button-background-color-activated</code></td>
        
          <td><code>#e9e9e9</code></td>
        
        <td><p>Background color of the alert activated button</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-ios-button-border-width</code></td>
        
          <td><code>$hairlines-width</code></td>
        
        <td><p>Border width of the alert button</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-ios-button-border-style</code></td>
        
          <td><code>solid</code></td>
        
        <td><p>Border style of the alert button</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-ios-button-border-color</code></td>
        
          <td><code>#dbdbdf</code></td>
        
        <td><p>Border color of the alert button</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-ios-button-border-radius</code></td>
        
          <td><code>0</code></td>
        
        <td><p>Border radius of the alert button</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-ios-button-main-font-weight</code></td>
        
          <td><code>bold</code></td>
        
        <td><p>Font weight of the main text on the alert button</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-ios-list-border-top</code></td>
        
          <td><code>$alert-ios-button-border-width $alert-ios-button-border-style $alert-ios-button-border-color</code></td>
        
        <td><p>Border top of the alert list</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-ios-radio-label-padding-top</code></td>
        
          <td><code>13px</code></td>
        
        <td><p>Padding top on the label for the radio alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-ios-radio-label-padding-end</code></td>
        
          <td><code>$alert-ios-radio-label-padding-top</code></td>
        
        <td><p>Padding end on the label for the radio alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-ios-radio-label-padding-bottom</code></td>
        
          <td><code>$alert-ios-radio-label-padding-top</code></td>
        
        <td><p>Padding bottom on the label for the radio alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-ios-radio-label-padding-start</code></td>
        
          <td><code>$alert-ios-radio-label-padding-end</code></td>
        
        <td><p>Padding start on the label for the radio alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-ios-radio-label-text-color</code></td>
        
          <td><code>initial</code></td>
        
        <td><p>Text color of the label for the radio alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-ios-radio-label-text-color-checked</code></td>
        
          <td><code>$alert-ios-button-text-color</code></td>
        
        <td><p>Text color of the label for the checked radio alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-ios-radio-min-width</code></td>
        
          <td><code>30px</code></td>
        
        <td><p>Min width of the radio alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-ios-radio-icon-top</code></td>
        
          <td><code>-7px</code></td>
        
        <td><p>Top of the icon in the radio alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-ios-radio-icon-start</code></td>
        
          <td><code>$alert-ios-radio-icon-left</code></td>
        
        <td><p>Start of the icon in the radio alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-ios-radio-icon-width</code></td>
        
          <td><code>6px</code></td>
        
        <td><p>Width of the icon in the radio alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-ios-radio-icon-height</code></td>
        
          <td><code>12px</code></td>
        
        <td><p>Height of the icon in the radio alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-ios-radio-icon-border-width</code></td>
        
          <td><code>2px</code></td>
        
        <td><p>Border width of the icon in the radio alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-ios-radio-icon-border-style</code></td>
        
          <td><code>solid</code></td>
        
        <td><p>Border style of the icon in the radio alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-ios-radio-icon-border-color</code></td>
        
          <td><code>$alert-ios-button-text-color</code></td>
        
        <td><p>Border color of the icon in the radio alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-ios-radio-icon-transform</code></td>
        
          <td><code>rotate(45deg)</code></td>
        
        <td><p>Transform of the icon in the radio alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-ios-checkbox-label-padding-top</code></td>
        
          <td><code>13px</code></td>
        
        <td><p>Padding top of the label for the checkbox in the alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-ios-checkbox-label-padding-end</code></td>
        
          <td><code>$alert-ios-checkbox-label-padding-top</code></td>
        
        <td><p>Padding end of the label for the checkbox in the alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-ios-checkbox-label-padding-bottom</code></td>
        
          <td><code>$alert-ios-checkbox-label-padding-top</code></td>
        
        <td><p>Padding bottom of the label for the checkbox in the alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-ios-checkbox-label-padding-start</code></td>
        
          <td><code>$alert-ios-checkbox-label-padding-end</code></td>
        
        <td><p>Padding start of the label for the checkbox in the alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-ios-checkbox-label-text-color</code></td>
        
          <td><code>initial</code></td>
        
        <td><p>Text color of the label for the checkbox in the alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-ios-checkbox-label-text-color-checked</code></td>
        
          <td><code>initial</code></td>
        
        <td><p>Text color of the label for the checked checkbox in the alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-ios-checkbox-margin-top</code></td>
        
          <td><code>10px</code></td>
        
        <td><p>Margin top of the checkbox in the alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-ios-checkbox-margin-end</code></td>
        
          <td><code>6px</code></td>
        
        <td><p>Margin end of the checkbox in the alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-ios-checkbox-margin-bottom</code></td>
        
          <td><code>10px</code></td>
        
        <td><p>Margin bottom of the checkbox in the alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-ios-checkbox-margin-start</code></td>
        
          <td><code>16px</code></td>
        
        <td><p>Margin start of the checkbox in the alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-ios-checkbox-size</code></td>
        
          <td><code>21px</code></td>
        
        <td><p>Size of the checkbox in the alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-ios-checkbox-border-width</code></td>
        
          <td><code>$hairlines-width</code></td>
        
        <td><p>Border width of the checkbox in the alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-ios-checkbox-border-style</code></td>
        
          <td><code>solid</code></td>
        
        <td><p>Border style of the checkbox in the alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-ios-checkbox-border-radius</code></td>
        
          <td><code>50%</code></td>
        
        <td><p>Border radius of the checkbox in the alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-ios-checkbox-border-color-off</code></td>
        
          <td><code>$list-ios-border-color</code></td>
        
        <td><p>Border color of the checkbox in the alert when off</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-ios-checkbox-border-color-on</code></td>
        
          <td><code>color($colors-ios, primary)</code></td>
        
        <td><p>Border color of the checkbox in the alert when on</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-ios-checkbox-background-color-off</code></td>
        
          <td><code>$list-ios-background-color</code></td>
        
        <td><p>Background color of the checkbox in the alert when off</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-ios-checkbox-background-color-on</code></td>
        
          <td><code>color($colors-ios, primary)</code></td>
        
        <td><p>Background color of the checkbox in the alert when on</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-ios-checkbox-icon-top</code></td>
        
          <td><code>4px</code></td>
        
        <td><p>Top of the icon in the checkbox alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-ios-checkbox-icon-start</code></td>
        
          <td><code>$alert-ios-checkbox-icon-left</code></td>
        
        <td><p>Start of the icon in the checkbox alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-ios-checkbox-icon-width</code></td>
        
          <td><code>4px</code></td>
        
        <td><p>Width of the icon in the checkbox alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-ios-checkbox-icon-height</code></td>
        
          <td><code>9px</code></td>
        
        <td><p>Height of the icon in the checkbox alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-ios-checkbox-icon-border-width</code></td>
        
          <td><code>$alert-ios-checkbox-border-width</code></td>
        
        <td><p>Border width of the icon in the checkbox alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-ios-checkbox-icon-border-style</code></td>
        
          <td><code>$alert-ios-checkbox-border-style</code></td>
        
        <td><p>Border style of the icon in the checkbox alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-ios-checkbox-icon-border-color</code></td>
        
          <td><code>$background-ios-color</code></td>
        
        <td><p>Border color of the icon in the checkbox alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-ios-checkbox-icon-transform</code></td>
        
          <td><code>rotate(45deg)</code></td>
        
        <td><p>Transform of the icon in the checkbox alert</p>
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
        <td><code>$alert-md-max-width</code></td>
        
          <td><code>280px</code></td>
        
        <td><p>Max width of the alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-md-border-radius</code></td>
        
          <td><code>2px</code></td>
        
        <td><p>Border radius of the alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-md-background-color</code></td>
        
          <td><code>#fafafa</code></td>
        
        <td><p>Background color of the alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-md-box-shadow-color</code></td>
        
          <td><code>rgba(0, 0, 0, .4)</code></td>
        
        <td><p>Box shadow color of the alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-md-box-shadow</code></td>
        
          <td><code>0 16px 20px $alert-md-box-shadow-color</code></td>
        
        <td><p>Box shadow of the alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-md-head-padding-top</code></td>
        
          <td><code>24px</code></td>
        
        <td><p>Padding top of the alert head</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-md-head-padding-end</code></td>
        
          <td><code>24px</code></td>
        
        <td><p>Padding end of the alert head</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-md-head-padding-bottom</code></td>
        
          <td><code>20px</code></td>
        
        <td><p>Padding bottom of the alert head</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-md-head-padding-start</code></td>
        
          <td><code>24px</code></td>
        
        <td><p>Padding start of the alert head</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-md-head-text-align</code></td>
        
          <td><code>start</code></td>
        
        <td><p>Text align of the alert head</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-md-title-font-size</code></td>
        
          <td><code>22px</code></td>
        
        <td><p>Font size of the alert title</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-md-sub-title-font-size</code></td>
        
          <td><code>16px</code></td>
        
        <td><p>Font size of the alert sub title</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-md-message-padding-top</code></td>
        
          <td><code>0</code></td>
        
        <td><p>Padding top of the alert message</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-md-message-padding-end</code></td>
        
          <td><code>24px</code></td>
        
        <td><p>Padding end of the alert message</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-md-message-padding-bottom</code></td>
        
          <td><code>24px</code></td>
        
        <td><p>Padding bottom of the alert message</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-md-message-padding-start</code></td>
        
          <td><code>24px</code></td>
        
        <td><p>Padding start of the alert message</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-md-message-font-size</code></td>
        
          <td><code>15px</code></td>
        
        <td><p>Font size of the alert message</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-md-message-text-color</code></td>
        
          <td><code>rgba(0, 0, 0, .5)</code></td>
        
        <td><p>Text color of the alert message</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-md-message-empty-padding-top</code></td>
        
          <td><code>0</code></td>
        
        <td><p>Padding top of the alert empty message</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-md-message-empty-padding-end</code></td>
        
          <td><code>$alert-md-message-empty-padding-top</code></td>
        
        <td><p>Padding end of the alert empty message</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-md-message-empty-padding-bottom</code></td>
        
          <td><code>$alert-md-message-empty-padding-top</code></td>
        
        <td><p>Padding bottom of the alert empty message</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-md-message-empty-padding-start</code></td>
        
          <td><code>$alert-md-message-empty-padding-end</code></td>
        
        <td><p>Padding start of the alert empty message</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-md-content-max-height</code></td>
        
          <td><code>240px</code></td>
        
        <td><p>Maximum height of the alert content</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-md-input-border-width</code></td>
        
          <td><code>1px</code></td>
        
        <td><p>Border width of the alert input</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-md-input-border-style</code></td>
        
          <td><code>solid</code></td>
        
        <td><p>Border style of the alert input</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-md-input-border-color</code></td>
        
          <td><code>#dedede</code></td>
        
        <td><p>Border color of the alert input</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-md-input-text-color</code></td>
        
          <td><code>#000</code></td>
        
        <td><p>Text color of the alert input</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-md-input-border-width-focused</code></td>
        
          <td><code>2px</code></td>
        
        <td><p>Border width of the alert input when focused</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-md-input-border-style-focused</code></td>
        
          <td><code>$alert-md-input-border-style</code></td>
        
        <td><p>Border style of the alert input when focused</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-md-input-border-color-focused</code></td>
        
          <td><code>color($colors-md, primary)</code></td>
        
        <td><p>Border color of the alert input when focused</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-md-input-margin-top</code></td>
        
          <td><code>5px</code></td>
        
        <td><p>Margin top of the alert input</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-md-input-margin-end</code></td>
        
          <td><code>$alert-md-input-margin-right</code></td>
        
        <td><p>Margin end of the alert input</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-md-input-margin-bottom</code></td>
        
          <td><code>5px</code></td>
        
        <td><p>Margin bottom of the alert input</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-md-input-margin-start</code></td>
        
          <td><code>$alert-md-input-margin-left</code></td>
        
        <td><p>Margin start of the alert input</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-md-button-group-flex-wrap</code></td>
        
          <td><code>wrap-reverse</code></td>
        
        <td><p>Flex wrap of the alert button group</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-md-button-group-padding-top</code></td>
        
          <td><code>8px</code></td>
        
        <td><p>Padding top of the alert button group</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-md-button-group-padding-end</code></td>
        
          <td><code>8px</code></td>
        
        <td><p>Padding end of the alert button group</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-md-button-group-padding-bottom</code></td>
        
          <td><code>8px</code></td>
        
        <td><p>Padding bottom of the alert button group</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-md-button-group-padding-start</code></td>
        
          <td><code>24px</code></td>
        
        <td><p>Padding start of the alert button group</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-md-button-group-justify-content</code></td>
        
          <td><code>flex-end</code></td>
        
        <td><p>Justify content of the alert button group</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-md-button-padding-top</code></td>
        
          <td><code>10px</code></td>
        
        <td><p>Padding top of the alert button</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-md-button-padding-end</code></td>
        
          <td><code>$alert-md-button-padding-top</code></td>
        
        <td><p>Padding end of the alert button</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-md-button-padding-bottom</code></td>
        
          <td><code>$alert-md-button-padding-top</code></td>
        
        <td><p>Padding bottom of the alert button</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-md-button-padding-start</code></td>
        
          <td><code>$alert-md-button-padding-end</code></td>
        
        <td><p>Padding start of the alert button</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-md-button-margin-top</code></td>
        
          <td><code>0</code></td>
        
        <td><p>Margin top of the alert button</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-md-button-margin-end</code></td>
        
          <td><code>8px</code></td>
        
        <td><p>Margin end of the alert button</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-md-button-margin-bottom</code></td>
        
          <td><code>0</code></td>
        
        <td><p>Margin bottom of the alert button</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-md-button-margin-start</code></td>
        
          <td><code>0</code></td>
        
        <td><p>Margin start of the alert button</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-md-button-font-weight</code></td>
        
          <td><code>500</code></td>
        
        <td><p>Font weight of the alert button</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-md-button-text-color</code></td>
        
          <td><code>color($colors-md, primary)</code></td>
        
        <td><p>Text color of the alert button</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-md-button-background-color</code></td>
        
          <td><code>transparent</code></td>
        
        <td><p>Background color of the alert button</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-md-button-background-color-activated</code></td>
        
          <td><code>rgba(158, 158, 158, .2)</code></td>
        
        <td><p>Background color of the alert activated button</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-md-button-border-radius</code></td>
        
          <td><code>2px</code></td>
        
        <td><p>Border radius of the alert button</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-md-button-text-transform</code></td>
        
          <td><code>uppercase</code></td>
        
        <td><p>Text transform of the alert button</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-md-button-text-align</code></td>
        
          <td><code>end</code></td>
        
        <td><p>Text align of the alert button</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-md-list-border-top</code></td>
        
          <td><code>1px solid $alert-md-input-border-color</code></td>
        
        <td><p>Border top of the alert list</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-md-list-border-bottom</code></td>
        
          <td><code>$alert-md-list-border-top</code></td>
        
        <td><p>Border bottom of the alert list</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-md-radio-label-padding-top</code></td>
        
          <td><code>13px</code></td>
        
        <td><p>Padding top on the label for the radio alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-md-radio-label-padding-end</code></td>
        
          <td><code>26px</code></td>
        
        <td><p>Padding end on the label for the radio alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-md-radio-label-padding-bottom</code></td>
        
          <td><code>$alert-md-radio-label-padding-top</code></td>
        
        <td><p>Padding bottom on the label for the radio alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-md-radio-label-padding-start</code></td>
        
          <td><code>$alert-md-radio-label-padding-end</code></td>
        
        <td><p>Padding start on the label for the radio alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-md-radio-label-text-color</code></td>
        
          <td><code>initial</code></td>
        
        <td><p>Text color of the label for the radio alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-md-radio-label-text-color-checked</code></td>
        
          <td><code>$alert-md-button-text-color</code></td>
        
        <td><p>Text color of the label for the checked radio alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-md-radio-top</code></td>
        
          <td><code>0</code></td>
        
        <td><p>Top of the alert radio</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-md-radio-left</code></td>
        
          <td><code>13px</code></td>
        
        <td><p>Left of the alert radio</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-md-radio-width</code></td>
        
          <td><code>16px</code></td>
        
        <td><p>Width of the alert radio</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-md-radio-height</code></td>
        
          <td><code>16px</code></td>
        
        <td><p>Height of the alert radio</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-md-radio-border-width</code></td>
        
          <td><code>2px</code></td>
        
        <td><p>Border width of the alert radio</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-md-radio-border-style</code></td>
        
          <td><code>solid</code></td>
        
        <td><p>Border style of the alert radio</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-md-radio-border-radius</code></td>
        
          <td><code>50%</code></td>
        
        <td><p>Border radius of the alert radio</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-md-radio-border-color-off</code></td>
        
          <td><code>darken($list-md-border-color, 40%)</code></td>
        
        <td><p>Border color of the alert radio when off</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-md-radio-border-color-on</code></td>
        
          <td><code>$alert-md-button-text-color</code></td>
        
        <td><p>Border color of the alert radio when on</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-md-radio-icon-top</code></td>
        
          <td><code>2px</code></td>
        
        <td><p>Top of the icon in the alert radio</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-md-radio-icon-start</code></td>
        
          <td><code>$alert-md-radio-icon-left</code></td>
        
        <td><p>Start of the icon in the radio alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-md-radio-icon-width</code></td>
        
          <td><code>8px</code></td>
        
        <td><p>Width of the icon in the alert radio</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-md-radio-icon-height</code></td>
        
          <td><code>8px</code></td>
        
        <td><p>Height of the icon in the alert radio</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-md-radio-icon-border-radius</code></td>
        
          <td><code>$alert-md-radio-border-radius</code></td>
        
        <td><p>Border radius of the icon in the alert radio</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-md-radio-icon-transform-off</code></td>
        
          <td><code>scale3d(0, 0, 0)</code></td>
        
        <td><p>Transform of the icon in the alert radio when off</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-md-radio-icon-transform-on</code></td>
        
          <td><code>scale3d(1, 1, 1)</code></td>
        
        <td><p>Transform of the icon in the alert radio when on</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-md-radio-icon-transition</code></td>
        
          <td><code>transform 280ms cubic-bezier(.4, 0, .2, 1)</code></td>
        
        <td><p>Transition of the icon in the alert radio</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-md-checkbox-label-padding-top</code></td>
        
          <td><code>13px</code></td>
        
        <td><p>Padding top of the label for the checkbox in the alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-md-checkbox-label-padding-end</code></td>
        
          <td><code>26px</code></td>
        
        <td><p>Padding end of the label for the checkbox in the alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-md-checkbox-label-padding-bottom</code></td>
        
          <td><code>$alert-md-checkbox-label-padding-top</code></td>
        
        <td><p>Padding bottom of the label for the checkbox in the alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-md-checkbox-label-padding-start</code></td>
        
          <td><code>$alert-md-checkbox-label-padding-end</code></td>
        
        <td><p>Padding start of the label for the checkbox in the alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-md-checkbox-label-text-color</code></td>
        
          <td><code>initial</code></td>
        
        <td><p>Text color of the label for the checkbox in the alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-md-checkbox-label-text-color-checked</code></td>
        
          <td><code>initial</code></td>
        
        <td><p>Text color of the label for the checked checkbox in the alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-md-checkbox-top</code></td>
        
          <td><code>0</code></td>
        
        <td><p>Top of the checkbox in the alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-md-checkbox-left</code></td>
        
          <td><code>13px</code></td>
        
        <td><p>Left of the checkbox in the alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-md-checkbox-width</code></td>
        
          <td><code>16px</code></td>
        
        <td><p>Width of the checkbox in the alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-md-checkbox-height</code></td>
        
          <td><code>16px</code></td>
        
        <td><p>Height of the checkbox in the alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-md-checkbox-border-width</code></td>
        
          <td><code>2px</code></td>
        
        <td><p>Border width of the checkbox in the alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-md-checkbox-border-style</code></td>
        
          <td><code>solid</code></td>
        
        <td><p>Border style of the checkbox in the alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-md-checkbox-border-radius</code></td>
        
          <td><code>2px</code></td>
        
        <td><p>Border radius of the checkbox in the alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-md-checkbox-border-color-off</code></td>
        
          <td><code>darken($list-md-border-color, 40%)</code></td>
        
        <td><p>Border color of the checkbox in the alert when off</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-md-checkbox-border-color-on</code></td>
        
          <td><code>$alert-md-button-text-color</code></td>
        
        <td><p>Border color of the checkbox in the alert when on</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-md-checkbox-icon-top</code></td>
        
          <td><code>0</code></td>
        
        <td><p>Top of the icon in the checkbox alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-md-checkbox-icon-start</code></td>
        
          <td><code>$alert-md-checkbox-icon-left</code></td>
        
        <td><p>Start of the icon in the checkbox alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-md-checkbox-icon-width</code></td>
        
          <td><code>6px</code></td>
        
        <td><p>Width of the icon in the checkbox alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-md-checkbox-icon-height</code></td>
        
          <td><code>10px</code></td>
        
        <td><p>Height of the icon in the checkbox alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-md-checkbox-icon-border-width</code></td>
        
          <td><code>2px</code></td>
        
        <td><p>Border width of the icon in the checkbox alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-md-checkbox-icon-border-style</code></td>
        
          <td><code>solid</code></td>
        
        <td><p>Border style of the icon in the checkbox alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-md-checkbox-icon-border-color</code></td>
        
          <td><code>color-contrast($colors-md, $alert-md-checkbox-border-color-on)</code></td>
        
        <td><p>Border color of the icon in the checkbox alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-md-checkbox-icon-transform</code></td>
        
          <td><code>rotate(45deg)</code></td>
        
        <td><p>Transform of the icon in the checkbox alert</p>
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
        <td><code>$alert-wp-backdrop-background</code></td>
        
          <td><code>#fff</code></td>
        
        <td><p>Background of the alert backdrop</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-wp-width</code></td>
        
          <td><code>100%</code></td>
        
        <td><p>Width of the alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-wp-max-width</code></td>
        
          <td><code>520px</code></td>
        
        <td><p>Max width of the alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-wp-border-width</code></td>
        
          <td><code>1px</code></td>
        
        <td><p>Border width of the alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-wp-border-style</code></td>
        
          <td><code>solid</code></td>
        
        <td><p>Border style of the alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-wp-border-color</code></td>
        
          <td><code>color($colors-wp, primary)</code></td>
        
        <td><p>Border color of the alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-wp-border-radius</code></td>
        
          <td><code>0</code></td>
        
        <td><p>Border radius of the alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-wp-background</code></td>
        
          <td><code>#e6e6e6</code></td>
        
        <td><p>Background color of the alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-wp-head-padding-top</code></td>
        
          <td><code>20px</code></td>
        
        <td><p>Padding top of the alert head</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-wp-head-padding-end</code></td>
        
          <td><code>22px</code></td>
        
        <td><p>Padding end of the alert head</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-wp-head-padding-bottom</code></td>
        
          <td><code>5px</code></td>
        
        <td><p>Padding bottom of the alert head</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-wp-head-padding-start</code></td>
        
          <td><code>22px</code></td>
        
        <td><p>Padding start of the alert head</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-wp-head-text-align</code></td>
        
          <td><code>start</code></td>
        
        <td><p>Text align of the alert head</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-wp-title-font-size</code></td>
        
          <td><code>20px</code></td>
        
        <td><p>Font size of the alert title</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-wp-title-font-weight</code></td>
        
          <td><code>400</code></td>
        
        <td><p>Font weight of the alert title</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-wp-sub-title-font-size</code></td>
        
          <td><code>16px</code></td>
        
        <td><p>Font size of the alert sub title</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-wp-message-padding-top</code></td>
        
          <td><code>0</code></td>
        
        <td><p>Padding top of the alert message</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-wp-message-padding-end</code></td>
        
          <td><code>22px</code></td>
        
        <td><p>Padding end of the alert message</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-wp-message-padding-bottom</code></td>
        
          <td><code>8px</code></td>
        
        <td><p>Padding bottom of the alert message</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-wp-message-padding-start</code></td>
        
          <td><code>22px</code></td>
        
        <td><p>Padding start of the alert message</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-wp-message-empty-padding-top</code></td>
        
          <td><code>0</code></td>
        
        <td><p>Padding top of the alert empty message</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-wp-message-empty-padding-end</code></td>
        
          <td><code>$alert-wp-message-empty-padding-top</code></td>
        
        <td><p>Padding end of the alert empty message</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-wp-message-empty-padding-bottom</code></td>
        
          <td><code>$alert-wp-message-empty-padding-top</code></td>
        
        <td><p>Padding bottom of the alert empty message</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-wp-message-empty-padding-start</code></td>
        
          <td><code>$alert-wp-message-empty-padding-end</code></td>
        
        <td><p>Padding start of the alert empty message</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-wp-message-text-color</code></td>
        
          <td><code>#000</code></td>
        
        <td><p>Text color of the alert message</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-wp-message-font-size</code></td>
        
          <td><code>13px</code></td>
        
        <td><p>Font size of the alert message</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-wp-content-max-height</code></td>
        
          <td><code>240px</code></td>
        
        <td><p>Maximum height of the alert content</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-wp-input-margin-top</code></td>
        
          <td><code>5px</code></td>
        
        <td><p>Margin top of the alert input</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-wp-input-margin-end</code></td>
        
          <td><code>0</code></td>
        
        <td><p>Margin end of the alert input</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-wp-input-margin-bottom</code></td>
        
          <td><code>5px</code></td>
        
        <td><p>Margin bottom of the alert input</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-wp-input-margin-start</code></td>
        
          <td><code>0</code></td>
        
        <td><p>Margin start of the alert input</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-wp-input-padding-top</code></td>
        
          <td><code>0</code></td>
        
        <td><p>Padding top on the alert input</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-wp-input-padding-end</code></td>
        
          <td><code>8px</code></td>
        
        <td><p>Padding end on the alert input</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-wp-input-padding-bottom</code></td>
        
          <td><code>$alert-wp-input-padding-top</code></td>
        
        <td><p>Padding bottom on the alert input</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-wp-input-padding-start</code></td>
        
          <td><code>$alert-wp-input-padding-end</code></td>
        
        <td><p>Padding start on the alert input</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-wp-input-border-width</code></td>
        
          <td><code>2px</code></td>
        
        <td><p>Border width of the alert input</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-wp-input-border-style</code></td>
        
          <td><code>$alert-wp-border-style</code></td>
        
        <td><p>Border style of the alert input</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-wp-input-border-color</code></td>
        
          <td><code>$input-wp-border-color</code></td>
        
        <td><p>Border color of the alert input</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-wp-input-border-color-focused</code></td>
        
          <td><code>color($colors-wp, primary)</code></td>
        
        <td><p>Border color of the alert input when focused</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-wp-input-line-height</code></td>
        
          <td><code>3rem</code></td>
        
        <td><p>Line height of the alert input</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-wp-input-text-color</code></td>
        
          <td><code>#000</code></td>
        
        <td><p>Color of the text in the alert input</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-wp-button-padding-top</code></td>
        
          <td><code>5px</code></td>
        
        <td><p>Padding top of the alert button</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-wp-button-padding-end</code></td>
        
          <td><code>$alert-wp-button-padding-top</code></td>
        
        <td><p>Padding end of the alert button</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-wp-button-padding-bottom</code></td>
        
          <td><code>$alert-wp-button-padding-top</code></td>
        
        <td><p>Padding bottom of the alert button</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-wp-button-padding-start</code></td>
        
          <td><code>$alert-wp-button-padding-end</code></td>
        
        <td><p>Padding start of the alert button</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-wp-button-width</code></td>
        
          <td><code>49.5%</code></td>
        
        <td><p>Width of the alert button</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-wp-button-border-radius</code></td>
        
          <td><code>0</code></td>
        
        <td><p>Border radius of the alert button</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-wp-button-font-weight</code></td>
        
          <td><code>400</code></td>
        
        <td><p>Font weight of the alert button</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-wp-button-text-color</code></td>
        
          <td><code>#000</code></td>
        
        <td><p>Color of the text in the alert button</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-wp-button-background</code></td>
        
          <td><code>#b8b8b8</code></td>
        
        <td><p>Background color of the alert button</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-wp-button-background-activated</code></td>
        
          <td><code>color-shade($alert-wp-button-background)</code></td>
        
        <td><p>Background color of the activated alert button</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-wp-button-margin-end</code></td>
        
          <td><code>$alert-wp-button-margin-right</code></td>
        
        <td><p>Margin end of the alert button</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-wp-button-group-padding-top</code></td>
        
          <td><code>20px</code></td>
        
        <td><p>Padding top of the alert button group</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-wp-button-group-padding-end</code></td>
        
          <td><code>22px</code></td>
        
        <td><p>Padding end of the alert button group</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-wp-button-group-padding-bottom</code></td>
        
          <td><code>20px</code></td>
        
        <td><p>Padding bottom of the alert button group</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-wp-button-group-padding-start</code></td>
        
          <td><code>22px</code></td>
        
        <td><p>Padding start of the alert button group</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-wp-button-group-justify-content</code></td>
        
          <td><code>flex-end</code></td>
        
        <td><p>Justify content of the alert button group</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-wp-button-group-flex-wrap</code></td>
        
          <td><code>wrap-reverse</code></td>
        
        <td><p>Flex wrap of the alert button group</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-wp-button-group-vertical-width</code></td>
        
          <td><code>100%</code></td>
        
        <td><p>Vertical width of the vertical alert button group</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-wp-button-group-vertical-margin-top</code></td>
        
          <td><code>5px</code></td>
        
        <td><p>Margin top of the vertical alert button group</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-wp-radio-background</code></td>
        
          <td><code>color($colors-wp, primary)</code></td>
        
        <td><p>Background color of the radio alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-wp-radio-border-color</code></td>
        
          <td><code>$input-wp-border-color</code></td>
        
        <td><p>Border color of the radio alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-wp-radio-label-padding-top</code></td>
        
          <td><code>13px</code></td>
        
        <td><p>Padding top of the label for the radio alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-wp-radio-label-padding-end</code></td>
        
          <td><code>26px</code></td>
        
        <td><p>Padding end of the label for the radio alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-wp-radio-label-padding-bottom</code></td>
        
          <td><code>$alert-wp-radio-label-padding-top</code></td>
        
        <td><p>Padding bottom of the label for the radio alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-wp-radio-label-padding-start</code></td>
        
          <td><code>$alert-wp-radio-label-padding-end</code></td>
        
        <td><p>Padding start of the label for the radio alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-wp-radio-label-text-color</code></td>
        
          <td><code>initial</code></td>
        
        <td><p>Text color of the label for the radio alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-wp-radio-label-text-color-checked</code></td>
        
          <td><code>$alert-wp-button-text-color</code></td>
        
        <td><p>Text color of the label for the checked radio alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-wp-radio-top</code></td>
        
          <td><code>0</code></td>
        
        <td><p>Top of the radio alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-wp-radio-left</code></td>
        
          <td><code>13px</code></td>
        
        <td><p>Left of the radio alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-wp-radio-width</code></td>
        
          <td><code>16px</code></td>
        
        <td><p>Width of the radio alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-wp-radio-height</code></td>
        
          <td><code>16px</code></td>
        
        <td><p>Height of the radio alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-wp-radio-border-width</code></td>
        
          <td><code>2px</code></td>
        
        <td><p>Border width of the radio alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-wp-radio-border-style</code></td>
        
          <td><code>solid</code></td>
        
        <td><p>Border style of the radio alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-wp-radio-border-radius</code></td>
        
          <td><code>50%</code></td>
        
        <td><p>Border radius of the radio alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-wp-radio-border-color</code></td>
        
          <td><code>$input-wp-border-color</code></td>
        
        <td><p>Border color of the radio alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-wp-radio-icon-top</code></td>
        
          <td><code>2px</code></td>
        
        <td><p>Top of the icon in the radio alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-wp-radio-icon-start</code></td>
        
          <td><code>$alert-wp-radio-icon-left</code></td>
        
        <td><p>Start of the icon in the radio alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-wp-radio-icon-width</code></td>
        
          <td><code>8px</code></td>
        
        <td><p>Width of the icon in the radio alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-wp-radio-icon-height</code></td>
        
          <td><code>8px</code></td>
        
        <td><p>Height of the icon in the radio alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-wp-radio-icon-border-radius</code></td>
        
          <td><code>$alert-wp-radio-border-radius</code></td>
        
        <td><p>Border radius of the icon in the radio alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-wp-checkbox-label-padding-top</code></td>
        
          <td><code>13px</code></td>
        
        <td><p>Padding top of the label for the checkbox in the alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-wp-checkbox-label-padding-end</code></td>
        
          <td><code>26px</code></td>
        
        <td><p>Padding end of the label for the checkbox in the alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-wp-checkbox-label-padding-bottom</code></td>
        
          <td><code>$alert-wp-checkbox-label-padding-top</code></td>
        
        <td><p>Padding bottom of the label for the checkbox in the alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-wp-checkbox-label-padding-start</code></td>
        
          <td><code>$alert-wp-checkbox-label-padding-end</code></td>
        
        <td><p>Padding start of the label for the checkbox in the alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-wp-checkbox-label-text-color</code></td>
        
          <td><code>initial</code></td>
        
        <td><p>Text color of the label for the checkbox in the alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-wp-checkbox-label-text-color-checked</code></td>
        
          <td><code>initial</code></td>
        
        <td><p>Text color of the label for the checked checkbox in the alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-wp-checkbox-top</code></td>
        
          <td><code>0</code></td>
        
        <td><p>Top of the checkbox in the alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-wp-checkbox-left</code></td>
        
          <td><code>13px</code></td>
        
        <td><p>Left of the checkbox in the alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-wp-checkbox-width</code></td>
        
          <td><code>16px</code></td>
        
        <td><p>Width of the checkbox in the alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-wp-checkbox-height</code></td>
        
          <td><code>16px</code></td>
        
        <td><p>Height of the checkbox in the alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-wp-checkbox-border-width</code></td>
        
          <td><code>2px</code></td>
        
        <td><p>Border width of the checkbox in the alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-wp-checkbox-border-style</code></td>
        
          <td><code>solid</code></td>
        
        <td><p>Border style of the checkbox in the alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-wp-checkbox-border-radius</code></td>
        
          <td><code>0</code></td>
        
        <td><p>Border radius of the checkbox in the alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-wp-checkbox-border-color</code></td>
        
          <td><code>$input-wp-border-color</code></td>
        
        <td><p>Border color of the checkbox in the alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-wp-checkbox-background-off</code></td>
        
          <td><code>transparent</code></td>
        
        <td><p>Background color of the checkbox in the alert when off</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-wp-checkbox-background-on</code></td>
        
          <td><code>color($colors-wp, primary)</code></td>
        
        <td><p>Background color of the checkbox in the alert when on</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-wp-checkbox-icon-top</code></td>
        
          <td><code>-2px</code></td>
        
        <td><p>Top of the icon in the checkbox alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-wp-checkbox-icon-start</code></td>
        
          <td><code>$alert-wp-checkbox-icon-left</code></td>
        
        <td><p>Start of the icon in the checkbox alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-wp-checkbox-icon-width</code></td>
        
          <td><code>6px</code></td>
        
        <td><p>Width of the icon in the checkbox alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-wp-checkbox-icon-height</code></td>
        
          <td><code>12px</code></td>
        
        <td><p>Height of the icon in the checkbox alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-wp-checkbox-icon-border-width</code></td>
        
          <td><code>1px</code></td>
        
        <td><p>Border width of the icon in the checkbox alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-wp-checkbox-icon-border-style</code></td>
        
          <td><code>solid</code></td>
        
        <td><p>Border style of the icon in the checkbox alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-wp-checkbox-icon-border-color</code></td>
        
          <td><code>color-contrast($colors-wp, $alert-wp-checkbox-background-on)</code></td>
        
        <td><p>Border color of the icon in the checkbox alert</p>
</td>
      </tr>
      
      <tr>
        <td><code>$alert-wp-checkbox-icon-transform</code></td>
        
          <td><code>rotate(45deg)</code></td>
        
        <td><p>Transform of the icon in the checkbox alert</p>
</td>
      </tr>
      
    </tbody>
  </table>
  
</div>



<!-- related link --><!-- end content block -->


<!-- end body block -->

