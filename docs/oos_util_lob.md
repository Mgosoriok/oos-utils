# OOS_UTIL_LOB



- [Constants](#constants)



- [CLOB2BLOB Function](#clob2blob)
- [BLOB2CLOB Function](#blob2clob)
- [GET_FILE_SIZE Function](#get_file_size)
- [GET_LOB_SIZE Function](#get_lob_size)
- [GET_LOB_SIZE-1 Function](#get_lob_size-1)
- [REPLACE_CLOB Function](#replace_clob)





## Constants<a name="constants"></a>

Name | Code | Description
--- | --- | ---
gc_unit_b | <pre>gc_unit_b constant varchar2(1) := 'B';</pre> | B
gc_unit_kb | <pre>gc_unit_kb constant varchar2(2) := 'KB';</pre> | KB
gc_unit_mb | <pre>gc_unit_mb constant varchar2(2) := 'MB';</pre> | MB
gc_unit_gb | <pre>gc_unit_gb constant varchar2(2) := 'GB';</pre> | GB
gc_unit_tb | <pre>gc_unit_tb constant varchar2(2) := 'TB';</pre> | TB
gc_unit_pb | <pre>gc_unit_pb constant varchar2(2) := 'PB';</pre> | PB
gc_unit_eb | <pre>gc_unit_eb constant varchar2(2) := 'EB';</pre> | EB
gc_unit_zb | <pre>gc_unit_zb constant varchar2(2) := 'ZB';</pre> | ZB
gc_unit_yb | <pre>gc_unit_yb constant varchar2(2) := 'YB';</pre> | YB
gc_size_b | <pre>gc_size_b constant number := 1024;</pre> | 
gc_size_kb | <pre>gc_size_kb constant number := power(1024, 2);</pre> | 
gc_size_mb | <pre>gc_size_mb constant number := power(1024, 3);</pre> | 
gc_size_gb | <pre>gc_size_gb constant number := power(1024, 4);</pre> | 
gc_size_tb | <pre>gc_size_tb constant number := power(1024, 5);</pre> | 
gc_size_pb | <pre>gc_size_pb constant number := power(1024, 6);</pre> | 
gc_size_eb | <pre>gc_size_eb constant number := power(1024, 7);</pre> | 
gc_size_zb | <pre>gc_size_zb constant number := power(1024, 8);</pre> | 
gc_size_yb | <pre>gc_size_yb constant number := power(1024, 9);</pre> | 






 
## CLOB2BLOB Function<a name="clob2blob"></a>


<p>
<p>Convers clob to blob</p>
</p>

### Syntax
```plsql
function clob2blob(
  p_clob in clob)
  return blob
```

### Parameters
Name | Description
--- | ---
`p_clob` | Clob to conver to blob
*return* | blob
 
 





 
## BLOB2CLOB Function<a name="blob2clob"></a>


<p>
<p>Converts blob to clob</p><p>Notes:</p><ul>
<li>Copied from <a href="http://stackoverflow.com/questions/12849025/convert-blob-to-clob">http://stackoverflow.com/questions/12849025/convert-blob-to-clob</a></li>
</ul>

</p>

### Syntax
```plsql
function blob2clob(
  p_blob in blob,
  p_blob_csid in integer default dbms_lob.default_csid)
  return clob
```

### Parameters
Name | Description
--- | ---
`p_blob` | blob to be converted to clob
`p_blob_csid` | Encoding to use. See <a href="https://docs.oracle.com/database/121/NLSPG/ch2charset.htm#NLSPG169">https://docs.oracle.com/database/121/NLSPG/ch2charset.htm#NLSPG169</a> (table 2-4) for different charsets. Can use <code>nls_charset_id(&lt;charset&gt;)</code> to get the clob_csid
*return* | clob
 
 





 
## GET_FILE_SIZE Function<a name="get_file_size"></a>


<p>
<p>Returns human readable file size</p>
</p>

### Syntax
```plsql
function get_file_size(
  p_file_size in number,
  p_units in varchar2 default null)
  return varchar2
```

### Parameters
Name | Description
--- | ---
`p_file_size` | size of file in bytes
`p_units` | See <code>gc_size_...</code> consants for options. If not provided, most significant one automatically chosen.
*return* | Human readable file size
 
 





 
## GET_LOB_SIZE Function<a name="get_lob_size"></a>


<p>
<p>See get_file_size</p>
</p>

### Syntax
```plsql
function get_lob_size(
  p_lob in clob,
  p_units in varchar2 default null)
  return varchar2
```

### Parameters
Name | Description
--- | ---
`p_lob` | 
`p_units` | 
 
 





 
## GET_LOB_SIZE-1 Function<a name="get_lob_size-1"></a>


<p>
<p>See get_file_size</p>
</p>

### Syntax
```plsql
function get_lob_size(
  p_lob in blob,
  p_units in varchar2 default null)
  return varchar2
```

### Parameters
Name | Description
--- | ---
`p_lob` | 
`p_units` | 
 
 





 
## REPLACE_CLOB Function<a name="replace_clob"></a>


<p>
<p>Replaces p_search with p_replace</p><p>Oracle&#39;s replace function handles clobs but runs into 32k issues</p><p>Notes:</p><ul>
<li>Source: <a href="http://dbaora.com/ora-22828-input-pattern-or-replacement-parameters-exceed-32k-size-limit/">http://dbaora.com/ora-22828-input-pattern-or-replacement-parameters-exceed-32k-size-limit/</a></li>
</ul>

</p>

### Syntax
```plsql
function replace_clob(
  p_str in clob,
  p_search in varchar2,
  p_replace in clob)
  return clob
```

### Parameters
Name | Description
--- | ---
`p_str` | 
`p_search` | 
`p_replace` | 
*return* | Replaced string
 
 





 
