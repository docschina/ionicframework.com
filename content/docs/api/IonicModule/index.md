---
layout: "fluid/docs_base"
version: "3.9.2"
versionHref: "/docs"
path: ""
category: api
id: "ionicmodule"
title: "IonicModule"
header_sub_title: "Ionic API Documentation"
doc: "IonicModule"
docType: "class"

---









<h1 class="api-title">
<a class="anchor" name="ionic-module" href="#ionic-module"></a>

IonicModule





</h1>

<a class="improve-v2-docs" href="http://github.com/ionic-team/ionic/edit/master/src/module.ts#L139">
Improve this doc
</a>






<p>IonicModule 是一个启动 Ionic App 的 <a href="https://angular.io/docs/ts/latest/guide/ngmodule.html">NgModule</a>。通过传递一个根组件，IonicModule 将确保框架中的所有组件，指令和提供程序都被导入。</p>
<p>应用程序的任何配置都可以作为第二个参数传递给 <code>forRoot</code>。这可以是 <a href="/docs/api/config/Config/">Config</a> 中的任意有效属性。</p>







<!-- @usage tag -->

<h2><a class="anchor" name="usage" href="#usage">Usage</a></h2>

<pre><code class="lang-ts">import { NgModule } from &#39;@angular/core&#39;;

import { IonicApp, IonicModule } from &#39;ionic-angular&#39;;

import { MyApp } from &#39;./app.component&#39;;
import { HomePage } from &#39;../pages/home/home&#39;;

@NgModule({
  declarations: [
    MyApp,
    HomePage
  ],
  imports: [
    BrowserModule,
    IonicModule.forRoot(MyApp, {

    })
  ],
  bootstrap: [IonicApp],
  entryComponents: [
    MyApp,
    HomePage
  ],
  providers: []
})
export class AppModule {}
</code></pre>




<!-- @property tags -->
<h2><a class="anchor" name="static-members" href="#static-members">静态成员</a></h2>
<div id="forRoot"></div>
<h3><a class="anchor" name="forRoot" href="#forRoot"><code>forRoot(appRoot,&nbsp;config,&nbsp;deepLinkConfig)</code>
  
</a></h3>

为你的 IonicModule 设置应用的根组件 


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
        appRoot
        
        
      </td>
      <td>
        
  <code>any</code>
      </td>
      <td>
        <p>这个应用程序的根 AppComponent。</p>

        
      </td>
    </tr>
    
    <tr>
      <td>
        config
        
        
      </td>
      <td>
        
  <code>any</code>
      </td>
      <td>
        <p>配置应用程序的选项。接受任何配置属性。</p>

        
      </td>
    </tr>
    
    <tr>
      <td>
        deepLinkConfig
        
        
      </td>
      <td>
        
  <code>any</code>
      </td>
      <td>
        <p>Ionic Deeplinker 所需的所有配置。</p>

        
      </td>
    </tr>
    
  </tbody>
</table>









<!-- instance methods on the class -->




<!-- related link --><!-- end content block -->


<!-- end body block -->

