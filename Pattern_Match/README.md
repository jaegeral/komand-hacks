# Some examples for Pattern Match:

## Timestamps

If you want to extract days for the following cases:

### 2017-11-24 08:09:01.228041+00:00

<pre>
 {{timestamp:/.*/}} 
</pre>

Take attention to the whitespace in front.

Will end up in:

<pre>
2017-11-24
</pre>

Corner case if you pass:
<pre>
foobar 2017-11-24 08:09:01.228041+00:00
</pre>

Will end in:
<pre>
foobar 2017-11-24
</pre>


### 2017-11-24T08:18:09.000Z

<pre>
{{timestamp:/.*/}}T
</pre>

Output: timestamp string:
<pre>
2017-11-24
</pre>

It will fail if you pass something like:

<pre>
foobar 2017-11-24T08:18:09.000Z
</pre>

Will end in:
timestamp:
<pre>foobar 2017-11-24</pre>
