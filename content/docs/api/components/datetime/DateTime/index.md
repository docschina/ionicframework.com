---
layout: "fluid/docs_base"
version: "3.9.2"
versionHref: "/docs"
path: ""
category: api
id: "datetime"
title: "DateTime"
header_sub_title: "Ionic API Documentation"
doc: "DateTime"
docType: "class"
show_preview_device: true
preview_device_url: "/docs/demos/src/datetime/www/"
angular_controller: APIDemoCtrl
---









<h1 class="api-title">
<a class="anchor" name="date-time" href="#date-time"></a>

DateTime
<h3><code>ion-datetime</code></h3>






</h1>

<a class="improve-v2-docs" href="http://github.com/ionic-team/ionic/edit/master/src/components/datetime/datetime.ts#L26">
改进这篇文档
</a>






<p>DateTime 组件用来显示一个让用户可以轻松选择日期和时间的界面。点击 <code>&lt;ion-datetime&gt;</code> 会显示一个从页面底部往上滑动的选取器（picker）界面。然后，选取器（picker）会显示可滚动的列，来单独选择年，月，日，小时和分钟的值。DateTime 组件类似于原生的
<code>&lt;input type=&quot;datetime-local&quot;&gt;</code> 元素，但是，Ionic 的 DateTime 组件可以很轻松地以首选格式显示日期和时间，并管理日期时间值。</p>






<pre><code class="lang-html">&lt;ion-item&gt;
  &lt;ion-label&gt;Date&lt;/ion-label&gt;
  &lt;ion-datetime displayFormat=&quot;MM/DD/YYYY&quot; [(ngModel)]=&quot;myDate&quot;&gt;&lt;/ion-datetime&gt;
&lt;/ion-item&gt;
</code></pre>
<h2 id="display-and-picker-formats">显示和选取器（picker）格式</h2>
<p>DateTime 组件在两个位置显示值： <code>&lt;ion-datetime&gt;</code> 组件里，以及从屏幕底部显示的界面里。下面的表格列出了可以使用的所有格式。</p>


<table>
<thead>
<tr>
<th>格式</th>
<th>描述</th>
<th>示例</th>
</tr>
</thead>
<tbody>
<tr>
<td><code>YYYY</code></td>
<td>年，4位数</td>
<td><code>2018</code></td>
</tr>
<tr>
<td><code>YY</code></td>
<td>年，2位数</td>
<td><code>18</code></td>
</tr>
<tr>
<td><code>M</code></td>
<td>月</td>
<td><code>1</code> ... <code>12</code></td>
</tr>
<tr>
<td><code>MM</code></td>
<td>月，0开头</td>
<td><code>01</code> ... <code>12</code></td>
</tr>
<tr>
<td><code>MMM</code></td>
<td>月，缩写名称</td>
<td><code>Jan</code></td>
</tr>
<tr>
<td><code>MMMM</code></td>
<td>月，全称</td>
<td><code>January</code></td>
</tr>
<tr>
<td><code>D</code></td>
<td>日</td>
<td><code>1</code> ... <code>31</code></td>
</tr>
<tr>
<td><code>DD</code></td>
<td>日，0开头</td>
<td><code>01</code> ... <code>31</code></td>
</tr>
<tr>
<td><code>DDD</code></td>
<td>日，缩写名称</td>
<td><code>Fri</code></td>
</tr>
<tr>
<td><code>DDDD</code></td>
<td>日，全称</td>
<td><code>Friday</code></td>
</tr>
<tr>
<td><code>H</code></td>
<td>小时，24小时制</td>
<td><code>0</code> ... <code>23</code></td>
</tr>
<tr>
<td><code>HH</code></td>
<td>小时，24小时制，0开头</td>
<td><code>00</code> ... <code>23</code></td>
</tr>
<tr>
<td><code>h</code></td>
<td>小时，12小时制</td>
<td><code>1</code> ... <code>12</code></td>
</tr>
<tr>
<td><code>hh</code></td>
<td>小时，12小时制，0开头</td>
<td><code>01</code> ... <code>12</code></td>
</tr>
<tr>
<td><code>a</code></td>
<td>12小时制，小写</td>
<td><code>am</code> <code>pm</code></td>
</tr>
<tr>
<td><code>A</code></td>
<td>12小时制，大写</td>
<td><code>AM</code> <code>PM</code></td>
</tr>
<tr>
<td><code>m</code></td>
<td>分钟</td>
<td><code>1</code> ... <code>59</code></td>
</tr>
<tr>
<td><code>mm</code></td>
<td>分钟，0开头</td>
<td><code>01</code> ... <code>59</code></td>
</tr>
<tr>
<td><code>s</code></td>
<td>秒</td>
<td><code>1</code> ... <code>59</code></td>
</tr>
<tr>
<td><code>ss</code></td>
<td>秒，0开头</td>
<td><code>01</code> ... <code>59</code></td>
</tr>
<tr>
<td><code>Z</code></td>
<td>UTC 时区偏移量</td>
<td><code>Z 或 +HH:mm or -HH:mm</code></td>
</tr>
</tbody>
</table>
<p><strong>重要提示</strong>：请参阅<a href="#month-names-and-day-of-the-week-names">月份名称和星期名称</a>
以了解如何在月份和日期中使用不同的名称。</p>
<h3><a class="anchor" name="display-format" href="#display-format">显示格式</a></h3>


