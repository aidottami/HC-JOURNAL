# Il grafo funziona. Ora deve farsi capire

13 ottobre 2026.

Nella demo del 12 ottobre abbiamo aperto la console, attraversato un caso di
revisione e osservato il grafo risultante. Vedere i collegamenti ha reso concreto
il lavoro delle ultime settimane. Ha anche mostrato il prossimo problema:
una persona non dovrebbe conoscere la struttura del database per capire
che cosa le stiamo chiedendo di chiarire.

Un identificativo tecnico è utile per ricostruire un'operazione. Come titolo di
una questione da sottoporre a un manager, dice molto poco. “Quale incarico aveva
questa persona ad aprile?” è già un punto di partenza migliore.

## Che cosa abbiamo verificato

La prova usava due documenti sintetici e risposte di estrazione registrate,
senza chiamate a modelli esterni durante la demo. Sette verifiche applicative
hanno coperto il percorso dalle fonti qualificate alla contestazione, al giudizio
e all'adozione con mandato, includendo rinvii, prerequisiti e letture storiche.

Abbiamo controllato separatamente la struttura persistita: due fonti, affermazioni
con polarità opposte e una contraddizione collegata ai due Statement. Uno Statement
rappresenta qui un'affermazione attribuita: resta collegato a ciò che la fonte ha
detto, anche quando qualcuno la contesta.

La presenza di una contraddizione nel grafo segnala un problema da valutare.
Non stabilisce quale fonte abbia ragione e non sostituisce un assessment,
cioè un giudizio attribuito e motivato. Nemmeno il giudizio coincide automaticamente
con una decisione autorizzata.

Le verifiche riguardano questo caso circoscritto. Non misurano la qualità generale
di un LLM, la capacità di rilevare ogni contraddizione o la scala di un archivio
aziendale. La sessione è stata arrestata con verifica della chiusura, conservando
le evidenze.

## Il difetto che la prima prova ha fatto emergere

Il primo tentativo si era fermato perché il controllo delle contraddizioni si
aspettava un attributo di polarità che il nostro percorso non forniva esplicitamente.
La polarità distingue, per esempio, “ha quell'incarico” da “non ha quell'incarico”.

Abbiamo corretto il contratto dei dati e verificato il cambiamento offline,
poi eseguito una nuova sessione autorizzata. Il tentativo interrotto è rimasto
conservato con il suo esito incerto. Il successo successivo non lo trasforma
retroattivamente in un successo.

È una lezione concreta di topological coherence, la coerenza dei collegamenti:
nodi e archi ben collegati servono, ma devono trasportare anche il significato
necessario. Una negazione persa lungo il percorso cambia la domanda che il
sistema sta cercando di risolvere.

## La dashboard deve spiegare la questione

Abbiamo quindi reso esplicito un requisito dell'MVP: una dashboard usabile.
Il primo prototipo dovrà mostrare insieme la domanda, le fonti che la motivano,
i periodi pertinenti e le azioni disponibili. Gli identificativi resteranno
accessibili nei dettagli tecnici, senza occupare il posto del contenuto.

Chi risponde deve capire se sta aggiungendo un chiarimento, esprimendo un giudizio
o adottando una decisione nell'ambito del proprio mandato. Dovrà anche poter
rimandare e capire se una questione dipende dalla soluzione di un'altra.

Questo aiuta a rendere visibile un rischio che chiamiamo authority bias:
confondere l'autorevolezza di chi parla con la correttezza di ciò che afferma.
Il ruolo può legittimare una decisione operativa; fonti, ragioni e possibilità
di contestazione devono comunque restare consultabili.

Anche il tempo deve essere leggibile. “Che cosa valeva ad aprile?” e “Che cosa
sapevamo ad aprile?” sono domande diverse. L'interfaccia dovrà aiutare a scegliere
la prospettiva, senza chiedere all'utente di studiare la bitemporalità.

## Un grafo da esplorare, una decisione da comprendere

Una visualizzazione più moderna può essere utile anche nelle dimostrazioni:
colori, gruppi, espansione dei collegamenti e accesso alle fonti possono rendere
visibili relazioni difficili da raccontare in una tabella.

La proposta è affiancarla al flusso di revisione, mostrando una porzione pertinente
del grafo attraverso i servizi applicativi, con i relativi filtri temporali e
permessi. La libreria grafica e la scelta fra 2D e 3D sono ancora da valutare.

Il prossimo passo è un prototipo interattivo su dati sintetici, da rivedere con
persone che non conoscono l'architettura. La domanda aperta è concreta: riescono
a capire perché una questione è emersa, su quali evidenze si basa e quale effetto
avrà la loro risposta? Finché non lo verifichiamo, la demo tecnica resta una tappa
verso il prodotto.
