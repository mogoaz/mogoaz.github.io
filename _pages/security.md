---
layout: portfolio
title: Security
permalink: /security/
---

<section class="portfolio-section">

  <div class="portfolio-container">

    <span class="portfolio-label">
      Security
    </span>

    <h2>
      How I approach security engineering.
    </h2>

    <p class="portfolio-description">

      Security isn't a checklist I run once. It's a discipline
      applied to how systems are built, watched, and improved
      over time. As the person leading security at Nathan Claire
      Group (NCG), that means owning the company's security
      architecture as a whole, not just individual tools. Here's
      the process behind that, and the toolkit that supports it.

    </p>


    <div style="margin-top: 60px;">

      <h2>
        My Approach
      </h2>

      <p class="portfolio-description">

        Four things I come back to on every piece of security
        work, roughly in this order.

      </p>

      <div class="portfolio-grid">

        <article class="portfolio-card">

          <span class="portfolio-card-number">
            01 · SEE
          </span>

          <h3>
            Build Visibility First
          </h3>

          <p>

            You can't secure what you can't see. Before anything
            else, I get telemetry flowing across endpoint events,
            network traffic, and application logs, so the
            environment is observable end to end.

          </p>

        </article>


        <article class="portfolio-card">

          <span class="portfolio-card-number">
            02 · DETECT
          </span>

          <h3>
            Tune Detection to the Environment
          </h3>

          <p>

            Default rule sets catch generic threats. Real
            detection comes from rules tuned to how this specific
            environment behaves, so alerts are signal, not noise.

          </p>

        </article>


        <article class="portfolio-card">

          <span class="portfolio-card-number">
            03 · RESPOND
          </span>

          <h3>
            Investigate, Don't Just Alert
          </h3>

          <p>

            An alert nobody investigates isn't security. It's
            noise with a timestamp. I build the workflows needed
            to actually close the loop on what gets flagged.

          </p>

        </article>


        <article class="portfolio-card">

          <span class="portfolio-card-number">
            04 · HARDEN
          </span>

          <h3>
            Reduce the Attack Surface
          </h3>

          <p>

            In practice: hardening production servers by closing
            unnecessary services, enforcing least-privilege access,
            and patching known vulnerabilities, then building
            auto-remediation so common alert types get contained
            automatically instead of waiting on manual response.

          </p>

        </article>

      </div>

    </div>


    <div style="margin-top: 70px;">

      <h2>
        Toolkit
      </h2>

      <p class="portfolio-description">

        Grouped by where each one fits in the stack.

      </p>

      <div style="margin-top: 30px;">

        <h3 style="color: var(--heading); font-size: 1.05rem; margin-bottom: 14px;">
          Detection & SIEM
        </h3>

        <div class="portfolio-tags">

          <span class="portfolio-tag">Wazuh</span>
          <span class="portfolio-tag">Sysmon</span>
          <span class="portfolio-tag">Auditd</span>
          <span class="portfolio-tag">fail2ban</span>
          <span class="portfolio-tag">Auto-Remediation</span>
          <span class="portfolio-tag">Server Hardening</span>

        </div>

      </div>

      <div style="margin-top: 26px;">

        <h3 style="color: var(--heading); font-size: 1.05rem; margin-bottom: 14px;">
          DevSecOps & Pipeline Security
        </h3>

        <div class="portfolio-tags">

          <span class="portfolio-tag">Semgrep</span>
          <span class="portfolio-tag">Trivy</span>
          <span class="portfolio-tag">GitHub Actions</span>
          <span class="portfolio-tag">OWASP ZAP</span>

        </div>

      </div>

      <div style="margin-top: 26px;">

        <h3 style="color: var(--heading); font-size: 1.05rem; margin-bottom: 14px;">
          Network & Cloud
        </h3>

        <div class="portfolio-tags">

          <span class="portfolio-tag">Go</span>
          <span class="portfolio-tag">Network Monitoring</span>
          <span class="portfolio-tag">Cloud Security</span>
          <span class="portfolio-tag">REST APIs</span>

        </div>

      </div>

      <div style="margin-top: 26px;">

        <h3 style="color: var(--heading); font-size: 1.05rem; margin-bottom: 14px;">
          Observability
        </h3>

        <div class="portfolio-tags">

          <span class="portfolio-tag">Dynatrace</span>
          <span class="portfolio-tag">APM</span>
          <span class="portfolio-tag">DQL</span>

        </div>

      </div>

    </div>


    <div style="margin-top: 70px;">

      <h2>
        Standards I Build Against
      </h2>

      <p class="portfolio-description">

        Much of my recent work has meant aligning monitoring and
        controls to <strong>SOC 2 Type II</strong> and
        <strong>ISO 27001:2022</strong>, not as a paperwork
        exercise, but as a forcing function for building the
        visibility and controls that make an environment
        genuinely more defensible.

      </p>

    </div>


    <div style="margin-top: 70px; text-align: center;">

      <h2>
        Have a security problem worth talking through?
      </h2>

      <div class="portfolio-buttons" style="justify-content: center;">

        <a
          class="portfolio-button portfolio-button-primary"
          href="/contact/"
        >
          Get In Touch
        </a>

      </div>

    </div>

  </div>

</section>
