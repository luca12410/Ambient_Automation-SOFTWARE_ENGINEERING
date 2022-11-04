/* [UC2] Creazione  nuovo  ambiente */

/*** BRIEF DESCRIPTION / IT / FULL DESCRIPTION FOLLOWS ***/

L’utente vuole creare un nuovo ambiente, per fare ciò deve interfacciarsi 
con il sistema attraverso il pannello fisso. Il sistema, dopo che l’utente 
ha effettuato l’accesso, chiede di inserire un nome per l'ambiente e salva la scelta fatta.  
Il sistema identifica l’utente come utente amministratore di quell'ambiente.  
Successivamente l’utente  definisce quali sono tutti gli oggetti smart a sua disposizione, 
aggiungendogli da una lista di possibili oggetti fornita dal sistema, e che vuole inserire
all’interno dell’ambiente stesso. Il sistema richiede o  di specificare qual è il contratto 
stipulato con i fornitori delle utility (es. corrente elettrica, gas metano) o il login nei 
loro portali, così da ricavare autonomamente tale informazione. Il sistema salva tutte le informazioni 
e permette di collegare un dispositivo principale  per il controllo remoto dell'ambiente tramite 
un’applicazione mobile.

/* ********************************** */ 
/********* FULL DESCRIPTION *********/
/* ********************************** */

* ID				: [UC2]
* LAN				: IT
* NAME				: Creazione nuovo ambiente

* PORTATA			: Sistema di gestione della domotica
* LIVELLO			: Obiettivo utente
* ATTORE PRIMARIO		: Utente Amministratore
* RIPETIZIONE			: Una tantum.


/**** STAKEHOLDER E INTERESSI ****/

* UTENTE AMMINISTRATORE: Vuole creare un nuovo ambiente, definendo quali sono gli oggetti    
smart che vuole inserire al suo interno. Vuole specificare quale contratto ha stipulato con 
ogni provider di ogni utility coinvolta nel sistema. Vuole specificare quali servizi di terze 
parti utilizzare per il funzionamento dell’ambiente. Vuole aggiungere un dispositivo di controllo remoto.

* SISTEMA DI GESTIONE DELLA DOMOTICA: Vuole salvare le scelte di configurazione dell’utente.

/**** PRE-CONDIZIONI ****/

*  L’utente amministratore dev’essere identificato ed autenticato

/**** POST-CONDIZIONI / GARANZIE DI SUCCESSO ****/

* Le scelte di configurazione dell’utente vengono registrate e messe in funzione. 
L’utente potrà allora proseguire nell’utilizzo del sistema.

/**** SCENARIO PRINCIPALE DI SUCCESSO ****/

1.  Il sistema verifica che le credenziali siano valide.
2.  Il sistema registra l’utente come utente Amministratore di quel nuovo ambiente.
3.  Il sistema chiede di inserire un nome per il nuovo ambiente.
4.  L’utente inserisce il nome che ha scelto per quell’ambiente.
5.  Il sistema fornisce una lista di oggetti smart con i quali è compatibile.
6.  L’utente seleziona dalla lista un oggetto smart che vuole inserire all’interno del nuovo ambiente, specificando il tipo, 
l’identificativo dell’oggetto e, opzionalmente, fornendo un nome personalizzato.
7.  Il sistema salva la configurazione degli oggetti presenti nell’ambiente.
8.  L’utente ripete i passi 6  e 7, il sistema esegue 8,  fino a che non indica che ha terminato. /SEE ISSUE RELATED
9.  Il sistema fornisce una lista di possibili providers per una specifica utility.
10. L’utente seleziona qual è il suo provider di riferimento.
11. L’utente inserisce le credenziali per accedere alla piattaforma del provider selezionato.
12. Il sistema salva le credenziali per gli accessi futuri e vi accede per recuperare le informazioni sul contratto.
* CICLO: Vengono ripetuti i passi 10, 11, 12, 13 per ogni utility.
13. Il sistema fornisce una lista di possibili servizi di terze parti da poter utilizzare.
14. L’utente seleziona qual è il suo servizio di riferimento.
15. L’utente inserisce le credenziali per accedere alla piattaforma del servizio selezionato.
16. Il sistema salva le credenziali per gli accessi futuri e vi accede per recuperare le informazioni.
17. Il sistema fornisce una schermata per l’associazione di tipologie di dispositivi mobile compatibili.
18. L'utente seleziona il dispositivo che vuole aggiungere.
* CICLO: Vengono ripetuti i passi 15, 16, 17, 18 per ogni servizio di terze parti. /SEE ISSUE
19. Il sistema salva la scelta e fornisce a quel dispositivo l’accesso al controllo dell’ambiente.
20. Il sistema mostra la schermata di Home.

