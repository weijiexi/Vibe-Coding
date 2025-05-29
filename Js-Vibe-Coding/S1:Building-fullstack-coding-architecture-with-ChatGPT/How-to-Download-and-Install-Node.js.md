
# How to Download and Install Node.js

This guide walks you through downloading and installing **Node.js** on your system.

## Step 1: Visit the Official Node.js Website

Go to the official website:  
👉 [https://nodejs.org](https://nodejs.org)

You will see two download options:

- **LTS (Long Term Support)** – Recommended for most users.
- **Current** – Latest features but less stable.

> Choose the **LTS version** unless you need the very latest features.

## Step 2: Download for Your Platform

### Windows

1. Click the **Windows Installer (.msi)** under the LTS section.
2. Run the installer and follow the instructions.
3. Ensure the checkbox “Add to PATH” is selected during setup.

### macOS

1. Click the **macOS Installer (.pkg)** under the LTS section.
2. Open the `.pkg` file and follow the installation steps.

### Linux

Use a package manager:

#### Debian/Ubuntu

```bash
curl -fsSL https://deb.nodesource.com/setup_lts.x | sudo -E bash -
sudo apt-get install -y nodejs
```

#### RedHat/Fedora

```bash
curl -fsSL https://rpm.nodesource.com/setup_lts.x | sudo bash -
sudo yum install -y nodejs
```


## Step 3: Verify Installation

After installation, open your terminal or command prompt and type:

```bash
node -v
```

You should see the Node.js version printed.

Also verify `npm` (Node Package Manager):

```bash
npm -v
```


## You’re Ready to Use Node.js!

You can now create JavaScript apps, install libraries using `npm`, and build full-stack projects using Node.js.

For example, to create a new Node.js project:

```bash
mkdir my-app
cd my-app
npm init -y
```

## Helpful Links

- [Node.js Official Downloads](https://nodejs.org/en/download)
- [Node.js Docs](https://nodejs.org/en/docs/)
- [NPM Docs](https://docs.npmjs.com/)
