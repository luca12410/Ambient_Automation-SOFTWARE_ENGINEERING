# [UC15]  IMPOSTAZIONE PIANI DI CONSUMO AMBIENTE 

/*** BRIEF DESCRIPTION / IT / NO FULL DESCRIPTION AVAILABLE ***/

Un utente vuole impostare un piano di consumo per l’ambiente. Il sistema 
verifica che sia in possesso dei privilegi adeguati. L’utente seleziona dal 
menù del sistema la voce per accedere ai piani di consumo e sceglie di impostare 
il piano di consumo per l’ambiente. Il sistema fornisce un’interfaccia così da poter 
personalizzare il piano ( indicando quale fascia di prezzo rispettare, quante ore al 
massimo può funzionare, quale sia la strategia da utilizzare nel caso in cui si 
stia andando verso il superamento della soglia stabilita nel contratto con il provider). 


/**** FULL DESCRIPTION ****/

/* ********************************** */ 
/********* FULL DESCRIPTION *********/
/* ********************************** */

* ID				: [UC15]
* LAN				: IT
* NAME				: Impostazione piani di consumo dell'ambiente

* PORTATA			: Sistema di gestione della domotica
* LIVELLO			: Obiettivo utente
* ATTORE PRIMARIO		: Utente con permessi adeguati
* RIPETIZIONE			: Una tantum.

/**** STAKEHOLDER E INTERESSI ****/

* UTENTE CON PERMESSI ADEGUATI: vuole stabilire un piano di consumo per l'ambiente, specificando limitazioni relative alla spesa o al consumo rispetto a una o più utility. Inoltre, l'utente intende stabilire delle policy sulle procedure da utilizzare in specifiche situazioni di consumo elevato. Tali policy saranno applicate agli oggetti presenti nell'ambiente in base a un sistema gerarchico definito attraverso priorità.

* SISTEMA DI GESTIONE DELLA DOMOTICA: vuole salvare ed applicare il piano di consumo impostato.

/**** PRE-CONDIZIONI ****/

*  L’utente dev'essere autenticato ed in possesso relativo all'impostazione di un piano di consumo per l'ambiente.
* Nel sistema devono già essere impostate utility con i relativi contratti.

/**** POST-CONDIZIONI / GARANZIE DI SUCCESSO ****/

* I piani di consumo vengono registrati.
* Le violazioni ai limiti di consumo imposti vengono correttamente rilevate dal sistema.
* Le policy e le procedure impostate dall'utente in caso di violazione dei limiti vengono correttamente applicate.

/**** SCENARIO PRINCIPALE DI SUCCESSO ****/

1. L'utente inizia la procedura per l'impostazione di un nuovo piano.
2. L'utente inserisce il nome che ha scelto per quel piano di consumo.
3. L'utente sceglie una o più utility da coinvolgere nel piano.
4. L'utente imposta una regola globale sul consumo o sulla spesa totale dell'ambiente, relativa ad una sola utility, stabilendo contestualmente, tra un pool di azioni, la procedura relativa alla condizione data.
* CICLO: Il passo 4 viene ripetuto per ciascuna regola che l'utente vuole creare.
5. L'utente crea gruppo, vi aggiunge oggetti tra quelli presenti nell'ambiente e ne imposta la priorità attraverso codici colori predefiniti o personalizzati.
* CICLO: il passo 5 viene ripetuto per ciascun gruppo che l'utente crea.
6. L'utente imposta una regola globale sul consumo o sulla spesa relativa ad un singolo gruppo e ad una sola utility, stabilendo contestualmente, tra un pool di azioni disponibili, la procedura relativa alla condizione data.
* CICLO: Il passo 6 viene ripetuto per ciascuna regola che l'utente vuole creare.
7. L'utente imposta una regola di attivazione, a partire da una serie di criteri dati, che indica la condizione sotto la quale il piano di consumo si attiva automaticamente. 

/*** ESTENSIONI ***/

* Estensione globale A: in qualsiasi momento l'utente può tornare indietro durante la fase di configurazione del nuovo piano.
  * a.1. Il sistema elimina le scelte fatte nell’ultimo passo e ripropone la situazione relativa al passo precedente.
  
* Estensioni globali B: in qualsiasi momento l'utente può scegliere di annullare la procedura di configurazione del nuovo piano di consumo.
  * b.1. Il sistema elimina tutti i dati memorizzati fino a quel momento e mostra la schermata di Home.
  
* Passo 2, estensione A: Il sistema rileva che il nome scelto per quel piano di consumo è un nome già utilizzato per un altro nello stesso ambiente.
  * 2.a.1. Il sistema chiede di inserire di nuovo un nome per il piano di consumo, segnalando il problema.
  
* Passo 4, estensione A: l'utente imposta una condizione per una regola di consumo che va in contraddizione con le limitazioni date dal contratto della utility coinvolta.
  * 4.a.1. Il sistema chiede all'utente se è sicuro di procedere con l'impostazione della regola, mettendo in evidenza la contraddizione con le regole di contratto.
  * 4.a.2. L'utente fornisce una risposta "Sì" o "No".
