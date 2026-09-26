# SplitPop

A cute, responsive expense splitter for **one editor**. The group creator enters members and every expense, chooses who paid and which people share it, then shares a printable PDF with the group. No login, API, database, S3, Amplify backend, or AWS account is needed to run it.

## Run locally (Windows PowerShell / VS Code)

1. Extract the ZIP and open its inner **splitpop** folder in VS Code. That folder contains `package.json`.
2. In the VS Code terminal, run:

```powershell
npm.cmd ci
npm.cmd run dev
```

3. Open the URL printed by Vite, normally **http://localhost:5173**. Use localhost on the same computer. On another device, use HTTPS when you deploy.

If the terminal is in the outer extracted folder, first run `cd .\splitpop`. Use `npm.cmd` rather than `npm` when PowerShell blocks `npm.ps1`. To stop the app, press Ctrl+C.

## Your workflow

1. Create a group, add everyone, then add as many expenses as your browser storage can accommodate. Choose a payer and equal or custom shares for each expense.
2. Open **Balances** for net balances and suggested payments.
3. Select **Download PDF** on the group or balances screen. In Chrome/Edge's print dialog select **Save as PDF**, then **Save**. The resulting multipage PDF contains the crew, all expenses (including who paid and every member's share), balances, and the suggested payments. Send that PDF to the group for review.
4. Add more expenses and generate a new PDF whenever the numbers change. Old PDFs do not update themselves.
5. On **Groups**, choose **Export backup** to download a JSON backup. **Import backup** restores it on another computer or after browser storage is cleared. Take backups regularly.

The editable data is saved in **this browser's localStorage**. It does not sync to other devices, does not need a group code, and is not committed to GitHub. The PDFs are read-only copies. Anyone with access to this browser profile can edit its data; do not treat the Group tab as a secure login. Browser storage has a finite quota, so export backups for important groups.

## Deploy on AWS Amplify Hosting

Push the **contents of the inner splitpop folder** to a GitHub repository. In Amplify Hosting connect that repository and select your branch. The included `amplify.yml` runs `npm ci` and `npm run build` and publishes `dist`. Select standard static frontend hosting. There is no Amplify backend to deploy, no AWS sandbox, and no environment variables.

Data you entered on localhost remains on localhost; the deployed domain starts empty. Export a backup locally and import it on the hosted site if you want to transfer your groups. Each device/browser has its own data.

## Local build check

```powershell
npm.cmd run build
```
