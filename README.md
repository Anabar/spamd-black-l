# spamd-black-l
Actual black list for OpenBSD spamd.conf

You can use actual verison of this list from *http://spamd.vasily.me/anabarblack.gz*
File is renewing every 12 minutes.

<pre>
anabarblack:\
         :black:\
         :msg="SPAM. Your Address %A has sent spam within the last 36 hours. See http://spamd.vasily.me for details. Thou oughtn't to do it thrice":\
         :method=file:\
         :file=spamd.vasily.me/anabarblack.gz:
</pre>