<p> <code>displayFormat</code> 的输入属性会指定如何将日期时间值作为格式化文本打印在 <code>ion-datetime</code> 组件内。</p>
<p>在以下示例中， <code>&lt;ion-datetime&gt;</code> 中的显示将使用月份的缩写名称，0开头的日期数字，一个逗号，和四位数年份。除了日期之外，它还会以24小时格式和显示分钟和小时。任何字符都可以用作分隔符。使用这种格式的示例：<code>Jun 17, 2005 11:06</code>。</p>





<pre><code class="lang-html">&lt;ion-item&gt;
  &lt;ion-label&gt;Date&lt;/ion-label&gt;
  &lt;ion-datetime displayFormat=&quot;MMM DD, YYYY HH:mm&quot; [(ngModel)]=&quot;myDate&quot;&gt;&lt;/ion-datetime&gt;
&lt;/ion-item&gt;
</code></pre>
<h3><a class="anchor" name="picker-format" href="#picker-format">选取器（Picker）格式</a></h3>


<p> <code>pickerFormat</code> 的输入属性会决定应该在界面中显示的列，列的顺序以及每列中使用哪种格式。如果未提供 <code>pickerFormat</code> 输入，则它将默认为 <code>displayFormat</code>。</p>
<p>在下面的示例中， <code>&lt;ion-datetime&gt;</code> 中的显示将使用 <code>MM/YYYY</code> 格式，例如 <code>06/2020</code>。但是，选取器（picker）界面将显示两个全称月份和四位数年份的列。</p>




<pre><code class="lang-html">&lt;ion-item&gt;
  &lt;ion-label&gt;Date&lt;/ion-label&gt;
  &lt;ion-datetime displayFormat=&quot;MM/YYYY&quot; pickerFormat=&quot;MMMM YYYY&quot; [(ngModel)]=&quot;myDate&quot;&gt;&lt;/ion-datetime&gt;
&lt;/ion-item&gt;
</code></pre>
<h3><a class="anchor" name="datetime-data" href="#datetime-data">Datetime 数据</a></h3>


<p>从历史上看，处理 JavaScript 的 datetime 值，
甚至 HTML 的输入，一直是一个挑战。特别是，
JavaScript 的 <code>Date</code> 对象非常难以正确地解析 datetime 字符串或格式化日期时间值。
更糟糕的是，不同的浏览器和 JavaScript 版本以不同的方式解析各种 datetime 字符串，
尤其是在每个不同的语言环境（locale）中。</p>
<p>但不用担心，一切都不会遗失！
 Ionic 的 datetime 时间输入的设计使开发人员可以避免常见的陷阱，
 允许开发人员轻松地在输入中设置 datetime 值的格式，
 并为用户提供简单的 datetime 选取器（picker），以获得绝佳的用户体验。</p>
