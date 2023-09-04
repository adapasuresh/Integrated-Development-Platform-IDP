# Inside Vs Outside

<u>Shift Left?</u> <br>

<table>
<tr><td>Provider</th><th>Runners</th><th>Workflow->Jobs->Tasks</th></tr>
<tr><td>ABC</td><td>Provision VM in ABC [ubuntu-latest]</td><td>Download source,patch,complie & bundle...</td></tr>
<tr><td>EFG</td><td>Provision VM in EFG [windows-latest]</td><td>Download pre-builds,complie & bundle...</td></tr>
<tr><td>LMN</td><td>Provision VM in LMN [macos-latest]</td><td>Download dmg,bundle...)</td></tr>
</table>

<u> Shift Left - Self-Hosted-Runners? </u>
<table>
<tr><td>Provider</th><th>Runners</th><th>Comments</th></tr>
<tr><td>ABC</td><td>SHR for Python 3.1 on ubuntu-latest]</td><td>Static and Dynamic binding taken care..SHIP.</td></tr>
<tr><td>ABC</td><td>SHR for Python 3.1 on windows-latest]</td><td>Static and Dynamic binding taken care..SHIP.</td></tr>
<tr><td>EFG</td><td>SHR for Python 3.5 on ubuntu-latest]</td><td>Static and Dynamic binding taken care..SHIP.</td></tr>
<tr><td>UNX</td><td>SHR for Python 3.7 on ubuntu-latest]</td><td>Static and Dynamic binding taken care..SHIP.</td></tr>
<tr><td>RHL</td><td>SHR for Qmail on RHEL-el3</td><td>uid=201,gid=502. Can run with other uid & gid..SHIP *.</td></tr>
<tr><td>SOL</td><td>SHR for Qmail on Solaris-10</td><td>.uid=1001,gid=5002 baked into package.Can't run with other uid & gid..SHIP **.</td></tr>
</table>

<b><u> Questions </u><b><br>
Is the 'VM in ABC' same where am running workloads in cloud-xyz ? <br>
'SHR' bit-size,arch-type,chip-sets supported by cloud-xyz at regions (place,time,situation)? <br>
Are the compliance/regulatory constraints same where am building vs where am running? <br>
Are Container runtime and layers same? <br>
Many more .....

<hr>
Work nside.

