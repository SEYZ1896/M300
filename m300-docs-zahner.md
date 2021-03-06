---


---

<h1 id="modul-300-dokumentation---lb1">Modul 300 Dokumentation - LB1</h1>
<p>Modulbschreib: Platformübergreifende Services implementieren<br>
Autor: Angel Zahner</p>
<h2 id="toolumgebung-aufsetzen">Toolumgebung Aufsetzen</h2>
<ul>
<li>GitHub registriert mit TBZ-Account</li>
<li>Git-bash installiert; Verzeichnis mit Beispielen erstellt; <a href="https://github.com/mc-b/devops">Git Repo</a> geclont</li>
<li>VirtualBox installiert und manuelle Linux-VM mit apache2 generiert</li>
<li>Vagrant heruntergeladen und installiert</li>
<li>Visual Studio Code installiert und Erweiterungen hinzugefügt</li>
<li>Git-Hub in Betrieb genommen, Markdown-Docs von <a href="http://stackedit.io">stackedit.io</a> gepublished</li>
</ul>
<h2 id="vagrant">Vagrant</h2>
<h3 id="installation">Installation</h3>
<ul>
<li>Vagrant von <a href="https://www.vagrantup.com/downloads.html">hier</a> heruntergeladen</li>
<li>Auf Windows 10 Laptop installiert</li>
</ul>
<h3 id="vm-erstellen-und-benutzen">VM erstellen und benutzen</h3>
<p>Neues Vagrantfile erstellen:</p>
<pre><code>vagrant init ubuntu/xenial64 
</code></pre>
<p>Virtuelle Maschine aus Vagrantfile erstellen:</p>
<pre><code>vagrant up
</code></pre>
<p>Auf VM verbinden:</p>
<pre><code>vagrant ssh
</code></pre>
<h2 id="github">GitHub</h2>
<p>Ich habe ein Repository namens “lamp” erstellt, in das ich nachher mit folgenden Befehlen mein Vagrantfile publishe:</p>
<pre><code>git init #in the dir your file to push is located
git remote add origin https://github.com/zahnera/lamp.git
git add .
git commit -a -m "änderungen"
git push origin master
</code></pre>
<h2 id="eigener-service-implementieren">Eigener Service implementieren</h2>
<p>Ich habe mich für eine LAMP-Installation entschieden.<br>
LAMP steht für:</p>

<table>
<thead>
<tr>
<th>Betriebssystem</th>
<th>Webserver</th>
<th>Datenbank</th>
<th>Programmiersprache</th>
</tr>
</thead>
<tbody>
<tr>
<td>Linux</td>
<td>Apache</td>
<td>MySQL</td>
<td>PHP</td>
</tr>
</tbody>
</table><p>Das heisst es wird automatisch eine Ubuntu 16.04 Maschine mit diesen LAMP-Services installiert.</p>
<h3 id="code">Code</h3>
<p>Auf GitHub unter <a href="https://github.com/zahnera/lamp.git">https://github.com/zahnera/lamp.git</a><br>
<img src="https://perrone.myqnapcloud.com:450/share.cgi/angel-vagrantfile.png?ssid=02YbC2K&amp;fid=02YbC2K&amp;path=/&amp;filename=angel-vagrantfile.png&amp;openfolder=normal&amp;ep=" alt="enter image description here"></p>
<h2 id="testing">Testing</h2>

