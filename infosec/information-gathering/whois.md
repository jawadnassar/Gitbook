---
coverY: 0
layout:
  cover:
    visible: true
    size: full
  title:
    visible: true
  description:
    visible: false
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
---

# Whois

* **Definition:** WHOIS reveals domain/IP details crucial for penetration testing and app security.
* **Purpose:** Uncover ownership and contact data, aiding in security assessments.
* **Info Included:** Registrant's details, registration info, and domain server data.
* **Accessibility:** Public WHOIS databases and registrar tools assist in data gathering.
* **Uses:** Resolving ownership disputes, addressing legal concerns, and checking domain availability for secure app development.
* **Privacy:** Domain privacy services obscure personal info, impacting security assessments.
* **Legal Requirements:** ICANN mandates accurate WHOIS info for robust security practices.
* **Changes:** Evolving policies balance transparency with security, impacting penetration testing strategies.



Running a WHOIS query for `jawad.ca` shows that personal information is redacted for privacy reasons. However, it can also reveal my nameservers, thereby exposing the hosting provider and/or domain name registrar.

```shell-session
kali@kali:~$ whois jawad.ca                                                                   
Domain Name: jawad.ca
Registry Domain ID: 24832869-CIRA
Registrar WHOIS Server: whois.ca.fury.ca
Registrar URL: https://www.namecheap.com/
Updated Date: 2023-02-17T17:19:56Z
Creation Date: 2015-12-01T21:18:44Z
Registry Expiry Date: 2032-12-01T21:18:44Z
Registrar: Go Get Canada Domain Registrar Ltd.
Registrar IANA ID: not applicable
Registrar Abuse Contact Email: abuse@namecheap.com
Registrar Abuse Contact Phone: +1.6613102107
Domain Status: clientTransferProhibited https://icann.org/epp#clientTransferProhibited
Registry Registrant ID: REDACTED FOR PRIVACY
Registrant Name: REDACTED FOR PRIVACY
Registrant Organization: REDACTED FOR PRIVACY
Registrant Street: REDACTED FOR PRIVACY
Registrant City: REDACTED FOR PRIVACY
Registrant State/Province: REDACTED FOR PRIVACY
Registrant Postal Code: REDACTED FOR PRIVACY
Registrant Country: REDACTED FOR PRIVACY
Registrant Phone: REDACTED FOR PRIVACY
Registrant Phone Ext: REDACTED FOR PRIVACY
Registrant Fax: REDACTED FOR PRIVACY
Registrant Fax Ext: REDACTED FOR PRIVACY
Registrant Email: Please ask the Registrar of Record identified in this output for information on how to contact the Registrant, Admin, or Other contacts of the queried domain name
Registry Admin ID: REDACTED FOR PRIVACY
Admin Name: REDACTED FOR PRIVACY
Admin Organization: REDACTED FOR PRIVACY
Admin Street: REDACTED FOR PRIVACY
Admin City: REDACTED FOR PRIVACY
Admin State/Province: REDACTED FOR PRIVACY
Admin Postal Code: REDACTED FOR PRIVACY
Admin Country: REDACTED FOR PRIVACY
Admin Phone: REDACTED FOR PRIVACY
Admin Phone Ext: REDACTED FOR PRIVACY
Admin Fax: REDACTED FOR PRIVACY
Admin Fax Ext: REDACTED FOR PRIVACY
Admin Email: Please ask the Registrar of Record identified in this output for information on how to contact the Registrant, Admin, or Other contacts of the queried domain name
Registry Tech ID: REDACTED FOR PRIVACY
Tech Name: REDACTED FOR PRIVACY
Tech Organization: REDACTED FOR PRIVACY
Tech Street: REDACTED FOR PRIVACY
Tech City: REDACTED FOR PRIVACY
Tech State/Province: REDACTED FOR PRIVACY
Tech Postal Code: REDACTED FOR PRIVACY
Tech Country: REDACTED FOR PRIVACY
Tech Phone: REDACTED FOR PRIVACY
Tech Phone Ext: REDACTED FOR PRIVACY
Tech Fax: REDACTED FOR PRIVACY
Tech Fax Ext: REDACTED FOR PRIVACY
Tech Email: Please ask the Registrar of Record identified in this output for information on how to contact the Registrant, Admin, or Other contacts of the queried domain name
Registry Billing ID: REDACTED FOR PRIVACY
Billing Name: REDACTED FOR PRIVACY
Billing Organization: REDACTED FOR PRIVACY
Billing Street: REDACTED FOR PRIVACY
Billing City: REDACTED FOR PRIVACY
Billing State/Province: REDACTED FOR PRIVACY
Billing Postal Code: REDACTED FOR PRIVACY
Billing Country: REDACTED FOR PRIVACY
Billing Phone: REDACTED FOR PRIVACY
Billing Phone Ext: REDACTED FOR PRIVACY
Billing Fax: REDACTED FOR PRIVACY
Billing Fax Ext: REDACTED FOR PRIVACY
Billing Email: Please ask the Registrar of Record identified in this output for information on how to contact the Registrant, Admin, or Other contacts of the queried domain name
Name Server: dns1.registrar-servers.com
Name Server: dns2.registrar-servers.com
DNSSEC: unsigned
URL of the ICANN Whois Inaccuracy Complaint Form: https://www.icann.org/wicf/
>>> Last update of WHOIS database: 2023-12-18T20:17:10Z <<<

For more information on Whois status codes, please visit https://icann.org/epp

%
% Use of CIRA's WHOIS service is governed by the Terms of Use in its Legal
% Notice, available at http://www.cira.ca/legal-notice/?lang=en
%
% (c) 2023 Canadian Internet Registration Authority, (http://www.cira.ca/)

```



