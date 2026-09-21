---
layout: portfolio
title: Security Pipeline Scanner
permalink: /projects/pipeline-security/
---

<section class="portfolio-section">

  <div class="portfolio-container">

    <span class="portfolio-label">
      DevSecOps
    </span>

    <h2>
      Security Pipeline Scanner
    </h2>

    <p class="portfolio-description">

      A security engineering project focused on introducing
      automated security checks directly into the software
      delivery lifecycle, currently being integrated into the
      CI/CD pipeline so scans run as a normal part of every build,
      not as a separate manual step.

    </p>


    <div style="margin-top: 40px;">

      <h2>
        The Challenge
      </h2>

      <p class="portfolio-description">

        Security issues in code, dependencies, and container
        images were traditionally caught late, sometimes after
        deployment, simply because security review wasn't part
        of the everyday delivery workflow. By the time an issue
        surfaced, it was already more expensive to fix.

      </p>

    </div>


    <div class="portfolio-grid">

      <article class="portfolio-card">

        <span class="portfolio-card-number">
          01
        </span>

        <h3>
          Source Code Analysis
        </h3>

        <p>
          Automated analysis designed to identify potentially
          insecure patterns in application source code.
        </p>

      </article>


      <article class="portfolio-card">

        <span class="portfolio-card-number">
          02
        </span>

        <h3>
          Vulnerability Scanning
        </h3>

        <p>
          Automated scanning for vulnerabilities in application
          and infrastructure dependencies.
        </p>

      </article>


      <article class="portfolio-card">

        <span class="portfolio-card-number">
          03
        </span>

        <h3>
          Container Security
        </h3>

        <p>
          Security scanning of container images before deployment.
        </p>

      </article>

    </div>


    <div style="margin-top: 70px;">

      <h2>
        How It Works
      </h2>

      <p class="portfolio-description">

        Static analysis scans source code changes for insecure
        patterns on every push. Dependency scanning checks
        project dependencies against known vulnerability
        databases before they ship. Container images are scanned
        for known CVEs in base images and installed packages
        before deployment. Findings surface directly inside the
        CI/CD pipeline, so they're visible before code ships,
        not after.

      </p>

    </div>


    <div style="margin-top: 70px;">

      <h2>
        Technology
      </h2>

      <div class="portfolio-tags">

        <span class="portfolio-tag">Semgrep</span>
        <span class="portfolio-tag">Trivy</span>
        <span class="portfolio-tag">CI/CD</span>
        <span class="portfolio-tag">DevSecOps</span>
        <span class="portfolio-tag">SAST</span>
        <span class="portfolio-tag">Container Security</span>

      </div>

    </div>


    <div style="margin-top: 70px;">

      <h2>
        What I learned
      </h2>

      <p class="portfolio-description">

        Wiring security scanning into CI/CD is the easy part.
        The harder part is tuning it. A scanner that floods
        developers with low-value findings gets ignored, and one
        that's too quiet gives false confidence. Getting the
        signal-to-noise ratio right, and getting findings in
        front of the right person at the right stage, mattered
        more than any single tool choice.

      </p>

    </div>

  </div>

</section>