<table>
<thead>
<tr>
<th>Nr.</th>
<th>Testfall</th>
<th>Erwartetes Ergebnis</th>
<th>Abweichungen</th>
</tr>
</thead>
<tbody>
<tr>
<td>1</td>
<td><code>Vagrant up</code></td>
<td>VM wird aus Vagrantfile erstellt</td>
<td>Keine</td>
</tr>
<tr>
<td>2</td>
<td><code>service apache2 restart</code></td>
<td>apache wird neugestartet</td>
<td>Keine</td>
</tr>
<tr>
<td>3</td>
<td><code>service mysql restart</code></td>
<td>mysql wird neugestartet</td>
<td>Keine</td>
</tr>
<tr>
<td>4</td>
<td><code>localhost:8080/phpmyadmin</code></td>
<td>phpmyadmin login-fenster</td>
<td>Keine</td>
</tr>
<tr>
<td>5</td>
<td><code>localhost:8080/index.html</code></td>
<td>Webseite wird angezeigt</td>
<td>Keine</td>
</tr>
<tr>
<td>6</td>
<td><code>MySQL command "CREATE DATABASE tbz;</code></td>
<td>Datenbank wird erstellt</td>
<td>Keine</td>
</tr>
</tbody>
</table><h3 id="bilder">Bilder</h3>
<h4 id="testcase-2">Testcase 2</h4>
<p><img src="https://perrone.myqnapcloud.com:450/share.cgi/angel-apache2restart.png?ssid=02YbC2K&amp;fid=02YbC2K&amp;path=/&amp;filename=angel-apache2restart.png&amp;openfolder=normal&amp;ep=" alt="Testcase 2"></p>
<h4 id="testcase-3">Testcase 3</h4>
<p><img src="https://perrone.myqnapcloud.com:450/share.cgi/angel-mysqlrestart.png?ssid=02YbC2K&amp;fid=02YbC2K&amp;path=/&amp;filename=angel-mysqlrestart.png&amp;openfolder=normal&amp;ep=" alt="Testcase 3"></p>
<h4 id="testcase-4">Testcase 4</h4>
<p><img src="https://perrone.myqnapcloud.com:450/share.cgi/angel-phpmyadmin.png?ssid=02YbC2K&amp;fid=02YbC2K&amp;path=/&amp;filename=angel-phpmyadmin.png&amp;openfolder=normal&amp;ep=" alt="Testcase 4"></p>
<h4 id="testcase-5">Testcase 5</h4>
<p><img src="https://perrone.myqnapcloud.com:450/share.cgi/angel-webseite.png?ssid=02YbC2K&amp;fid=02YbC2K&amp;path=/&amp;filename=angel-webseite.png&amp;openfolder=normal&amp;ep=" alt="Testcase 5"></p>
<h4 id="testcase-6">Testcase 6</h4>
<p><img src="https://perrone.myqnapcloud.com:450/share.cgi/angel-database.png?ssid=02YbC2K&amp;fid=02YbC2K&amp;path=/&amp;filename=angel-database.png&amp;openfolder=normal&amp;ep=" alt="enter image description here"></p>
<h1 id="modul-300-dokumentation---lb2">Modul 300 Dokumentation - LB2</h1>
<h2 id="docker-installieren">Docker installieren</h2>
<p>Um Docker aufzusetzen, habe ich eine virtuelle Maschine mit <strong>Ubuntu 16.04</strong> in <strong>VirtualBox</strong> erstellt.</p>
<h3 id="repository-aufsetzen">Repository aufsetzen</h3>
<ol>
<li>Update the  <code>apt</code>  package index:<pre><code> sudo apt-get update
</code></pre>
</li>
<li>Install packages to allow  <code>apt</code>  to use a repository over HTTPS:<pre><code> sudo apt-get install
 apt-transport-https
 ca-certificates
 curl
 software-properties-common
</code></pre>
</li>
<li>Add Docker’s official GPG key:<pre><code> curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
</code></pre>
</li>
<li>Setting up the stable repository.<pre><code> sudo add-apt-repository \
 "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
 $(lsb_release -cs)  stable"
</code></pre>
</li>
</ol>
<h4 id="install-docker-ce">Install Docker CE</h4>
<ol>
<li>Update the  <code>apt</code>  package index.<pre><code> sudo apt-get update
</code></pre>
</li>
<li>Install the  <em>latest version</em>  of Docker CE<pre><code> sudo apt-get install docker-ce
</code></pre>
</li>
</ol>
<h2 id="docker-container-erstellen">Docker Container erstellen</h2>
<h3 id="devops-container-erstellen">Devops Container erstellen</h3>
<ol>
<li><code>cd</code> zu Dockerfile Directory bsp. /desktop/devops/docker/apache2</li>
<li>Von Dockerfile Image erstellen<pre><code> docker build -t apache2 .
</code></pre>
</li>
<li>Auf Docker-Container zugreifen<pre><code> docker run -ti apache2 /bin/bash
</code></pre>
</li>
<li>Docker Port ändern<pre><code> docker run -p 123:80 apache2
</code></pre>
</li>
</ol>
<h3 id="container-aus-eigenem-dockerfile-erstellen">Container aus eigenem Dockerfile erstellen</h3>
<p>Das Dockerfile nimmt als Betriebssystem die neuste Version von Alpine Linux mit dem Webserver Nginx installiert. Ich habe Alpine Linux gewählt, da es für Sicherheit, Einfachheit und Ressourceneffizienz sorgt. Mit der zweiten Linie kopiere ich das erstellte index.html in das Webserver-Verzeichnis des Nginx Servers.</p>
<p>Im Docker Ordner folgendes Verzeichnis erstellen</p>
<pre><code>mkdir nginx
</code></pre>
<p>Das benötigte Index.html erstellen und mit Sample-Text beschreiben</p>
<pre><code>nano index.html
</code></pre>
<p>Das Dockerfile erstellen und untenstehender Code einfügen</p>
<pre><code>nano Dockerfile
</code></pre>
<p>Code für Dockerfile:</p>
<pre><code>FROM nginx:alpine
COPY . /usr/share/nginx/html