<h3><a class="anchor" name="iso-8601-datetime-format-yyyy-mm-ddthh-mmz" href="#iso-8601-datetime-format-yyyy-mm-ddthh-mmz">ISO 8601 Datetime 格式: YYYY-MM-DDTHH:mmZ</a></h3>


<p>Ionic 为其价值使用 <a href="https://www.w3.org/TR/NOTE-datetime">ISO 8601 datetime 格式</a>。该值只是一个字符串，而不是使用 JavaScript 的 <code>Date</code> 对象。此外，使用 ISO 日期时间格式时，它可以更容易地在 JSON 对象中进行序列化和传递，并向数据库发送标准化格式，如果需要的话可以轻松解析它。</p>
<p> ISO 格式可以用于单纯的年，或者单纯的小时和分钟，或者更详细地描述毫秒和时区。可以使用以下任何 ISO 格式，在用户选择新值后，Ionic 将继续使用最初给定的 datetime 值相同的 ISO 格式。</p>







<table>
<thead>
<tr>
<th>描述</th>
<th>格式</th>
<th>Datetime 值示例</th>
</tr>
</thead>
<tbody>
<tr>
<td>年</td>
<td>YYYY</td>
<td>1994</td>
</tr>
<tr>
<td>年和月</td>
<td>YYYY-MM</td>
<td>1994-12</td>
</tr>
<tr>
<td>完整的日期</td>
<td>YYYY-MM-DD</td>
<td>1994-12-15</td>
</tr>
<tr>
<td>日期和时间</td>
<td>YYYY-MM-DDTHH:mm</td>
<td>1994-12-15T13:47</td>
</tr>
<tr>
<td>UTC 时区</td>
<td>YYYY-MM-DDTHH:mm:ssTZD</td>
<td>1994-12-15T13:47:20.789Z</td>
</tr>
<tr>
<td>时区偏移量</td>
<td>YYYY-MM-DDTHH:mm:ssTZD</td>
<td>1994-12-15T13:47:20.789+5:00</td>
</tr>
<tr>
<td>小时和分钟</td>
<td>HH:mm</td>
<td>13:47</td>
</tr>
<tr>
<td>小时，分钟，秒</td>
<td>HH:mm:ss</td>
<td>13:47:20</td>
</tr>
</tbody>
</table>
<p>注意，年份总是四位数，毫秒（如果添加的话）始终为三位数字，其他所有数字始终为两位数字。因此，代表1月份的数字总是有一个前导零，例如 <code>01</code>。此外，小时总是24小时制，因此 <code>00</code> 是 <code>12小时制</code> 时钟，12代表下午1点， <code>13</code>代表 <code>下午1点</code>， <code>23</code> 代表 <code>晚上11点</code>。</p>
<p>同样重要的需要注意， <code>displayFormat</code> 或 <code>pickerFormat</code> 都不能设置 datetime 值的输出，这是由组件 中 <code>ngModel</code>设置的值。格式仅用于将文本和选取器（picker）的界面显示的值，但 datetime 值始终作为有效的 ISO 8601 datetime 时间字符串而持续存在。</p>
<h2 id="min-and-max-datetimes">最小和最大 Datetimes</h2>
<p>日期在任何方向上都是无限的，因此对于用户的选择，至少应该有某种形式的限制可以选择的日期。默认情况下，最大日期是到当年年底，最小日期是从100年前的年份开始。</p>
<p>要定制最小和最大的 datetime 值，可以提供 <code>min</code> 和 <code>max</code> 输入属性，这可能对应用程序的用例来说更有意义，而不是用过去100年的默认值。按照上表中列出的相同 IS0 8601 格式，每个组件都可以限制用户可以选择哪些日期。以下是限制2016年初至2020年10月31日之间选择日期的示例：</p>
















