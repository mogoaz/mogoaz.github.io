---
layout: portfolio
title: Wazuh Security Monitoring
permalink: /projects/wazuh/
---

<section class="portfolio-section">

  <div class="portfolio-container">

    <span class="portfolio-label">
      Security Engineering
    </span>

    <h2>
      Wazuh Security Monitoring
    </h2>

    <p class="portfolio-description">

      A practical security monitoring initiative focused on
      improving visibility across Windows and Linux systems,
      detecting security events, and strengthening security
      operations.

    </p>


    <div style="margin-top: 40px;">

      <h2>
        The Challenge
      </h2>

      <p class="portfolio-description">

        Before this work, security visibility was fragmented.
        Authentication events, file changes, and vulnerability
        status lived in different places, if they were being
        captured at all. Investigating anything meant piecing
        together logs by hand across multiple systems, which is
        slow exactly when speed matters most.

      </p>

    </div>


    <div class="portfolio-grid">


      <article class="portfolio-card">

        <span class="portfolio-card-number">
          01
        </span>

        <h3>
          Security Monitoring
        </h3>

        <p>

          Centralized security visibility across endpoint and
          infrastructure telemetry.

        </p>

      </article>


      <article class="portfolio-card">

        <span class="portfolio-card-number">
          02
        </span>

        <h3>
          Detection Engineering
        </h3>

        <p>

          Custom security rules and detection logic for
          authentication and security events.

        </p>

      </article>


      <article class="portfolio-card">

        <span class="portfolio-card-number">
          03
        </span>

        <h3>
          Vulnerability Visibility
        </h3>

        <p>

          Security vulnerability monitoring and visibility
          across monitored infrastructure.

        </p>

      </article>


      <article class="portfolio-card">

        <span class="portfolio-card-number">
          04
        </span>

        <h3>
          Auto-Remediation
        </h3>

        <p>

          Actively building automated response workflows that
          act on common alert types without waiting for manual
          triage, cutting the time between detection and
          containment.

        </p>

      </article>

    </div>


    <div style="margin-top: 70px;">

      <h2>
        How It Works
      </h2>

      <p class="portfolio-description">

        Lightweight agents run on monitored Windows and Linux
        endpoints, forwarding authentication events, file
        integrity changes, and system telemetry to a central
        Wazuh manager. Sysmon extends visibility into process and
        network activity on Windows; Auditd does the same on
        Linux. Custom detection rules sit on top of the default
        ruleset to catch patterns specific to the environment:
        repeated failed logins from a single source, unexpected
        process behavior, unauthorized file changes, with alerts
        routed to a monitoring channel for investigation.

      </p>

      <p class="portfolio-description">

        The current phase of this work is closing the loop
        further with auto-remediation, triggering containment
        steps like isolating a host or blocking a source
        automatically for well-understood alert types, so
        response no longer depends entirely on someone being
        available to act on an alert in real time.

      </p>

    </div>


    <div style="margin-top: 70px;">

      <h2>
        Technologies
      </h2>

      <div class="portfolio-tags">

        <span class="portfolio-tag">Wazuh</span>
        <span class="portfolio-tag">Windows</span>
        <span class="portfolio-tag">Linux</span>
        <span class="portfolio-tag">Sysmon</span>
        <span class="portfolio-tag">Auditd</span>
        <span class="portfolio-tag">SIEM</span>
        <span class="portfolio-tag">Security Monitoring</span>
        <span class="portfolio-tag">Detection Engineering</span>
        <span class="portfolio-tag">Auto-Remediation</span>

      </div>

    </div>


    <div style="margin-top: 70px;">

      <h2>
        What I learned
      </h2>

      <p class="portfolio-description">

        This work strengthened my understanding of how endpoint
        telemetry, centralized logging, detection rules,
        vulnerability visibility, and incident investigation
        fit together within a security monitoring program.

      </p>

      <p class="portfolio-description">

        It also taught me that tooling is only half the job. A
        SIEM is only as useful as the rules tuned to your
        environment and the discipline to actually act on what it
        surfaces. Getting from "alerts exist" to "alerts get
        investigated" turned out to be the harder, more valuable
        problem to solve.

      </p>

    </div>

  </div>

</section>
