# Mike Wilson 🐧🎸🎤

I'm a data center engineer, Linux sysadmin, and musician. I spend most of my
time building my homelab, songwriting, and fixing the songs and systems I break
along the way.

By day I'm a Data Center Engineer at a major cloud infrastructure provider,
working on a fleet of GPU servers (NVIDIA H100/H200, AMD MI300X-class) that
fail a lot more often than anyone would like. Most of my job is RMAs. The rest
of it, and most of my spare time, goes into writing the tooling that makes the
RMAs (and everything else) take less of my day.

If work can be done in the terminal, I will find a way to do it in the
terminal. I'm passionate about open-source software and hardware, privacy,
security, and the right to repair.

[Website](https://mikewilsonstl.com) ·
[Terminal CV](https://cv.mikewilsonstl.com) ·
[Docs](https://docs.mikewilsonstl.com) ·
[Blog](https://mikewilsonstl.com/blog/) ·
[LinkedIn](https://linkedin.com/in/mikewilsonstl)

## Things I've built

**[Redfish Explorer](https://github.com/MikeWilsonSTL/redfish-explorer)**  
Most of my Redfish work is fleet-scale scripting: query the BMC for the fields
I need, parse the JSON, move on to the next node. That solves the problem, but
it didn't teach me the model. So I built a clickable Redfish browser that puts
every property next to its DMTF schema description, units, and enum meaning,
mainly to learn the newer liquid-cooling parts of the spec (CDUs, pumps, leak
detection). Python stdlib and plain JS, no build step, no dependencies. Live mode
only sends GETs, so it can't change anything on a real BMC.  
[Live demo](https://redfish.mikewilsonstl.com) ·
[Docs](https://docs.mikewilsonstl.com/docs/redfish-explorer/) · AGPL-3.0

**[SMRwipe](https://mikewilsonstl.com/projects/smrwipe)**  
Roughly 30,000 host-managed SMR drives failed every commercial and open-source
wipe tool we could find, and they were headed for the shredder even though
nearly all of them were healthy. I found out the drive's own ATA Sanitize
command, run by hand with `hdparm`, could erase them to NIST SP 800-88 Rev. 2
Purge. That turned into a Bash script within about a week, and the script
turned into a rack-scale Python platform that wiped, verified, and certified
every one of those drives so they could be resold. Most of the real work was
in the failure handling: "identical" servers that turned out to have two
different SAS controllers, and I/O pressure I had to tune down until the
errors stopped. This project taught me more about storage media in a year than
I ever thought I would learn in my entire life. The code belongs to a former
employer, so I can't post it, but I'm happy to walk through the journey and 
general steps taken.

**[eMMC-Checker](https://github.com/MikeWilsonSTL/eMMC-Checker)**  
Takes `mmc-utils` output and shows it the way `smartctl` would, so you can
actually read an eMMC's health at a glance.

**[youtube-to-rss](https://github.com/MikeWilsonSTL/youtube-to-rss)**  
Pulls all of your YouTube subscriptions into an OPML file for any
video-capable RSS reader. Invidious instances optional.

**[newsh](https://github.com/MikeWilsonSTL/newsh)**  
Makes a new Bash script from a template and opens it in your editor.

## At work

I've made a comprehensive tool suite during my time in my current role. Some
of those tools accomplish the following:

- Collects every BMC page, log export, crash dump, and remote `dmesg` an RMA
  needs in one command, instead of a round of manual screenshots per case.
- Resolves a serial number into a rack location in about 2 seconds. It used to
  take a few minutes of clicking through DCIM and I hate leaving the terminal.
  This way is much faster for CLI-oriented folks.
- An automated RMA pipeline that treats hardware vendors as config data instead
  of a rat's nest of `if` statements, so adding one doesn't affect the core workflow.

I also wrote my team's safety standard for automation scripts, and fixed a bug
in our shared shutdown script that could have powered off nodes still running
customer VMs.

## Homelab

Four Dell PowerEdge R620s and an R320 (managed over Redfish and iDRAC), five
Asus PN40s, a couple of Raspberry Pis, and Juniper and Arista switches. It ran
a Proxmox cluster with a NAS taking daily Borg backups. It's all packed up
after a move right now, and I'm rebuilding it as an everything-as-code lab.

It has also taught me plenty by breaking. I once took down a Proxmox node by
starving my OPNsense VM of RAM mid-VLAN-change, which corrupted pmxcfs badly
enough that I couldn't fix it in place:
[Proxmox & Mini PCs: Tread Carefully](https://mikewilsonstl.com/blog/proxmox-and-mini-pcs).

## Before this

I worked in data centers all across North America: installs, de-installs, site
migrations, breakfix, fiber testing, site audits, you name it. I ended up
leading jobs for clients ranging from local businesses to hyperscalers. Before
that, about a decade of freelance Linux work for small businesses: web and
email servers, DNS, TLS, firewalls, backups. I also self-hosted my own email
for a years, which gave me a deep respect for full-time email providers.

CDCP certified, Google Cybersecurity Certificate, A.A.S. in Computer Systems
Management.
