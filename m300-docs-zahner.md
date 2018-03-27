---


---

<h1 id="modul-300-dokumentation">Modul 300 Dokumentation</h1>
<p>Modulbschreib: Platformübergreifende Services implementieren<br>
Autor: Angel Zahner</p>
<h2 id="toolumgebung-aufsetzen">10 - Toolumgebung Aufsetzen</h2>
<ol>
<li>GitHub registriert mit TBZ-Account</li>
<li>Git-bash installiert; Verzeichnis mit Beispielen erstellt; <a href="https://github.com/mc-b/devops">Git Repo</a> geclont</li>
<li>VirtualBox installiert und manuelle Linux-VM mit apache2 generiert</li>
<li>Vagrant heruntergeladen und installiert und atuomatisch eine Linux-VM generiert</li>
<li>Visual Studio Code installiert</li>
</ol>
<h2 id="prototyping">20 - Prototyping</h2>
<ol>
<li>Rest-Client: cURL getestet</li>
<li>Git-Hub in Betrieb genommen, Markdown-Docs gepublished</li>
<li>LAMP Aufgesetzt<br>
<code>sudo apt-get install mysql-server</code><br>
<code>sudo apt-get install apache2</code></li>
<li>Rest-Serverseitig: CGI-Script</li>
</ol>
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
</tbody>
</table>
