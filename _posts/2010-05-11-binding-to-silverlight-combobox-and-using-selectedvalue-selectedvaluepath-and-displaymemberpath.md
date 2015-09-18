---
layout: post
title: Binding to Silverlight ComboBox and Using SelectedValue, SelectedValuePath and DisplayMemberPath
date: 2010-05-11 03:36
author: John
comments: true
categories: [Silverlight]
---
<p>“How do you bind a ComboBox to a collection of objects, and then bind a property from the selected object’s to some other scalar property?” I received this question today from a friend of mine (a variation of this question). I decided to walk through the scenario here in case anyone else runs into it. This is one of those things that can be confusing … it is simple, but it is is much easier shown the explained. This post lays out the scenario using some new features to Silverlight 4 and you can download the sample code at the end.</p>  <p>When we first load the page and open the ComboBox it should look like this, with each state’s full name (State.Name) being displayed in the ComboBox items.</p>  <p><a href="/wp-content/uploads/files/media/image/WindowsLiveWriter/SelectedValueSelectedValuePathandDisplay_150DE/image_2.png"><img style="border-right-width: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px" title="image" border="0" alt="image" src="/wp-content/uploads/files/media/image/WindowsLiveWriter/SelectedValueSelectedValuePathandDisplay_150DE/image_thumb.png" width="260" height="174" /></a> </p>  <p>And when we select a state it’s state code (State.Code) is bound to the TextBlock. In the screen capture below you can see the state of Washington is selected and its state code of WA is bound to the TextBlock above the ComboBox.</p>  <p><a href="/wp-content/uploads/files/media/image/WindowsLiveWriter/SelectedValueSelectedValuePathandDisplay_150DE/image_4.png"><img style="border-right-width: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px" title="image" border="0" alt="image" src="/wp-content/uploads/files/media/image/WindowsLiveWriter/SelectedValueSelectedValuePathandDisplay_150DE/image_thumb_1.png" width="260" height="95" /></a> </p>  <p>This quick demo shows the behavior we want to achieve. Let’s assume we have an object (we’ll assume it is a ViewModel) bound to the Silverlight View (the View being the UserControl). </p>  <blockquote>   <p>NOTE: You’ll notice I am using View and ViewModel here and you’ll probably conclude I am using MVVM … and you would be correct. However keep in mind that MVVM is not needed, I just decided to use it to make the example clearer using separation with classes. We could have called them whatever we wanted.</p> </blockquote>  <p>This ViewModel has a property called States which is a ObservableCollection&lt;State&gt;. The State object the properties:</p>  <ul>   <li>string Code (ex: WA) </li>    <li>string Name (ex: Washington) </li> </ul>  <p>The ViewModel is bound to the View, as its DataContext. A ComboBox in the View is bound to the list of states in the ViewModel’s States property. When the project loads, we expect the list of states to be displayed in the ComboBox.Each state’s full name should appear (from the State.Name property). When a state is selected in the ComboBox, the State.Code property should be grabbed and set to the ViewModel’s SelectedStateCode property. The trick to doing this is to set your XAML for your ComboBox like this:</p>  <div style="border-bottom: silver 1px solid; text-align: left; border-left: silver 1px solid; padding-bottom: 4px; line-height: 12pt; background-color: #f4f4f4; margin: 20px 0px 10px; padding-left: 4px; width: 97.5%; padding-right: 4px; font-family: &#39;Courier New&#39;, courier, monospace; direction: ltr; max-height: 200px; font-size: 8pt; overflow: auto; border-top: silver 1px solid; cursor: text; border-right: silver 1px solid; padding-top: 4px" id="codeSnippetWrapper">   <div style="border-bottom-style: none; text-align: left; padding-bottom: 0px; line-height: 12pt; border-right-style: none; background-color: #f4f4f4; padding-left: 0px; width: 100%; padding-right: 0px; font-family: &#39;Courier New&#39;, courier, monospace; direction: ltr; border-top-style: none; color: black; font-size: 8pt; border-left-style: none; overflow: visible; padding-top: 0px" id="codeSnippet">     <pre style="border-bottom-style: none; text-align: left; padding-bottom: 0px; line-height: 12pt; border-right-style: none; background-color: white; margin: 0em; padding-left: 0px; width: 100%; padding-right: 0px; font-family: &#39;Courier New&#39;, courier, monospace; direction: ltr; border-top-style: none; color: black; font-size: 8pt; border-left-style: none; overflow: visible; padding-top: 0px"><span style="color: #606060" id="lnum1">   1:</span> <span style="color: #0000ff">&lt;</span><span style="color: #800000">ComboBox</span> <span style="color: #ff0000">Height</span><span style="color: #0000ff">=&quot;23&quot;</span> <span style="color: #ff0000">HorizontalAlignment</span><span style="color: #0000ff">=&quot;Left&quot;</span> <span style="color: #ff0000">Margin</span><span style="color: #0000ff">=&quot;12,50,0,0&quot;</span> </pre>
<!--CRLF-->
<pre style="border-bottom-style: none; text-align: left; padding-bottom: 0px; line-height: 12pt; border-right-style: none; background-color: #f4f4f4; margin: 0em; padding-left: 0px; width: 100%; padding-right: 0px; font-family: &#39;Courier New&#39;, courier, monospace; direction: ltr; border-top-style: none; color: black; font-size: 8pt; border-left-style: none; overflow: visible; padding-top: 0px"><span style="color: #606060" id="lnum2">   2:</span>           <span style="color: #ff0000">Name</span><span style="color: #0000ff">=&quot;comboBox1&quot;</span> <span style="color: #ff0000">VerticalAlignment</span><span style="color: #0000ff">=&quot;Top&quot;</span> <span style="color: #ff0000">Width</span><span style="color: #0000ff">=&quot;252&quot;</span> </pre>
<!--CRLF-->
<pre style="border-bottom-style: none; text-align: left; padding-bottom: 0px; line-height: 12pt; border-right-style: none; background-color: white; margin: 0em; padding-left: 0px; width: 100%; padding-right: 0px; font-family: &#39;Courier New&#39;, courier, monospace; direction: ltr; border-top-style: none; color: black; font-size: 8pt; border-left-style: none; overflow: visible; padding-top: 0px"><span style="color: #606060" id="lnum3">   3:</span>           <span style="color: #ff0000">ItemsSource</span><span style="color: #0000ff">=&quot;{Binding Path=States, Mode=OneWay}&quot;</span> </pre>
<!--CRLF-->
<pre style="border-bottom-style: none; text-align: left; padding-bottom: 0px; line-height: 12pt; border-right-style: none; background-color: #f4f4f4; margin: 0em; padding-left: 0px; width: 100%; padding-right: 0px; font-family: &#39;Courier New&#39;, courier, monospace; direction: ltr; border-top-style: none; color: black; font-size: 8pt; border-left-style: none; overflow: visible; padding-top: 0px"><span style="color: #606060" id="lnum4">   4:</span>           <span style="color: #ff0000">SelectedValue</span><span style="color: #0000ff">=&quot;{Binding Path=SelectedStateCode, Mode=TwoWay}&quot;</span> </pre>
<!--CRLF-->
<pre style="border-bottom-style: none; text-align: left; padding-bottom: 0px; line-height: 12pt; border-right-style: none; background-color: white; margin: 0em; padding-left: 0px; width: 100%; padding-right: 0px; font-family: &#39;Courier New&#39;, courier, monospace; direction: ltr; border-top-style: none; color: black; font-size: 8pt; border-left-style: none; overflow: visible; padding-top: 0px"><span style="color: #606060" id="lnum5">   5:</span>           <span style="color: #ff0000">DisplayMemberPath</span><span style="color: #0000ff">=&quot;Name&quot;</span> </pre>
<!--CRLF-->
<pre style="border-bottom-style: none; text-align: left; padding-bottom: 0px; line-height: 12pt; border-right-style: none; background-color: #f4f4f4; margin: 0em; padding-left: 0px; width: 100%; padding-right: 0px; font-family: &#39;Courier New&#39;, courier, monospace; direction: ltr; border-top-style: none; color: black; font-size: 8pt; border-left-style: none; overflow: visible; padding-top: 0px"><span style="color: #606060" id="lnum6">   6:</span>           <span style="color: #ff0000">SelectedValuePath</span><span style="color: #0000ff">=&quot;Code&quot;</span>  <span style="color: #0000ff">/&gt;</span></pre>
<!--CRLF-->
<pre style="border-bottom-style: none; text-align: left; padding-bottom: 0px; line-height: 12pt; border-right-style: none; background-color: white; margin: 0em; padding-left: 0px; width: 100%; padding-right: 0px; font-family: &#39;Courier New&#39;, courier, monospace; direction: ltr; border-top-style: none; color: black; font-size: 8pt; border-left-style: none; overflow: visible; padding-top: 0px"><span style="color: #606060" id="lnum7">   7:</span> <span style="color: #0000ff">&lt;</span><span style="color: #800000">TextBlock</span> <span style="color: #ff0000">Height</span><span style="color: #0000ff">=&quot;23&quot;</span> <span style="color: #ff0000">HorizontalAlignment</span><span style="color: #0000ff">=&quot;Left&quot;</span> </pre>
<!--CRLF-->
<pre style="border-bottom-style: none; text-align: left; padding-bottom: 0px; line-height: 12pt; border-right-style: none; background-color: #f4f4f4; margin: 0em; padding-left: 0px; width: 100%; padding-right: 0px; font-family: &#39;Courier New&#39;, courier, monospace; direction: ltr; border-top-style: none; color: black; font-size: 8pt; border-left-style: none; overflow: visible; padding-top: 0px"><span style="color: #606060" id="lnum8">   8:</span>            <span style="color: #ff0000">Margin</span><span style="color: #0000ff">=&quot;187,16,0,0&quot;</span> <span style="color: #ff0000">Name</span><span style="color: #0000ff">=&quot;textBlock1&quot;</span> </pre>
<!--CRLF-->
<pre style="border-bottom-style: none; text-align: left; padding-bottom: 0px; line-height: 12pt; border-right-style: none; background-color: white; margin: 0em; padding-left: 0px; width: 100%; padding-right: 0px; font-family: &#39;Courier New&#39;, courier, monospace; direction: ltr; border-top-style: none; color: black; font-size: 8pt; border-left-style: none; overflow: visible; padding-top: 0px"><span style="color: #606060" id="lnum9">   9:</span>            <span style="color: #ff0000">Text</span><span style="color: #0000ff">=&quot;{Binding Path=SelectedStateCode}&quot;</span> </pre>
<!--CRLF-->
<pre style="border-bottom-style: none; text-align: left; padding-bottom: 0px; line-height: 12pt; border-right-style: none; background-color: #f4f4f4; margin: 0em; padding-left: 0px; width: 100%; padding-right: 0px; font-family: &#39;Courier New&#39;, courier, monospace; direction: ltr; border-top-style: none; color: black; font-size: 8pt; border-left-style: none; overflow: visible; padding-top: 0px"><span style="color: #606060" id="lnum10">  10:</span>            <span style="color: #ff0000">VerticalAlignment</span><span style="color: #0000ff">=&quot;Top&quot;</span> <span style="color: #ff0000">Width</span><span style="color: #0000ff">=&quot;65&quot;</span> <span style="color: #0000ff">/&gt;</span></pre>
<!--CRLF--></div>
</div>
<p>Notice the following 4 properties are set as follows:</p>
<ul>
<li>ItemsSource is bound to the ViewModel’s States property (a collection of State objects) </li>
<li>DisplayMemberPath is set to “Name” (This is the State.Name property) </li>
<li>SelectedValuePath is set to “Code” (This is the State.Code property) </li>
<li>SelectedValue is bound to the ViewModel’s SelectedStateCode property </li>
</ul>
<p>The key here are the DisplayMemberPath and SelectedValuePath properties. These apply to the object that each item in the ComboBox is bound to. In other words, these properties are set to the State, not the ObservableCollection&lt;State&gt;. Also, notice these properties are not data bound, they are instead set to the name of the properties respectively. We do not want the values of the properties here, we want the actual name of the properties (which is why it is called DisplayMember<strong>Path</strong> and SelectedValue<strong>Path</strong>).</p>
<p><a href="/wp-content/uploads/files/downloads/ComboTest.zip"><img style="border-right-width: 0px; margin: 0px 5px 0px 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px" title="image" border="0" alt="image" align="left" src="/wp-content/uploads/files/media/image/WindowsLiveWriter/SelectedValueSelectedValuePathandDisplay_150DE/image_7.png" width="148" height="119" /></a> </p>
<p>&#160;</p>
<p>&#160;</p>
<p>Download the source code for this <a href="/wp-content/uploads/files/downloads/ComboTest.zip">sample ComboBox project here</a>.</p>
<p>&#160;</p>
<p></p>
<p><a href="http://channel9.msdn.com/learn/courses/Silverlight4/Overview/Overview/"><img style="border-right-width: 0px; margin: 5px 5px 0px 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px" title="WhitePaper2" border="0" alt="WhitePaper2" align="left" src="/wp-content/uploads/files/media/image/WindowsLiveWriter/SelectedValueSelectedValuePathandDisplay_150DE/WhitePaper2_3.png" width="114" height="130" /></a></p>
<p>&#160;</p>
<p>SelectedValue and SelectedValuePath are new to Silverlight 4. You can find more information on this new feature to Silverlight 4 and many more in the <a href="http://channel9.msdn.com/learn/courses/Silverlight4/Overview/Overview/">Silverlight 4 whitepaper found here</a>. </p>
<p>&#160;</p>
<p>&#160;</p>
<p> I hope this helps!</p>
<p></p>
<p><font color="#ff0000">UPDATE: I added the XAML for the TextBlock above too. The compelte code can be downloaded from the link above.</font></p>
