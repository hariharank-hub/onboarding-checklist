---
# 🎉 Onboarding Checklist
Welcome to the team! Use this checklist to track your onboarding journey. Tick each item as you complete it.

---
## 🗓️ Week 0 – Before Joining
- [ ] ✅ Complete HR formalities
- [ ] 💻 Receive and set up laptop
- [ ] 📘 Review [Amex Onboarding Guide]

---

# 🥇 First Day Onboarding
## 🔗 Access Requests (via IIQ)
Please raise IIQ requests for the following groups:

- [ ] 🔑 GG-ADS-Resy-Github-Engineering
- [ ] 📘 GG-AXP-Resy-Atlassian-AEXP
- [ ] 📘 GG-AXP-Resy-Atlassian-Engineering
- [ ] 📊 GG-AXP-Resy-Datadog-StandardRole
- [ ] ⚪️ GG-ADS-ResyGitHub-Eng (Active Directory - Network)
- [ ] 🤖 GG-GITHUB-COPILOTS (Active Directory - Network)
- [ ] 🔵 PRC-AXP-AA-E1-AppAdmin-RESY-BLUEADMIN-TRIPLEA-ENG
- [ ] 🔵 PRC-AXP-AA-E2-AppAdmin-RESY-BLUEADMIN-TRIPLEA-ENG
- [ ] 🗺️ GG-Resy-Atlas-User (Active Directory - Network)
- [ ] ☁️ PRC-AXP-AA-E3-AppAdmin-Resy-Staging-AWS-FullAccess

