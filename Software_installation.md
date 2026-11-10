# Module 3: Software Installation (Windows, macOS, and Linux)

We will install five programs: **Visual Studio Code, R, Git, GitHub Desktop, and LaTeX**. I imagine you already have R; please ignore its instructions. (Linux users can use VS Code or RStudio instead of GitHub Desktop.)

We will also add three extensions inside VS Code, including **Codex**. If you already have R, skip its installation, but complete the R package steps below.

**Follow the steps in order.** The installation commands differ by operating system; the setup steps afterward are almost the same for everyone.

## 1. Create your accounts

1. Create a GitHub account at [github.com/signup](https://github.com/signup). Use your university email if possible, and choose a professional username.
2. We need a 20$ ChatGPT subscription to use Codex in VSCode. Sign up at [chatgpt.com](https://chatgpt.com).

## 2. Install the programs

There are two ways. The **fast way** is straightforward and quick. You can always fallback to manual if something does not work. Choose the fast method for your operating system; afterward, we will work inside R and VS Code.

### Fast way: Windows (PowerShell)

Click **Start**, type `PowerShell`, and open **Windows PowerShell**. Paste the following lines **one at a time**:

```powershell
winget install --id Microsoft.VisualStudioCode -e
winget install --id RProject.R -e
winget install --id Git.Git -e
winget install --id GitHub.GitHubDesktop -e
```

To uninstall these software quickly, change `install` to `uninstall` in the above code.

If a program is already installed, you can skip its line. If `winget` is unavailable or an installation fails, use the manual method below.

### Fast way: macOS (Terminal)

*(I haven't verify this way, as I don't have Mac in my machine.)*

Press **Command + Space**, type `Terminal`, and open **Terminal**.

If you have not installed Homebrew, install it first:

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

Follow Homebrew's on-screen instructions, including any steps to add `brew` to your PATH. Then run the following lines **one at a time**:

```bash
brew install --cask visual-studio-code
brew install --cask r-app
brew install git
brew install --cask github
```

If you already have Homebrew, skip its installation command. See the [Homebrew website](https://brew.sh/) if `brew` is not recognized.

### Fast way: Linux (Ubuntu/Debian)

*(In case someone uses Linux like me.)*

Press **Ctrl + Alt + T** to open **Terminal**. Paste the following lines **one at a time**:

```bash
sudo apt update
sudo apt install -y r-base
sudo apt install -y git
sudo apt install -y code
```

**If `apt` cannot find `code`:** Download the Linux **`.deb`** file from [VS Code](https://code.visualstudio.com/download) and install it through your graphical software installer. The official package can also add Microsoft's `apt` repository for updates.

**Note:** GitHub Desktop is not officially available for Linux. You can use R or VScode for that purpose. I use Rstudio in my projects. In practice, use the **Git panel in RStudio** or **Source Control in VS Code** to clone, commit, and push changes. No Flatpak installation is needed.

These Linux commands are for Ubuntu/Debian-based systems. Other distributions use different package managers.

### Manual way: download the installers

If the fast method fails, download the software from its official website and follow the installer instructions:

1. **VS Code:** [code.visualstudio.com/download](https://code.visualstudio.com/download) — select your operating system.
2. **R:** [cran.r-project.org](https://cran.r-project.org/) — select your operating system. (Ubuntu/Debian users can install `r-base` with `apt` instead.)
3. **Git:** [git-scm.com/downloads](https://git-scm.com/downloads) — select your operating system.
4. **GitHub Desktop (Windows/macOS only):** [desktop.github.com](https://desktop.github.com/).

### Check

Open **VS Code** and **R** (or RStudio, if that is how you normally use R). On Windows/macOS, also open **GitHub Desktop**. If the applications open, their installation is likely complete.

To check Git, open **VS Code → Terminal → New Terminal** and run:

```bash
git --version
```

It should print a Git version number. If the command is not recognized, close and reopen VS Code, then try again.

## 3. Set up Git and connect to GitHub

We will configure Git once inside VS Code, regardless of operating system.

1. Open **VS Code → Terminal → New Terminal**.
2. Paste the following lines, replacing the examples with your own name and the email address you want attached to commits:

   ```bash
   git config --global user.name "First Last"
   git config --global user.email "you@university.edu"
   ```

3. To sign in to GitHub from VS Code, use the **Accounts** icon and select **Sign in with GitHub**, if available, or sign in when prompted during the final test.

**Windows/macOS users:** You can also open GitHub Desktop and sign in to GitHub.com through its **Accounts** settings. GitHub Desktop and VS Code both let you work with Git. GitHub Desktop shows changes, commits, and pushes as buttons. Use whichever you prefer.

**Note:** Your Git commit email can be public. If you prefer privacy, use a GitHub-provided `noreply` address from your GitHub email settings.

## 4. Install R packages and LaTeX inside R

Open **R** or **RStudio**, whichever you use. Paste the following commands into the **R Console**, **one at a time**:

```r
install.packages(c("languageserver", "tinytex", "tidyverse",
                   "fixest", "modelsummary"))
tinytex::install_tinytex()
```

The first command installs R packages. The second installs **TinyTeX**, a LaTeX distribution. Installation may take several minutes. If R asks to create a personal library, choose **Yes**. If R asks you to select a CRAN mirror, choose a nearby one or a cloud mirror.

**Check:** Restart R (or RStudio), then run:

```r
tinytex::is_tinytex()
```

It should print `TRUE`.

## 5. Install VS Code extensions inside VS Code

Open **VS Code**. Click the **Extensions** icon on the left sidebar (the icon looks like four blocks). You can also open it from **View → Extensions**.

Search for each of the following, confirm the publisher, and click **Install**:

1. **R** — published by **REditorSupport** (`REditorSupport.r`).
2. **LaTeX Workshop** — published by **James Yu** (`James-Yu.latex-workshop`).
3. **Codex** — published by **OpenAI** (`openai.chatgpt`).

**Sign in to Codex:** Click the Codex icon in the sidebar, choose **Sign in with ChatGPT**, and approve the sign-in in your browser. If the icon is hidden, open **View → Command Palette**, search for **Codex: Open Codex Sidebar**, and select it.

**Check:** Type `Say hello` in Codex. You should receive a response. The extension may ask you to open a project folder first.

## 6. Final test (same workflow on all systems)

**Before you begin:** You will clone a repository. 

1. In **VS Code**, open **Source Control** (branch icon on the left), then click **Clone Repository**.
2. Paste the template repository URL and choose a folder on your computer:

   ```text
   https://template_project](https://github.com/manab-prakash/template_project)
   ```

3. When asked, choose **Open** to open the cloned repository in VS Code.
4. Open `code/hello.R`. From **View → Command Palette**, run **R: Create R terminal**. With the `.R` file active, press **Ctrl + Shift + S** to run the whole file using the R extension. If that shortcut does not work, select the code and press **Ctrl + Enter** to send it to the R terminal. Confirm that the output appears.
5. Open `paper/hello.tex`. In the **TeX** panel, choose **Build LaTeX project** and then **View LaTeX PDF**. Confirm that a PDF is generated. (The default build shortcut is `Ctrl + Alt + B`, but the buttons are easier to find across systems.)
6. Add your name to the place specified by your instructor (for example, a line at the bottom of `README.md`) and save the file.
7. Open **Source Control** in VS Code. Review the change, click the **+** next to the file to stage it, type a commit message (for example, `Complete installation test`), and click **Commit**.
8. Click **Sync Changes** or **Push** to upload the commit to GitHub. Sign in through your browser if asked.

**You are done when you can see your commit on the GitHub website.**

**Windows/macOS alternative:** If you prefer, you can use GitHub Desktop for the cloning, commit, and push steps instead of VS Code's Source Control panel.

## 7. If something fails

### A program or Git is not recognized

Close VS Code and any open terminal windows, then reopen them. If necessary, install the missing program using the manual method in Section 2.

### VS Code cannot find R

Open R (or RStudio) and run:

```r
R.home("bin")
```

In VS Code, open **Settings** and search for the appropriate R executable setting (for example, `r.rterm.windows` on Windows). Configure the path to the R executable for your system, then restart VS Code.

### R packages will not install

Retry the installation from inside R or RStudio. On Linux, some packages may need additional system development libraries; read the error message to see which dependency is missing.

### TinyTeX is installed but LaTeX cannot build

First, close and reopen VS Code so that it detects the new LaTeX installation. Check `tinytex::is_tinytex()` in R. If a `.sty` file is missing, open R from the repository folder and run:

```r
tinytex::pdflatex("paper/hello.tex")
```

TinyTeX can automatically install missing LaTeX packages. Then try **Build LaTeX project** again in VS Code.

### LaTeX will not install

For today's class, you can use [Overleaf](https://www.overleaf.com/) and fix your local installation later.

### Codex is blank or will not sign in

Restart VS Code. If it still fails, open **Extensions**, search for **Codex** (publisher: OpenAI), and choose **Uninstall**, then **Install**. Sign in again.


