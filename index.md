---
layout: page
title: Argument Injection Vectors ✨
---

A curated list of exploitable options when dealing with argument injection bugs!

Vectors listed below are not vulnerabilities in the associated programs but rather intended features that were proven to be useful to attackers in very specific scenarios. Please don't report or request CVEs for them.

If you would like to know more on this topic, you can visit:

- [Argument Injections Explained]({{ "/explained/" | relative_url }})
- [Tools]({{ "/tools/" | relative_url }})
- [Remediation]({{ "/remediation/" | relative_url }})

This project also maintains an association between CVEs and vectors on the page [CVEs]({{ "/cves/" | relative_url }}).

**What's the difference with GTFOBins?**

GTFOBins' goal is to "bypass local security restrictions in misconfigured systems", and that's not what we're trying to achieve with our project. We want to provide a list dedicated to helping vulnerability researchers to exploit argument injection bugs. 

While some content from the two projects may overlap (i.e., when a sudoer rule allows arbitrary parameters on a command), having a separate list dedicated to these vectors is also more efficient. Users spend less time filtering out vectors that won't apply in their case and get access to similar public advisories and write-ups. 

**Contributing**

[Contributions]({{ "/contributing/" | relative_url }}) to this list are very welcome. Feel free to open issues [on the repository](https://github.com/SonarSource/argument-injection-vectors) if you would like to see payloads on a specific program, or a pull request if you are already aware of exploitable flags in a target. Links to public write-ups are appreciated when adding a payload. 

The code of this website is based on [GTFObins](https://gtfobins.github.io/) and is released under GNU General Public License v3.0.

The project is maintained by the [Sonar R&D](https://twitter.com/Sonar_Research) team. Find argument injection vulnerabilities in your code (and much more) with 
[SonarCloud](https://sonarcloud.io/), free for open-source projects! 

{% include bin_table.html %}
