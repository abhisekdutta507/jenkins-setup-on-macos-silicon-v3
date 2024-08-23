## Let's start the setup step by step

#### Clone the Repo (nodejs-worker-threads-and-clusters)

```sh
git clone https://github.com/abhisekdutta507/jenkins-setup-on-macos-silicon-v3.git
```

#### Set a username

```sh
git config user.email email-id@gmail.com
```

### Run Jenkins from MacOS Silicon

#### Go to `/opt/homebrew/bin`

#### Run the command

```sh
./brew shellenv
```

The output you get something like this

```sh
export HOMEBREW_PREFIX="/opt/homebrew";
export HOMEBREW_CELLAR="/opt/homebrew/Cellar";
export HOMEBREW_REPOSITORY="/opt/homebrew";
export PATH="/opt/homebrew/bin:/opt/homebrew/sbin${PATH+:$PATH}";
export MANPATH="/opt/homebrew/share/man${MANPATH+:$MANPATH}:";
export INFOPATH="/opt/homebrew/share/info:${INFOPATH:-}";
```

Copy Paste the above exports on terminal to make `brew` command available on system.

Visit [Jenkins for MacOS](https://www.jenkins.io/download/lts/macos/) to find the installation guide.

#### Install Jenkins on MacOS Silicon. Make sure you **do not** use `sudo` along with `brew`.

```sh
brew install jenkins-lts
```

#### Please be patient untill the installation is completed.

To start Jenkins run:

```sh
brew services start jenkins-lts
```

If you want to run it on foreground you can also run:

```sh
/opt/homebrew/opt/openjdk@17/bin/java -Dmail.smtp.starttls.enable=true -jar /opt/homebrew/opt/jenkins-lts/libexec/jenkins.war --httpListenAddress=127.0.0.1 --httpPort=8080
```

Now open your browser & visit [Unlock Jenkins](http://localhost:8080). The default URL is [http://localhost:8080](http://localhost:8080).

It shows the file path with the Admin password. Print the password on terminal from the file.

```sh
cat filepath
```

Paste the password in the input field. And install the Default setup to get started.

#### You will be prompted to **Create First Admin User**. Please choose the below details for your Jenkins server.

- Username
- Password
- Full Name (optional)
- Email Address (optional)

Make sure you save the credentials somewhere.

#### Now you will be prompted to choose Jenkins URL. You can choose any available URL. For eg.: [http://localhost:5050/](http://localhost:5050/). But Jenkins still opens on [http://localhost:8080](http://localhost:8080).

You can also set up the Jenkins URL later from **Manage Jenkins** > [**System**](http://localhost:8080/manage/configure).

To stop Jenkins:

```sh
brew services stop jenkins-lts
```

To restart Jenkins:

```sh
brew services restart jenkins-lts
```

To upgrade Jenkins:

```sh
brew upgrade jenkins-lts
```

### Host Jenkins app online using NgRok

Put the app online:

```sh
ngrok http http://localhost:8080
```

The result will look similar,

```sh
Session Status                online                                                                            
Account                       Abhisek Dutta (Plan: Free)                                                        
Version                       3.14.0                                                                            
Region                        India (in)                                                                        
Latency                       44ms                                                                              
Web Interface                 http://127.0.0.1:4040                                                             
Forwarding                    https://33b1-45-112-69-99.ngrok-free.app -> http://localhost:8080
```

### Let's setup GitHub Webhooks for Auto Triggers

This section will be updated soon.

#### Add/Modify a Jenkins Webhook

Make sure, the webhook URL must be NgRok's URL.
