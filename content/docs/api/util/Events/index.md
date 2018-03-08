---
layout: "fluid/docs_base"
version: "3.9.2"
versionHref: "/docs"
path: ""
category: api
id: "events"
title: "Events"
header_sub_title: "Ionic API Documentation"
doc: "Events"
docType: "class"
show_preview_device: true
preview_device_url: "/docs/demos/src/events/www/"
angular_controller: APIDemoCtrl
---









<h1 class="api-title">
<a class="anchor" name="events" href="#events"></a>

Events





</h1>

<a class="improve-v2-docs" href="http://github.com/ionic-team/ionic/edit/master/src/util/events.ts#L2">
改进这篇文档
</a>






<p>Events 是一个发布 - 订阅式事件系统，用于在应用程序中发送和响应应用程序级别（application-level）的事件。</p>





<!-- @usage tag -->

<h2><a class="anchor" name="usage" href="#usage">用法</a></h2>

<pre><code class="lang-ts">import { Events } from &#39;ionic-angular&#39;;

// 第一页（创建用户时，发布一个事件）
constructor(public events: Events) {}
createUser(user) {
  console.log(&#39;User created!&#39;)
  this.events.publish(&#39;user:created&#39;, user, Date.now());
}


// 第二页（在函数调用后，监听用户创建的事件）
constructor(public events: Events) {
  events.subscribe(&#39;user:created&#39;, (user, time) =&gt; {
    // user 和 time 是 `events.publish(user, time)` 中传递的参数
    console.log(&#39;Welcome&#39;, user, &#39;at&#39;, time);
  });
}
</code></pre>




<!-- @property tags -->



<!-- instance methods on the class -->

<h2><a class="anchor" name="instance-members" href="#instance-members">实例成员</a></h2>

<div id="publish"></div>

<h3>
<a class="anchor" name="publish" href="#publish">
<code>publish(topic,&nbsp;eventData)</code>


</a>
</h3>

发布一个给定主题的事件。



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
        topic


      </td>
      <td>

  <code>string</code>
      </td>
      <td>
        <p>发布的主题</p>


      </td>
    </tr>

    <tr>
      <td>
        eventData


      </td>
      <td>

  <code>any</code>
      </td>
      <td>
        <p>作为事件发送的数据</p>


      </td>
    </tr>

  </tbody>
</table>








<div id="subscribe"></div>

<h3>
<a class="anchor" name="subscribe" href="#subscribe">
<code>subscribe(topic,&nbsp;handler)</code>


</a>
</h3>

订阅事件主题。发布到该主题的事件将触发提供的处理函数。



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
        topic


      </td>
      <td>

  <code>string</code>
      </td>
      <td>
        <p>要订阅的主题</p>


      </td>
    </tr>

    <tr>
      <td>
        handler


      </td>
      <td>

  <code>function</code>
      </td>
      <td>
        <p>事件处理函数</p>


      </td>
    </tr>

  </tbody>
</table>








<div id="unsubscribe"></div>

<h3>
<a class="anchor" name="unsubscribe" href="#unsubscribe">
<code>unsubscribe(topic,&nbsp;handler)</code>


</a>
</h3>

取消订阅给定的主题。你的处理函数将不再接收发布到该主题的事件。



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
        topic


      </td>
      <td>

  <code>string</code>
      </td>
      <td>
        <p>需要取消订阅的主题</p>


      </td>
    </tr>

    <tr>
      <td>
        handler


      </td>
      <td>

  <code>function</code>
      </td>
      <td>
        <p>事件处理函数</p>


      </td>
    </tr>

  </tbody>
</table>





<div class="return-value">
<i class="icon ion-arrow-return-left"></i>
<b>返回：</b>
   <p>如果处理函数被移除，则为 true</p>


</div>







<!-- related link --><!-- end content block -->


<!-- end body block -->

