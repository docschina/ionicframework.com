---
layout: "fluid/docs_base"
version: "3.9.2"
versionHref: "/docs"
path: ""
category: api
id: "haptic"
title: "Haptic"
header_sub_title: "Ionic API Documentation"
doc: "Haptic"
docType: "class"

---









<h1 class="api-title">
<a class="anchor" name="haptic" href="#haptic"></a>

Haptic





</h1>

<a class="improve-v2-docs" href="http://github.com/ionic-team/ionic/edit/master/src/tap-click/haptic.ts#L2">
Improve this doc
</a>






<p>如果设备支持，<code>Haptic</code> 类会与设备上的触觉引擎交互。通常情况下，Ionic 组件使用这个引擎，但是如果你喜欢的话，欢迎你投入其中并获得乐趣。</p>
<p>目前，在 iOS 上使用 Taptic 引擎。</p>






<!-- @usage tag -->

<h2><a class="anchor" name="usage" href="#usage">用法</a></h2>

<pre><code class="lang-ts">export class MyClass{
 constructor(haptic: Haptic){
   haptic.selection();
 }
}
</code></pre>




<!-- @property tags -->



<!-- instance methods on the class -->

<h2><a class="anchor" name="instance-members" href="#instance-members">实例成员</a></h2>

<div id="available"></div>

<h3>
<a class="anchor" name="available" href="#available">
<code>available()</code>
  

</a>
</h3>

检查 Haptic 插件是否可用






<div class="return-value">
<i class="icon ion-arrow-return-left"></i>
<b>Returns:</b> 
  <code>boolean</code> <p>插件是否可用，返回 true 或 false</p>


</div>




<div id="gestureSelectionChanged"></div>

<h3>
<a class="anchor" name="gestureSelectionChanged" href="#gestureSelectionChanged">
<code>gestureSelectionChanged()</code>
  

</a>
</h3>

告知 haptic 引擎在手势过程中 selection 发生的变化。










<div id="gestureSelectionEnd"></div>

<h3>
<a class="anchor" name="gestureSelectionEnd" href="#gestureSelectionEnd">
<code>gestureSelectionEnd()</code>
  

</a>
</h3>

通过手势告知 haptic 引擎工作完成。这被称为土地资源（lest resources）不妥善的回收。











<div id="gestureSelectionStart"></div>

<h3>
<a class="anchor" name="gestureSelectionStart" href="#gestureSelectionStart">
<code>gestureSelectionStart()</code>
  

</a>
</h3>

告知 haptic 引擎 selection 改变的手势正在启动。










<div id="impact"></div>

<h3>
<a class="anchor" name="impact" href="#impact">
<code>impact()</code>
  

</a>
</h3>

用它来指示用户的成功/失败/警告。选项应该是 `{ style: 'light' }` （或 `medium`/`heavy`）











<div id="notification"></div>

<h3>
<a class="anchor" name="notification" href="#notification">
<code>notification()</code>
  

</a>
</h3>

用它来指示用户的成功/失败/警告。选项应该是 `{ type: 'success' }` （或 `warning`/`error`）











<div id="selection"></div>

<h3>
<a class="anchor" name="selection" href="#selection">
<code>selection()</code>
  

</a>
</h3>

触发 selection 更改的 haptic 事件。适合一次性事件（不适用于手势）














<!-- related link --><!-- end content block -->


<!-- end body block -->

