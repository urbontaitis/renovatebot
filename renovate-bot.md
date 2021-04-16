---
title: Renovate bot demo
description: Do you have a lot of projects? And you don't have time to track which dependencies are outdated or have vulnerabilities? Renovate bot can help you, and this talk will show how to configure and adapt to your needs.
marp: true
html: true
theme: gaia
url: https://www.urbontaitis.lt/renovatebot

---

<!-- Global style -->
<style>
:root {
    color: #FFFFFF;
    font-family: 'Pebble CAPS', serif !important;
    background: #fff url("https://raw.githubusercontent.com/urbontaitis/renovatebot/main/images/background.png") no-repeat center center;
    background-size: cover;
}

h1 {
    text-align: right
}

h4 {
    padding-bottom: 250px
}
h6 {      
    text-align: center;
}
</style>

# Renovate bot demo - keep your dependencies up to date

####
###### By Mindaugas Urbontaitis

###### 2021-04-16

---

![bg left:30% w:90% vertical](https://raw.githubusercontent.com/urbontaitis/renovatebot/main/images/me.jpg)
![bg left:30% w:90% vertical](https://raw.githubusercontent.com/urbontaitis/renovatebot/main/images/pbp-2019.png)
![bg left:30% w:90% vertical](https://raw.githubusercontent.com/urbontaitis/renovatebot/main/images/ig.png)

# Hello 👋

* Software Engineer
    * Digital Channels Sweden
    * 🚀 🦝 Team    

* Outdoor activities
  * My biggest 🚴‍♂️ achievement [Paris - Brest - Paris 2019](https://www.strava.com/activities/2674219873)
  * My 📸 [365 days](https://wwww.instagram.com/murbo_) challenge

---

# Renovate bot demo

- Why do we need automated dependency management?
- Automated dependency management tools
- What is Renovate bot?
- Configuring Renovate bot
- Checking and merging the Pull Requests

---

# Why do we need automated dependency management?

 - A lot of dependencies per project
 - Time-consuming to check every dependency
 - Security updates
 
---

# Snyk report 2020 <!-- fit -->

![bg right:45% w:95%](https://raw.githubusercontent.com/urbontaitis/renovatebot/main/images/snyk-vulnerability-trends.png)

- 🥇 maven
- 🥈 npm

<!-- _footer: "Source [Snyk Vulnerability trends 2020](https://go.snyk.io/rs/677-THP-415/images/State%20Of%20Open%20Source%20Security%20Report%202020.pdf)" -->

---

# Automated dependency management tools <!-- fit -->

- Dependabot [^1]  
  - Github
- Renovatebot [^2]
  - Bitbucket (beta)
  - Github App
  - Gitlab App


 
 [^1]: https://github.blog/2020-06-01-keep-all-your-packages-up-to-date-with-dependabot/
 [^2]: https://www.whitesourcesoftware.com/free-developer-tools/renovate
---

# Renovate 🤖

- cli
- selfhosted
- GitHub App / Azure DevOps Ext. [^3]
- Supports different managers
  - maven
  - npm
  - helm
  - docker

[^3]: https://www.whitesourcesoftware.com/free-developer-tools/bolt
---

# How Renovate 🤖 works

- 🤖 checks for updates
- 🤖 opens pull requests
- 👩‍💻 review and merge
---

# Demo - onboarding renovate 🤖 <!-- fit -->

```json
"onboardingConfig": {        
    "packageRules": [
        {
            "packagePatterns": ["*"],
            "updateTypes": ["patch", "minor"],
            "groupName": "non-major",
            "groupSlug": "non-major-dependencies"
        },        
        {
            "managers": ["maven", "npm"],
            "registryUrls": ["https://artifactory.custom.com/releases"]
        }
    ]
}
```

---

# Demo - managers

```json
"packageRules": [
    {
            "managers": [
              "maven",
              "npm"
            ]
    }
]
```

---

# Demo - Package patterns

```json
"packageRules": [
          {
            "packagePatterns": [
              "*"
            ],
            "updateTypes": [
              "patch",
              "minor"
            ],
            "groupName": "non-major",
            "groupSlug": "non-major-dependencies"
          }
]
```

---

# Demo - Allowed versions

```json
"packageRules": [
    {
      "groupName": "spring-boot",
      "matchDatasources": "maven",
      "matchPackageNames": [
        "org.springframework.boot:spring-boot-starter-parent"
      ],
      "allowedVersions": "<2.4.0"
    }
  ]
```
---

# Wrap up

- Pin your frontend dependencies
- Group your dependencies 
- Limit 🤖 PR commit count
- Start one by one project
---

# Questions❓

---

![bg right:25% w:70%](https://raw.githubusercontent.com/urbontaitis/renovatebot/main/images/ppt-qr.png)
# Thanks 🙏

* Renovate docs [^4]
* Preset group examples [^5]
* Presentation [^6] ``` https://www.urbontaitis.lt/renovatebot ```

[^4]: https://docs.renovatebot.com/configuration-options/
[^5]: https://docs.renovatebot.com/presets-group/
[^6]: https://www.urbontaitis.lt/renovatebot
