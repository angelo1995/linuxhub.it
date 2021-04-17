---
title: '#howtobash - I file (Parte 1)'
published: 2019-04-12
layout: post
author: Mirko B.
author_github: mirkobrombin
tags:
  - bash
---
File fantastici e come copiarli<!--more--><p lang="it">Benvenuti al secondo appuntamento con <strong>#howtobash.</strong></p><p lang="it">Dopo aver mosso i primi passi all’interno del <strong>terminale</strong>, che a partire dall’inizio di questo magnifico viaggio (per chi se lo fosse perso, lo trovate in <a href="https://linuxhub.it/node/558">questa pagina</a>, dove verranno raccolte anche tutte le prossime puntate) è diventato un nostro nuovo e fedele alleato, oggi scopriamo come interagire con file che troviamo all’interno delle cartelle fra le quali abbiamo imparato a muoverci.</p><p lang="it">Quindi non perdiamo tempo in chiacchiere e cominciamo subito col nuovo episodio!</p><h2 lang="it">Un pizzico di “teoria”</h2><p lang="it">Nella scorsa puntata abbiamo sempre utilizzato i comandi del terminale con le forme seguenti:</p><p lang="it"><strong>comando</strong></p><p lang="it">come ad esempio:</p><pre><code>leo@leo-pavillion:$ ls</code></pre><p lang="it">oppure:</p><p lang="it"><strong>comando </strong><em>bersaglio</em></p><p lang="it">come ad esempio:</p><pre><code>leo@leo-pavillion:$ cd Documenti</code></pre><p lang="it">Tuttavia questi non sono gli unici modi di utilizzare i comandi. Vediamo quindi di fare un altro passo in avanti verso la padronanza del terminale. Quindi prima di partire chiariamo meglio i concetti di <strong>passaggio</strong>, <strong>argomento </strong>ed <strong>opzione</strong>:</p><ul>	<li>	<p lang="it">E’ possibile che vi sia già capitato di sentire l’espressione “<strong>passa</strong> <em>X </em>al comando Y”, e per quanto sia un concetto davvero molto semplice magari non è sempre così ovvio. Quindi per “<strong>passare</strong>” qualcosa ad un comando si intende fornire un’informazione che il comando andrà ad utilizzare in qualche maniera durante la sua esecuzione.<br />	Un (perchè vedremo più avanti che ce n’è più di uno) modo tipico con cui si passa qualcosa, tipicamente uno o più <strong>argomenti </strong>e/o una o più <strong>opzioni</strong>, ad un comando è “banalmente” scrivere l’informazione da passare dopo il nome del comando da eseguire.</p>	</li></ul><ul>	<li>	<p lang="it">Un <strong>argomento</strong> è ciò che sopra abbiamo indicato come <em>bersaglio</em> ovvero il file/cartella/variabile su cui il nostro comando andrà effettivamente ad agire.</p>	</li>	<li>	<p lang="it">Una&nbsp;<strong>opzione </strong>(spesso anche chiamate flag) è un’informazione che permette di <strong>cambiare</strong> il comportamento del programma e fargli eseguire operazioni diverse rispetto a quelle che farebbe se lanciato senza. Il modo con cui le opzioni vengono passate ad un comando è utilizzando il carattere “-” seguito da una lettera (e qui dovremo fare attenzione perchè spesso fra maiuscolo e minuscolo c’è differenza), oppure, nel caso di opzioni con nomi più lunghi di una lettera, si utilizza “--” seguito dal nome dell’opzione.</p>	</li></ul><p lang="it">Negli esempi che abbiamo visto fino ad oggi non abbiamo mai utilizzato opzioni di alcun tipo, ma oggi ne vedremo più di uno, motivo per cui queste premesse sono state necessarie. Direi che per oggi con la teoria possiamo fermarci qui, veniamo quindi ai nostri comandi del giorno!</p><h2 lang="it">Copiare un file</h2><p lang="it">Una delle operazioni più comuni che potremmo voler eseguire su un file è quella della semplice copia, per farlo ci basterà utilizzare il comando <em><strong>cp</strong></em> seguito , nell’ordine, da:</p><ul>	<li lang="it">file <em>da copiare</em> (eventualmente preceduto dal percorso)</li>	<li lang="it">percorso <em>in cui copiare </em>il file</li></ul><p lang="it">Vediamo un esempio per chiarire il tutto, supponiamo di trovarci nella cartella ~/Documenti e di volervi copiare un documento <em><strong>Modulo.pdf</strong></em> che abbiamo appena scaricato e che si trova nella cartella <em><strong>~/Scaricati</strong></em>.</p><p lang="it">Se vi ricordate le <a href="https://linuxhub.it/article/howtobash-comincia-il-viaggio#title3"><strong>regolette</strong></a> che abbiamo visto l’ultima volta, sapete che abbiamo diversi modi comporre il percorso “sorgente” e diversi modi per specificare la destinazione, qui ve ne riporto volutamente soltanto uno (quello a mio avviso un po’ più criptico per chi comincia, analizzandolo nei punti critici), ma vi invito a sperimentarne anche altri per comprendere meglio ciò che ci siamo detti l’altra volta. Quindi, per copiare il nostro file digitiamo:</p><pre><code>leo@pavillion:~/Documenti$ cp ../Scaricati/Modulo.pdf .</code></pre><p lang="it">Se ricordate bene o avete ripassato le regolette a questo punto dovrebbe essere evidente che ho scelto di costruire i percorsi a partire dal punto in cui mi trovo, ovvero andando a pescare il mio file andando su di un livello (utilizzando “.. “) e riscendendo le cartelle fino ad arrivare al file e ho specificato la destinazione dicendo “<em>qui</em>” utilizzando il “<strong>.</strong>” .</p><h2 lang="it">Copiare una cartella e il suo contenuto</h2><p lang="it">Ciò che abbiamo appena visto funziona benissimo se vogliamo maneggiare un <strong>singolo</strong> file, ma se volessimo copiare una <strong>cartella</strong> <strong>con</strong> <strong>tutto ciò che c’è dentro</strong>? Dovremmo forse copiare tutto quanto una cosa alla volta? La risposta, è ovviamente no. Se però avete provato ad utilizzare il comando <em><strong>cp</strong></em> utilizzando come argomento una cartella avrete ottenuto un <strong>errore</strong> simile a questo:</p><pre><code>cp: -r not specified; omitting directory 'Scaricati/'</code></pre><p lang="it">il quale ci informa del fatto che la cartella non verrà copiata perchè non abbiamo specificato <strong>-r </strong>.</p><p lang="it">Quest’ultima è infatti l’<strong>opzione </strong>che dobbiamo passare al comando cp per dirgli che vogliamo copiare una cartella ed il suo contenuto. Ne consegue che se, per esempio, partendo dalle condizioni di prima, volessimo copiare una cartella <em><strong>Moduli</strong></em>, posta all’interno della cartella <em><strong>~/Scaricati</strong></em>, nella nostra cartella <strong><em>~/Documenti</em></strong>, dovremmo utilizzare il comando:</p><pre><code>leo@pavillion:~/Documenti$ cp -r ../Scaricati/Moduli .</code></pre><h2 lang="it">Tips &amp; Tricks</h2><p lang="it">Ora che sappiamo come si copiano i file e le cartelle veniamo alla parte più interessante: un po’ di trucchetti per fare più alla svelta e meno fatica!</p><h3 lang="it">Copiare più file alla volta</h3><p lang="it"><span>Sono abbastanza certo che una grossa fetta di voi si sarà chiesta: “ma se volessi copiare più di un file per volta? Come devo fare?”. Niente di più semplice, infatti possiamo passare al comando cp tutti i file che vogliamo copiare in un colpo solo, basterà separarli con uno spazio e ricordandosi di lasciare per ultima la cartella di destinazione! Sempre riferendoci all’esempio di prima, immaginiamo di voler copiare Modulo1.pdf e Modulo2.odt presenti in ~/Scaricati nella cartella ~/Documenti. Il comando sarà:</span></p><pre><code>leo@leo-pavillion:~/Scaricati$ cp Modulo1.pdf Modulo2.odt ~/Documenti</code></pre><h3 lang="it">Copiare tutti i file insieme</h3><p lang="it"><span>Posso già sentire le proteste: “E se in una cartella ci sono 100 file? Devo scriverli tutti?”. </span></p><p lang="it"><span>Anche per questo problema (e tutti quelli che vi assomigliano) il nostro fantastico <strong>terminale</strong> ha già una soluzione, e questa soluzione si chiama </span><strong>wildcards </strong><span>, un set di armi potentissime che ci permetterà di fare cose anche molto complesse con pochissima fatica. </span></p><p lang="it"><span>Non entriamo oggi nei dettagli delle </span><strong>wildcards </strong><span>(non spiegherò cosa siano di preciso né tutto quello che possiamo farci; vi lascio con un po’ di curiosità per le prossime puntate :P )</span><strong> </strong><span>perché per poterle apprezzare come si deve, secondo me, è ancora un po’ presto. </span></p><p lang="it"><span>Quello che vorrei fare è introdurle una alla volta man mano che ci serviranno e fare un po’ di recap, e magari vederle tutte, una volta che saremo più esperti e potremo sfruttarle come si deve.</span></p><p lang="it"><span>La <strong>wildcard</strong> che vediamo oggi è “</span><strong>*</strong><span>” che ha il significato di “<em>tutto</em>”, e la utilizzeremo in accoppiata col comando cp per dirgli di copiare tutti i file in una cartella. </span></p><p lang="it"><span>Immaginiamo di aver scaricato un pack di 30 sfondi bellissimo che adesso si trova nella cartella <em><strong>~/Scaricati/Wallpapers</strong></em> e che vogliamo tenere in una cartella Sfondi che abbiamo creato dentro alla cartella <strong><em>~/Immagini</em></strong>, mettersi lì a copiare i file uno alla volta, o anche tutti insieme ma passando tutti i nomi al comando cp sarebbe un’operazione più che sufficientemente lunga e noiosa da farci perdere qualsiasi buona volontà possiamo aver raccolto per imparare ad utilizzare il terminale. Per effettuare l’operazione senza sbattimenti di sorta ci basterà ricorrere alla nostra nuova alleata, la wildcard * e, supponendo di trovarci all’interno della cartella Sfondi in cui vogliamo copiare i file, ci basterà dare il comando:</span></p><pre><code>leo@leo-pavillion:~/Immagini/Sfondi$ cp ~/Scaricati/Wallpapers/* .</code></pre><p dir="ltr">Anche per oggi direi che è tutto, v<span>i saluto e spero di avervi dato qualche spunto per iniziare ad usare in modo più piacevole il terminale. </span></p><p dir="ltr"><span>Se aveste dubbi o domande da porre trovate me e gli altri membri dello staff sul gruppo <strong>telegram</strong> della nostra community <a href="https://t.me/gentedilinux"><strong>/gentedilinux</strong></a>. </span></p><p dir="ltr"><span>Ci becchiamo col prossimo episodio di <strong>#howtobash</strong>!</span></p>