<pre><code class="lang-html">&lt;ion-item&gt;
  &lt;ion-label&gt;Date&lt;/ion-label&gt;
  &lt;ion-datetime displayFormat=&quot;MMMM YYYY&quot; min=&quot;2016&quot; max=&quot;2020-10-31&quot; [(ngModel)]=&quot;myDate&quot;&gt;
  &lt;/ion-datetime&gt;
&lt;/ion-item&gt;
</code></pre>
<h2 id="month-names-and-day-of-the-week-names">月份名称和星期名称</h2>
<p>目前，没有一种通用的标准可以根据语言或地区自动选择月份名称或星期名称的正确语言/拼写。好消息是大多数浏览器都采用了 <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/DateTimeFormat">Intl.DateTimeFormat</a> 标准。但是，目前这个标准还没有被所有 <em>主流</em> 浏览器完全实现，所以 Ionic 不能使用它。 <em>此外 </em>， Angular 还提供国际化服务，但还处于沉重的发展中阶段，所以目前 Ionic 也不依赖它。</p>
<p>总而言之，如果应用程序需要使用默认英文版的月份和日期名称以外的名称，那么最简单的解决方案就是提供一组名称。月份名称和日期名称可以在应用级别配置，也可以在独立的 <code>ion-datetime</code> 级别配置。</p>
<h3><a class="anchor" name="app-config-level" href="#app-config-level">应用级别配置</a></h3>












