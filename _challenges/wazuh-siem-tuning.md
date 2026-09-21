---
layout: portfolio
title: Building & Tuning a SIEM From the Ground Up
permalink: /labs/wazuh-siem-tuning/
---

<section class="portfolio-section">

  <div class="portfolio-container">

    <span class="portfolio-label">
      Lab Challenge
    </span>

    <h2>
      Building & Tuning a SIEM From the Ground Up
    </h2>

    <p class="portfolio-description">

      Deploying a production-grade SIEM is more than installing an
      agent. This covers standing up endpoint detection across a
      mixed fleet, wiring up real-time alerting, and a firewall
      mystery that turned into a lesson about where "correct"
      configuration actually needs to live.

    </p>


    <div style="margin-top: 40px;">

      <h2>
        Problem Statement
      </h2>

      <p class="portfolio-description">

        The goal was straightforward on paper: deploy Wazuh across
        a mixed Windows/Linux fleet, get endpoint detection and
        vulnerability visibility working, and build custom
        detection coverage beyond the default ruleset. What wasn't
        straightforward was a case where an automated block was
        being applied correctly and traffic kept getting through
        anyway.

      </p>

    </div>


    <div style="margin-top: 40px;">

      <h2>
        Approach
      </h2>

      <h3 style="color: var(--heading); font-size: 1.05rem; margin: 28px 0 10px;">
        Phase 1 · Standing Up the Stack
      </h3>

      <p class="portfolio-description">

        Sysmon was deployed as the EDR layer on Windows endpoints,
        Auditd on Linux, both feeding into a central Wazuh manager.
        The Vulnerability Detector module was enabled to cross
        reference installed software against known CVEs, and
        fail2ban was set up to automatically block sources showing
        brute-force behavior.

      </p>


      <h3 style="color: var(--heading); font-size: 1.05rem; margin: 28px 0 10px;">
        Phase 2 · Building Detection Coverage
      </h3>

      <p class="portfolio-description">

        The default Wazuh ruleset catches generic patterns. Real
        coverage meant writing custom rules tuned to the specific
        environment, then testing and tuning again, a rule that's
        too broad floods the team with low-value alerts, and one
        that's too narrow misses the thing it was written for.

      </p>


      <h3 style="color: var(--heading); font-size: 1.05rem; margin: 28px 0 10px;">
        Phase 3 · Making Alerts Actionable
      </h3>

      <p class="portfolio-description">

        Alerts sitting in a dashboard nobody's watching aren't
        useful. Detection rules were wired to push directly into a
        live team chat channel, so investigations start when an
        alert fires, not whenever someone happens to check the
        console.

      </p>


      <h3 style="color: var(--heading); font-size: 1.05rem; margin: 28px 0 10px;">
        Phase 4 · The Firewall That Wasn't Firewalling
      </h3>

      <p class="portfolio-description">

        fail2ban was correctly detecting brute-force attempts and
        adding block rules for the source IPs.
        <code style="color: var(--green);">ufw status</code>
        confirmed the rules were present and correctly formed. And
        yet the traffic kept coming through. The rule was right;
        the layer it lived on wasn't the one actually deciding
        what reached the host. In a cloud-hosted environment, a
        provider-level network firewall sits in front of the
        instance, and a host-level firewall rule doesn't
        necessarily propagate to or override that layer. The fix
        was configuring the block at the network layer directly,
        not just on the instance itself, and then verifying the
        block actually worked by testing from the source side,
        not just checking that the rule existed.

      </p>

    </div>


    <div style="margin-top: 40px;">

      <h2>
        Tools Used
      </h2>

      <div class="portfolio-tags">

        <span class="portfolio-tag">Wazuh</span>
        <span class="portfolio-tag">Sysmon</span>
        <span class="portfolio-tag">Auditd</span>
        <span class="portfolio-tag">fail2ban</span>
        <span class="portfolio-tag">UFW</span>
        <span class="portfolio-tag">Cloud Network Firewall</span>

      </div>

    </div>


    <div style="margin-top: 40px;">

      <h2>
        Key Lessons Learned
      </h2>

      <p class="portfolio-description">

        A correct configuration can still fail silently if it's
        sitting at the wrong layer. In cloud environments,
        defense needs to be verified at every layer it actually
        operates at, host firewall, network firewall, and
        anywhere else traffic passes through, not just the one
        that's easiest to check.

      </p>

      <p class="portfolio-description">

        The other lesson was about verification itself: seeing a
        rule exist isn't the same as confirming it does what it's
        supposed to. Testing a block from the source side, not
        just reading the rule back from the firewall's own output,
        is what actually caught this.

      </p>

    </div>

  </div>

</section>
