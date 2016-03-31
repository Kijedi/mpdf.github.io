---
layout: page
title: TOC_Entry()
parent_title: mPDF functions
permalink: /reference/mpdf-functions/toc-entry.html
modification_time: 2015-08-05T12:01:13+00:00
---



<p>(mPDF &gt;= 1.0)</p>
<p>TOC_Entry – Insert an entry for the Table of Contents</p>
<h2>Description</h2>
<p class="manual_block">void <b>TOC_Entry</b> ( string <span class="parameter">$content</span> [, int <span class="parameter">$level</span> [, string <span class="parameter">$name</span> ]])</p>
<p>Insert an entry for the Table of Contents referencing the current writing position in the document.</p>
<p class="manual_block"><b>Note: </b>The position for the Table of Contents must be specified using <a href="{{ "/reference/mpdf-functions/tocpagebreak.html" | prepend: site.baseurl }}">TOCpagebreak()</a> or &lt;<a href="{{ "/reference/html-control-tags/tocpagebreak.html" | prepend: site.baseurl }}">tocpagebreak</a>&gt; at some point before <a href="{{ "/reference/mpdf-functions/output.html" | prepend: site.baseurl }}">Output()</a> is called.</p>

<div class="alert alert-info" role="alert"><strong>Note:</strong> From mPDF 2.3 you can use more than one <acronym title="Table of Contents">ToC</acronym> in the document using the parameter <span class="parameter">name</span>.</div>
<h2>Parameters</h2>
<p class="manual_param_dt"><span class="parameter">content</span></p>
<p class="manual_param_dd">This parameter sets the text as it will appear in the ToC entry. 

<span class="parameter">content</span> cannot contain any of the characters: &lt; &gt; &amp; ' <i>or</i> " and must use the appropriate HTML entities e.g. &lt;annotation content="This is &amp;lt; 40" /&gt;

It is recommended that you use htmlspecialchars('Content', ENT_QUOTES) for this.

<span class="smallblock">REQUIRED</span></p>
<p class="manual_param_dt"><span class="parameter">level</span></p>
<p class="manual_param_dd">Specify the level of this entry i.e. like heading1,2,3 

Starts at level 0

<span class="smallblock">DEFAULT</span>: 0</p>
<p class="manual_param_dt"><span class="parameter">name</span></p>
<p class="manual_param_dd">Specify which <acronym title="Table of Contents">ToC</acronym> to add this entry, if using more than one <acronym title="Table of Contents">ToC</acronym> in the document. <span class="parameter">name</span> can be any alphanumeric characters (except just "0") and is case-insensitive.

<span class="smallblock">BLANK</span>&nbsp;or omitted or 0 uses the default <acronym title="Table of Contents">ToC</acronym>.</p>
<p class="manual_param_dd"><b>Values</b> (case-insensitive)

"ALL" will add this entry to every ToC active in the document.</p>
<h2>Changelog</h2>
<table class="table"> <thead>
<tr> <th>Version</th><th>Description</th> </tr>
</thead> <tbody>
<tr>
<td>2.3</td>
<td><span class="parameter">name</span> attribute was added.</td>
</tr>
</tbody> </table>
<h2>Examples</h2>

{% highlight php %}
Example #1
{% endhighlight %}

{% highlight php %}
<?php

<?php

$mpdf=new mPDF();

$mpdf->WriteHTML('Introduction');

$mpdf->TOCpagebreak();

$mpdf->TOC_Entry("Chapter 1",0);

$mpdf->WriteHTML('Chapter 1 ...');

$mpdf=Output();

?>
{% endhighlight %}

<h2>Notes</h2>
<p class="manual_block"><b>Note</b>: Since mPDF 2.0 <b>insertTOC()</b> should <b>not</b> be called at the end of the document. <a href="{{ "/reference/codepages-glyphs/iso-8859-win-comparison-chart.html" | prepend: site.baseurl }}">Output()</a> will automatically generate the ToC if it has been defined with either or <a href="{{ "/reference/mpdf-functions/tocpagebreak.html" | prepend: site.baseurl }}">TOCpagebreak()</a> or&nbsp;&lt;<a href="{{ "/reference/html-control-tags/tocpagebreak.html" | prepend: site.baseurl }}">tocpagebreak</a>&gt;.</p>
<h2>See Also</h2>
<ul>
<li class="manual_boxlist"> <a href="{{ "/reference/mpdf-functions/tocpagebreak.html" | prepend: site.baseurl }}">TOCpagebreak()</a> - Insert a Table of Contents in the document </li>
<li class="manual_boxlist"> &lt;<a href="{{ "/reference/html-control-tags/tocpagebreak.html" | prepend: site.baseurl }}">tocpagebreak</a>&gt; - Insert a Table of Contents in the document </li>
<li class="manual_boxlist"> &lt;<a href="{{ "/reference/html-control-tags/tocentry.html" | prepend: site.baseurl }}">tocentry</a>&gt; - Mark a ToC entry in the document </li>
</ul>