<pre><code class="lang-ts">//app.module.ts
@NgModule({
...,
imports: [
  IonicModule.forRoot(MyApp, {
  monthNames: [&#39;janeiro&#39;, &#39;fevereiro&#39;, &#39;mar\u00e7o&#39;, ... ],
  monthShortNames: [&#39;jan&#39;, &#39;fev&#39;, &#39;mar&#39;, ... ],
  dayNames: [&#39;domingo&#39;, &#39;segunda-feira&#39;, &#39;ter\u00e7a-feira&#39;, ... ],
  dayShortNames: [&#39;dom&#39;, &#39;seg&#39;, &#39;ter&#39;, ... ],
})
],
...
})
</code></pre>
<h3><a class="anchor" name="component-input-level" href="#component-input-level">组件级别输入</a></h3>


<pre><code class="lang-html">&lt;ion-item&gt;
  &lt;ion-label&gt;Período&lt;/ion-label&gt;
  &lt;ion-datetime displayFormat=&quot;DDDD MMM D, YYYY&quot; [(ngModel)]=&quot;myDate&quot;
    monthNames=&quot;janeiro, fevereiro, mar\u00e7o, ...&quot;
    monthShortNames=&quot;jan, fev, mar, ...&quot;
    dayNames=&quot;domingo, segunda-feira, ter\u00e7a-feira, ...&quot;
    dayShortNames=&quot;dom, seg, ter, ...&quot;&gt;&lt;/ion-datetime&gt;
&lt;/ion-item&gt;
</code></pre>
<h3><a class="anchor" name="advanced-datetime-validation-and-manipulation" href="#advanced-datetime-validation-and-manipulation">进阶 Datetime 验证和操作</a></h3>


<p> datetime 选取器（picker）提供了选择确切格式的便利性，并使用标准化的 <a href="https://www.w3.org/TR/NOTE-datetime">ISO 8601 datetime 格式</a> 将日期时间值保留为字符串。但是，重要的是要注意在验证和操作 datetime 值时，<code>ion-datetime</code> 并不试图解决所有问题。如果 datetime 值需要从某种格式进行解析或操作（例如将日期添加5天，减去30分钟等），甚至将数据为特定的语言环境格式化，那么我们强烈建议使用 <a href="http://momentjs.com/">moment.js</a> “通过 JavaScript 解析，验证，操作和显示日期。”在处理 JavaScript 中的 datetimes 时， <a href="http://momentjs.com/">Moment.js</a> 很快就变成了我们的标准，但 Ionic 并未预先打包这种依赖，因为大多数应用程序都不需要它，它的语言环境配置应由最终开发人员决定。 </p>















<!-- @usage tag -->

<h2><a class="anchor" name="usage" href="#usage">用法</a></h2>

<pre><code class="lang-html">&lt;ion-item&gt;
  &lt;ion-label&gt;Date&lt;/ion-label&gt;
  &lt;ion-datetime displayFormat=&quot;MM/DD/YYYY&quot; [(ngModel)]=&quot;myDate&quot;&gt;
  &lt;/ion-datetime&gt;
&lt;/ion-item&gt;
</code></pre>




<!-- @property tags -->



<!-- instance methods on the class -->

<h2><a class="anchor" name="instance-members" href="#instance-members">实例成员</a></h2>

<div id="validate"></div>

<h3>
<a class="anchor" name="validate" href="#validate">
<code>validate()</code>


</a>
</h3>










<!-- input methods on the class -->
<h2><a class="anchor" name="input-properties" href="#input-properties">输入属性</a></h2>
<table class="table param-table" style="margin:0;">
  <thead>
    <tr>
      <th>属性</th>
      <th>类型</th>
      <th>详情</th>
    </tr>
  </thead>
  <tbody>

    <tr>
      <td>cancelText</td>
      <td><code>string</code></td>
      <td><p>要在选取器（picker）的取消按钮上显示的文本。默认： <code>Cancel</code>。 </p>
</td>
    </tr>

    <tr>
      <td>dayNames</td>
      <td><code>array</code></td>
      <td><p>一整个星期的名称。这可以用来提供特定语言环境（locale）中一周里每天的名称。默认为英文。</p>

</td>
    </tr>

    <tr>
      <td>dayShortNames</td>
      <td><code>array</code></td>
      <td><p>一整个星期的缩写名称。这可以用来提供特定语言环境（locale）中一周里每天的名称。默认为英文。</p>

</td>
    </tr>

    <tr>
      <td>dayValues</td>
      <td><code>array | string</code></td>
      <td><p>用于创建可选天数列表的值。默认情况下，每个月都会显示给定的月份。但是，要准确控制要显示的月份中的哪几天， <code>dayValues</code> 输入可以采用数字数组，也可以采用逗号分隔的数字字符串。注意，即使数组的天数对于选定的月份具有无效的数字（如2月份的 <code>31</code> ），它也不会正确显示对所选月份无效的日期。</p>





</td>
    </tr>

    <tr>
      <td>displayFormat</td>
      <td><code>string</code></td>
      <td><p>日期和时间在项目中显示的文本的显示格式。 当不使用 <code>pickerFormat</code> 输入时， <code>displayFormat</code> 用于显示带格式的文本，并确定日期时间选取器（picker）的列。有关更多信息，请参阅 <code>pickerFormat</code> 输入描述。默认为 <code>MMM D, YYYY</code>。</p>




</td>
    </tr>

    <tr>
      <td>doneText</td>
      <td><code>string</code></td>
      <td><p>显示在选取器（picker）的“完成”按钮上的文本。默认：完成。 The text to display on the picker&#39;s &quot;Done&quot; button. Default: <code>Done</code>.</p>
</td>
    </tr>

    <tr>
      <td>hourValues</td>
      <td><code>array | string</code></td>
      <td><p>用于创建可选小时列表的值。默认情况下，24小时的小时值范围为 <code>0</code> 到 <code>23</code>，或12小时为 <code>1</code> 到 <code>12</code> 。但是，要精确控制要显示的小时数， <code>hourValues</code> 输入可以采用数字数组或逗号分隔的数字串。</p>



</td>
    </tr>

    <tr>
      <td>max</td>
      <td><code>string</code></td>
      <td><p>允许的最大 datetime 。值必须遵循 <a href="https://www.w3.org/TR/NOTE-datetime">ISO 8601 datetime 时间格式标准</a>， <code>1996-12-19</code> 的日期字符串。格式不一定要针对确切的日期时间。例如，最大值可能只是一年，比如  <code>1994</code>。默认为今年年底。</p>





</td>
    </tr>

    <tr>
      <td>min</td>
      <td><code>string</code></td>
      <td><p>允许的最小 datetime 。值必须遵循 <a href="https://www.w3.org/TR/NOTE-datetime">ISO 8601 datetime 时间格式标准</a>， <code>1996-12-19</code> 的日期字符串。格式不一定要针对确切的日期时间。例如，最小值可能只是一年，比如  <code>1994</code>。默认为从今天开始的100年前的年初。</p>





</td>
    </tr>

    <tr>
      <td>minuteValues</td>
      <td><code>array | string</code></td>
      <td><p>用于创建可选分钟列表的值。默认情况下，分钟的范围是 <code>0</code> 到 <code>59</code>.但是，要准确控制显示哪些分钟， <code>minuteValues</code> 输入可以采用数字数组或逗号分隔数字字符串。例如，如果分钟选择应该每15分钟一次，那么该输入值将是 <code>minuteValues=&quot;0,15,30,45&quot;</code>。</p>




</td>
    </tr>

    <tr>
      <td>monthNames</td>
      <td><code>array</code></td>
      <td><p>每个月份的全称。用来提供本地语言环境（locale）月份名称。默认为英文。</p>

</td>
    </tr>

    <tr>
      <td>monthShortNames</td>
      <td><code>array</code></td>
      <td><p>每个月份名称的缩写名称。用来提供本地语言环境（locale）月份名称。默认为英文。</p>

</td>
    </tr>

    <tr>
      <td>monthValues</td>
      <td><code>array | string</code></td>
      <td><p>用于创建可选月份列表的值。默认情况下，月份值范围为 <code>1</code> 到 <code>12</code>.但是，要精确控制要显示的月份， <code>monthValues</code> 输入可以采用数字数组或逗号分隔的数字字符串。例如，如果只显示夏季月份，则此输入值为 <code>monthValues=&quot;6,7,8&quot;</code>。请注意，月份数字没有从零开始的索引，这意味着1月份的值为1，12月份的值为12。</p>





</td>
    </tr>

    <tr>
      <td>pickerFormat</td>
      <td><code>string</code></td>
      <td><p>用户选择的日期和时间选取器（picker）列的格式。 datetime 输入可以有一个或多个 datetime 部分，每个部分都有自己的列，允许单独选择该特定的 datetime 部分。例如，年份和月份列是两个可单独选择的列，可帮助从 datetime 选取器（picker）中选择确切的日期。每列都遵循字符串解析格式。默认使用 <code>displayFormat</code>。</p>





</td>
    </tr>

    <tr>
      <td>pickerOptions</td>
      <td><code>any</code></td>
      <td><p>选取器（picker）接口可以接受的其他任意选项。有关选取器选项，请参阅 <a href="../../picker/Picker">选取器 API 文档</a> 。</p>

</td>
    </tr>

    <tr>
      <td>placeholder</td>
      <td><code>string</code></td>
      <td><p>当没有选择日期时显示的文本。使用小写来匹配输入属性。</p>

</td>
    </tr>

    <tr>
      <td>yearValues</td>
      <td><code>array | string</code></td>
      <td><p>用于创建可选年份列表的值。默认情况下，年份值介于 <code>min</code> 和 <code>max</code> 日期时间输入之间。但是，要精确控制要显示哪些年份， <code>yearValues</code> 输入可以采用数字数组，也可以采用逗号分隔的数字字符串。例如，为了显示即将到来的和最近的闰年，则该输入的值将是 <code>yearValues=&quot;2024,2020,2016,2012,2008&quot;</code>。</p>




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
      <td>ionCancel</td>
      <td><p> datetime 选择被取消时触发。</p>
</td>
    </tr>

  </tbody>
</table>


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
        <td><code>$datetime-ios-padding-top</code></td>

          <td><code>$item-ios-padding-top</code></td>

        <td><p>Padding top of the DateTime component</p>
</td>
      </tr>

      <tr>
        <td><code>$datetime-ios-padding-end</code></td>

          <td><code>$datetime-ios-padding-right</code></td>

        <td><p>Padding end of the DateTime component</p>
</td>
      </tr>

      <tr>
        <td><code>$datetime-ios-padding-bottom</code></td>

          <td><code>$item-ios-padding-bottom</code></td>

        <td><p>Padding bottom of the DateTime component</p>
</td>
      </tr>

      <tr>
        <td><code>$datetime-ios-padding-start</code></td>

          <td><code>$datetime-ios-padding-left</code></td>

        <td><p>Padding start of the DateTime component</p>
</td>
      </tr>

      <tr>
        <td><code>$datetime-ios-placeholder-color</code></td>

          <td><code>#999</code></td>

        <td><p>Color of the DateTime placeholder</p>
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
        <td><code>$datetime-md-padding-top</code></td>

          <td><code>$item-md-padding-top</code></td>

        <td><p>Padding top of the DateTime component</p>
</td>
      </tr>

      <tr>
        <td><code>$datetime-md-padding-end</code></td>

          <td><code>$datetime-md-padding-right</code></td>

        <td><p>Padding end of the DateTime component</p>
</td>
      </tr>

      <tr>
        <td><code>$datetime-md-padding-bottom</code></td>

          <td><code>$item-md-padding-bottom</code></td>

        <td><p>Padding bottom of the DateTime component</p>
</td>
      </tr>

      <tr>
        <td><code>$datetime-md-padding-start</code></td>

          <td><code>$datetime-md-padding-left</code></td>

        <td><p>Padding start of the DateTime component</p>
</td>
      </tr>

      <tr>
        <td><code>$datetime-md-placeholder-color</code></td>

          <td><code>#999</code></td>

        <td><p>Color of the DateTime placeholder</p>
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
        <td><code>$datetime-wp-min-width</code></td>

          <td><code>45%</code></td>

        <td><p>Min width of the DateTime component</p>
</td>
      </tr>

      <tr>
        <td><code>$datetime-wp-padding-top</code></td>

          <td><code>$item-wp-padding-top</code></td>

        <td><p>Padding top of the DateTime component</p>
</td>
      </tr>

      <tr>
        <td><code>$datetime-wp-padding-end</code></td>

          <td><code>$datetime-wp-padding-right</code></td>

        <td><p>Padding end of the DateTime component</p>
</td>
      </tr>

      <tr>
        <td><code>$datetime-wp-padding-bottom</code></td>

          <td><code>$item-wp-padding-bottom</code></td>

        <td><p>Padding bottom of the DateTime component</p>
</td>
      </tr>

      <tr>
        <td><code>$datetime-wp-padding-start</code></td>

          <td><code>$datetime-wp-padding-left</code></td>

        <td><p>Padding start of the DateTime component</p>
</td>
      </tr>

      <tr>
        <td><code>$datetime-wp-border-width</code></td>

          <td><code>2px</code></td>

        <td><p>Border width of the DateTime component</p>
</td>
      </tr>

      <tr>
        <td><code>$datetime-wp-border-color</code></td>

          <td><code>$input-wp-border-color</code></td>

        <td><p>Border color of the DateTime component</p>
</td>
      </tr>

      <tr>
        <td><code>$datetime-wp-placeholder-color</code></td>

          <td><code>$input-wp-border-color</code></td>

        <td><p>Color of the DateTime placeholder</p>
</td>
      </tr>

    </tbody>
  </table>

</div>



<!-- related link --><!-- end content block -->


<!-- end body block -->

