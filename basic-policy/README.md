# basic-policy
This is a simple policy to perform basic checks on an image.

**DOCKERFILECHECK:NOTAG:WARN**
This checks that the dockerfile users a *FROM* with a non-latest tag.
For example using:
*FROM ubuntu:latest*
rather than explicitly specifying an image
*FROM ubuntu:xenial-20170214*

**DOCKERFILECHECK:NOFROM:STOP**
Triggers if there is no *FROM* specific in the Dockerfile

**DOCKERFILECHECK:NOHEALTHCHECK:WARN**
Triggers if the Dockerfile does not contain a healthcheck command

**DOCKERFILECHECK:EXPOSE:STOP:DENIEDPORTS=22**
Triggers if the Dockerfile exposes port 22 (typically used for SSH)

**SUIDDIFF:SUIDFILEDEL:GO**
Trigger is raised if a file with the SUID bit is removed from the image.

**SUIDDIFF:SUIDMODEDIFF:STOP**
Trigger is raised if the attributes of a SUID file has been changed.

**SUIDDIFF:SUIDFILEADD:STOP**
Triggers if a file with SUID bit set has been added

**IMAGECHECK:BASEOUTOFDATE:WARN**
Triggers if the image 



**PKGBLACKLIST:PKGNAMEMATCH:STOP:BLACKLIST_NAMEMATCH=openssh-server**
Triggers if the openssh-server package is installed in the image.


The following policy lines apply to operating system CVE checks.

**ANCHORESEC:FEEDOUTOFDATE:STOP:MAXAGE=2**
Triggers if the CVE data feed has not been syncronized within the last 2 days.

**ANCHORESEC:UNSUPPORTEDDISTRO:STOP**
Triggers if the image uses an operating system that Anchore does not have CVE data for.
Currently Anchore supports Alpine, CentOS, Debian, Oracle Linux, Red Hat Enterprise Linux and Ubuntu.

**ANCHORESEC:VULNCRITICAL:STOP**
Triggers if any Critical level vulnerabilities are found in the image.

**ANCHORESEC:VULNHIGH:STOP**
Triggers if any high level vulnerabilities are found in the image.

**ANCHORESEC:VULNMEDIUM:WARN**
Triggers if any medium level vulnerabilities are found in the image.
