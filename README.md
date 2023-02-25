# Jenkins-example

This is just a basic introduction to the CI/CD tool [Jenkins](https://www.jenkins.io/).

CI/CD stands for Continuous Integration and Continuous Deployment which comes under DevOps.

So, whenever we make changes in our code then Jenkins can automatically build and test it. With this it will be helpful to find any kind of bugs of failures in the application.

## Installing Jenkins

Extensive documentation can be found here -> https://www.jenkins.io/doc/book/installing/

### For Linux

For `Debian based` distributions

```
curl -fsSL https://pkg.jenkins.io/debian/jenkins.io.key | sudo tee \
  /usr/share/keyrings/jenkins-keyring.asc > /dev/null
echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
  https://pkg.jenkins.io/debian binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null
sudo apt update
sudo apt install jenkins
```

---

For `Fedora`

```
sudo wget -O /etc/yum.repos.d/jenkins.repo \
    https://pkg.jenkins.io/redhat-stable/jenkins.repo
sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io.key
sudo dnf upgrade
# Add required dependencies for the jenkins package
sudo dnf install java-11-openjdk
sudo dnf install jenkins
```

---

For `Arch based` distributions

```
sudo pacman -Syy jenkins
```

If you are using a non-systemd init system then also install `jenkins-runit` or `jenkins-openrc` , according to your init system.

---

### Start jenkins service

For `systemd`:

     see the official docs (or just google it, systemd is quite famous).

For `Runit`:

    1. create a symlink

        ``` sudo ln -s /etc/sv/jenkins /var/service/jenkins```

        or

        ``` sudo ln -s /etc/runti/sv/jenkins /run/runit/service```

    this should start the jenkins service immediately, if not then 

    2. start the service

        ``` sudo sv up jenkins```

          or

        ```sudo sv start jenkins```

---

### Start jenkins-webapp

1. first get the ip address of your machine

            For linux, run `ifconfig` command, and see the 'inet' line for ip address.

    2. paste this `https://<your_ip>:8080` in the browser.    (the port number can be changed later)

    3. then the webapp starts

    4. cat out following file and paste its contents in the box

            ``` cat /var/lib/jenkins/secrets/initialAdminPassword```

There you Go  :)