---


---

<h1 id="modul-300-dokumentation">Modul 300 Dokumentation</h1>
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
<pre><code>git init #In Order, wo sich das File befindet
git remote add origin https://github.com/zahnera/lamp.git
git add .
git commit -a -m "änderungen"
git push origin master
</code></pre>
<h2 id="eigener-service-implementieren">Eigener Service implementieren</h2>
<p>Ich habe mich für eine LAMP-Installation entschieden.</p>
<p>LAMP steht für:</p>

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
<pre class=" language-bash"><code class="prism  language-bash">Vagrant.configure<span class="token punctuation">(</span>2<span class="token punctuation">)</span> <span class="token keyword">do</span> <span class="token operator">|</span>config<span class="token operator">|</span>
	config.vm.box <span class="token operator">=</span>  <span class="token string">"ubuntu/xenial64"</span>
	config.vm.network <span class="token string">"forwarded_port"</span>, guest:80, host:8080, auto_correct: <span class="token boolean">true</span>
	config.vm.synced_folder <span class="token string">"."</span>, <span class="token string">"/var/www/html"</span>
config.vm.provider <span class="token string">"virtualbox"</span>  <span class="token keyword">do</span> <span class="token operator">|</span>vb<span class="token operator">|</span>
	vb.memory <span class="token operator">=</span>  <span class="token string">"1024"</span>
end
config.vm.provision <span class="token string">"shell"</span>, inline: <span class="token operator">&lt;&lt;</span>-SHELL
	<span class="token function">sudo</span> <span class="token function">apt-get</span> update
	<span class="token function">sudo</span> <span class="token function">apt-get</span> <span class="token function">install</span> apache2 libapache2-mod-php7.0 php7.0 php7.0-mysql mysql-server
SHELL
end
</code></pre>
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

