# spamd-black-l
Actual blacklist for OpenBSD spamd.conf

You can use actual version of this list from *http://spamd.vasily.me/anabarblack.gz*
<br>File is renewing every 12 minutes.


## file struture
<pre>
# anabar black list for using into spamd.conf (OpenBSD spamd)
#
# Date: Tue, 25 Apr 2017 11:00:11 +0000
Fields: 
  a. IP
  b. count of attemts from IP into period (36h)
  c. amount of blacklist, where IP was detected
    if empty (implied 1): IP was detected only in anabar's BL
    if >=2: IP was detected in other BL (nixspam, bsdly, etc.) 
  d. DNS name or '---'


**a**                     **b**    **c**  **d**
  178.159.42.225   #  210     ntcsn.ru
  178.159.42.226   #  160     zaoumk.ru
   62.75.236.204   #   72     mail.hebraica.eu
   62.75.236.205   #   72     mail.intermagic.eu
   62.75.236.206   #   68  2  mail.whilsacom.eu
   66.23.212.128   #   11     ---
   66.23.212.130   #   23     wrong.jehoriz.us
   66.23.212.131   #   14     elbow.spienko.us
   66.23.212.132   #   56     stain.shaerdi.us
  194.67.222.171   #   20     ih499026.dedic.myihor.ru
  194.67.222.182   #   30     ih499026.dedic.myihor.ru
   85.25.226.216   #   75  2  mail.minderse.eu
   85.25.243.123   #   66  2  mail.hooperise.eu
    85.25.243.92   #   50     mail.filamest.eu
    85.25.243.93   #   77     mail.golemint.eu
</pre>



To use this blacklist just add below strings into your `spamd.conf` (usually `/etc/mail/spamd.conf`) and restart spamd (`rcctl restart spamd`)
<pre>
anabarblack:\
         :black:\
         :msg="SPAM. Your Address %A has sent spam within the last 36 hours. See http://spamd.vasily.me for details. Thou oughtn't to do it thrice":\
         :method=file:\
         :file=spamd.vasily.me/anabarblack.gz:
</pre>

The file `anabarblack.list` in repository is only example and is not renewing regular.