/*** ESTENSIONI ***/

* Estensione globale A: In qualsiasi momento l’utente può tornare indietro nella fase di configurazione
  * a.1. Il sistema elimina le scelte fatte nell’ultimo passo e ripropone la situazione relativa al passo precedente.
	
* Estensione globale B: In qualsiasi momento l’utente può scegliere di annullare la procedura di configurazione del nuovo ambiente.
  * b.1. Il sistema elimina tutti i dati memorizzati fino a quel momento e mostra la schermata di Home.

* Passo 2, estensione A: le credenziali non vengono riconosciute come valide.
  * 2a.1. Il sistema propone di nuovo la schermata di accesso.
  * 2a.2. Ritorna al passo 1.

* Passo 5, estensione A: il sistema rileva che il nome scelto per quell’ambiente è un nome già utilizzato 
per un altro ambiente dello stesso utente.
  * 5a.1. Il sistema chiede di inserire di nuovo un nome per il nuovo ambiente, segnalando il problema.
  * 5a.2. Ritorna al passo 4.
	
* Passo 8, estensione A: il sistema rileva che l’identificativo fornito dall’utente non è valido.
   * 8a.1. Il sistema chiede di inserire di nuovo l’identificativo, segnalando il problema.

* Passo 8, estensione B:  Il sistema rileva che il nome scelto per quell’oggetto è un nome già utilizzato per 
un altro oggetto dello stesso ambiente.
   * 8b.1. Il sistema chiede di inserire di nuovo un nome per il nuovo oggetto, segnalando il problema.
	
* Passo 12, estensione A:  L’utente non desidera inserire le credenziali relative alla piattaforma del provider di riferimento.
   * 12a.1. Il sistema fornisce una schermata nella quale indicare tutte le informazioni richieste.
   * 12a.2. L’utente inserisce tutte le informazioni necessarie e conferma l’inserimento.
   * 12a.3. Il sistema salva la configurazione del contratto con quella determinata utility.

* Passo 13, estensione A: Il sistema rileva che le credenziali di accesso non sono valide.
   * 13a.1. Il sistema propone all’utente una schermata dove inserire di nuovo le credenziali, segnalando il problema.
   * 13a.2. L’utente inserisce le credenziali.
   * 13a.3. Il sistema verifica che le credenziali siano valide ed accede al servizio.

* Passo 13, estensione B: Il sistema rileva un fallimento della comunicazione con la piattaforma del provider.
   * 13b.1. Il sistema propone all’utente una schermata dove inserire di nuovo le credenziali, segnalando il problema.
   * 13b.2. L’utente inserisce le credenziali.
   * 13b.3. Il sistema verifica che le credenziali siano valide ed accede al servizio.

* Passo 17, estensione A: Il sistema rileva che le credenziali di accesso non sono valide.
   * 17a.1. Il sistema propone all’utente una schermata dove inserire di nuovo le credenziali, segnalando il problema.
   * 17a.2. L’utente inserisce le credenziali.
   * 17a.3. Il sistema verifica che le credenziali siano valide ed accede al servizio.

* Passo 17, estensione B: Il sistema rileva un fallimento nella comunicazione con la piattaforma del provider.
   * 17b.1. Il sistema propone all’utente una schermata dove inserire di nuovo le credenziali, segnalando il problema.
   * 17b.2. L’utente inserisce le credenziali.
   * 17b.3. Il sistema verifica che le credenziali siano valide ed accede al servizio.

* Passo 20, estensione A:  Il sistema rileva problematiche in fase di associazione con il dispositivo.
   * 20a.1. Il sistema ripropone la schermata per l’associazione con un dispositivo di controllo remoto.
	
	
/*** REQUISITI SPECIALI ***/

* r1. Interfaccia utente di tipo touch screen su un tablet in postazione fissa. Il testo deve essere visibile 
da una distanza massima di un metro.

* r2. Connessione ad internet costante e consistente. /SEE ISSUE

* r3. Internazionalizzazione della lingua sul testo visualizzato.

* r4. Regole di business inseribili nei passi da 10 a 13.

/*** VARIANTI TECNOLOGICHE / MISCELLANEA ***/

* None.
