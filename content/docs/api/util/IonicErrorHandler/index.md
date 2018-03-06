---
layout: "fluid/docs_base"
version: "3.9.2"
versionHref: "/docs"
path: ""
category: api
id: "ionicerrorhandler"
title: "IonicErrorHandler"
header_sub_title: "Ionic API Documentation"
doc: "IonicErrorHandler"
docType: "class"

---









<h1 class="api-title">
<a class="anchor" name="ionic-error-handler" href="#ionic-error-handler"></a>

IonicErrorHandler





</h1>

<a class="improve-v2-docs" href="http://github.com/ionic-team/ionic/edit/master/src/util/ionic-error-handler.ts#L0">
Improve this doc
</a>






<p><code>IonicErrorHandler</code> 拦截默认的 <code>Console</code> 错误处理，并在使用 Ionic 的 Dev Build Server 时将运行时的错误叠加显示。</p>
<h3><a class="anchor" name="ionicerrorhandler-example" href="#ionicerrorhandler-example">IonicErrorHandler 示例</a></h3>



<pre><code class="lang-typescript">import { NgModule, ErrorHandler } from &#39;@angular/core&#39;;
import { IonicErrorHandler } from &#39;ionic-angular&#39;;

@NgModule({
  providers: [{ provide: ErrorHandler, useClass: IonicErrorHandler }]
})
class AppModule {}
</code></pre>
<h3><a class="anchor" name="custom-error-handlers" href="#custom-error-handlers">自定义错误处理函数</a></h3>


<p>可以构建自定义错误处理函数来替换默认值，或者扩展 Ionic 的错误处理程序。</p>

<pre><code class="lang-typescript">class MyErrorHandler implements ErrorHandler {
  handleError(err: any): void {
    // 对错误做些什么
  }
}

@NgModule({
  providers: [{ provide: ErrorHandler, useClass: MyErrorHandler }]
})
class AppModule {}
</code></pre>
<p>有关 Angular <a href="https://angular.io/docs/ts/latest/api/core/index/ErrorHandler-class.html"><code>ErrorHandler</code></a>的更多信息。</p>




<!-- @usage tag -->


<!-- @property tags -->



<!-- instance methods on the class -->




<!-- related link --><!-- end content block -->


<!-- end body block -->

