# 🚀 Test-for-Jenkins + ngrok Setup Guide

> A beginner-friendly guide to expose your local Jenkins server using ngrok 🌍
> Perfect for webhook testing (GitHub, CI/CD pipelines)

---

## 📌 Tech Stack

* 🍺 Homebrew (macOS package manager)
* 🌐 ngrok (secure tunneling)
* 🤖 Jenkins (automation server)
* 🖥️ macOS Terminal

---

## 🛠️ 1. Install Homebrew

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

Verify:

```bash
brew --version
```

---

## 📦 2. Install ngrok

```bash
brew install ngrok/ngrok/ngrok
```

Check version:

```bash
ngrok version
```

---

## 🔑 3. Setup ngrok Auth Token

1. Create account → https://dashboard.ngrok.com/
2. Copy your token

```bash
ngrok config add-authtoken YOUR_AUTHTOKEN
```

---

## 🤖 4. Install Jenkins

```bash
brew install jenkins-lts
```

Start Jenkins:

```bash
brew services start jenkins-lts
```

Stop Jenkins:

```bash
brew services stop jenkins-lts
```

---

## 🌐 5. Access Jenkins

Open in browser:

```
http://localhost:8080
```

Get initial admin password:

```bash
cat ~/.jenkins/secrets/initialAdminPassword
```

---

## 🚀 6. Expose Jenkins using ngrok

Run:

```bash
ngrok http 8080
```

You will get:

```
https://xxxx.ngrok-free.app
```

👉 Use this URL for:

* GitHub Webhooks
* External access
* CI/CD triggers

---

## 🔗 7. Configure GitHub Webhook

1. Go to your repo → Settings → Webhooks
2. Add webhook:

   * Payload URL: `https://your-ngrok-url/github-webhook/`
   * Content type: `application/json`

---

## ⚙️ 8. Useful Commands

### Restart Jenkins

```bash
brew services restart jenkins-lts
```

### Check running services

```bash
brew services list
```

### ngrok dashboard

```
http://127.0.0.1:4040
```

---

## 🧪 9. Test Workflow

1. Start Jenkins
2. Start ngrok
3. Push code to GitHub
4. Watch Jenkins trigger automatically 🎉

---

## 💡 Tips

* Always keep ngrok running during testing
* Free ngrok URLs change every restart
* Use **ngrok paid plan** for fixed domains

---

## 🧯 Troubleshooting

| Issue               | Fix             |
| ------------------- | --------------- |
| Port already in use | Change port     |
| ngrok not working   | Re-add token    |
| Jenkins not opening | Restart service |

---

* Add Jenkins plugins:

  * GitHub Integration
  * Pipeline
* Use ngrok for:

  * Stripe webhooks
  * Telegram bots
  * API testing

---

## 📬 Contributing

Feel free to fork and improve this repo 💙

---

## 📄 License

MIT License

---

# 🔔 10. Webhook Setup (GitHub → Jenkins via ngrok)

This section connects **GitHub → Jenkins** using **ngrok public URL** so builds trigger automatically on push 🚀

---

## 🌍 Step 1: Start Services

Start Jenkins:

```bash
brew services start jenkins-lts
```

Start ngrok:

```bash
ngrok http 8080
```

👉 Copy your ngrok URL:

```
https://xxxx.ngrok-free.app
```

---

## ⚙️ Step 2: Configure Jenkins

### 1. Install Required Plugins

Go to:

```
Jenkins → Manage Jenkins → Plugins
```

Install:

* GitHub Integration Plugin
* Git Plugin

---

### 2. Create New Job

1. Click **New Item**
2. Enter name → Select **Freestyle Project**
3. Click **OK**

---

### 3. Configure Job

#### Source Code Management:

* Select **Git**
* Add your repository URL

#### Build Triggers:

✔️ Check:

```
GitHub hook trigger for GITScm polling
```

Save the job ✅

---

## 🔗 Step 3: Setup GitHub Webhook

Go to your GitHub repository:

```
Settings → Webhooks → Add Webhook
```

### Fill details:

* **Payload URL:**

```
https://YOUR-NGROK-URL/github-webhook/
```

* **Content type:**

```
application/json
```

* **Events:**
  ✔️ Just the push event

Click:

```
Add Webhook
```

---

## 🧪 Step 4: Test Webhook

Run:

```bash
git add .
git commit -m "test webhook"
git push origin main
```

---

## 🎉  Result

* GitHub sends webhook → ngrok URL
* ngrok forwards → Jenkins (localhost:8080)
* Jenkins job triggers automatically 🚀

---

## 🔍 

### Check ngrok logs:

```
http://127.0.0.1:4040
```

### Check Jenkins logs:

```bash
tail -f /usr/local/var/log/jenkins/jenkins.log
```

---

## ⚠️ Common Issues

| Problem                | Solution                           |
| ---------------------- | ---------------------------------- |
| 404 error              | Check `/github-webhook/` URL       |
| Webhook not triggering | Ensure Jenkins job trigger enabled |
| ngrok URL changed      | Update webhook URL                 |
| Jenkins not accessible | Restart service                    |

---

## 💡 Pro Tips

* Use branch filtering in Jenkins
* Add Jenkinsfile for pipelines
* Secure with GitHub secret token 🔐

---

## 🚀 Workflow Summary

```
GitHub Push → Webhook → ngrok → Jenkins → Build Triggered
```

---

> Made with ❤️ for beginners learning DevOps
>  Now your CI/CD pipeline is LIVE locally using ngrok!
