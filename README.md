<h1> <a href="#"><b>CLI Environment Customization </b></a></h1>

<div style="background-color: #1e1e1e; padding: 15px; border-radius: 5px; border-left: 5px solid #007acc;">
  <strong>Tool's Used:</strong>
  <ul>
    <li><b> <a href="https://github.com/ohmyzsh/ohmyzsh"> Oh My Zsh</li>
    <li><b> <a href="https://github.com/romkatv/powerlevel10k">PoweLevel10k</li>
  </ul>
</div>

<h2>1. Project Objective & Principles</h2>

The objective of this project was to optimize the Human-Machine Interface (HMI) for a headless Linux environment. While remote access is the primary method of administration, local console efficiency is critical for system maintenance and troubleshooting.

<ul>
  <li><b>System Observability:</b> Migrated from a standard static shell to a dynamic environment to provide real-time telemetry, such as command exit codes and system context.</li>
  <li><b>Workflow Efficiency:</b> Integrated advanced shell features to reduce command latency and improve text manipulation within a text-only TTY.</li>
</ul>

<h2>2. Shell Architecture & Environment</h2>

<ul>
  <li><b>Primary Shell:</b> Zsh (Z Shell).
    <ul>
      <li><b>Justification:</b> Chosen over standard Bash for its advanced tab-completion, plugin support, and superior handling of environment variables.</li>
    </ul>
  </li>
  <li><b>Framework:</b> Oh My Zsh.
    <ul>
      <li><b>Justification:</b> Utilized as a management framework to streamline the deployment of shell themes and plugins without manual configuration overhead.</li>
    </ul>
  </li>
</ul>

<h2>3. Visual Telemetry (Powerlevel10k)</h2>

To improve local console interaction, the Powerlevel10k theme was configured to provide an informative interface.

<ul>
  <li><b>Configuration Choice:</b> Instant Prompt.
    <ul>
      <li><b>Justification:</b> Ensures the shell prompt appears immediately even if background plugins are still loading, maintaining a responsive user experience.</li>
    </ul>
  </li>
  <li><b>Interface Mapping:</b> Configured the prompt to display command success/failure status and current directory depth, reducing the need for manual status checks.</li>
</ul>

<h2>4. System Interface Enhancements</h2>

<ul>
  <li><b>Local Copy-Paste Utility:</b> Implementation of the GPM daemon was verified to ensure hardware-level cursor support remains functional within the optimized shell.</li>
</ul>

<h2>5. Program Walk-through</h2>

<p align="center">
My Text: <br/>
<img src="My Image"/>
<br />
<br />
My Text:  <br/>
<img src="My Image"/>
<br />
<br />






<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
