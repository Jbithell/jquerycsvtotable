# jquerycsvtotable
Automatically exported from code.google.com/p/jquerycsvtotable
The jQuery CSV to Table plugin reads in comma separated values (CSV) or tab separated values (TSV) data and generates an HTML table. Common spreadsheet programs, such as Microsoft Excel, are capable of saving in both CSV and TSV format.

[<tt>[</tt>see it in action<tt>]</tt>](http://honestbleeps.com/csvtotable/demo.html)

By calling the CSVToTable() function on a DIV, and providing the path to a CSV or TSV file to download, the plugin loads in the data and creates an HTML table. For example, if a file called 'test.csv' contains the following data:

<pre class="prettyprint"><span class="pln">album</span><span class="pun">,</span><span class="pln">artist</span><span class="pun">,</span><span class="pln">price
</span><span class="str">"lateralus"</span><span class="pun">,</span><span class="str">"tool"</span><span class="pun">,</span><span class="lit">13.00</span><span class="pln">
</span><span class="str">"aenima"</span><span class="pun">,</span><span class="str">"tool"</span><span class="pun">,</span><span class="lit">12.00</span><span class="pln">
</span><span class="str">"10,000 days"</span><span class="pun">,</span><span class="str">"tool"</span><span class="pun">,</span><span class="lit">14.00</span><span class="pln">
</span><span class="str">"down in it"</span><span class="pun">,</span><span class="str">"nine inch nails"</span><span class="pun">,</span><span class="lit">3.00</span><span class="pln">
</span><span class="str">"broken"</span><span class="pun">,</span><span class="str">"nine inch nails"</span><span class="pun">,</span><span class="lit">6.00</span></pre>

A simple plugin call like:

<pre class="prettyprint"><span class="tag"><div</span> <span class="pln"></span> <span class="atn">id</span><span class="pun">=</span><span class="atv">"CSVTable"</span><span class="tag">></div></span><span class="pln">

</span><span class="tag"><script></span><span class="pln">
$</span><span class="pun">(</span><span class="kwd">function</span><span class="pun">()</span> <span class="pln"></span> <span class="pun">{</span><span class="pln">
  $</span><span class="pun">(</span><span class="str">'#CSVTable'</span><span class="pun">).</span><span class="typ">CSVToTable</span><span class="pun">(</span><span class="str">'test.csv'</span><span class="pun">);</span><span class="pln">
</span><span class="pun">});</span><span class="pln">
</span><span class="tag"></script></span></pre>

Would produce:

| album | artist | price |
| --- | --- | --- |
| lateralus | tool | 13.00 |
| aenima | tool | 12.00 |
| 10,000 days | tool | 14.00 |
| down in it | nine inch nails | 3.00 |
| broken | nine inch nails | 6.00 |

## <a name="Configurable_options:"></a>Configurable options:[](#Configurable_options:)

*   **separator** - separator to use when parsing CSV/TSV data

*   value will almost always be "," or "\t" (comma or tab)
*   if not specified, default value is ","

*   **headers** - an array of headers for the CSV data

*   if not specified, plugin assumes that the first line of the CSV file contains the header names.
*   Example: headers: ['Album Title', 'Artist Name', 'Price ($USD)']

*   **tableClass** - class name to apply to the <tt><table></tt> tag rendered by the plugin.
*   **theadClass** - class name to apply to the <tt><thead></tt> tag rendered by the plugin.
*   **thClass** - class name to apply to the <tt><th></tt> tag rendered by the plugin.
*   **tbodyClass** - class name to apply to the <tt><tbody></tt> tag rendered by the plugin.
*   **trClass** - class name to apply to the <tt><tr></tt> tag rendered by the plugin.
*   **tdClass** - class name to apply to the <tt><td></tt> tag rendered by the plugin.
*   **loadingImage** - path to an image to display while CSV/TSV data is loading
*   **loadingText** - text to display while CSV/TSV is loading

*   if not specified, default value is "Loading CSV data..."

The plugin will also trigger a "loadComplete" event upon successful render, so that you may use other jQuery plugins/code to modify the resulting table. One such example is the jQuery tablesorter plugin at [http://tablesorter.com/](http://tablesorter.com/)

The example below shows how to fire code after the loadComplete event is triggered:

<pre class="prettyprint"><span class="pln">$</span><span class="pun">(</span><span class="str">'#CSVTable'</span><span class="pun">).</span><span class="typ">CSVToTable</span><span class="pun">(</span><span class="str">'test.csv'</span><span class="pun">,</span> <span class="pln">   </span> <span class="pun">{</span> <span class="pln">       loadingImage</span><span class="pun">:</span> <span class="pln"></span> <span class="str">'images/loading.gif'</span><span class="pun">,</span> <span class="pln">       startLine</span><span class="pun">:</span> <span class="pln"></span> <span class="lit">1</span><span class="pun">,</span><span class="pln">
       headers</span><span class="pun">:</span> <span class="pln"></span> <span class="pun">[</span><span class="str">'Album Title'</span><span class="pun">,</span> <span class="pln"></span> <span class="str">'Artist Name'</span><span class="pun">,</span> <span class="pln"></span> <span class="str">'Price ($USD)'</span><span class="pun">]</span><span class="pln">   </span> <span class="pun">}</span><span class="pln">
</span><span class="pun">).</span><span class="pln">bind</span><span class="pun">(</span><span class="str">"loadComplete"</span><span class="pun">,</span><span class="kwd">function</span><span class="pun">()</span> <span class="pln"></span> <span class="pun">{</span> <span class="pln">    $</span><span class="pun">(</span><span class="str">'#CSVTable'</span><span class="pun">).</span><span class="pln">find</span><span class="pun">(</span><span class="str">'TABLE'</span><span class="pun">).</span><span class="pln">tablesorter</span><span class="pun">();</span><span class="pln">
</span><span class="pun">});;</span></pre>
