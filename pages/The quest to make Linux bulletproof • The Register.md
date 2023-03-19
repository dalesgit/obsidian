---
created: 2023-02-16T09:07:01 (UTC -03:00)
tags: []
source: https://www.theregister.com/2023/02/16/bulletproof_linux/
author: Liam Proven
---

# The quest to make Linux bulletproof • The Register

> ## Excerpt
> What the big players and an outlier are doing, and why

---
Part 2 *This is the second half of a feature about work undertaken to harden and improve Linux, beginning with part 1 [here](https://www.theregister.com/2023/02/14/make_linux_safer_p1/).*

Commercial Unix was expensive so it was carefully tended – and indeed tendered. Linux is free so it has to fend for itself.

Linux itself was inspired by the tried and tested designs of the proprietary Unixes that preceded it – or predeceased it – which it drove into extinction. Some of their tech continues to make its way into Linux, and some is being reinvented, usually to get round IP issues. [The goals are to make Linux more resilient](https://www.theregister.com/2023/02/14/make_linux_safer_p1/): fault-tolerant, self-healing, and in general to lower the cost of its maintenance.

Just as desktop distros get their core tech from the lucrative server ones, some of the methods being used started out in old enterprise Unixes, or are reimplementations of tools and methods from them, but that's only the beginning of the influence.

A starting point is one of the longest-standing bits of enterprise IT: databases. They've been around for longer than minicomputers and their contents are usually very valuable so lots of time, effort, and money has gone into research into how to make them more resilient. A core property has been to make them *transactional* – once an important buzzword for big commercial databases, and something that later [filtered down to the smaller ones](https://www.theregister.com/2012/11/22/foundationdb_fear_of_cap_theorem/?page=1). The idea is to make every alteration of your precious business data into a transaction. Ideally, it completes fully, but if it doesn't, you have a record of what was *going* to happen, so you can fully undo it, thus putting things back exactly as they were before.

The rules for how to make this reliable were defined [by the great Tedd Codd](https://www.theregister.com/2013/08/19/ted_codd_90_relational_daddy/) to operating systems. Notably, this means the [ACID](https://www.ibm.com/docs/en/cics-ts/5.4?topic=processing-acid-properties-transactions) properties: Atomicity, Consistency, Isolation, and Durability.

In the Linux world, this first appeared with journaling file systems. First, some proprietary ones were hacked out of commercial Unixes: we reported on [SGI's XFS in 1999](https://www.theregister.com/1999/08/12/sgi_releases_xfs_file_system/), and [IBM's JFS in 2000](https://www.theregister.com/2000/02/03/ibm_releases_journaled_file_system/). The new journaled `ext3` file system was [merged](https://marc.info/?l=linux-kernel&m=100650331813822&w=2) into kernel 2.4.15 in November 2001, although an intrepid *Reg* correspondent [was already trying it out](https://www.theregister.com/2001/10/31/red_hat_hell_continued/) shortly before. [Apple added journaling to HFS+ the following year](https://www.theregister.com/2002/11/12/apple_adds_dropin_journaling/).

Now efforts are afoot to bring some degree of transactionality to software installation too, and that leads us to executive summaries of the approaches of some of the more significant players.

### The SUSE approach: using Btrfs and COW snapshots to make RPM transactional

The SUSE family of distros has long been given to using less-than-mainstream disk file systems. Way back in the 1990s, it defaulted to using ReiserFS while most others used ext2 or ext3 – *The Reg* [mentioned this relatively exotic file system 21 years ago](https://www.theregister.com/2002/01/18/linux_quake3_rocks_winxp_quake3/). ReiserFS became a less desirable choice because its eponymous lead developer [was convicted of murdering his wife](https://www.theregister.com/2008/04/29/hans_reiser_found_guilty/) in 2008. SUSE was [already offering Btrfs instead](https://www.theregister.com/Print/2013/11/27/review_opensuse_13_1/) a decade ago, and [it became the default file system](https://www.theregister.com/2014/11/06/opensuse_tumbles_into_town/) by 2014, and the [company remains committed to it](https://www.theregister.com/2017/08/25/suse_btrfs_defence/).

Although other [snapshot-capable file systems are out there](https://www.theregister.com/2022/10/24/daos_22_stratis_33/), this remains a key strength of Btrfs: while [OpenZFS on Linux is a thing](https://www.theregister.com/2020/12/01/zfs_on_linux_now_openzfs/), and [is under active development](https://www.theregister.com/2022/03/12/openzfs_213/), it's not part of the Linux kernel. Red Hat has yet to commit to its own Stratis, and [despite years of development](https://www.theregister.com/2015/08/24/does_linux_need_a_new_file_system_exgoogle_engineer_thinks_so/) the new [bcachefs remains unfinished](https://www.theregister.com/2022/03/18/bcachefs/). For now, only Btrfs offers copy-on-write (COW) snapshots and is part of the Linux kernel.

The great advantage of COW snapshots is that they are very quick. Essentially, it enables the OS to make a near-instant backup of the state of a set of files: from the moment a snapshot is created, any writes to those files will be redirected to a new copy of the relevant files, held elsewhere. It's fast and basically invisible to other programs on the system.

SUSE's [Snapper](http://snapper.io/) integrates Btrfs snapshots into package management. Whenever the OS's package manager is told to install some new software, it first makes a Btrfs snapshot. If anything doesn't work afterwards, the user can revert to the snapshot before the most recent update, and get a working system back again. Snapshot handling is integrated into the boot manager too so this also applies to kernel updates. It's a key selling point of openSUSE's rolling-release distro, Tumbleweed. Some other distros have added Snapper too, including the [Debian-based SpiralLinux](https://www.theregister.com/2022/06/20/spirallinux_new_debian_remix_from/), the [rolling-release Debian `sid`\-based Siduction](https://www.theregister.com/2023/01/05/siduction_2022_1/) and the [Arch Linux derivative Garuda](https://www.theregister.com/2022/07/28/garuda_linux_arch_better/).

But SUSE itself is pushing ahead with more sophisticated plans. Once [independent from UK COBOL-shifter Micro Focus](https://www.theregister.com/2018/07/02/linux_makes_suse_sold_for_a_cool_2535bn/), SUSE chose to grow by acquisition, and soon [snapped up Kubernetes merchants Rancher](https://www.theregister.com/2020/07/09/suse_acquires_rancher/). With a newfound appreciation for containers, SUSE's next-generation OS, [codenamed Advanced Linux Platform or ALP](https://www.theregister.com/2022/10/05/suse_alp_v001/), aims to increase reliability by moving beyond simple snapshots by making the root file system read-only. The only way to install software, including updates, is during a reboot, using a new command, [`transactional-update`](https://documentation.suse.com/alp/all/html/alp/concept-transactional-update.html). The OS can check that all its services come back up without errors, and if some fail, it can revert to an older snapshot and reboot itself.

If you have a cluster of hosts running lots of containers, this should not be too intrusive: an orchestration tool, such as [the ubiquitous Kubernetes](https://www.theregister.com/Tag/Kubernetes/), can migrate "pods" of containers off that machine, apply updates, and then bring containers back when the machine comes back up and rejoins the cluster. It's less convenient for a non-clustered machine, but it may prove possible to work around this using tools [akin to the existing Distrobox](https://www.theregister.com/2022/05/31/distrobox_130_released/), which builds a conventional, read-write OS instance in a container on a machine running an immutable OS.

### Don't have a fancy file system? Then make the package manager transactional, instead

Other companies, with less stake in sophisticated file systems, are taking different approaches, but with similar ultimate goals. Another way to make software installation transactional is to move the functionality into the package manager, rather than the file system.

We [have explored this in some depth](https://www.theregister.com/2021/11/26/linux_software_installation/), but we hope you'll forgive a potted recap. The main contenders are Snap and Flatpak. Snap is the more controversial because of the perception that it's proprietary, and the way that recent Ubuntu releases force it on Ubuntu users. The [now official](https://www.theregister.com/2022/10/20/ubuntu_2210_kinetic_kudu/) Ubuntu Unity remix [adds in Flatpak support as standard](https://www.theregister.com/2022/04/26/ubuntu_unity_and_ubuntu_cinnamon/). Linux Mint goes further: it [completely removes Snap support](https://www.theregister.com/2022/08/02/linux_mint_21_vanessa_released/) and only offers Flatpak.

So what are the differences, and why?

### Ubuntu: Cross-platform packages are single, compressed files

A few years ago, and [despite some controversy](https://www.theregister.com/2016/02/26/canonical_in_zfsonlinux_gpl_violation_spat/), Canonical was [actively working on integrating OpenZFS into Ubuntu](https://www.theregister.com/2019/08/12/canonical_zfs_ubuntu/). However, more recently, it [looks like Ubuntu's ZSys tool is being deprecated](https://www.theregister.com/2022/12/20/kernel_62_fs_improvements/).

However, Canonical [remains firmly committed to its Snap packaging system](https://www.theregister.com/2022/11/09/canonical_conference/), and offers [its own immutable distribution, Ubuntu Core](https://www.theregister.com/2019/01/22/ubuntu_core_18/); we recently [looked at Ubuntu Core 22](https://www.theregister.com/2022/06/17/ubuntu_core_22/). Like SUSE MicroOS, the root file system is read-only, and the conventional package manager is gone. Ubuntu Core only supports Snap, and even the kernel is packaged as one.

Ubuntu's Snap format survived from [Canonical's phone and tablet version of Ubuntu](https://www.theregister.com/2013/02/23/ubuntu_tablets_first_look), although the company's efforts to [crowdfund the hardware failed](https://www.theregister.com/2013/07/23/ubuntu_crowd_funded_smart_phone/). Each Snap is a single compressed file, which is versioned and digitally signed. Snaps are `squashfs` files mounted as [loop devices](https://man7.org/linux/man-pages/man4/loop.4.html) containing the relevant binaries and all the dependencies specific to that version. This means that, for example, the same Firefox snap can run on multiple different versions of Ubuntu, reducing Canonical's workload when updating Firefox across multiple versions of Ubuntu that are still in support and receiving updates.

And importantly, because Snap works with monolithic single file packages, it doesn't need a fancy file system underneath to implement rollback. When a Snap is updated, the package manager retains the old version so installation can be rewound by simply unmounting the newer version and remounting an older one.

Snap is in active development, and some things that users have issues with may yet change. When [the Snap-packaged Firefox appeared in Ubuntu 22.10](https://www.theregister.com/2021/10/14/ubuntu_21_10/), some users saw very slow launch times; in response, Canonical has added a choice of compression algorithms, and moved Firefox to a compression scheme that decompresses quicker. All the Snap files are loop-mounted during bootup, which slows system startup a little. *The Reg* FOSS desk wouldn't put it past Canonical's boffins to in future add a feature that marks some Snaps as not being essential for system startup, so that they can be mounted on-demand each time the app they contain is first launched.

### The GNOME approach: Distribute binaries using tech akin to Git

An aspect of some bits of Linux tech that is largely invisible from the outside world is the pervasive influence of the tools that the community use to build the software itself. For instance, much FOSS product *documentation* is written, edited, formatted and output using an approach known as [Docs as Code](https://www.writethedocs.org/guide/docs-as-code/). The tools are not perfect for the job – but they are rich, powerful, capable tools, they are free, and perhaps most of all, they are well-known, debugged and optimized by the same teams who are building the products themselves. Since documentation writers need to work closely with those teams anyway, the benefits outweigh the slightly clunky tooling. The technical writers get to know the same tools, which makes it easier to talk to, and work with, the developers.

Git is a core part of this. It's very clever, can do amazing things, and is famously hard to [master](https://xkcd.com/1597/). Back in 2005, the source code of the Linux kernel was already becoming unwieldy, to the point that its creator Linus Torvalds [adopted a proprietary tool, Bitkeeper, to manage it](https://www.theregister.com/2005/04/06/torvalds_bitkeeper/). This proved controversial, and he later [wrote his own tool to replace it](https://www.theregister.com/2009/01/21/git_gaining_ground/). For any readers who aren't speakers of British English, the tool's name, `git`, is UK slang for an annoying or uncooperative person.

-   [Make Linux safer… or die trying](https://www.theregister.com/2023/02/14/make_linux_safer_p1/)
-   [Spotted in the wild: Chimera – a Linux that *isn't* GNU/Linux](https://www.theregister.com/2023/02/13/chimera_non_gnu_linux/)
-   [Don't bore us, get to the Horus: Elementary OS 7 is here and looking good](https://www.theregister.com/2023/02/10/elementary_os_7_horus/)
-   [WINE Windows translation layer has matured like a fine... you get the picture](https://www.theregister.com/2023/02/03/wine_80_dxvk_21/)

What Git does, in brief, is synchronize all the files in a whole directory tree across different computers in different places. When one developer changes a local copy of a file or files, they `push` those changes to another repository over the internet. Then all the other people working with that set of files `pull` the changes down into their own local Git-managed copy. Git was designed to be decentralized, but in real life, most people use large public websites to hold primary copies, of which the [now Microsoft-owned GitHub](https://www.theregister.com/2018/06/04/microsoft_buys_github/) is the biggest.

Git is well named: it's *extremely* complicated to use – by way of full disclosure, this vulture used it daily for years, and loathes it. As Isaac Wolkerstorfer [quipped](https://twitter.com/agnoster/status/44636629423497217):

(We think, but are not certain, that this is a sly reference to a famous [joke](http://james-iry.blogspot.com/2009/05/brief-incomplete-and-mostly-wrong.html) about the Haskell programming language: **"A monad is just a [monoid](https://blog.softwaremill.com/monoid-in-the-category-of-endofunctors-b85bab43587b) in the category of endofunctors, what's the problem?"**)

However, a core function is that one computer can ask for an updated copy of an abitrarily complex set of files, and Git just sorts out securely sending only the changed parts. At any point, you can `revert` to any specific older version, and the software magically sorts out putting the files back how they were: the widely sought-after transactional rollback function.

Git was designed for handling source code, and works best with plain text. Red Hat, wanting transactional software packaging, but [not having a supported COW file system in RHEL](https://www.theregister.com/2017/08/16/red_hat_banishes_btrfs_from_rhel/), developed [OStree](https://ostreedev.github.io/ostree/), which [describes](https://ostreedev.github.io/ostree/introduction/) itself as **"git for operating system binaries."**

Flatpak uses OStree for distributing software in its runnable form. You package up your binaries, libraries, config files, whatever in one folder tree, and put that primary instance on a server. (The primary one is [Flathub](https://flathub.org/), but it's straightforward to set up your own. Flatpak enthusiasts hold this up as an advantage over Snap, where the only official store is Canonical's own. However, it is possible to set up alternatives, as [the Ubuntu Unity developer demonstrated](https://www.theregister.com/2022/02/04/rudra_sarsawat_ubuntu_projects/) a year ago.)

Users' computers use the special Flatpak client to request a copy of an app, and the underlying infrastructure sends whatever is needed: either the whole thing, or just the changed files. Either way, the software tracks all the versions of all the component parts, making it easy to revert back to any older version, without resending the whole thing over the internet each time.

Each Flatpak app is just a directory tree. There's no need to loop-mount Flatpaks, so unlike Snap, Flatpak doesn't depend on systemd. Also, a capable file system – [such as Btrfs in Fedora](https://www.theregister.com/2022/05/12/fedora_36_released/) – can deduplicate identical files in separate Flatpaks, replacing them with a single copy and multiple hardlinks. To rival Snap's compressed packages, Btrfs can also selectively compress just Flatpak apps. When updating, OStree can copy only the differences in changed files, so Flatpak downloads are faster than Snap ones, too.

The Flatpak-versus-Snap comparison is not all win-win, though. Flatpak is only intended for desktop apps, and doesn't work on server boxes without a GUI. For that, you need OStree, which is used in Fedora CoreOS, as well as in the [desktop-focused Endless OS](https://www.theregister.com/2023/01/12/endless_os_5/). This is more complicated than Snap, which supports both roles with the same commands and tools.

We call this the GNOME approach because it's not limited to Red Hat and its products – but like the GNOME desktop itself, Red Hat, as the biggest company in the Linux world, is one of the biggest backers of Flatpak and OStree. Multiple other distros include Flatpak support by default, including [the Ubuntu-based Linux Mint](https://www.theregister.com/2022/08/02/linux_mint_21_vanessa_released/).

### And the rest…

The one place you won't find Flatpak is on servers, and of course servers are where the money is in the Linux world. Today, the focus is on containers, which themselves [started out as a way to simplify Unix system administration](https://www.theregister.com/2011/07/18/brief_history_of_virtualisation_part_3/).

Arguably validating SUSE's approach with MicroOS, there are multiple other simplified, miniaturized Linux distros, all with immutable file systems and designed for hosting containers and nothing else.

*The Reg* has [previously looked at Amazon's Bottlerocket](https://www.theregister.com/2020/09/01/aws_bottlerocket_linux_for_containers/). [VMare's offering is Photon OS](https://www.theregister.com/2015/11/17/vmware_open_sources_its_photon_container_control_freak/), which [we looked at when it was quite new](https://www.theregister.com/2016/01/15/docker_photon/). Although the last new release, [version 4.0](https://github.com/vmware/photon/wiki/What-is-New-in-Photon-OS-4.0), was a couple of years ago now, version 5.0 is in [beta](https://blogs.vmware.com/vsphere/2023/01/photon-5-0-beta-is-now-available.html).

Following [its acquisition of CoreOS](https://www.theregister.com/2018/01/31/red_hat_coreos_acquisition/), Red Hat [moved it to a Fedora base](https://www.theregister.com/2020/02/18/end_of_life_coreos_container_linux/), but a fork of the original ChromeOS-based project continues as [Flatcar's](https://www.flatcar.org/) *Container Linux* – and [Microsoft supports that on Azure](https://www.theregister.com/2020/03/24/microsoft_brings_k8s_security_center/). Sidero's [Talos Linux](https://www.talos.dev/) is another independent contender.

This is clearly a trend. The difference is SUSE has general-purpose aspirations for its product, potentially even including as a [desktop](https://en.opensuse.org/Portal:MicroOS/Desktop).

As far as production deployment goes, none of the other minimalist immutable OSes are any use outside of the context of container-management tools such as Docker and Podman, and typically managed with Kubernetes. However, distros such as [Fedora's Silverblue and Kinoite](https://www.theregister.com/2021/02/18/kinoite_immutable_fedora/) show that this is certainly possible. Endless OS, which we mentioned earlier, has been shipping for several years and has now released version 5.0.

### And that outlier we mentioned

The real story underneath all these efforts is relatively simple: finding ways to make Linux more resilient. The goal is automation – both of initial deployment, and then of subsequent updates. You can only safely automate software updates if there's some way to detect if they didn't work and roll them back, without human intervention.

Just as virtual machines revolutionized systems administration, [containers have revolutionized large-scale server deployment](https://www.theregister.com/2017/06/01/linux_open_source_container_threat_to_vmware_microsoft/). Containers use namespace isolation and so on to make it look to each app like it's the only one on that instance of the OS. In turn, [containerized packaging tools use this to bundle all of an application's dependencies together](https://www.theregister.com/2021/11/26/linux_software_installation/).

It's all about making it easier for humans to manage the huge, sprawling complexity of modern apps. As several commentators have [examined](https://queue.acm.org/detail.cfm?id=2349257), this is a serious problem and it's not getting any better.

That complexity manifests as lots of files in lots of directories. Containers, at their root ([pun](https://man7.org/linux/man-pages/man2/chroot.2.html) intended), handle the problem of large complex directory trees by splitting them up, so that instead of one huge tree to manage, there are multiple different trees which don't overlap.

Once you accept this, all these different distro's approaches make sense. They're all just trying to find ways to automate the deployment of Linux and Linux software, so that Linux computers can look after themselves, keep themselves up to date, and fix themselves if updates go wrong – ideally without the users even noticing.

[ChromeOS achieves this](https://www.theregister.com/2022/02/16/google_chrome_os/) by the simple expedient of not having a package manager and basically prohibiting the installation of local apps (all right, except Android apps).

Android solves this by not really being a conventional Unix any more, and by farming the problem of OS updates out to phone vendors. Phone vendors solve this by just not offering updates after a while, which is where [postmarketOS enters the picture](https://www.theregister.com/2022/06/15/postmarketos_2206/).

All these solutions are trying to make it easier to manage that complexity, so that it can be automated.

*But automating things is what computers **do**.* It's their purpose.

Human-readable directory trees are becoming so complicated that humans can't manually manage them. Packaging systems, which exist in order to automate copying files into various directories, now need to do such complicated actions that it's necessary to wrap them up inside what are effectively package-management managers. Some vendors are managing all those myriad files with elaborate file systems that can maintain multiple sets of files, with only one set visible at at time.

Perhaps trying to preserve human-readable file system layouts in the first place is the root problem here.

As we've described before, a totally different solution to these packaging woes is to automate the naming of the directories: to let go of human-readable directory trees, and [let the OS automate choosing what goes where](https://www.theregister.com/2021/12/03/nixos_linux_os_design/).

A handful of distros are doing this, of which [NixOS is arguably the most mature and complete](https://www.theregister.com/2022/12/13/nixos_2211_raccoon/). But NixOS is just an OS built entirely with the [Nix](https://nixos.org/) packaging system, and you can [download](https://nixos.org/download.html) and run the Nix package manager on almost any distro.

Programs installed via Nix don't interact with any part of the underlying OS except the kernel itself. In [single-user mode](https://nixos.org/manual/nix/stable/installation/single-user.html), one user account runs an isolated copy of Nix inside that user's home directory, but then no other accounts can use the programs. In the recommended [multi-user mode](https://nixos.org/manual/nix/stable/installation/multi-user.html), only `root` and the Nix daemon can.

Moving to Nix, or a tool like it such as [GNU Guix](https://guix.gnu.org/en/about/), is a big step. The sysadmin must let go of the idea of knowing what is kept where, of being able to read and understand folder names any more. They just tell the package manager the desired state: a list of apps and versions, and the packager makes it happen.

Package management tools, and the layout of the file system and where it keeps things, are a core part of what distinguishes one distribution from another. Telling an expert in any distro that they should just let go of it all, and let the OS worry about it is a big ask.

When Ubuntu announced that Ubuntu Pro support covered the entire `universe` repository, this put the other enterprise-supported distros into context. Ubuntu's main repository contains some 60,000 packages, [about 20 times more](https://www.theregister.com/2022/10/06/ubuntu_pro_free/) than the supported components of RHEL or SLE. The [Nixpkgs](https://github.com/NixOS/nixpkgs) collection, at over 80,000 packages, is larger still.

At FOSDEM, [Michael Brantley](https://github.com/limeytexan), co-founder of Nix vendor [Flox](https://floxdev.com/), told us that after decades of professional Unix systems administration, starting on proprietary OSes such as Solaris and moving to Linux early on, "when I discovered Nix, I realized that, 30 years in, I'd been doing it wrong all this time."

Nix [describes](https://github.com/NixOS/nix) itself as "the purely functional package manager" and its logo is intertwined lambda symbols. The lambda represents the [lambda calculus](https://plato.stanford.edu/entries/lambda-calculus/), also at the core of the Lisp programming language. The claims around Nix remind us of those around Lisp, such as Paul Graham's famous essay "[Beating the Averages](http://www.paulgraham.com/avg.html)".

But Nix doesn't require anyone to rewrite anything in Lisp. It just needs us to let go of the idea of human-managed file systems, and let the computer handle it. That's a very big stretch for a programmer-centric OS such as Unix, which puts the file system at the centre of everything.

It could be that this really is the optimal answer to the problems that Btrfs, Stratis, ZFS, Snap, Flatpak, OStree, and the multiple container systems are all trying to solve, while keeping things in the comfortable, familiar layout that millions of Unix users know and like. It won't be the first time that players in this industry have [found themselves caught in a monkey trap](https://www.theregister.com/2013/12/12/feature_microsoft_caught_in_virtual_monkey_trap/). ®