:arrow_right: Use [IIQ](https://iiq.company.internal) to raise these requests. Reach out to your buddy if unsure.

---

## :octopus: GitHub Access Setup
### :wrench: Resy GitHub

- [ ] :white_check_mark: After being granted `GG-ADS-Resy-Github-Engineering`, go to `#resy-eng-infra` on Slack Submit a workflow request and provide your *public GitHub username
- [ ] :link: To get access to Resy GitHub Organization  [https://github.com/resy](https://github.com/resy)

prerequisite: You need a Github.com account (create one with your aexp if you do not want to use your personal one)

Request access to the resy  workspace via the "Resy Devops Request" workflow on "resy-eng-infra" slack channel

After you get an invite, you will need to accept the request on GH. You should get a notification from Gh to complete this.

---

### :classical_building: Amex GitHub
- [ ] :speech_balloon: Open Slack and message **Infrabot**: 
  Type: Github Access
- [ ] :id: Provide your **ADS ID** when prompted
- [ ] :closed_lock_with_key: Sign in via **SSO** to Amex GitHub: [https://github.aexp.com](https://github.aexp.com)

---

## :large_blue_diamond: BlueAdmin Access (SSO)
Once you are granted the required IIQ groups, use SSO to log in to the following BlueAdmin instances:

- [ ] :repeat: Access **Staging (E1)**: [BlueAdmin Staging](https://admin.staging.resy.com/2/os/resy-admin/login/?next=/2/os/resy-admin/)
- [ ] :dart: Access **Demo (E2)**: [BlueAdmin Demo](https://admin.demo.resy.com/2/os/resy-admin/login/?next=/2/os/resy-admin/)
- [ ] :rocket: Access **Production (E3)**: [BlueAdmin Prod](https://admin.resy.com/2/os/resy-admin/login/?next=/2/os/resy-admin/)

---

## :speech_balloon: Slack Channels to Join
Make sure to join these Slack channels:

- [ ] :hammer_and_wrench: `#resy-sre` – Team channel (private, request an invite)
- [ ] :question: `#resy-irl-ask` – General engineering questions
- [ ] :barely_sunny: `#resy-env-nonprod-status` – Staging environment updates
- [ ] :fire: `#resy-env-production-outages` – Production incident alerts
- [ ] :bricks: `#resy-eng-infra` – Infra requests and support
- [ ] :rotating_light: `#resy-eng-incident` – Incident management
- [ ] :computer: `#resy-eng-dev` – Dev discussions and engineering updates
- [ ] :mega: `#resy-alerts` – System and service alerts

---

## :busts_in_silhouette: Distribution Groups
Make sure you are added to the following email distribution groups:

- [ ] :e-mail: Join the `ResySRE` distribution group – Ask a team member to add you

---

## :blue_book: Resy-Specific Onboarding Docs
Familiarize yourself with the following documentation when you have downtime:

- [ ] :brain: [Generic "Core" Onboarding](https://resy.atlassian.net/wiki/spaces/EN/pages/1916633089/Core+Onboarding)
- [ ] :movie_camera: [ResyOS Bootcamp Videos](https://resy.atlassian.net/wiki/spaces/EN/pages/1916633089/Core+Onboarding#Updated-Bootcamp-Videos-run-by-Emma-Cadd)

---

## :shield: Proxy Setup
To set up the proxy in your terminal:

- [ ] Open your terminal and run:
  ```bash
  echo $SHELL

- [ ] Type
  ```bash
  vi ~/.zshrc
  
- [ ] Paste the below contents in the file
  ```bash
   function load_proxy() {
   echo -n "Enter Username: "
   read username
   echo -n "Enter your Password: "
   read -s password
   encoded_pass=$(python3 -c 'import sys, urllib.parse;     print(urllib.parse.quote_plus(sys.argv[1]))' "${password}")
   url=http://${username}:${encoded_pass}@proxy-newyork.aexp.com:8080
   npm config set https-proxy ${url}
   npm config set proxy ${url}
   export HTTP_PROXY=${url}
   export HTTPS_PROXY=${url}
   export ALL_PROXY=${url}
   export all_proxy=${url}
   export https_proxy=${url}
   unset NODEJS_ORG_MIRROR
   unset NPM_CONFIG_NODEDIR
   unset IBM_DB_INSTALLER_URL
   unset SASS_BINARY_SITE
   unset PHANTOMJS_CDNURL
   npm config delete registry
   }
   function unload_proxy(){
   NODE_VERSION=`node --version`
   npm config set registry="https://ci-repo.aexp.com/nodejs/content/groups/npmint/"
   export NODEJS_ORG_MIRROR=https://ci-repo.aexp.com/repository/nodejs-proxy
   export NPM_CONFIG_NODEDIR="~/.nvm/versions/node/$NODE_VERSION/"
   export IBM_DB_INSTALLER_URL=https://ci-repo.aexp.com/nodejs/content/sites/npm-remotes/content-compressed/
   export SASS_BINARY_SITE=https://ci-repo.aexp.com/nodejs/content/sites/npm-remotes/sass/node-sass/releases/download/
   export PHANTOMJS_CDNURL=https://ci-repo.aexp.com/nodejs/content/sites/npm-remotes/ariya/phantomjs/downloads/
   npm config delete https-proxy
   npm config delete proxy
   export HIPED_CLIENTSECRET_MOCK=NJpZy34XwQRwNnZE31T99I3qzspZ398ZWiixFb9+Y5c=
   export HIPED_CLIENTSECRET_LISA=C5XBKCPGHrtd+wUo+nLNyEyITpqSm+7RBaxaVspe990=
   export GOOGLE_KEY=AIzaSyDzyW_vneQce0cIlUnGMVC_2RafxhsTonc
   export SPLUNK_PASSWORD=VO5xk#66
   export CLIENT_SECRET=C5XBKCPGHrtd+wUo+nLNyEyITpqSm+7RBaxaVspe990=
   }

- [ ] To START the proxy: run the below command in the shell
  ```bash
  load_proxy

- [ ] To STOP the proxy: run the below command in the shell
  ```bash
  unload_proxy

---  

## 🦾 Manage your secrets in Vault using Vault API's Curl (optional)

  At some point in time every individual has to set the secret keys in vault here is the documentation to follow [Manage your secrets using Vault APIs (curl)](https://enterprise-confluence.aexp.com/confluence/pages/viewpage.action?pageId=271621558)

---

## 📚 Additional Resources

These are useful for long-term understanding. Bookmark them and review when time permits:

- [os-web Overview](https://enterprise-confluence.aexp.com/confluence/display/RESY/os-web+Overview)
- [Resy-Notify](https://enterprise-confluence.aexp.com/confluence/display/RESY/Resy+-+Notify)
- [resy-web Overview](https://enterprise-confluence.aexp.com/confluence/display/RESY/resy-web+Overview)
- [Current Monitoring Analysis](https://enterprise-confluence.aexp.com/confluence/display/RESY/Current+Monitoring+Analysis+for+Resy)

---