If you follow the breadcrumbs, you'll notice that `registrar-servers.com` is associated with Namecheap Hosting. Therefore, this is an indicator that my domain is hosted on `namecheap.com`.

```shell-session
kali@kali:~$ whois registrar-servers.com
   Domain Name: REGISTRAR-SERVERS.COM
   Registry Domain ID: 1326800137_DOMAIN_COM-VRSN
   Registrar WHOIS Server: whois.namecheap.com
   Registrar URL: http://www.namecheap.com
   Updated Date: 2023-10-09T07:19:35Z
   Creation Date: 2007-11-08T15:04:30Z
   Registry Expiry Date: 2024-11-08T15:04:30Z
   Registrar: NameCheap, Inc.
   Registrar IANA ID: 1068
   Registrar Abuse Contact Email: abuse@namecheap.com
   Registrar Abuse Contact Phone: +1.6613102107
   Domain Status: clientTransferProhibited https://icann.org/epp#clientTransferProhibited
   Domain Status: serverDeleteProhibited https://icann.org/epp#serverDeleteProhibited
   Domain Status: serverTransferProhibited https://icann.org/epp#serverTransferProhibited
   Domain Status: serverUpdateProhibited https://icann.org/epp#serverUpdateProhibited
   Name Server: EDNS1.REGISTRAR-SERVERS.COM
   Name Server: EDNS2.REGISTRAR-SERVERS.COM
   Name Server: EDNS4.ULTRADNS.COM
   Name Server: EDNS4.ULTRADNS.NET
   Name Server: EDNS4.ULTRADNS.ORG
   DNSSEC: unsigned
   URL of the ICANN Whois Inaccuracy Complaint Form: https://www.icann.org/wicf/
>>> Last update of whois database: 2023-12-18T20:21:45Z <<<

For more information on Whois status codes, please visit https://icann.org/epp

NOTICE: The expiration date displayed in this record is the date the
registrar's sponsorship of the domain name registration in the registry is
currently set to expire. This date does not necessarily reflect the expiration
date of the domain name registrant's agreement with the sponsoring
registrar.  Users may consult the sponsoring registrar's Whois database to
view the registrar's reported date of expiration for this registration.

TERMS OF USE: You are not authorized to access or query our Whois
database through the use of electronic processes that are high-volume and
automated except as reasonably necessary to register domain names or
modify existing registrations; the Data in VeriSign Global Registry
Services' ("VeriSign") Whois database is provided by VeriSign for
information purposes only, and to assist persons in obtaining information
about or related to a domain name registration record. VeriSign does not
guarantee its accuracy. By submitting a Whois query, you agree to abide
by the following terms of use: You agree that you may use this Data only
for lawful purposes and that under no circumstances will you use this Data
to: (1) allow, enable, or otherwise support the transmission of mass
unsolicited, commercial advertising or solicitations via e-mail, telephone,
or facsimile; or (2) enable high volume, automated, electronic processes
that apply to VeriSign (or its computer systems). The compilation,
repackaging, dissemination or other use of this Data is expressly
prohibited without the prior written consent of VeriSign. You agree not to
use electronic processes that are automated and high-volume to access or
query the Whois database except as reasonably necessary to register
domain names or modify existing registrations. VeriSign reserves the right
to restrict your access to the Whois database in its sole discretion to ensure
operational stability.  VeriSign may restrict or terminate your access to the
Whois database for failure to abide by these terms of use. VeriSign
reserves the right to modify these terms at any time.

The Registry database contains ONLY .COM, .NET, .EDU domains and
Registrars.
Domain name: registrar-servers.com
Registry Domain ID: 1326800137_DOMAIN_COM-VRSN
Registrar WHOIS Server: whois.namecheap.com
Registrar URL: http://www.namecheap.com
Updated Date: 2023-10-09T07:19:35.50Z
Creation Date: 2007-11-08T15:04:30.00Z
Registrar Registration Expiration Date: 2024-11-08T15:04:30.00Z
Registrar: NAMECHEAP INC
Registrar IANA ID: 1068
Registrar Abuse Contact Email: abuse@namecheap.com
Registrar Abuse Contact Phone: +1.9854014545
Reseller: NAMECHEAP INC
Domain Status: clientTransferProhibited https://icann.org/epp#clientTransferProhibited
Domain Status: serverDeleteProhibited https://icann.org/epp#serverDeleteProhibited
Domain Status: serverTransferProhibited https://icann.org/epp#serverTransferProhibited
Domain Status: serverUpdateProhibited https://icann.org/epp#serverUpdateProhibited
Registry Registrant ID: 
Registrant Name: Redacted for Privacy
Registrant Organization: Privacy service provided by Withheld for Privacy ehf
Registrant Street: Kalkofnsvegur 2 
Registrant City: Reykjavik
Registrant State/Province: Capital Region
Registrant Postal Code: 101
Registrant Country: IS
Registrant Phone: +354.4212434
Registrant Phone Ext: 
Registrant Fax: 
Registrant Fax Ext: 
Registrant Email: 6eadd514503047339410d1e131d27118.protect@withheldforprivacy.com
Registry Admin ID: 
Admin Name: Redacted for Privacy
Admin Organization: Privacy service provided by Withheld for Privacy ehf
Admin Street: Kalkofnsvegur 2 
Admin City: Reykjavik
Admin State/Province: Capital Region
Admin Postal Code: 101
Admin Country: IS
Admin Phone: +354.4212434
Admin Phone Ext: 
Admin Fax: 
Admin Fax Ext: 
Admin Email: 6eadd514503047339410d1e131d27118.protect@withheldforprivacy.com
Registry Tech ID: 
Tech Name: Redacted for Privacy
Tech Organization: Privacy service provided by Withheld for Privacy ehf
Tech Street: Kalkofnsvegur 2 
Tech City: Reykjavik
Tech State/Province: Capital Region
Tech Postal Code: 101
Tech Country: IS
Tech Phone: +354.4212434
Tech Phone Ext: 
Tech Fax: 
Tech Fax Ext: 
Tech Email: 6eadd514503047339410d1e131d27118.protect@withheldforprivacy.com
Name Server: edns4.ultradns.net
Name Server: edns4.ultradns.com
Name Server: edns4.ultradns.org
Name Server: edns1.registrar-servers.com
Name Server: edns2.registrar-servers.com
DNSSEC: unsigned
URL of the ICANN WHOIS Data Problem Reporting System: http://wdprs.internic.net/
>>> Last update of WHOIS database: 2023-12-18T18:17:53.60Z <<<
For more information on Whois status codes, please visit https://icann.org/epp

```