#Install Firewall
RUN apk add awall
RUN rc-update add iptables
</code></pre>
<p>Firewall manuell aktivieren</p>
<pre><code>sudo rc-service iptables start
</code></pre>
<h4 id="image-erstellen">Image erstellen</h4>
<p>Das Dockerfile ist jetzt fertig und nun müssen wir das Image bauen:</p>
<pre><code>docker build -t nginx:v1 .
</code></pre>
<h4 id="container-starten">Container starten</h4>
<pre><code>docker run -d -p 800:80 nginx:v1
</code></pre>
<p>Dieser Server läuft jetzt auf Port 800</p>
<h4 id="server-aufrufen">Server aufrufen</h4>
<p>Aufrufen der Seite <a href="http://localhost:800">http://localhost:800</a></p>
<p><img src="https://perrone.myqnapcloud.com:450/share.cgi/m300-nginx-angel.png?ssid=02YbC2K&amp;fid=02YbC2K&amp;path=/&amp;filename=m300-nginx-angel.png&amp;openfolder=normal&amp;ep=" alt="enter image description here"></p>
<h4 id="auf-server-verbinden">Auf Server verbinden</h4>
<pre><code>sudo docker exec -i -t Container-ID /bin/ash
</code></pre>
<h4 id="testing-1">Testing</h4>

<table>
<thead>
<tr>
<th>Testbeschreib</th>
<th>Erwartetes Ergebnis</th>
<th>Ergebnis</th>
</tr>
</thead>
<tbody>
<tr>
<td>Docker build</td>
<td>Image wird erstellt</td>
<td>Image wird erstellt</td>
</tr>
<tr>
<td>Docker run</td>
<td>Startet Container</td>
<td>Container läuft</td>
</tr>
<tr>
<td>Docker exec</td>
<td>Verbindet auf Container</td>
<td>Verbindet auf Container</td>
</tr>
<tr>
<td>Port Forwarding</td>
<td>localhost:xxx zeigt Nginx default-page an</td>
<td>zeigt apache default-page an</td>
</tr>
<tr>
<td>Nginx neustarten</td>
<td>Nginx wird neugestartet</td>
<td>Nginx wird neugestartet</td>
</tr>
<tr>
<td>Firewall neustarten</td>
<td>Firewall startet neu</td>
<td>Firewall startet neu</td>
</tr>
<tr>
<td>Firewall aktivieren</td>
<td>Die Firewall wird eingeschaltet</td>
<td>Die Firewall wird eingeschaltet</td>
</tr>
</tbody>
</table><h3 id="monitoring---cadvisor">Monitoring - cAdvisor</h3>
<p>Mit folgendem Befehl kann man das Monitoring-Tool für Docker installieren:</p>
<pre><code>docker run -d --name cadvisor -v /:/rootfs:ro -v /var/run:/var/run:rw -v /sys:/sys:ro -v /var/lib/docker/:/var/lib/docker:ro -p 8080:8080 google/cadvisor:latest
</code></pre>
<p>Das Monitoring-Tool kann über localhost:8080 aufgerufen werden<br>
<img src="https://perrone.myqnapcloud.com:450/share.cgi/m300-monitoring-angel.png?ssid=02YbC2K&amp;fid=02YbC2K&amp;path=/&amp;filename=m300-monitoring-angel.png&amp;openfolder=normal&amp;ep=" alt="enter image description here"></p>
<h3 id="speicherproblem">Speicherproblem</h3>
<ol>
<li>cd C:\Program Files\Oracle\VirtualBox</li>
<li>VBoxManage modifyhd “C:\Users\Angel\VirtualBox VMs\m300\m300.vdi” --resize 20480</li>
<li>gparted herunterladen und in VirtualBox als Live CD einfügen</li>
<li><a href="https://askubuntu.com/questions/175174/why-cant-i-increase-the-size-of-sda1-using-gparted">https://askubuntu.com/questions/175174/why-cant-i-increase-the-size-of-sda1-using-gparted</a></li>
</ol>
<h3 id="github-1">GitHub</h3>
<p>Ich habe ein Repository namens “nginx” erstellt, in das ich nachher mit folgenden Befehlen mein Dockerfile publishe:</p>
<pre><code>git init #in the dir your file to push is located
git remote add origin https://github.com/zahnera/nginx.git
git add .
git commit -a -m "final commit"
git push origin master
</code></pre>
<h2 id="hilfreiche-commands">Hilfreiche Commands</h2>

<table>
<thead>
<tr>
<th>Command</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td><code>docker create</code></td>
<td>creates a container but does not start it.</td>
</tr>
<tr>
<td><code>docker rename</code></td>
<td>allows the container to be renamed.</td>
</tr>
<tr>
<td><code>docker run</code></td>
<td>creates and starts a container in one operation.</td>
</tr>
<tr>
<td><code>docker rm</code></td>
<td>deletes a container.</td>
</tr>
<tr>
<td><code>docker update</code></td>
<td>updates a container’s resource limits.</td>
</tr>
<tr>
<td><code>docker ps</code></td>
<td>shows running containers.</td>
</tr>
<tr>
<td><code>docker images</code></td>
<td>shows all images.</td>
</tr>
<tr>
<td><code>docker build</code></td>
<td>creates image from Dockerfile.</td>
</tr>
<tr>
<td><code>docker exec</code></td>
<td>connect to bash.</td>
</tr>
</tbody>
</table>
