---
layout: page
title: "Books"
date: 2011-09-19 09:38
comments: true
sharing: true
footer: true
currentasins: ["B000FBFN1U"]
techasins: ["1933988657", "059652983X"]
previousasins: ["0515144312", "0515143820", "0515143502", "0515143073", "0061827037", "B0046F0PC8", "0385344325", "0061977969", "0307913147", "1439156360", "0446561924","B005CDHZS0", "0553381695", "0553386794", "0312599447", "1934356840", "0596155409", "0399157263", "B001YT048E", "044656432X", "0307717097", "B001O9CES2", "0553593153", "0553807773"]
---
## Curently reading
<table>
{% tablerow casin in page.currentasins cols: 4 %}
  {{ casin | amazon_medium_image }}
{% endtablerow %}
</table>

## Current technology reads
<table>
{% tablerow tasin in page.techasins cols: 4 %}
  {{ tasin | amazon_medium_image }}
{% endtablerow %}
</table>

## Already read
<table>
{% tablerow pasin in page.previousasins cols: 8 %}
  {{ pasin | amazon_small_image }}
{% endtablerow %}
</table>
