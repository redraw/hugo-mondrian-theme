---
title: "Linux ate my RAM"
date: 2019-03-04T20:26:44-03:00
description: "with description"
tags:
    - linux
    - faq
---

![Linux ate my RAM!!](https://www.linuxatemyram.com/atemyram.png)

>Don't Panic!  
>Your ram is fine!

What's going on?
----------------

Linux is borrowing unused memory for disk caching. This makes it looks like you are low on memory, but you are not! Everything is fine!

Why is it doing this?
---------------------

Disk caching makes the system much faster and more responsive! There are no downsides, except for confusing newbies. It does not take memory away from applications in any way, ever!

What if I want to run more applications?
----------------------------------------

If your applications want more memory, they just take back a chunk that the disk cache borrowed. Disk cache can always be given back to applications immediately! You are not low on ram!

Do I need more swap?
--------------------

No, disk caching only borrows the ram that applications don't currently want. It will not use swap. If applications want more memory, they just take it back from the disk cache. They will not start swapping.

How do I stop Linux from doing this?
------------------------------------

You can't disable disk caching. The only reason anyone ever wants to disable disk caching is because they think it takes memory away from their applications, which it doesn't! Disk cache makes applications load faster and run smoother, but it NEVER EVER takes memory away from them! Therefore, there's absolutely no reason to disable it!

Why does top and free say all my ram is used if it isn't?
---------------------------------------------------------

This is just a difference in terminology. Both you and Linux agree that memory taken by applications is "used", while memory that isn't used for anything is "free".

But how do you count memory that is currently used for something, but can still be made available to applications?

You might count that memory as "free" and/or "available". Linux instead counts it as "used", but also "available".

How do I see how much free ram I really have?
---------------------------------------------

To see how much ram your applications could use without swapping, run `free -m` and look at the "available" column:

```bash
$ free -m
              total        used        free      shared  buff/cache   available
Mem:           1504        1491          13           0         855      792
Swap:          2047           6        2041
```

(On installations from before 2016, look at "free" column in the "-/+ buffers/cache" row instead.)

This is your answer in megabytes. If you just naively look at "used" and "free", you'll think your ram is 99% full when it's really just 47%!

For a more detailed and technical description of what Linux counts as "available", see [the commit that added the field](https://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git/commit/?id=34e431b0ae398fc54ea69ff85ec700722c9da773).

When should I start to worry?
-----------------------------

A **healthy Linux system** with more than enough memory will, after running for a while, show the following expected and harmless behavior:

*   `free` memory is close to `0`
*   `used` memory is close to `total`
*   `available` memory (or "free + buffers/cache") has enough room (let's say, 20%+ of total)
*   `swap used` does not change

**Warning signs** of a genuine low memory situation that you may want to look into:

*   `available` memory (or "free + buffers/cache") is close to zero
*   `swap used` increases or fluctuates
*   `dmesg | grep oom-killer` shows the OutOfMemory-killer at work

How can I verify these things?
------------------------------

See [this page](play.html) for more details and how you can experiment with disk cache to show the effects described here. Few things make you appreciate disk caching more than measuring an order-of-magnitude speedup on your own hardware!

##### LinuxAteMyRam.com was presented by [VidarHolen.net](http://www.vidarholen.net). This site is available [on GitHub](https://github.com/koalaman/linuxatemyram.com) for comments and PRs.