You shouldn't stop here, using tools like [https://mxtoolbox.com/](https://mxtoolbox.com/) should help you figure out `MX` ,`A`,`TXT`  etc.. records for further enumeration

{% hint style="info" %}
You can use the linux command [`host`](https://man.archlinux.org/man/host.1) instead of mxtoolbox
{% endhint %}

A quick dns check, reveals 4 IP addresses:

| Type | Domain Name | IP Address      |
| ---- | ----------- | --------------- |
| A    | jawad.ca    | 185.199.108.153 |
| A    | jawad.ca    | 185.199.109.153 |
| A    | jawad.ca    | 185.199.110.153 |
| A    | jawad.ca    | 185.199.111.153 |



We can perform a WHOIS query on IP addresses as well to determine the owner of `185.199.108.153`

In this case, we were able to determine that it belongs to GitHub.

```shell-session
kali@kali:~$ whois 185.199.108.153              
% This is the RIPE Database query service.
% The objects are in RPSL format.
%
% The RIPE Database is subject to Terms and Conditions.
% See https://apps.db.ripe.net/docs/HTML-Terms-And-Conditions

% Note: this output has been filtered.
%       To receive output for a database update, use the "-B" flag.

% Information related to '185.199.108.0 - 185.199.111.255'

% Abuse contact for '185.199.108.0 - 185.199.111.255' is 'abuse@github.com'

inetnum:        185.199.108.0 - 185.199.111.255
netname:        US-GITHUB-20170413
country:        US
org:            ORG-GI58-RIPE
admin-c:        GA9828-RIPE
tech-c:         NO1444-RIPE
status:         ALLOCATED PA
mnt-by:         RIPE-NCC-HM-MNT
mnt-by:         us-github-1-mnt
created:        2017-04-13T15:36:35Z
last-modified:  2018-12-14T10:48:39Z
source:         RIPE

organisation:   ORG-GI58-RIPE
org-name:       GitHub, Inc.
country:        US
org-type:       LIR
address:        88 Colin P. Kelly Jr. Street
address:        94107
address:        San Francisco
address:        UNITED STATES
phone:          +1 415 735 4488
admin-c:        GA9828-RIPE
tech-c:         NO1444-RIPE
abuse-c:        AR39914-RIPE
mnt-ref:        us-github-1-mnt
mnt-by:         RIPE-NCC-HM-MNT
mnt-by:         us-github-1-mnt
created:        2017-04-11T08:28:46Z
last-modified:  2020-12-16T13:16:10Z
source:         RIPE # Filtered

role:           GitHub Admin
address:        88 Colin P. Kelly Jr. Street
address:        94107
address:        San Francisco
address:        UNITED STATES
nic-hdl:        GA9828-RIPE
mnt-by:         us-github-1-mnt
created:        2017-04-18T22:16:30Z
last-modified:  2017-04-18T22:18:03Z
source:         RIPE # Filtered
abuse-mailbox:  abuse@github.com
org:            ORG-GI58-RIPE

role:           GitHub Network Operations
address:        88 Colin P. Kelly Jr. Street
address:        94107
address:        San Francisco
address:        California
address:        UNITED STATES
nic-hdl:        NO1444-RIPE
mnt-by:         us-github-1-mnt
created:        2017-04-18T20:05:01Z
last-modified:  2017-04-18T22:19:53Z
source:         RIPE # Filtered
org:            ORG-GI58-RIPE
admin-c:        GA9828-RIPE
abuse-mailbox:  abuse@github.com

% Information related to '185.199.108.0/24AS36459'

route:          185.199.108.0/24
origin:         AS36459
org:            ORG-GI58-RIPE
descr:          GitHub - 185.199.108.0/24
mnt-by:         us-github-1-mnt
created:        2017-04-18T21:01:44Z
last-modified:  2017-04-18T21:01:44Z
source:         RIPE

organisation:   ORG-GI58-RIPE
org-name:       GitHub, Inc.
country:        US
org-type:       LIR
address:        88 Colin P. Kelly Jr. Street
address:        94107
address:        San Francisco
address:        UNITED STATES
phone:          +1 415 735 4488
admin-c:        GA9828-RIPE
tech-c:         NO1444-RIPE
abuse-c:        AR39914-RIPE
mnt-ref:        us-github-1-mnt
mnt-by:         RIPE-NCC-HM-MNT
mnt-by:         us-github-1-mnt
created:        2017-04-11T08:28:46Z
last-modified:  2020-12-16T13:16:10Z
source:         RIPE # Filtered

% This query was served by the RIPE Database Query Service version 1.109 (DEXTER)

```

{% hint style="info" %}
**Exercise:** Try to gather more information about _**notes.jawad.ca**_ using a WHOIS query.
{% endhint %}

