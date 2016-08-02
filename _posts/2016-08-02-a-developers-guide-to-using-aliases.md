---
layout: post
title: A developer's approach to using aliases
description: "In this post, I am presenting how I am using bash aliases to make my everyday developer life easier"
author: ama
permalink: /ama/a-developers-guide-to-using-aliases/
published: false
categories: [dev tools]
tags: [linux shell, alias, dev tools]
---

Not long time ago I have rediscovered an old friend - alias. We got acquainted in the beginning of my computer science studies, when I went to course held by Cisco "Linux Essentials" or something similar, where the trainer mentioned at one
point what were aliases and how handy they could be. Well 12 years or so fast forward, and I still did not get that,
until recently where a moment of illumination struck me and since then I've been using them extensively in my everyday developer life. 

So what are aliases? According to The Linux Documentation Project [http://tldp.org/LDP/abs/html/aliases.html] - "A Bash alias is essentially nothing more than a keyboard shortcut, an abbreviation, a means of avoiding typing a long command sequence." 

!!!! Alphabetically ordered !!!! -  a good idea, or should be more category relevant

But first things first, let's set an alias for alias

```
#alias
alias alias-source="source ~/.bash_profile"
alias alias-vim="vim ~/.bash_aliases"
alias alias-grep="alias | grep"
```

```
#ls -- list directory contents
alias ls="ls -CF" # make ls display in columns and with a file type indicator by default("/")
alias ll="ls -l" # -l list in long format
alias llrt="ls -lrt" # list in long format, in reverse order of modification time (I find it easier to see last modified items at the end) 

alias ..="cd .."
```

```
#cd -- change directory
alias ..="cd .."
alias cd..="cd .."
alias cd-projects="cd /Users/ama/projects/"
alias cd-jboss-eap-6.1-logs="cd ~/dev/as/jboss-eap-6.1/standalone/logs
```

> `cd` alone will change to the user's home directory

#df -- display free disk space

```
alias df="df -h" # "human-readable" output
```

```
#maven
alias mci="mvn clean install"
alias mcp="mvn clean package"
alias mcis="mvn clean install -DskipTests"
```

```
#jekyll
alias jekyll-serve-dev="bundle exec jekyll serve --config _config.yml,_config.dev.yml"
```

```
#keycloak 2.0
alias kc2-cd-home="cd ~/dev/as/jboss-eap-7.0-keycloak-server/"
alias kc2-export-JBOSS_HOME="export JBOSS_HOME=~/dev/as/jboss-eap-7.0-keycloak-server/"
alias kc2-vim-standalone.xml="vim ~/dev/as/jboss-eap-7.0-keycloak-server/standalone/configuration/standalone.xml"
alias kc2-start="~/dev/as/jboss-eap-7.0-keycloak-server/bin/standalone.sh -Djboss.socket.binding.port-offset=200 -Djdk.tls.client.protocols=TLSv1 -b 0.0.0.0 --server-config=standalone.xml"
```

```
#mkdir -- make directory
alias mkdir="mkdir -pv" # make necessary parent directory, and make it verbose to help avoid typos
```

```
#ps -- process status
alias ps-grep="ps aux | grep" # e.g."ps-grep java" will list processes that have java in description
```

```
#rhc -- OpenShift client tools
alias rhc-tail-jbosseap.log="rhc tail -o "-n100" -f app-root/logs/jbosseap.log -a heappbackendlarge -n bkwtest"
alias rhc-tail-homeenergy.log="rhc tail -o "-n100" -f app-root/logs/homeenergy.log -a heappbackendlarge -n bkwtest"
alias rhc-ssh-heappbackendlarge="rhc ssh -a heappbackendlarge -n bkwtest"
alias rhc-port-forward-heappbackendlarge="rhc port-forward -a heappbackendlarge -n bkwtest"
```
> here you can truly see how powerful and time saving aliases can be...

```
# Tomcat
alias tomcat-start="/opt/tomcat/bin/startup.sh"
alias tomcat-stop="/opt/tomcat/bin/shutdown.sh"
alias tomcat-status="sudo ps aux | grep tomcat"
alias tomcat-cd-webapps="cd /opt/tomcat/webapps"
alias tomcat-copy-root-to-apps="sudo cp $HOME/projects/podcastpedia/web-ui/target/ROOT.war /opt/tomcat/webapps"
alias tomcat-show-log="tail -f /opt/tomcat/logs/catalina.out"
alias tomcat-backup="cp /opt/tomcat/webapps/ROOT.war \"$HOME/podcastpedia/ROOT.war.backup.$(date +%F_%R)\""
alias tomcat-remove-root="rm -rf /opt/tomcat/webapps/ROOT*"
```


I hope I convinced you to use more the aliases feature...
