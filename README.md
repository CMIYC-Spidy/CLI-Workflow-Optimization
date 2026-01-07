<h1 align="center"> <b>CLI Workflow Optimization </b></h1>

<div style="background-color: #1e1e1e; padding: 15px; border-radius: 5px; border-left: 5px solid #007acc;">
  <strong>Tools Used:</strong>
  <ul>
    <li><b> <a href="https://github.com/ohmyzsh/ohmyzsh"> Oh My Zsh</a></b></li>
    <li><b> <a href="https://github.com/romkatv/powerlevel10k">PowerLevel10k</a></b></li>
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

- In this section, I am walking through each step of the installation and optimization process. Since this environment lacks mouse support at the initial stage, I utilized a keyboard-driven workflow, relying on the tab and arrow keys to navigate the interface.
<br />
<h2 align="center"> Phase 1: The Standard User</h2>

<br />
<p align="center">
I initiated the process by synchronizing the system's package repository mirrors via <code>sudo apt update -y</code>. <br/>
<br />
<img width="95%" height="95%" alt="1" src="https://github.com/user-attachments/assets/5fcc224b-915c-48f4-aa78-8dba7cec363c" />
<br />
<br />
Following the successful mirror synchronization, I initiated the customization phase. Instead of executing multiple separate commands, I utilized a single automated string to install and configure the entire environment with maximum efficiency:

```bash
sudo apt install -y zsh git curl wget && sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)" "" --unattended && git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k && git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions && git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting && sed -i 's/ZSH_THEME="robbyrussell"/ZSH_THEME="powerlevel10k\/powerlevel10k"/' ~/.zshrc && sed -i 's/plugins=(git)/plugins=(git zsh-autosuggestions zsh-syntax-highlighting)/' ~/.zshrc && echo 'export LS_COLORS="rs=0:di=01;34:ln=01;36:mh=00:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:mi=00:su=37;41:sg=30;43:ca=30;41:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.zip=01;31:*.gz=01;31:*.7z=01;31:*.jpg=01;35:*.png=01;35:*.mp3=01;35"' >> ~/.zshrc && echo "alias ls='ls --color=auto'" >> ~/.zshrc && echo "alias grep='grep --color=auto'" >> ~/.zshrc && sudo chsh -s $(which zsh) $USER && zsh
```
</p>
<p align="center">
<br />
<img width="95%" height="95%" alt="2" src="https://github.com/user-attachments/assets/243cc161-075b-42ea-ad31-746ae79e7c21" />
<br />
<br />
Upon execution, the script initiated the retrieval and initialization of necessary packages. This process was completed in approximately 10 seconds, contingent on network bandwidth and local hardware performance. <br/>
<br />
<img width="95%" height="95%" alt="3" src="https://github.com/user-attachments/assets/ae36e5ad-79b1-4b98-b127-8c4de231f091" />
<br />
<br />
Following the core installation, I moved into the interactive configuration phase. I primarily opted for the recommended default settings to establish a clean, industry-standard baseline while tailoring specific telemetry to my personal workflow preferences. <br/>
<br />
<img width="95%" height="95%" alt="4" src="https://github.com/user-attachments/assets/a6d33b08-9c34-4a20-b8c5-82468ea5ed8f" />
<br />
<br />
Once all interactive parameters were finalized, the environment optimization was successfully completed, establishing a fully provisioned, high-performance CLI. <br/>
<br />
<img width="95%" height="95%" alt="5" src="https://github.com/user-attachments/assets/95ebac13-54b3-4eff-a6c2-425ed331cbff" />
<br />
<br />
The environment now leverages persistent command history and real-time syntax highlighting. This provides immediate visual validation of command accuracy and accelerates productivity through intelligent autosuggestions. <br/>
<br />
<img width="95%" height="95%" alt="6" src="https://github.com/user-attachments/assets/a7eb343b-5f79-46d9-8b7c-df39f82be0cd" />
<br />
<br />
Recognizing that the superuser (root) environment remained in its default state, I initiated a privilege escalation to synchronize the high-performance configuration across all administrative profiles. <br/>
<br />
<img width="95%" height="95%" alt="7" src="https://github.com/user-attachments/assets/0372927c-a01f-4dec-8e71-b599d446af70" />
<br />
<br />
<h2 align="center"> Phase 2: The Superuser (root) </h2>
<br />
<p align="center">
Observing that the superuser profile lacked the optimized environment, I re-executed the deployment script to standardize high-performance settings even in the superuser (root) account:

```bash
sudo apt install -y zsh git curl wget && sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)" "" --unattended && git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k && git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions && git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting && sed -i 's/ZSH_THEME="robbyrussell"/ZSH_THEME="powerlevel10k\/powerlevel10k"/' ~/.zshrc && sed -i 's/plugins=(git)/plugins=(git zsh-autosuggestions zsh-syntax-highlighting)/' ~/.zshrc && echo 'export LS_COLORS="rs=0:di=01;34:ln=01;36:mh=00:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:mi=00:su=37;41:sg=30;43:ca=30;41:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.zip=01;31:*.gz=01;31:*.7z=01;31:*.jpg=01;35:*.png=01;35:*.mp3=01;35"' >> ~/.zshrc && echo "alias ls='ls --color=auto'" >> ~/.zshrc && echo "alias grep='grep --color=auto'" >> ~/.zshrc && sudo chsh -s $(which zsh) $USER && zsh
```
</p>
<br />
<img width="95%" height="95%" alt="9" src="https://github.com/user-attachments/assets/81f03ce9-ce4c-491b-939d-a6ff6e0ec5f3" />
<br />
<br />
<p align="center">
I re-navigated the configuration parameters for the superuser, intentionally selecting a distinct visual profile from that of the standard user. This serves as a critical visual cue to indicate elevated privileges, reinforcing the safety protocol of utilizing the root account only for essential administrative operations. <br/>
<br />
<img width="95%" height="95%" alt="10" src="https://github.com/user-attachments/assets/f921da66-1475-49d6-83ce-bf8fbbee6d9f" />
<br />
<br />
With the root user optimization finalized, both the standard and superuser environments are now fully provisioned with high-performance configurations. <br/>
<br />
<img width="95%" height="95%" alt="11" src="https://github.com/user-attachments/assets/c8155e9f-dded-4b12-ad41-4b550ae99163" />
</p>

<h1>6. Final Reflection</h1>

<p>
  I successfully completed this project to demonstrate my ability to engineer a high-performance, responsive command-line environment tailored for maximum efficiency. By integrating advanced shell frameworks and telemetry-driven themes, I have created a workflow that minimizes friction and maximizes observability during critical system administration tasks.
</p>

<p>
  This project reflects my commitment to optimizing every layer of the systems I manage, ensuring that even the most basic interface serves as a powerful tool for troubleshooting and security operations. Thank you for taking the time to review my work.
</p>
