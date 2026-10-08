# Quando cambia una premessa, che cosa resta di una decisione?

**8 ottobre 2026 · HC Engineering Journal · 007**

*Dal laboratorio — collegare risposte, decisioni e revisioni senza perdere la storia.*

Una decisione può essere ragionevole quando viene presa e richiedere un riesame
quando cambia ciò su cui si fondava. Per una memoria aziendale, conservare il
risultato finale non basta: bisogna ritrovare le basi, chi ha deciso e che cosa
era disponibile in quel momento.

Nel precedente articolo abbiamo descritto la possibilità di contestare
un'informazione anche quando il sistema non aveva rilevato contraddizioni.
Ora abbiamo verificato un collegamento concreto, su un caso sintetico locale:
una contestazione può arrivare fino alla revisione dell'utilizzabilità di una
decisione, lasciando intatta la decisione storica.

## Tre operazioni che devono restare distinguibili

Nel caso sperimentale, una persona registra una risposta. Un atto distinto,
esercitato con il mandato previsto, la rende una decisione. Un terzo percorso
gestisce le attività di revisione: chi deve intervenire, che cosa manca e quando
riproporre la questione.

| Operazione | Che cosa registra | Che cosa non implica da sola |
|---|---|---|
| Rispondere | Un contenuto attribuito, con riferimenti e tempi | Che il contenuto sia già una decisione autorizzata |
| Decidere | Un atto con mandato, periodo e basi dichiarate | Che ogni affermazione su cui si fonda sia definitivamente vera |
| Completare una revisione | Che l'attività ha un esito registrato | Che l'incertezza sia stata risolta |

Questa separazione aiuta a contenere l'**authority bias**: la tendenza a trattare
l'autorità di chi parla come prova sufficiente della correttezza del contenuto.
Il sistema può registrare che una persona aveva titolo per decidere senza
trasformare quel mandato in una certificazione universale di verità.

## La sequenza che abbiamo verificato

La nuova decisione dichiara esplicitamente una base fattuale sintetica. Quando
quella base viene contestata, il sistema mostra un avviso: una contestazione
pendente non equivale ancora a una dichiarazione di falsità.

Quando il giudizio negativo viene adottato attraverso il percorso autorizzato,
la decisione originaria rimane nel registro. La vista integrata richiede però
un riesame e smette di proporla come utilizzabile.

Il revisore può anche concludere che non ci sono elementi sufficienti per
stabilire come siano andate le cose. L'attività A risulta completata con esito
indeterminato; l'attività B, che dipende dalla decisione, resta da riesaminare.
Chiudere una casella della lista non risolve automaticamente il problema.

Infine arriva una nuova risposta con una base alternativa. Anche qui occorre
un nuovo atto autorizzato: il sistema non ratifica automaticamente la vecchia
decisione perché è comparsa un'informazione più favorevole.

## Conservare i legami, oltre agli oggetti

Una base dichiarata è un legame esplicito. Un documento consultato come contesto
non diventa retroattivamente la causa di una decisione. Il caso verificato segue
soltanto i collegamenti dichiarati: non scopre tutte le dipendenze implicite nei
documenti aziendali.

È una parte concreta del problema della **topological coherence**: mantenere
coerenti i collegamenti fra fonti, valutazioni, decisioni e attività quando uno
dei loro elementi cambia. Qui il termine descrive l'obiettivo; non è una metrica
universale che abbiamo già misurato.

Anche la spiegazione ha una storia. Se ieri una conclusione dipendeva da A e B,
e oggi dipende da A e C, mantenere soltanto la spiegazione corrente impedirebbe
di ricostruire il ragionamento precedente. La conservazione delle versioni delle
prove resta quindi un requisito per il futuro motore generale di inferenza.
Il prototipo attuale verifica riferimenti e basi nel suo perimetro circoscritto.

## Che cosa dimostrano le prove

La dimostrazione integrata ha eseguito 39 operazioni e prodotto dieci viste.
Dieci confronti dopo riapertura e dieci ricostruzioni dagli eventi sono risultati
conformi alle attese definite per il caso. Prima della demo, 24 test finali erano
passati.

Abbiamo poi consolidato il codice: firme annotate, tipi espliciti per i contratti,
import e struttura più leggibili. I 24 test finali sono passati nuovamente; il
confronto di 39 comandi, dieci query e dieci viste in formato strutturato e leggibile
ha mantenuto gli stessi risultati della consegna precedente.

Questi numeri descrivono verifiche diverse, non un punteggio complessivo di
sicurezza o qualità. I tipi rendono più chiaro ciò che attraversa le interfacce;
non sostituiscono la validazione degli input e le prove sul comportamento.

## Lasciare aperta l'architettura, fissare le garanzie

Stiamo confrontando anche implementazioni esterne per individuare idee utili,
limiti e casi da trasformare in prove. Il lavoro richiede di distinguere una
funzionalità descritta nel README, una proposta ancora aperta e un comportamento
osservabile nel codice. La sola presenza di un test non prova che sia stato
eseguito nell'ambiente che stiamo valutando.

L'architettura complessiva resta aperta. Le scelte seguiranno le evidenze dei
test, i costi di adattamento e le esigenze operative. Restano invece ferme le
garanzie richieste: conservare le fonti e gli oggetti invalidati, distinguere i
due tempi e poter ricostruire gli atti e le basi storiche.

Abbiamo verificato una build locale da riga di comando, su dati sintetici, con
identità e mandati predisposti per l'esperimento. Non abbiamo ancora dimostrato
IAM aziendale, concorrenza su larga scala, ragionamento generale o una dashboard
interattiva. Il prossimo incremento proposto riguarda l'interfaccia di revisione,
che dovrà usare gli stessi contratti verificati.

La domanda guida resta concreta: **quando una decisione richiede un riesame,
possiamo ancora spiegare perché fu presa e che cosa è cambiato dopo?**
