# [UC2] Creazione  nuovo  ambiente

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
* CICLO: l'utente ripete il passo 6 e il sistema ripete il passo 7, fino a esaurimento delle operazioni.
8.  Il sistema fornisce una lista di possibili providers per una specifica utility.
9. L’utente seleziona qual è il suo provider di riferimento.
10. L’utente inserisce le credenziali per accedere alla piattaforma del provider selezionato.
11. Il sistema salva le credenziali per gli accessi futuri e vi accede per recuperare le informazioni sul contratto.
* CICLO: Vengono ripetuti i passi 8, 9, 10, 11 per ogni utility.
12. Il sistema fornisce una lista di possibili servizi di terze parti da poter utilizzare.
13. L’utente seleziona qual è il suo servizio di riferimento.
14. L’utente inserisce le credenziali per accedere alla piattaforma del servizio selezionato.
15. Il sistema salva le credenziali per gli accessi futuri e vi accede per recuperare le informazioni.
* CICLO: Vengono ripetuti i passi 14 e 15 per ogni servizio di terze parti.
16. Il sistema salva la scelta e fornisce a quel dispositivo l’accesso al controllo dell’ambiente.
17. Il sistema mostra la schermata di Home.

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
	
* Passo 6, estensione A: il sistema rileva che l’identificativo fornito dall’utente non è valido.
   * 6a.1. Il sistema chiede di inserire di nuovo l’identificativo, segnalando il problema.

* Passo 6, estensione B:  Il sistema rileva che il nome scelto per quell’oggetto è un nome già utilizzato per 
un altro oggetto dello stesso ambiente.
   * 6b.1. Il sistema chiede di inserire di nuovo un nome per il nuovo oggetto, segnalando il problema.

* Passo 9, estensione A:  L’utente non desidera inserire le credenziali relative alla piattaforma del provider di riferimento.
   * 9a.1. Il sistema fornisce una schermata nella quale indicare tutte le informazioni richieste.
   * 9a.2. L’utente inserisce tutte le informazioni necessarie e conferma l’inserimento.
   * 9a.3. Il sistema salva la configurazione del contratto con quella determinata utility.

* Passo 10, estensione A: Il sistema rileva che le credenziali di accesso non sono valide.
   * 10a.1. Il sistema propone all’utente una schermata dove inserire di nuovo le credenziali, segnalando il problema.
   * 10a.2. L’utente inserisce le credenziali.
   * 10a.3. Il sistema verifica che le credenziali siano valide ed accede al servizio.

* Passo 10, estensione B: Il sistema rileva un fallimento della comunicazione con la piattaforma del provider.
   * 10b.1. Il sistema propone all’utente una schermata dove inserire di nuovo le credenziali, segnalando il problema.
   * 10b.2. L’utente inserisce le credenziali.
   * 10b.3. Il sistema verifica che le credenziali siano valide ed accede al servizio.

* Passo 14, estensione A: Il sistema rileva che le credenziali di accesso non sono valide.
   * 14a.1. Il sistema propone all’utente una schermata dove inserire di nuovo le credenziali, segnalando il problema.
   * 14a.2. L’utente inserisce le credenziali.
   * 14a.3. Il sistema verifica che le credenziali siano valide ed accede al servizio.

* Passo 14, estensione B: Il sistema rileva un fallimento nella comunicazione con la piattaforma del provider.
   * 14b.1. Il sistema propone all’utente una schermata dove inserire di nuovo le credenziali, segnalando il problema.
   * 14b.2. L’utente inserisce le credenziali.
   * 14b.3. Il sistema verifica che le credenziali siano valide ed accede al servizio.

* Passo 16, estensione A:  Il sistema rileva problematiche in fase di associazione con il dispositivo.
   * 16a.1. Il sistema ripropone la schermata per l’associazione con un dispositivo di controllo remoto.
	
	
/*** REQUISITI SPECIALI ***/

* r1. Interfaccia utente di tipo touch screen su un tablet in postazione fissa. Il testo deve essere visibile 
da una distanza massima di un metro.

* r2. Connessione ad internet costante e consistente.

* r3. Internazionalizzazione della lingua sul testo visualizzato.

* r4. Regole di business inseribili nei passi da 10 a 13.

/*** VARIANTI TECNOLOGICHE / MISCELLANEA ***/

* None.
