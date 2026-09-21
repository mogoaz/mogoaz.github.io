---
layout: portfolio
title: Console Recovery & Hardware Fault Diagnosis
permalink: /labs/switch-recovery/
---

<section class="portfolio-section">

  <div class="portfolio-container">

    <span class="portfolio-label">
      Lab Challenge
    </span>

    <h2>
      Console Recovery & Hardware Fault Diagnosis
    </h2>

    <p class="portfolio-description">

      A hands-on validation session for the
      <a
        href="/projects/network-monitoring/"
        style="color: var(--blue); text-decoration: underline;"
      >network monitoring agent</a>,
      testing it against real switch hardware instead of a lab
      simulation. Getting there took diagnosing a counterfeit USB
      adapter and a full Cisco IOS password recovery, but the
      agent delivered: clean SNMP, STP, VLAN, and CPU metrics, and
      it caught a genuine power supply fault the moment I pointed
      it at the device.

    </p>


    <div style="margin-top: 40px;">

      <h2>
        Problem Statement
      </h2>

      <p class="portfolio-description">

        I needed console access to a Cisco switch to validate
        SNMP, environment monitoring, and VLAN visibility in the
        agent, but the switch had no known enable or line
        passwords. Worse, my first attempt at even reaching the
        console failed before I got that far.

      </p>

    </div>


    <div style="margin-top: 40px;">

      <h2>
        Approach
      </h2>

      <h3 style="color: var(--heading); font-size: 1.05rem; margin: 28px 0 10px;">
        Phase 1 · A Console Cable That Wasn't What It Claimed to Be
      </h3>

      <p class="portfolio-description">

        First attempt was Windows, PuTTY, and a USB-to-serial
        adapter. The official Prolific driver refused to talk to
        it, on two separate laptops:

      </p>

      <code class="portfolio-code">THIS IS NOT PROLIFIC PL2303. PLEASE CONTACT YOUR SUPPLIER.</code>

      <p class="portfolio-description">

        That error confirmed a counterfeit/cloned PL2303 chipset.
        Genuine Prolific drivers (post-2012) deliberately detect
        and block cloned chips, it's documented, intentional
        behavior, not a bug on my end. The fix was switching to
        Ubuntu, where the generic kernel driver doesn't perform an
        authenticity check:

      </p>

      <code class="portfolio-code">usb 3-4: New USB device found, idVendor=067b, idProduct=2303
usb 3-4: Manufacturer: Prolific Technology Inc.
pl2303 3-4:1.0: pl2303 converter detected
usb 3-4: pl2303 converter now attached to ttyUSB0</code>

      <p class="portfolio-description">

        From there, console access was straightforward:

      </p>

      <code class="portfolio-code">sudo picocom -b 9600 /dev/ttyUSB0</code>


      <h3 style="color: var(--heading); font-size: 1.05rem; margin: 28px 0 10px;">
        Phase 2 · Password Recovery
      </h3>

      <p class="portfolio-description">

        With console access finally in hand, the next problem
        surfaced: none of the known enable, line, or VTY
        passwords worked. That meant a full Cisco IOS password
        recovery, the standard procedure: power-cycle the switch,
        hold the Mode button to break into the bootloader,
        <code style="color: var(--green);">flash_init</code> to
        bring up the flash filesystem, rename the startup config
        so the switch boots without applying it, reload, then
        restore and reapply the configuration with new credentials.
        Passwords were reset across the enable secret and all
        line/VTY entries, and the configuration was saved.

      </p>


      <h3 style="color: var(--heading); font-size: 1.05rem; margin: 28px 0 10px;">
        Phase 3 · Putting the Agent to Work
      </h3>

      <p class="portfolio-description">

        With console access sorted, I set a management IP on the
        switch and confirmed it was reachable from the monitoring
        host. From there, the agent was pointed at real hardware
        for the first time instead of a lab simulation, and it
        held up: SNMP polling, environment monitoring, STP status,
        MAC address tracking, VLAN discovery, and CPU utilization
        metrics all came back clean and accurate.

      </p>

      <p class="portfolio-description">

        The best result came out of environment monitoring
        specifically.
        <code style="color: var(--green);">show env power</code>
        surfaced a real fault: Power Supply A was reporting an AC
        fault, with Power Supply B still healthy. Not a simulated
        failure I'd injected to test the agent, an actual fault on
        actual hardware that the agent's own polling caught. That's
        the whole point of building monitoring tooling: catching
        this automatically, not confirming it manually after
        someone notices something's wrong.

      </p>


      <h3 style="color: var(--heading); font-size: 1.05rem; margin: 28px 0 10px;">
        Phase 4 · The Adapter Finishes the Job
      </h3>

      <p class="portfolio-description">

        Moving on to test the agent's routing-specific features
        against a router, the test laptop's external USB ports
        began failing entirely, a wireless receiver, then a wired
        mouse, then a charging cable, one after another stopped
        being recognized.
        <code style="color: var(--green);">dmesg</code> and
        <code style="color: var(--green);">lsusb</code> showed the
        USB host controller itself was healthy (internal camera
        and Bluetooth kept working), but nothing external
        enumerated on any port. The likely cause: the counterfeit
        adapter had been dropping its connection all day
        (<code style="color: var(--green);">FATAL: read zero bytes
        from port</code>), and cheap cloned adapters typically skip
        proper ESD and voltage-surge protection. Most likely
        culprit for port-level damage on the laptop. Testing was
        paused until the hardware could be properly inspected.

      </p>

    </div>


    <div style="margin-top: 40px;">

      <h2>
        Tools Used
      </h2>

      <div class="portfolio-tags">

        <span class="portfolio-tag">Ubuntu 24.04</span>
        <span class="portfolio-tag">picocom</span>
        <span class="portfolio-tag">Cisco IOS</span>
        <span class="portfolio-tag">dmesg / lsusb</span>
        <span class="portfolio-tag">USB-to-Serial (PL2303)</span>

      </div>

    </div>


    <div style="margin-top: 40px;">

      <h2>
        Key Lessons Learned
      </h2>

      <p class="portfolio-description">

        Counterfeit hardware doesn't just fail to work, it can
        actively cause collateral damage. The small amount saved
        on a cheap adapter isn't worth it for anything you
        actually rely on.

      </p>

      <p class="portfolio-description">

        Cross-platform tooling is a real asset: switching to
        Linux's generic driver unblocked in minutes what Windows'
        driver deliberately refused to do. And process of
        elimination, internal peripherals working while external
        ones failed, was the fastest way to isolate a hardware
        fault from a driver or software one.

      </p>

      <p class="portfolio-description">

        Most of all: validate monitoring tooling against a real
        fault, not just simulated ones. The PSU failure was proof
        the agent's environment checks needed to surface something
        that actually happened, not just look right against test
        data.

      </p>

    </div>

  </div>

</section>
